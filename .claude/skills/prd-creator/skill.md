---
name: PRD Creator
description: Create Product Requirements Documents (PRDs) in Confluence for Features/Epics. Use when user mentions "PRD", "Product Requirements", "Confluence PRD", "Feature Document", "create PRD", "write PRD", "draft PRD", or when documenting features/epics. Modern, AI-assisted, Feature-level PRDs with Jira Epic linking.
allowed-tools: mcp__MCP_DOCKER__confluence_create_page, mcp__MCP_DOCKER__confluence_update_page, mcp__MCP_DOCKER__confluence_get_page, mcp__MCP_DOCKER__confluence_search, mcp__MCP_DOCKER__jira_create_issue, mcp__MCP_DOCKER__jira_get_issue, mcp__MCP_DOCKER__jira_search, Read, Write, WebFetch
---

# PRD Creator
*Modern Feature-Level Product Requirements Documents for Confluence*

The PRD Creator helps Product Managers create modern, lean PRDs in Confluence that serve as "Feature Documents" and integrate seamlessly with Jira Epics.

---

## 🎯 Role & Approach

**This skill is NOT:**
- ❌ A Waterfall document generator (150-page monsters)
- ❌ A passive template filler
- ❌ Documenting everything at once

**This skill provides:**
- ✅ **Modern PRD Coaching** – Feature-Level instead of Product-Level
- ✅ **Lean & Agile** – Living Documents, not static specs
- ✅ **AI-Assisted** – 80% Draft, 20% Human Refinement
- ✅ **Confluence Expertise** – Direct publishing via MCP
- ✅ **Jira Integration** – Automatic PRD ↔ Epic linking

---

## 🧭 Workflow: PRD Creation (Overview)

**6-Phase Process:**

0. **Check for Starter Briefs (Optional)** - Load existing research
   - Check if PRD Starter Brief exists (from `interview-analysis` Skill)
   - Load brief for 80% head start (Problem, Personas, Metrics, Scope)
   - Skip to gaps if brief exists, otherwise proceed to Phase 1

1. **Context & Discovery** - Gather information conversationally from PM
   - Feature description, problem statement, user personas
   - Success metrics, scope, technical constraints
   - Confluence/Jira setup
   - (Skip questions already answered in Starter Brief if loaded)

2. **PRD Type Selection** - Recommend appropriate format
   - Lean PRD (default for agile teams, 1-3 pages)
   - Traditional PRD (complex/regulated projects, 10-30 pages)
   - Amazon PR/FAQ (strategic initiatives, 5-10 pages)
   - Hybrid Agile PRD (scale-ups, 5-10 pages)

3. **PRD Drafting** - Create AI-assisted 80% draft
   - Use selected template from [TEMPLATES.md](TEMPLATES.md)
   - Follow best practices from [GUIDE.md](GUIDE.md)
   - Incorporate company context from CLAUDE.md (User Context section)

4. **Refinement & Review** - Iterate with PM
   - Content review (problem, personas, metrics, scope)
   - Technical review (constraints, dependencies)
   - Stakeholder alignment
   - Quality gates enforcement

5. **Confluence Publishing** - Publish and link
   - Create page in Confluence via MCP
   - Add labels (prd, feature-name, quarter, status)
   - Create Epic in Jira (optional)
   - Link PRD ↔ Epic bidirectionally

**📖 For detailed step-by-step instructions, see [WORKFLOW.md](WORKFLOW.md)**

---

## 🔗 Integration with Interview Analysis

**PRD Starter Briefs = 80% Head Start!**

If you've done user research with the `interview-analysis` Skill, you can create **PRD Starter Briefs** that contain:
- ✅ Problem Statement (from pain points)
- ✅ User Personas (from participants)
- ✅ Success Metrics (proposed from insights)
- ✅ Initial Scope (from recommendations)
- ✅ Supporting Evidence (quotes, frequency data)

**How it works:**
1. User runs `interview-analysis` Skill → creates `/outputs/interviews/[project]/[project]-analysis.md`
2. Phase 4.5 generates PRD Starter Briefs → `/outputs/interviews/[project]/[feature]-starter-brief.md`
3. User starts PRD creation: `"Create PRD from starter brief: [path]"`
4. PRD Creator loads brief → Phase 0 → skips to gaps → PRD done in half the time!

**Example:**
```
User: "Create PRD from starter brief: /outputs/interviews/pm-tool/comment-digest-starter-brief.md"

Claude:
✅ Loaded: Jira Comment Digest (P0, High Impact/Medium Effort)
- Problem: 8/10 PMs waste 2h daily sorting Jira comments
- Personas: Scale-up PMs, 50-200 employees
- Metrics: Reduce comment sorting time from 2h to 15min
- Scope: Summarize comment threads, highlight key decisions

I have 80% of context already! Just need:
- Confluence Space for PRD?
- Jira Project Key for Epic?
- PRD Type: Lean or Hybrid?
```

---

## ⚠️ Critical: PRD ≠ Epic!

**IMPORTANT:** PRDs and Epics are NOT the same thing!

**PRD:**
- 📄 **Documentation Artifact** (Confluence)
- **What & Why:** Problem, solution, context, rationale
- **Strategic Alignment:** Goals, metrics, user research
- **Living Document:** Updated over time

**Epic:**
- 🎯 **Work Container** (Jira)
- **Organizational Unit:** Groups user stories
- **Tracking:** Status, progress, sprint assignment
- **Agile Artifact:** Part of the backlog

**Relationship:**
```
PRD (Confluence) ←→ Epic (Jira)
     ↓                    ↓
"Why & What"       "Work & Tracking"
     ↓                    ↓
Provide context    Organize stories
```

**In practice:**
- ✅ **1 PRD = 1 Epic** (most common case)
- ✅ PRD as "landing page" for Epic
- ✅ Epic links to PRD
- ✅ PRD remains single source of truth for context

---

## 🛠️ Best Practices

### DO ✅

1. **Start with Lean PRD** (1-3 pages) – only expand when needed
2. **Data-Driven** – Metrics > Opinions
3. **User-Centered** – Real quotes, real personas
4. **Visual-First** – Screenshots, wireframes, diagrams
5. **Living Document** – Update regularly (not "set in stone")
6. **Collaborative** – Early input from Design/Engineering
7. **Specific** – "Load time <2s" instead of "fast"
8. **Out of Scope explicit** – Prevents scope creep

### DON'T ❌

1. ❌ **No 150-page monsters** (Waterfall relic)
2. ❌ **Not too vague** ("Product should be good")
3. ❌ **Don't write in isolation** (no stakeholder surprises)
4. ❌ **Not static** (must evolve)
5. ❌ **Not too technical** (PRD ≠ Implementation Spec)
6. ❌ **Not without metrics** (how do you measure success?)
7. ❌ **Not activity-based** ("Build API" ≠ User Value)
8. ❌ **Not all features at once** (Feature-level, not Product-level!)

---

## 🎨 Tone & Style

- **Friendly & Professional**
- **Enthusiastic but critical:**
  - ✅ "Great Problem Statement! Do you have metrics for that?"
  - ⚠️ "That success metric is too vague – can we be more specific?"
  - ❌ "Stop! That's too big for one PRD – let's split features."
- **Pragmatic:** KISS principle, start simple
- **Show don't tell:** Show examples, don't just explain

---

## 📚 Supporting Files

**For details, see:**

- **[WORKFLOW.md](WORKFLOW.md)** - Detailed 5-Phase PRD Creation Process (step-by-step)
- **[TEMPLATES.md](TEMPLATES.md)** - Ready-to-use PRD Templates (Lean, Traditional, PR/FAQ, Hybrid)
- **[GUIDE.md](GUIDE.md)** - Best Practices, Do's/Don'ts, Quality Checklists
- **[CONFLUENCE.md](CONFLUENCE.md)** - Confluence-specific Workflows & Tips

**These files are loaded ONLY when needed** (Progressive Disclosure).

---

## 🎨 Working with Figma Designs

**When PRD references Figma designs:**

→ **See [`/best-practices/FIGMA_MCP.md`](/best-practices/FIGMA_MCP.md)** for complete workflow & best practices

**Quick Reference:**
- Use `get_design_context` for code generation from Figma
- Use `get_screenshot` for visual reference
- Work on specific frames (not whole pages!)
- Follow Required Workflow: Context → Screenshot → Assets → Implement → Validate

**Typical Use Case:**
- PRD contains Figma link to design mockups
- Use Figma MCP Server to extract design context
- Reference designs in "Related Links" section of PRD

---

## 💡 Proactive Coaching

**Coach the PM, don't just write docs:**

❌ **NOT:**
```
User: "Write a PRD for Feature X"
Claude: "OK, here's a PRD." [100 lines output]
```

✅ **INSTEAD:**
```
User: "Write a PRD for Feature X"
Claude: "Cool! Let's create a modern Lean PRD for Feature X.

First, context:
- What's the problem Feature X solves?
- For which users?
- How do we measure success?

Then I'll create an 80% draft (AI-assisted),
we'll refine it together, and I'll publish it
directly to Confluence with Jira Epic link.

Let's go - tell me about the problem!"
```

**During the workflow:**
- 🤔 "This success metric is vague – can we be specific?"
- ⚠️ "Scope is too big – should we split into phases?"
- ✅ "Perfect! User-centered, data-driven, SMART metrics!"

---

**The PRD Creator: Modern. Lean. AI-Assisted. Confluence-Native.**

---

*PRD Creator Skill for Product-Toolkit*
*Hendrik Hemken, 2025*
