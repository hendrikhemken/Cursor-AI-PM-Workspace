---
name: hook-creator
description: Creates Cursor hooks for tool control, logging, and automation. Use ONLY when user explicitly requests 'create hook', 'new hook', 'block MCP tool', or 'hook for [tool]'. Covers all hook types (PreToolUse, PostToolUse, UserPromptSubmit, SessionStart, Stop, etc.) with focus on MCP tool blocking and permission control. NOT for general use - requires explicit user request.
---

# Hook Creator
*Create Cursor Hooks for Tool Control & Automation*

---

## ⚠️ IMPORTANT: Claude Code Restart Required!

**After every hook update, Claude Code MUST be restarted:**
- Hooks are only loaded at startup
- Changes during the session are NOT applied
- **→ Completely quit and restart Claude Code!**

**Debugging:**
- `/hooks` command shows registered hooks
- `claude --debug` for detailed execution logs

---

## 🎯 Core Workflow

### 1. Understand User Intent

**Ask:**
- **What should the hook do?** (Block, Log, Transform, Validate?)
- **For which tools?** (Specific tool or pattern?)
- **When to trigger?** (Before tool call, after, on prompt submit, etc?)

### 2. Choose Hook Event Type

**9 Hook Events available:**

| Event | When | Use Cases |
|-------|------|-----------|
| **PreToolUse** | Before tool execution | Block tools, validate params, permission control |
| **PostToolUse** | After tool success | Log results, validate output, post-process |
| **UserPromptSubmit** | Before Claude processes prompt | Filter/block prompts, inject context |
| **SessionStart** | On startup/resume | Setup env vars, load context, init state |
| **Stop** | When agent finishes | Validate completion, run checks |
| **SubagentStop** | When Task completes | Validate subagent output |
| **Notification** | On permission requests | Custom permission handling |
| **PreCompact** | Before context compaction | Save state, backup data |
| **SessionEnd** | On session end | Cleanup, persist state |

**Most common use cases:**
- **MCP Tool Blocking:** PreToolUse + Permission Decision
- **Logging:** PostToolUse
- **Validation:** PreToolUse or PostToolUse
- **Context Injection:** SessionStart or UserPromptSubmit

### 3. Build Hook Configuration

**Config Location:**
- User: `~/.claude/settings.json` (user-wide hooks)
- Project: `.claude/settings.json` (project-specific hooks)
- Project Local: `.claude/settings.local.json` (local, not committed)
- Managed: OS-specific managed-settings.json (enterprise)

**Basic Structure:**
```json
{
  "hooks": {
    "EventName": [
      {
        "matcher": "ToolPattern",
        "hooks": [
          {
            "type": "command",
            "command": "your-command-here",
            "timeout": 60
          }
        ]
      }
    ]
  }
}
```

**Key Fields:**
- `matcher`: Regex pattern for tool names (PreToolUse/PostToolUse only)
- `type`: Currently only "command" supported
- `command`: Bash command to execute
- `timeout`: Optional limit in seconds (default: 60)

### 4. Choose Control Method

**Exit Codes:**
- **0:** Success (output to user/Claude depending on event)
- **2:** Blocking error (stderr fed to Claude)
- **Other:** Non-blocking error (stderr to user, continues)

**JSON Output (Advanced):**
```json
{
  "continue": true,
  "stopReason": "string",
  "suppressOutput": false,
  "systemMessage": "string",
  "hookSpecificOutput": {}
}
```

**Permission Decisions (PreToolUse only):**
```json
{
  "hookSpecificOutput": {
    "hookEventName": "PreToolUse",
    "permissionDecision": "allow|deny|ask",
    "permissionDecisionReason": "Explanation for user/Claude"
  }
}
```

---

## 🔥 Common Patterns

### Pattern 1: Block MCP Tool (Simple)

**Use Case:** Block Jira delete operations

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "mcp__MCP_DOCKER__jira_delete_issue",
        "hooks": [
          {
            "type": "command",
            "command": "echo '{\"hookSpecificOutput\": {\"hookEventName\": \"PreToolUse\", \"permissionDecision\": \"deny\", \"permissionDecisionReason\": \"⚠️ Jira Delete is disabled. Please delete manually in Jira.\"}}'"
          }
        ]
      }
    ]
  }
}
```

### Pattern 2: Block Multiple Tools (Regex)

**Use Case:** Block all delete operations across Jira & Confluence

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "mcp__MCP_DOCKER__.*(delete|remove).*",
        "hooks": [
          {
            "type": "command",
            "command": "echo '{\"hookSpecificOutput\": {\"hookEventName\": \"PreToolUse\", \"permissionDecision\": \"deny\", \"permissionDecisionReason\": \"Delete operations are disabled for security reasons.\"}}'"
          }
        ]
      }
    ]
  }
}
```

### Pattern 3: Log Tool Usage (PostToolUse)

**Use Case:** Track all Write operations

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo \"[$(date)] Write: $TOOL_INPUT\" >> ~/claude-write-log.txt"
          }
        ]
      }
    ]
  }
}
```

### Pattern 4: Validate File Operations

**Use Case:** Block writes to sensitive directories

```bash
#!/bin/bash
# Save as: .claude/hooks/validate-write.sh

# Read stdin JSON
INPUT=$(cat)
FILE_PATH=$(echo "$INPUT" | jq -r '.tool_input.file_path // empty')

# Block sensitive paths
if [[ "$FILE_PATH" == *".env"* ]] || [[ "$FILE_PATH" == *".git/"* ]]; then
  echo '{
    "hookSpecificOutput": {
      "hookEventName": "PreToolUse",
      "permissionDecision": "deny",
      "permissionDecisionReason": "⚠️ Write access to sensitive files blocked!"
    }
  }'
  exit 0
fi

# Allow
echo '{
  "hookSpecificOutput": {
    "hookEventName": "PreToolUse",
    "permissionDecision": "allow"
  }
}'
```

**Hook Config:**
```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "\"$CLAUDE_PROJECT_DIR\"/.claude/hooks/validate-write.sh"
          }
        ]
      }
    ]
  }
}
```

### Pattern 5: Inject Context on SessionStart

**Use Case:** Load project-specific context at startup

```json
{
  "hooks": {
    "SessionStart": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo '{\"hookSpecificOutput\": {\"hookEventName\": \"SessionStart\", \"additionalContext\": \"📋 Project: Company Website. Stack: Vanilla HTML/CSS/JS. No frameworks!\"}}'"
          }
        ]
      }
    ]
  }
}
```

### Pattern 6: Persist Environment Variables (SessionStart)

**Use Case:** Setup NVM on startup

```bash
#!/bin/bash
# Read stdin to avoid blocking
cat > /dev/null

if [ -n "$CLAUDE_ENV_FILE" ]; then
  # Capture env before
  ENV_BEFORE=$(export -p | sort)

  # Load NVM
  source ~/.nvm/nvm.sh
  nvm use 20

  # Capture env after & write diff
  ENV_AFTER=$(export -p | sort)
  comm -13 <(echo "$ENV_BEFORE") <(echo "$ENV_AFTER") >> "$CLAUDE_ENV_FILE"
fi
```

---

## 🛡️ Security Best Practices

**ALWAYS:**
- ✅ **Validate input data** (especially file paths)
- ✅ **Quote shell variables:** `"$VAR"` not `$VAR`
- ✅ **Block path traversal:** Check for `..` in paths
- ✅ **Use absolute paths** or `$CLAUDE_PROJECT_DIR`
- ✅ **Skip sensitive files:** `.env`, `.git/`, keys, credentials
- ✅ **Test in safe env first** before production

**NEVER:**
- ❌ Trust unvalidated input
- ❌ Execute arbitrary user input directly
- ❌ Access files outside project scope
- ❌ Expose secrets or credentials
- ❌ Skip error handling

---

## 📋 MCP Tool Naming Pattern

**Format:** `mcp__<server-name>__<tool-name>`

**Examples:**
```
mcp__MCP_DOCKER__jira_create_issue
mcp__MCP_DOCKER__jira_delete_issue
mcp__MCP_DOCKER__confluence_create_page
mcp__memory__create_entities
mcp__filesystem__read_file
```

**Matcher Patterns:**
```json
"mcp__MCP_DOCKER__jira_delete_.*"      // All Jira deletes
"mcp__MCP_DOCKER__.*_delete_.*"        // All deletes from MCP_DOCKER
"mcp__.*__delete.*"                     // All delete ops from any MCP server
"mcp__memory__.*"                       // All memory server tools
```

---

## 🔧 Environment Variables

**Available in ALL hooks:**
- `CLAUDE_PROJECT_DIR` - Absolute project root path
- `CLAUDE_CODE_REMOTE` - "true" if remote env, else not set

**SessionStart only:**
- `CLAUDE_ENV_FILE` - File path for persisting env vars

**Hook Input (stdin JSON):**
```json
{
  "session_id": "string",
  "transcript_path": "string",
  "cwd": "string",
  "hook_event_name": "string",
  "tool_name": "string",        // PreToolUse/PostToolUse
  "tool_input": {},             // PreToolUse/PostToolUse
  "tool_output": {},            // PostToolUse
  "user_prompt": "string"       // UserPromptSubmit
}
```

---

## 📊 Exit Code Behavior by Event

| Hook Event | Exit 0 | Exit 2 | Other |
|-----------|--------|--------|-------|
| **PreToolUse** | Success (output to Claude) | Block tool + stderr to Claude | Non-blocking error |
| **PostToolUse** | Success (output to Claude) | Stderr to Claude (tool ran) | Non-blocking error |
| **UserPromptSubmit** | Add to context | Block + erase prompt | Show error |
| **SessionStart** | Add to context | Show error | Show error |
| **Stop** | Show to user | Block + stderr to Claude | Show error |
| **Notification** | Show to user | Show error | Show error |

---

## 🎯 Step-by-Step Implementation

### Step 1: Design Hook Logic

**Questions to answer:**
1. What event should trigger? (PreToolUse, PostToolUse, etc.)
2. Which tools to match? (Specific or pattern?)
3. What action to take? (Block, log, validate, transform?)
4. What control method? (Exit code, JSON, permission decision?)

### Step 2: Write Hook Command/Script

**For simple hooks:**
- Inline command in settings.json

**For complex logic:**
- Create script in `.claude/hooks/` directory
- Use `$CLAUDE_PROJECT_DIR` to reference it
- Make executable: `chmod +x .claude/hooks/script.sh`

### Step 3: Test Hook Configuration

**Validation checklist:**
- [ ] JSON syntax valid (use `jq` or VS Code)
- [ ] Matcher pattern correct (case-sensitive!)
- [ ] Script executable (if using external script)
- [ ] Quotes escaped properly in commands
- [ ] Security checks in place

### Step 4: Add to settings.json

**Read existing config:**
```bash
cat ~/.claude/settings.json
# or
cat .claude/settings.json
```

**Merge with new hook** (don't overwrite existing hooks!)

### Step 5: Restart Claude Code

**⚠️ CRITICAL: Hook changes are ONLY loaded at startup!**

**After update:**
1. Save settings.json
2. **Completely quit Claude Code**
3. Restart Claude Code
4. Run `/hooks` to verify registration

### Step 6: Test & Debug

**Verify registration:**
```bash
/hooks
```

**Test hook execution:**
- Trigger the tool/event
- Check expected behavior
- Review debug logs if needed: `claude --debug`

**Common issues:**
- Matcher doesn't match (case-sensitive!)
- Script not executable
- Unescaped quotes in JSON
- Wrong event type

---

## 📚 Hook Type Reference

### PreToolUse

**Triggers:** After Claude creates tool parameters, before tool execution

**Use Cases:**
- Block tools based on parameters
- Validate input
- Request user permission
- Log tool calls

**Input (stdin JSON):**
```json
{
  "tool_name": "Write",
  "tool_input": {
    "file_path": "/path/to/file",
    "content": "..."
  }
}
```

**Output Options:**
1. Exit 2 → Block tool
2. JSON with `permissionDecision: "deny"` → Block tool
3. JSON with `permissionDecision: "allow"` → Bypass permission system
4. Exit 0 → Continue normally

---

### PostToolUse

**Triggers:** Immediately after tool completes successfully

**Use Cases:**
- Log tool results
- Validate output
- Post-process data
- Trigger follow-up actions

**Input (stdin JSON):**
```json
{
  "tool_name": "Write",
  "tool_input": {...},
  "tool_output": "Success message or data"
}
```

**Output Options:**
1. Exit 0 → Show output to Claude
2. Exit 2 → Show error to Claude (tool already ran)
3. JSON with `decision: "block"` → Prevent further processing

---

### UserPromptSubmit

**Triggers:** When user submits prompt, before Claude processes

**Use Cases:**
- Filter/sanitize prompts
- Block certain requests
- Inject additional context
- Transform user input

**Input (stdin JSON):**
```json
{
  "user_prompt": "User's submitted text"
}
```

**Output Options:**
1. Exit 0 with stdout → Add to context
2. Exit 2 → Block prompt, erase it
3. JSON with `decision: "block"` → Block prompt

---

### SessionStart

**Triggers:** On Claude Code startup, resume, /clear, or compact

**Use Cases:**
- Load project context
- Setup environment variables
- Initialize state
- Run project checks

**Matchers Available:**
- `startup` - Fresh startup
- `resume` - From resume command
- `clear` - From /clear
- `compact` - From auto/manual compact

**Input (stdin JSON):**
```json
{
  "session_id": "...",
  "matcher": "startup|resume|clear|compact"
}
```

**Output Options:**
1. Exit 0 with stdout → Add to context
2. Write to `$CLAUDE_ENV_FILE` → Persist env vars

**Persist Environment Variables:**
```bash
if [ -n "$CLAUDE_ENV_FILE" ]; then
  echo 'export MY_VAR=value' >> "$CLAUDE_ENV_FILE"
fi
```

---

### Stop / SubagentStop

**Triggers:** When agent/subagent finishes responding

**Use Cases:**
- Validate completion
- Run final checks
- Generate reports
- Cleanup temp files

**Output Options:**
1. Exit 0 → Show to user
2. Exit 2 → Block stop, continue agent
3. JSON with `decision: "block"` → Prevent stopping

---

### Notification

**Triggers:** When Claude Code sends notifications (permission requests, idle prompts)

**Use Cases:**
- Custom permission handling
- Log permission requests
- Auto-approve certain tools

**Output Options:**
1. Exit 0 → Show to user
2. Exit 2 → Show error

---

### PreCompact

**Triggers:** Before Claude Code compacts conversation

**Matchers Available:**
- `manual` - User ran /compact
- `auto` - Auto-compact (context full)

**Use Cases:**
- Save conversation state
- Backup important data
- Log compact events

---

### SessionEnd

**Triggers:** When Claude Code session ends

**Use Cases:**
- Cleanup temp files
- Persist session state
- Generate session reports

---

## 🎨 Output to User After Hook Creation

**Always include:**

1. ✅ **Hook config snippet** (copy-pasteable JSON)
2. ✅ **Where to add** (hooks.json location)
3. ✅ **Restart reminder:** "⚠️ Claude Code MUST be restarted!"
4. ✅ **Verification command:** `/hooks` to check registration
5. ✅ **Test instructions** (how to trigger & verify)

**Template:**
```markdown
## ✅ Hook created!

**Config:**
```json
[Hook JSON]
```

**Location:** `~/.claude/settings.json` (user-wide) or `.claude/settings.json` (project-specific)

**⚠️ IMPORTANT: Claude Code MUST be restarted!**
1. Save settings.json
2. Completely quit Claude Code
3. Restart
4. Run `/hooks` to verify

**Test:**
[How to trigger this hook]
```

---

## 🧪 Testing Checklist

Before finalizing:

- [ ] JSON syntax valid
- [ ] Matcher pattern matches intended tools (case-sensitive!)
- [ ] Security checks in place (validate paths, block sensitive files)
- [ ] Proper quoting in shell commands
- [ ] Script executable (if external script)
- [ ] Tested in safe environment
- [ ] Documented what hook does
- [ ] User knows to restart Claude Code

---

## 🔍 Debugging Tips

**Hook not triggering?**
1. Run `/hooks` - is it registered?
2. Check matcher pattern (case-sensitive!)
3. Check event type (PreToolUse vs PostToolUse?)
4. Did you restart Claude Code?

**Hook failing?**
1. Run `claude --debug` for detailed logs
2. Check script permissions (executable?)
3. Check shell command quoting
4. Test script standalone: `bash script.sh < test-input.json`

**Permission decision not working?**
1. Only works with PreToolUse!
2. JSON format correct?
3. Proper escaping in command string?

---

## 📖 References

**Official Docs:**
- 🔥 [Claude Code Hooks Documentation](https://docs.claude.com/en/docs/claude-code/hooks.md)
- 🔥 [Settings Documentation](https://docs.claude.com/en/docs/claude-code/settings.md)

**Complete Reference:**
- 📚 `reference/hooks-reference.md` - Complete Hooks Documentation (load on-demand only!)

**Project:**
- `.claude/hooks/` - Project hook scripts
- `~/.claude/settings.json` - User hooks (user-wide)
- `.claude/settings.json` - Project hooks (project-specific)
- `.claude/settings.local.json` - Local project hooks (not committed)

---

*Hook Creator Skill - Cursor AI PM Operating System*
*For internal use only - not part of public system*
