---
name: skill-creator
description: Create new Cursor Skills efficiently. Use when user says "create a skill", "new skill for...", "skill that does...", or asks how to structure a skill. Focuses on lean, core workflow with proper CLAUDE.md registration.
---

# Skill Creator

*Create focused, minimal Cursor Skills for the AI PM Operating System*

## When to Use

- User wants to create a new Skill
- User asks "how do I create a skill for..."
- User mentions "skill" + specific use case

---

## 🎯 Key Principles

**Context is a Public Good:**
- Keep SKILL.md **< 500 lines** (split into supporting files if bigger)
- Every token competes with conversation history
- Only add what the LLM doesn't already know

**Description is Critical:**
- ALWAYS write in **third person** ("Processes Excel files", not "I can help...")
- Include **what it does + when to use it**
- List **specific trigger keywords** (file types, scenarios, terms)

**Supporting Documents:**
- Split complex skills into SKILL.md + supporting files
- **IMPORTANT:** Supporting files are NOT auto-loaded!
- SKILL.md must explicitly instruct to read supporting files
- Keep references **one level deep** (no nested references!)

**Workflows & Examples:**
- Complex tasks → provide **checklist** the LLM can copy & check off
- Show **input → output examples** (like regular prompting)
- Use **feedback loops** for quality-critical tasks (validate → fix → repeat)

**Anti-Patterns to Avoid:**
- ❌ Vague descriptions ("helps with stuff")
- ❌ Nested references (SKILL.md → advanced.md → details.md)
- ❌ Assuming supporting files are auto-loaded
- ❌ Time-sensitive info ("before August 2025...")
- ❌ Inconsistent terminology (mix "field", "box", "element")
- ❌ Too many options without clear default

---

## Core Workflow

### 1. Clarify Use Case

Ask user:
- **What's the core task?** (1 sentence)
- **When should it trigger?** (specific keywords/scenarios)
- **Supporting files needed?** (templates, guides, references)
- **🔒 Public or Private Skill?**
  - **Public:** Listed in CLAUDE.md, synced to GitHub (shareable)
  - **Private:** In .gitignore, NOT in CLAUDE.md (personal data safe)

### 2. Design Skill Structure

**Minimal by default:**
```
.claude/skills/[skill-name]/
└── SKILL.md
```

**Add supporting files only if needed:**
```
.claude/skills/[skill-name]/
├── SKILL.md           # Main skill file (< 500 lines)
├── TEMPLATES.md       # Templates for outputs
├── GUIDE.md           # Detailed how-to guide
└── reference/         # Reference materials
    └── best-practices.md
```

**When to split:**
- SKILL.md exceeds 500 lines
- Complex domain knowledge needed
- Reusable templates exist
- Multiple workflow variations

### 3. Create SKILL.md

**Basic Structure:**
```yaml
---
name: [skill-name]
description: [What it does + When to use it. THIRD PERSON. Specific triggers!]
---

# [Skill Name]

## When to Use
[Specific triggers and scenarios]

## Instructions
[Step-by-step workflow - keep it to 3-7 steps max]

## Examples
[1-2 concrete examples showing input → output]
```

**With Supporting Files Structure:**
```yaml
---
name: [skill-name]
description: [What it does + When to use it. THIRD PERSON. Specific triggers!]
---

# [Skill Name]

## When to Use
[Specific triggers and scenarios]

---

## 📚 Supporting Files

**Read these files when needed during the workflow:**

| File | Purpose | When to Read |
|------|---------|--------------|
| [TEMPLATES.md](TEMPLATES.md) | Output templates | Before creating deliverables |
| [GUIDE.md](GUIDE.md) | Detailed instructions | For complex scenarios |
| [reference/best-practices.md](reference/best-practices.md) | Domain knowledge | When applying best practices |

---

## Instructions

### 1. [First Step]
[Instructions...]

### 2. [Step That Needs Templates]
**→ Read [TEMPLATES.md](TEMPLATES.md) first**
[Then proceed with...]

### 3. [Step That Needs Guide]
**→ For complex cases, read [GUIDE.md](GUIDE.md)**
[Instructions...]

## Examples
[1-2 concrete examples showing input → output]
```

**Description Requirements:**
- ✅ **Third person** ("Processes PDFs", not "I can help process PDFs")
- ✅ **Specific triggers** (file types, keywords, scenarios)
- ✅ **What + When** (functionality + use cases)
- ✅ **Max 1024 chars** (concise!)

### 4. Register in CLAUDE.md (PUBLIC Skills only)

**This is the critical step for skill discovery!**

Add to `## 📋 Available Skills` section in `CLAUDE.md`:

```markdown
**[Skill Name]** → `.claude/skills/[skill-name]/SKILL.md`
Use when: [trigger keywords], [scenarios], [file types], or [specific context].
```

**Example Entry:**
```markdown
**User Stories** → `.claude/skills/user-stories/SKILL.md`
Use when: Writing user stories from PRDs, breaking down epics, sprint planning, backlog work, bug tickets, or acceptance criteria.
```

**With special notes (if needed):**
```markdown
**User Context** → `.claude/skills/user-context/SKILL.md`
Use when: First-time setup, onboarding, updating company/team info, new job, or "configure my context."
**Note:** This skill updates the User Context section at the bottom of this file.
```

### 5. Configure Public/Private Mode

**If PRIVATE Skill:**
1. **Add to `.gitignore`:**
   ```
   # Private Skills (personal data, not synced to GitHub)
   .claude/skills/[skill-name]/
   ```
2. **DO NOT add to `CLAUDE.md`** (skill stays local only)

**If PUBLIC Skill:**
1. **Skip .gitignore** (will be synced to GitHub)
2. **Add to `CLAUDE.md`** (step 4 above)

### 6. Test & Validate

**Functionality Test:**
- Test: Start a new conversation and say something matching the description
- Check: Does the LLM recognize the skill should be used?
- Debug: If not triggering → check description specificity in CLAUDE.md
- Refine: Remove unnecessary steps, keep it lean

**Supporting Files Test:**
- Test: Does the LLM read supporting files when instructed?
- Check: Are the file paths correct (relative paths)?
- Debug: If not reading → make the instruction more explicit in SKILL.md

**Validation Checklist:**

**For PRIVATE Skills:**
- ✅ Skill folder added to `.gitignore`
- ✅ Skill NOT listed in `CLAUDE.md`

**For PUBLIC Skills:**
- ✅ Skill NOT in `.gitignore` (will sync to GitHub)
- ✅ Skill added to `CLAUDE.md` → `## 📋 Available Skills` section
- ✅ Description is specific with trigger keywords
- ✅ Path to SKILL.md is correct

---

## 📖 Supporting Files: Detailed Guide

### Why Supporting Files?

Skills often need more context than fits in 500 lines:
- **Templates** for consistent outputs
- **Guides** for complex workflows
- **Reference materials** for domain knowledge
- **Examples** for edge cases

### Critical Rule: Explicit Loading

**⚠️ Supporting files are NOT automatically loaded!**

The LLM only reads SKILL.md initially. Supporting files must be:
1. Referenced with relative paths in SKILL.md
2. Explicitly instructed to be read at the right workflow step

### Pattern 1: Read Before Starting

Use when supporting files contain essential context:

```markdown
## Instructions

**Before starting, read:**
- [GUIDE.md](GUIDE.md) - Complete workflow details
- [TEMPLATES.md](TEMPLATES.md) - Output templates

### 1. [First Step]
...
```

### Pattern 2: Read On-Demand

Use when supporting files are only needed for specific steps:

```markdown
## Instructions

### 1. Gather Requirements
[Instructions...]

### 2. Create Output
**→ Read [TEMPLATES.md](TEMPLATES.md) for the correct format**
[Then create the output using the template...]

### 3. Handle Edge Cases
**→ If complex scenario, read [GUIDE.md](GUIDE.md) for details**
[Instructions...]
```

### Pattern 3: Conditional Reading

Use when different files apply to different scenarios:

```markdown
## Instructions

### 1. Identify Workflow Type

**Workflow A: PRD → User Stories**
- Trigger: "PRD", "Requirements Document"
- **→ Read [PRD.md](PRD.md) for this workflow**

**Workflow B: Epic Breakdown**
- Trigger: "break down epic", "EPIC-123"
- **→ Read [BREAKDOWN.md](BREAKDOWN.md) for this workflow**

### 2. [Continue with identified workflow...]
```

### File Naming Conventions

| File | Purpose |
|------|---------|
| `SKILL.md` | Main skill file (required) |
| `TEMPLATES.md` | Output templates |
| `GUIDE.md` | Detailed how-to guide |
| `WORKFLOW.md` | Multi-step workflow details |
| `EXAMPLES.md` | Extended examples |
| `reference/*.md` | Reference materials (subfolder) |

---

## Best Practices

**✅ DO:**
- **One capability per Skill** (focused scope)
- **Third-person descriptions** with specific trigger keywords
- **Keep SKILL.md < 500 lines** (split into files if needed)
- **Explicit read instructions** for supporting files
- **One-level-deep references** (SKILL.md → reference.md, NOT SKILL.md → a.md → b.md)
- **3-7 step workflows** (digestible, with checklists for complex tasks)
- **Concrete input → output examples** (show don't tell)
- **Consistent terminology** throughout (pick one term, stick with it)
- **Test the trigger description** (does it actually match user intent?)

**❌ DON'T:**
- Bundle multiple unrelated tasks in one Skill
- Use **first person** in descriptions ("I can help...")
- Use **second person** in descriptions ("You can use this to...")
- Assume supporting files are auto-loaded
- Create vague descriptions ("helps with stuff")
- Create 20-step workflows with edge cases everywhere
- Create **nested references** (keep one level deep!)
- Over-engineer before validation
- Create supporting files "just in case"

**🔒 Public/Private Decision Guide:**
- ✅ **Make PRIVATE if:**
  - Contains personal company data (client names, internal URLs)
  - Uses sensitive API keys or credentials
  - Includes proprietary workflows or methodologies
  - References internal tools/systems not shareable
- ✅ **Make PUBLIC if:**
  - Generic workflow applicable to anyone
  - No personal/sensitive data dependencies
  - Adds value to AI PM Operating System for others
  - Safe to share on GitHub publicly

---

## Template: Minimal Skill

```yaml
---
name: [kebab-case-name]
description: [THIRD PERSON. What it does + when to use it. Specific triggers. Max 1024 chars.]
---

# [Title Case Name]

## When to Use
- [Trigger scenario 1]
- [Trigger scenario 2]
- Keywords: "[keyword1]", "[keyword2]", "[keyword3]"

---

## Instructions

1. [First step]
2. [Second step]
3. [Third step]

---

## Examples

**Example 1:**
Input: [User request]
Output: [What Skill produces]
```

---

## Template: Skill with Supporting Files

```yaml
---
name: [kebab-case-name]
description: [THIRD PERSON. What it does + when to use it. Specific triggers. Max 1024 chars.]
---

# [Title Case Name]

## When to Use
- [Trigger scenario 1]
- [Trigger scenario 2]
- Keywords: "[keyword1]", "[keyword2]", "[keyword3]"

---

## 📚 Supporting Files

**Read these files when needed during the workflow:**

| File | Purpose | When to Read |
|------|---------|--------------|
| [TEMPLATES.md](TEMPLATES.md) | Output templates | Before creating deliverables |
| [GUIDE.md](GUIDE.md) | Detailed instructions | For complex scenarios |

---

## Instructions

### 1. [First Step]
[Instructions...]

### 2. [Step Needing Templates]
**→ Read [TEMPLATES.md](TEMPLATES.md) first**
[Then proceed with...]

### 3. [Step Needing Guide]
**→ For complex cases, read [GUIDE.md](GUIDE.md)**
[Instructions...]

---

## Examples

**Example 1:**
Input: [User request]
Output: [What Skill produces]
```

---

## Template: CLAUDE.md Entry

Add this to `## 📋 Available Skills` section in `CLAUDE.md`:

```markdown
**[Skill Name]** → `.claude/skills/[skill-name]/SKILL.md`
Use when: [trigger keywords], [scenarios], [file types], or [specific context].
```

**With notes:**
```markdown
**[Skill Name]** → `.claude/skills/[skill-name]/SKILL.md`
Use when: [trigger keywords], [scenarios], [file types], or [specific context].
**Note:** [Any special behavior or considerations]
```

---

## Examples

### Example 1: Minimal Skill (okr-friday)

**SKILL.md:**
```yaml
---
name: okr-friday
description: Weekly OKR wrap-up for Fridays. Celebrates wins, reviews progress, updates confidence scores. Use when user mentions "Friday", "weekly review", "celebrate wins", or "end of week".
---

# OKR Friday

## When to Use
- Friday / end of week
- Weekly review / retro
- Celebrating wins
- Updating weekly progress

## Instructions

1. Ask about wins this week
2. Review OKR progress vs. commitments
3. Update confidence scores
4. Celebrate achievements
5. Note learnings for next week

## Examples

**Input:** "It's Friday, let's wrap up the week"
**Output:** Guided review of wins, progress update, confidence adjustment
```

**CLAUDE.md Entry:**
```markdown
**OKR Friday** → `.claude/skills/okr-friday/SKILL.md`
Use when: Friday/end of week, celebrating wins, weekly review, or reflecting on OKR progress.
```

---

### Example 2: Skill with Supporting Files (user-stories)

**Folder Structure:**
```
.claude/skills/user-stories/
├── SKILL.md
├── BREAKDOWN.md
├── PRD.md
├── TEMPLATES.md
└── GUIDE.md
```

**SKILL.md (excerpt):**
```yaml
---
name: user-stories
description: Create User Stories from PRDs, break down EPICs, write standalone stories. Use when user mentions "PRD", "Epic", "User Stories", "break down", "Backlog", or "Sprint Planning".
---

# User Stories & Epic Breakdown

## 📚 Supporting Files

| File | Purpose | When to Read |
|------|---------|--------------|
| [PRD.md](PRD.md) | PRD → Stories workflow | When working from a PRD |
| [BREAKDOWN.md](BREAKDOWN.md) | Epic breakdown logic | When breaking down an epic |
| [TEMPLATES.md](TEMPLATES.md) | Story templates | Before creating stories |

## Instructions

### 1. Identify Workflow

**Workflow A: PRD → User Stories**
- Trigger: "PRD", "Requirements Document"
- **→ Read [PRD.md](PRD.md) for this workflow**

**Workflow B: Epic Breakdown**
- Trigger: "break down epic", "EPIC-123"
- **→ Read [BREAKDOWN.md](BREAKDOWN.md) for this workflow**

### 2. Gather Context
...

### 3. Create Stories
**→ Read [TEMPLATES.md](TEMPLATES.md) for story format**
...
```

**CLAUDE.md Entry:**
```markdown
**User Stories** → `.claude/skills/user-stories/SKILL.md`
Use when: Writing user stories from PRDs, breaking down epics, sprint planning, backlog work, bug tickets, or acceptance criteria.
```

---

### Example 3: Private Skill

**Why Private?**
- References specific client names
- Contains internal tool URLs
- Uses proprietary methodologies

**Implementation:**

1. Create `.claude/skills/client-automation/SKILL.md`
2. Add to `.gitignore`:
   ```
   # Private Skills
   .claude/skills/client-automation/
   ```
3. **DO NOT** add to `CLAUDE.md`

The skill works locally but won't sync to GitHub or be discoverable by others.

---

## Project Context

**Aligned with AI PM Operating System CLAUDE.md:**
- 🎯 START SIMPLE Principle (minimal by default)
- 🎯 Add complexity ONLY when proven need
- 🎯 One focused task per Skill
- 🎯 No over-engineering
- 🎯 Files over configuration (portable across setups)

---

*Skill Creator for Cursor AI PM Operating System*
*Beyond 7, 2025*
