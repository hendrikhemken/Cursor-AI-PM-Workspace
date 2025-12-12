---
name: jira-comment-digest
description: Summarizes Jira ticket comment threads and ongoing discussions. Use when user mentions 'Jira Comments', 'Comment Digest', 'Ticket Discussions', 'Jira Updates', 'show comments', 'comment summary', or wants to review recent Jira conversations.
---

# Jira Comment Digest

Summarizes ongoing Jira ticket discussions into digestible conversation summaries.

**Focus:** Understand the current state of discussions, identify open questions, and highlight different positions — NOT just list individual comments.

---

## Instructions

### 1. Determine Scope

Ask user OR infer from context:
- **Specific tickets?** (e.g., "BW-1, BW-2")
- **Time range?** (e.g., "last 24h", "today", "this week")
- **Status filter?** (e.g., "In Progress", "In Review")

**Default if not specified:** Last 24 hours, all tickets updated

### 2. Search Jira Tickets

Use `jira_search` with appropriate JQL:

**Recently updated (last 24h):**
```jql
updated >= -24h ORDER BY updated DESC
```

**Specific status:**
```jql
status = 'In Progress' ORDER BY updated DESC
```

**Combined:**
```jql
(updated >= -24h OR status = 'In Progress') ORDER BY updated DESC
```

**Specific tickets:**
```jql
key in (BW-1, BW-2, BW-3)
```

**Limit:** Start with 10 tickets, adjust if user wants more

### 3. Get Full Issue Details + Comments

For each ticket from search results:

Use `jira_get_issue` with:
- `issue_key`: The ticket key
- `fields`: "summary,status,assignee,description,updated,comment" ⚠️ **IMPORTANT: "comment" MUST be in fields!**
- `comment_limit`: 50 (or 100 for deep discussions)
- `expand`: "renderedFields" (optional, for rendered content)

**🔥 Critical Fix:**
The `comment` field **MUST** be explicitly included in `fields` parameter!
Without it, comments won't be returned even if `comment_limit` is set.

**Wrong:** `fields="summary,status"` → No comments in response!
**Right:** `fields="summary,status,comment"` → Comments included!

### 3.5 Load Team Member Mapping (Optional but Awesome!)

**Check for:** `/user_context/COMPANY_CONTEXT.md` → "Team Members & Jira Roles" section

If section exists in COMPANY_CONTEXT.md:
- Parse team member info from Body (NOT YAML!)
- Use in comment summaries: "Botti (Frontend Dev) suggested..."
- Adds context who is who!

**Format expected in COMPANY_CONTEXT.md:**
```markdown
### Team Members & Jira Roles
*For Jira Comment Digest context mapping*

**John Doe**
- Email: john@company.com
- Role: Product Manager
- Jira Active: Yes

**Jane Smith**
- Email: jane@company.com
- Role: Frontend Developer
- Jira Active: Yes
```

**Parsing:**
- Look for "### Team Members & Jira Roles" section
- Extract name (bold **Name**), email, role for each member
- Build mapping: email → (name, role)

**In comment summaries:**
- Map comment author email → team member
- Display as: "Botti (Frontend Dev) suggested..."
- Fallback to name matching if no email match
- If no mapping found: Use display_name only

**If section doesn't exist:**
- User hasn't set up team mapping yet
- Show display_name only (still works!)
- Optionally suggest: "💡 Tip: Run user-context Skill to set up team mapping!"

### 4. Analyze & Summarize Conversations

**For each ticket's comments:**

**Focus on:**
- ✅ **Overall conversation flow** (NOT individual comments!)
- ✅ **Different positions/perspectives** mentioned
- ✅ **Latest state of discussion** (newest comments = most important!)
- ✅ **Open questions** that need answering
- ✅ **Decisions made** (if any)
- ✅ **Action items** mentioned (if any)

**Avoid:**
- ❌ Listing every single comment
- ❌ Treating all comments equally (newest = more weight!)
- ❌ Ignoring context (who said what matters!)

**Synthesis approach:**
- Read all comments chronologically
- Identify themes/topics discussed
- Note how discussion evolved (early → late comments)
- Highlight current state/conclusion
- Extract open questions

### 5. Output Structured Digest

**Format per ticket:**

```markdown
## [KEY]: [Summary]
**Status:** [Jira Status] | **Assignee:** [Name]

**Conversation:**
[2-4 sentences summarizing the discussion flow and key points]

**Current State:**
[Where the discussion is NOW - based on latest comments]

**Open Questions:**
- [Question 1]
- [Question 2]

**Next Steps:** [If clear from discussion]
- [Action 1]
- [Action 2]

---
```

**If no comments:**
```markdown
## [KEY]: [Summary]
**Status:** [Jira Status] | **Assignee:** [Name]

_No comments available._

---
```

**Overall structure:**

```markdown
# Jira Comment Digest
*[Scope description, e.g., "Last 24 hours" or "Tickets: BW-1, BW-2"]*

[Ticket summaries as above]

---

**Total:** [X] tickets reviewed, [Y] with active discussions
```

---

## Examples

### Example 1: Time-based digest

**User Request:**
"Show me today's Jira comments"

**Skill Actions:**
1. JQL: `updated >= -24h ORDER BY updated DESC`
2. Find 3 tickets: BW-1, BW-5, BW-8
3. Get comments for each
4. Summarize conversations

**Output:**
```markdown
# Jira Comment Digest
*Last 24 hours (updated since Oct 23, 14:00)*

## BW-1: Beyond7 Website Tech Stack
**Status:** In Progress | **Assignee:** Hendrik

**Conversation:**
Max asked about analytics tool for GDPR compliance. Sarah suggested Plausible.io
(cookieless tracking, no consent banner needed). Team discussed pros/cons vs.
Google Analytics. Hendrik prefers Plausible for simplicity + privacy-first.

**Current State:**
Team leans toward Plausible.io. Waiting for budget approval from Hendrik.

**Open Questions:**
- Budget for Plausible.io approved? ($9/month)
- Which events exactly should we track?

**Next Steps:**
- Hendrik decides budget (today)
- Sarah sets up Plausible.io (once approved)

---

## BW-5: Claude Code Skill Implementation
**Status:** In Review | **Assignee:** Hendrik

**Conversation:**
Discussion about Skill Trigger Description. Max noted that "helps with..." is too vague.
Team agrees that third-person descriptions with specific keywords work better.
Hendrik tested new version, it works now.

**Current State:**
Skill works, ready to merge. Waiting for final review.

**Open Questions:**
_No open questions._

**Next Steps:**
- Final review (Max)
- Merge to main

---

## BW-8: Jira MCP Integration
**Status:** To Do | **Assignee:** Unassigned

_No comments available._

---

**Total:** 3 tickets reviewed, 2 with active discussions
```

---

### Example 2: Specific tickets

**User Request:**
"What's the status on BW-1 and BW-2?"

**Skill Actions:**
1. JQL: `key in (BW-1, BW-2)`
2. Get comments for both tickets
3. Summarize

**Output:**
```markdown
# Jira Comment Digest
*Tickets: BW-1, BW-2*

## BW-1: Beyond7 Website Tech Stack
[... same as above ...]

## BW-2: Product Toolkit PRD Creator Skill
**Status:** Done | **Assignee:** Hendrik

**Conversation:**
Skill was completed. Team tested integration with Confluence MCP.
Works perfectly. Max praised the clear structure.

**Current State:**
✅ Done and deployed!

**Open Questions:**
_None._

---

**Total:** 2 tickets reviewed, 1 with active discussions
```

---

## Edge Cases & Handling

### No tickets found
```markdown
# Jira Comment Digest
*[Scope]*

_No tickets found for these criteria._

**Hint:** Try a different time range or status filter.
```

### Tickets without comments
- Show ticket in list but mark "_No comments available._"
- Don't skip ticket entirely (user should know it exists!)

### Very long comment threads (20+ comments)
- Focus on **last 5-10 comments** (most recent state!)
- Mention older discussion briefly if relevant: "Earlier there was discussion about... but currently..."
- Prioritize synthesis over completeness

### Multiple topics in one ticket
- Group by topic: "**Topic 1:** ... **Topic 2:** ..."
- Or summarize flow: "Discussion started with X, evolved to Y, currently at Z"

### User asks follow-up questions
- "What does Max say about BW-1?" → Go deeper into that ticket's comments
- "Are there any blockers?" → Highlight comments mentioning blockers/impediments

---

## Tips for Great Summaries

✅ **DO:**
- Focus on conversation FLOW (how discussion evolved)
- Weight recent comments higher (they represent current state!)
- Identify different perspectives ("Max thinks X, Sarah thinks Y")
- Extract actionable questions/next steps
- Be concise (2-4 sentences for most discussions)

❌ **DON'T:**
- List every comment individually
- Treat all comments equally (chronological order matters!)
- Over-quote (paraphrase instead)
- Lose context (mention who said what when it matters)

**Good summary:**
"Team discussed analytics tool. Max asked about GDPR, Sarah suggested Plausible.io.
Currently: Waiting for budget approval."

**Bad summary:**
"Max wrote: 'Which analytics tool?' Sarah replied: 'How about Plausible?' Max said: 'Sounds good.'
Hendrik commented: 'Let me check budget.'"

---

## Context Awareness

**Respect user's project context:**
- If user has `JIRA_PROJECTS_FILTER` in Company Context → use it!
- Default to user's own tickets/projects if unclear
- Adapt language based on user preference (English or German)

**Integration with OKRs:**
- If discussion relates to current OKRs → mention it!
- Example: "This discussion contributes to KR1 (MRR from Retainer Clients)"

---

*Jira Comment Digest Skill*
*Part of Product-Toolkit by Beyond 7*
