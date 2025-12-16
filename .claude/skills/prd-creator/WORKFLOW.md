# PRD Creation Workflow
*Detailed 6-Phase Process (Phase 0 → Phase 5)*

This document contains the detailed step-by-step workflow for creating PRDs. For overview, see [SKILL.md](SKILL.md).

---

## 🧭 6-Phase PRD Creation Process

### Phase 0: Check for PRD Starter Briefs (Optional)

**BEFORE asking questions, check if user has existing PRD Starter Briefs.**

PRD Starter Briefs are created by the `interview-analysis` Skill and contain:
- Problem Statement (from user research)
- User Personas (from interviews)
- Success Metrics (proposed)
- Initial Scope
- Supporting Evidence (quotes, insights)

**Workflow:**

1. **Ask User:**
   ```
   "Quick check: Do you have a PRD Starter Brief from interview analysis?

   If yes, give me the path (e.g., /outputs/interviews/[project]/[feature]-starter-brief.md)
   and I'll load it for an 80% head start!

   If no, no worries - we'll gather context together."
   ```

2. **If User provides path:**
   - Load Starter Brief using Read tool
   - Extract from YAML Front Matter:
     - `feature`: Feature Name
     - `analysis_ref`: Link to original analysis
     - `insight_refs`: Which insights support this
     - `priority`: P0/P1/P2
     - `impact/effort`: Quick assessment
     - `participants`: Frequency data
   - Extract from Content:
     - Problem Statement
     - User Personas
     - Success Metrics
     - Scope (In/Out)
     - Constraints & Context (user-added!)
     - Supporting Evidence

3. **Show Loaded Info:**
   ```
   "✅ Loaded Starter Brief: [Feature Name]

   Here's what we have:
   - Problem: [from brief]
   - Personas: [from brief]
   - Metrics: [proposed from brief]
   - Scope: [initial from brief]
   - Evidence: [X/Y participants mentioned this]

   This gives us an 80% head start!

   I'll still ask a few clarifying questions, but we're way ahead already."
   ```

4. **Proceed to Phase 1:**
   - Skip questions already answered in Starter Brief
   - Focus on gaps: Technical constraints, Confluence/Jira setup, PRD Type
   - Validate/refine what's in brief with user

**If no Starter Brief:**
- Proceed directly to Phase 1 (Context & Discovery)
- Gather all information conversationally

**Hint to User:**
If user is about to create PRD without research, suggest:
```
"💡 Pro Tip: Have you done user interviews yet?

The `interview-analysis` Skill can create PRD Starter Briefs
from research insights - saves a ton of time and ensures
data-driven feature definition!

Want to proceed anyway? (Yes/No)"
```

---

### Phase 1: Context & Discovery (Conversational)

**Ask the PM:**

1. **What are we building?** (Feature Name & High-Level Description)
   - "Describe the feature in 1-2 sentences"
   - Example: "Multi-Video Upload with Batch-Processing"

2. **Why are we building this?** (Problem Statement)
   - "What problem are we solving?"
   - "For whom?"
   - "What's the impact if we DON'T build it?"
   - → Quantitative (Metrics) + Qualitative (User Quotes)

3. **Who uses this?** (User Personas)
   - Primary Users (1-2 personas max)
   - Use Cases / User Stories
   - Pain Points

4. **How do we measure success?** (Success Metrics)
   - SMART Metrics (Specific, Measurable, Attainable, Relevant, Time-bound)
   - Baseline vs. Target
   - Example: "Upload Success Rate from 85% to 95% in Q1"

5. **What's the scope?** (In/Out of Scope)
   - Must-Have Features (P0)
   - Nice-to-Have (P1/P2)
   - Explicitly OUT of Scope (Scope Creep Prevention!)

6. **Technical Constraints?**
   - API Limits, Legacy Systems, Performance Requirements
   - Dependencies (other features, teams)

7. **Confluence & Jira Setup:**
   - **Confluence Space:**
     - Check CLAUDE.md → User Context → "🛠️ Product & Tech" → "PM Tools" for Confluence Spaces
     - If found: Use listed spaces (ask which one if multiple)
     - If empty: Ask "Which Confluence Space? (e.g., 'PROD', 'DEV')"
   - **Jira Project:**
     - Check CLAUDE.md → User Context → "🛠️ Product & Tech" → "PM Tools" for Jira Projects
     - If found: Use listed projects (ask which one if multiple)
     - If empty: Ask "Jira Project Key? (e.g., 'PROD', 'DEV')"
   - **Parent Page:** (Optional) "Parent Page? (if part of a larger initiative)"

---

### Phase 2: PRD Type Selection

**Ask: "Which PRD type do we need?"**

Based on context, recommend a type:

**1. Lean PRD** ✅ (DEFAULT for Agile Teams)
- ✅ Agile/Scrum Environment
- ✅ Small-Medium Feature (2 weeks - 3 months)
- ✅ Startup or small team (2-20 people)
- ✅ MVP or Early-Stage
- ✅ Fast iteration desired
- **Format:** 1-3 pages, Focus on Why/What, minimal How
- **Template:** [TEMPLATES.md](TEMPLATES.md) → Lean PRD

**2. Traditional PRD** (for complex/regulated projects)
- ⚠️ Waterfall or highly regulated industry (Finance, Healthcare)
- ⚠️ Large Feature (3+ months)
- ⚠️ High Risk, High Investment
- ⚠️ >50 Stakeholders
- ⚠️ Compliance/Legal Requirements
- **Format:** 10-30 pages, comprehensive Documentation
- **Template:** [TEMPLATES.md](TEMPLATES.md) → Traditional PRD

**3. Amazon PR/FAQ** (for Strategic Initiatives)
- 🚀 Major Strategic Initiative
- 🚀 Customer Obsession Culture
- 🚀 Evaluating multiple solution approaches
- 🚀 Executive-Level Decision needed
- **Format:** Press Release + FAQ (5-10 pages)
- **Template:** [TEMPLATES.md](TEMPLATES.md) → PR/FAQ

**4. Hybrid Agile PRD** (Balance for Scale-Ups)
- 🔄 Medium-Large Team (10-50 people)
- 🔄 Complex Feature with Cross-Functional Collaboration
- 🔄 Agile methodology, but more structure needed
- 🔄 Remote/Distributed Teams
- **Format:** 5-10 pages, Living Document
- **Template:** [TEMPLATES.md](TEMPLATES.md) → Hybrid PRD

**💡 Make a recommendation:**
```
"Based on your context I recommend:
→ Lean PRD (1-3 pages)

Why:
✅ Agile Team
✅ Feature Scope (2-3 months)
✅ Fast iteration desired

Alternative would be Hybrid PRD if more structure needed.
What do you think?"
```

---

### Phase 3: PRD Drafting (AI-Assisted)

**Create an 80% draft based on:**

1. **Gathered information** from Phase 1
2. **Chosen Template** from Phase 2
3. **Best Practices** from [GUIDE.md](GUIDE.md)
4. **Company Context** from `CLAUDE.md` (User Context section)

**Structure (for Lean PRD - most common case):**

```markdown
---
title: [Feature Name] - PRD
space_key: [PROD]
status: Draft
author: [PM Name]
created: [Date]
last_updated: [Date]
epic_link: [JIRA-XXX]
---

# [Feature Name] - Product Requirements Document

**Status:** 🟡 Draft | In Review | Approved | Shipped
**Owner:** [PM Name]
**Target Release:** Q[X] 202[X]
**Epic:** [JIRA-XXX](link)

---

## 📋 Executive Summary

[2-3 sentences: What are we building, why, for whom]

---

## 🎯 Problem Statement

**Problem:** [Specific Problem]

**Impact:**
- Quantitative: [Metrics, Data]
- Qualitative: [User Quotes, Feedback]

**Evidence:**
- [Metric 1]: Baseline → Target
- [User Quote]: "..."

**Vision:** [What does the world look like when problem is solved?]

---

## 👥 User Personas & Use Cases

### Primary Persona: [Name]
- **Role:** [e.g., Content Creator]
- **Goals:** [What does the user want to achieve?]
- **Pain Points:** [Current frustrations]
- **Quote:** "[Direct quote from research]"

### Use Case: [Title]
**As** [User Type]
**I want** [Action]
**to** [Benefit]

**Happy Path:**
1. [Step 1]
2. [Step 2]
3. [Step 3]

---

## 📊 Success Metrics

| Metric | Baseline | Target | Timeframe | Method |
|--------|----------|--------|-----------|--------|
| [KPI 1] | [Value] | [Goal] | Q[X] 202[X] | [How to measure?] |
| [KPI 2] | [Value] | [Goal] | Q[X] 202[X] | [How to measure?] |

---

## ⚙️ Features & Requirements

### Must-Have (P0)
- ✅ [Feature 1]: [Description]
- ✅ [Feature 2]: [Description]

### Should-Have (P1)
- 🔵 [Feature 3]: [Description]

### Nice-to-Have (P2)
- 🟢 [Feature 4]: [Description]

### OUT of Scope ❌
- ❌ [Feature X]: [Why out of scope?]

---

## 🛠️ Technical Considerations

**Architecture:**
- [High-Level Tech Approach]

**Dependencies:**
- [System/Team Dependencies]

**Constraints:**
- Performance: [e.g., "<2s Load Time"]
- Security: [Requirements]
- Scalability: [e.g., "100k concurrent users"]

**Assumptions:**
- [Key Assumptions]

**Risks:**
- [Risk 1]: Mitigation: [Plan]

---

## 📅 Timeline & Milestones

**Phase 1 - MVP** (Q[X] 202[X])
- [Core Features]

**Phase 2 - Enhancement** (Q[X] 202[X])
- [Additional Features]

**Phase 3 - Scale** (Q[X] 202[X])
- [Optimization]

---

## 🔗 Related Links

- **Epic:** [JIRA-XXX](link)
- **Design:** [Figma Link]
- **Research:** [User Research Doc]
- **Roadmap:** [Product Roadmap]

---

## 📝 Open Questions

- [ ] [Question 1]
- [ ] [Question 2]

---

## 📜 Changelog

| Date | Author | Changes |
|------|--------|---------|
| 202[X]-[MM]-[DD] | [Name] | Initial Draft |

```

**Show the PM the draft:**
```
"Here's an 80% draft based on our conversation.

Key Highlights:
✅ Problem Statement with Metrics
✅ 2 User Personas with Use Cases
✅ 4 Success Metrics (SMART)
✅ Features prioritized (P0/P1/P2)
✅ Out of Scope explicitly defined

What's missing or needs to be adjusted?"
```

---

### Phase 4: Refinement & Review

**Iterate with PM:**

1. **Content Review:**
   - "Is the Problem Statement clear?"
   - "Missing important User Personas?"
   - "Are the Success Metrics SMART?"
   - "Is the prioritization correct?"

2. **Technical Review:**
   - "Do the Technical Constraints fit?"
   - "Missing dependencies?"
   - "Are Non-Functional Requirements complete?"

3. **Stakeholder Alignment:**
   - "Who needs to review this?"
   - "Which teams are affected?"
   - "Are there Legal/Compliance considerations?"

**Quality Gates enforced:**

✅ **Problem Statement:**
- Quantitative Evidence? (Metrics)
- Qualitative Evidence? (User Quotes)
- Impact Statement? (What happens if we DON'T build it?)

✅ **Success Metrics:**
- SMART? (Specific, Measurable, Attainable, Relevant, Time-bound)
- Baseline vs. Target defined?
- Measurable with true/false?

✅ **Scope Clarity:**
- Must-Have vs. Nice-to-Have clear?
- OUT of Scope explicitly stated?
- Scope Creep Prevention?

✅ **User-Centricity:**
- Personas based on real users?
- User Quotes included?
- Use Cases concrete?

---

### Phase 5: Confluence Publishing

**When PM is satisfied:**

1. **Create Page in Confluence:**

   **→ Use the `confluence_create_page` tool**

   **Parameters:**
   - `space_key`: "[SPACE]" (e.g., "PROD", "DEV")
   - `title`: "[Feature Name] - PRD"
   - `content`: Markdown content (automatically converted to HTML)
   - `parent_id`: [optional] - Parent Page ID if part of larger initiative

   **→ Save the Page ID** from the Response for later updates!

2. **Add Labels:**

   **→ Use `confluence_add_label` for each label:**

   - `prd` (always!)
   - `feature-[name]` (feature-specific)
   - `q[x]-202[x]` (timeline)
   - `status-draft` (status)

   **Example:**
   ```
   → confluence_add_label(page_id, "prd")
   → confluence_add_label(page_id, "feature-multi-upload")
   → confluence_add_label(page_id, "q2-2025")
   → confluence_add_label(page_id, "status-draft")
   ```

3. **Create Epic in Jira (optional):**

   **→ Use the `jira_create_issue` tool**

   **Parameters:**
   - `project_key`: "[PROJ]" (e.g., "PROD")
   - `issue_type`: "Epic"
   - `summary`: "[Feature Name]"
   - `description`: PRD Link + Summary
   - `additional_fields`: Labels, etc.

   **Epic Description Example:**
   ```markdown
   📄 Product Requirements Document:
   https://[company].atlassian.net/wiki/spaces/[SPACE]/pages/[ID]

   ## Summary
   [Brief Summary from PRD]

   See PRD for full details.
   ```

   **→ Save the Epic Key** (e.g., "PROD-123") from the Response!

4. **Link PRD ↔ Epic:**
   - PRD contains Epic Link
   - Epic Description contains PRD Link

**Output for PM:**
```
✅ PRD created in Confluence!

📄 PRD: https://[company].atlassian.net/wiki/spaces/[SPACE]/pages/[ID]
🎯 Epic: [JIRA-XXX] (optional)

Next Steps:
1. Share PRD with stakeholders (Design, Engineering)
2. Gather feedback & iterate
3. Update status: Draft → In Review → Approved
4. Derive User Stories from PRD (via user-stories Skill)
```

---

*Detailed PRD Workflow for PRD Creator Skill*
*Part of Cursor AI PM Operating System*
