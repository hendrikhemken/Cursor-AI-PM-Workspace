---
name: interview-analysis
description: Analyzes user interview sessions against research goals from interview guides. Extracts insights, identifies patterns across multiple sessions, maps findings to original objectives. Use when user mentions 'analyze interviews', 'analyze my interviews', 'interview analysis', 'interview extraction', 'research synthesis', 'interview insights', 'user research analysis', or has interview transcripts/notes to process. Works with .txt, .md, .pdf files in /user_context/raw/interviews/[project-name]/.
---

# Interview Analysis
*Synthesize User Research Insights from Interview Sessions*

## What This Skill Does

Analyzes user interview transcripts and notes to:
- Map findings back to original research goals (from interview guide)
- Identify patterns and themes across multiple sessions
- Extract verbatim quotes as evidence
- Score confidence levels based on frequency
- Generate actionable recommendations

**Perfect for:**
- Discovery Research analysis
- Validation Research synthesis
- Usability Testing insights
- Post-interview pattern detection

---

## Workflow

### Phase 1: Setup & Context

1. **Load Interview Guide**
   - Ask user: "Which project? What's the interview guide location?"
   - Default: `/outputs/interview-guides/[project-name].md`
   - Extract: Research Goals, Key Questions, Success Criteria

2. **Scan Interview Files**
   - Location: `/user_context/raw/interviews/[project-name]/`
   - Supported formats: .txt, .md, .pdf
   - List files found, ask for confirmation

3. **Clarify Context (optional)**
   ```
   "Quick context questions:
   - How many participants? (for frequency analysis)
   - Any segments to track? (e.g., B2B vs. B2C, roles)
   - Which prototype/version tested? (if applicable)"
   ```

### Phase 2: Analysis (per interview file)

For each interview file:

1. **Read & Classify**
   - Identify: Participant info, date, format
   - Quick scan: Topics covered, length

2. **Extract Core Elements**
   - **Goal Mapping:** Which research goals addressed?
   - **Key Insights:** Main takeaways (3-5 per interview)
   - **Pain Points:** Problems mentioned
   - **Jobs to be Done:** What user wants to achieve
   - **Verbatim Quotes:** Best quotes (evidence!)
   - **Unexpected Findings:** Surprises not in guide
   - **UI/Prototype Feedback:** If tested (optional)

3. **Tag & Categorize**
   - Theme tags (e.g., "Navigation", "Pricing", "Onboarding")
   - Sentiment (positive, negative, neutral, mixed)
   - Confidence flag (strong statement vs. hesitant)

### Phase 3: Synthesis (cross-interview)

1. **Pattern Detection**
   - Identify recurring themes
   - Count frequency (how many participants mentioned?)
   - Segment differences (if applicable)

2. **Confidence Scoring**
   Per insight:
   - **High Confidence:** 5+ mentions, clear pattern, consistent sentiment
   - **Medium Confidence:** 2-4 mentions, emerging pattern
   - **Low Confidence:** 1 mention, anecdotal, needs validation

3. **Goal Achievement Check**
   For each goal from interview guide:
   - ✅ **Fully Answered:** Clear findings, high confidence
   - 🟡 **Partially Answered:** Some data, needs more research
   - ❌ **Not Answered:** No coverage, follow-up needed

### Phase 4: Report Generation

Create: `/outputs/interviews/[project-name]/[project-name]-analysis.md`

**Report Structure:**

```markdown
---
project: [Name]
interview_guide: /outputs/interview-guides/[name].md
sessions_analyzed: [X]
participants: [Y]
date: [YYYY-MM-DD]
confidence: High/Medium/Low
---

# User Interview Analysis: [Project Name]

## 📊 Executive Summary
[2-3 sentences: Top 3 insights, biggest surprises, clear direction]

## 🎯 Goal Achievement
[Per goal from interview guide]

**Goal 1: [Original Research Goal]**
- Status: ✅ Fully / 🟡 Partial / ❌ Not Answered
- Confidence: High/Medium/Low
- Finding: [1-2 sentences summary]
- Evidence:
  > "Quote 1" - P3, B2B User
  > "Quote 2" - P7, Scale-up PM

## 💡 Key Insights (Ranked by Confidence)

1. **[Insight Title]** (High Confidence)
   - **Frequency:** 7/10 participants
   - **Context:** [What's the situation?]
   - **Evidence:**
     > "Quote 1" - P2
     > "Quote 2" - P5
   - **Implication:** [What does this mean for product?]
   - **Recommendation:** [Concrete next step]

2. **[Insight Title]** (Medium Confidence)
   ...

## 🚨 Pain Points (Severity Ranked)

1. **[Pain Point]** - Severity: High
   - Mentioned by: 8/10 participants
   - Context: [When does this occur?]
   - Current workaround: [How do they cope?]
   - Impact: [Business/user impact]
   - Quote: "[...]" - P4

## 🎨 UI/Prototype Feedback
[If prototype/UI tested - organize by feature/screen]

**Feature X:**
- ✅ **Positive:** [What worked well]
- ❌ **Negative:** [What didn't work]
- ❓ **Confusion:** [What was unclear]
- Quotes: "[...]"

## 🔍 Cross-Cutting Themes

**Theme: [Name]**
- Observed in: 6/10 sessions
- Description: [Pattern across interviews]
- Segments: [Any differences? B2B vs. B2C?]
- Quotes:
  > "[...]" - P1, Corporate PM
  > "[...]" - P9, Startup Founder

## 💬 Best Verbatim Quotes
[Grouped by theme - these are your evidence!]

**Theme: Current Workflow Pain**
> "I spend 2 hours daily just sorting Jira comments. It's insane." - P3
> "We lose context between Confluence PRDs and Jira tickets." - P7

## ❓ Open Questions & Research Gaps

**Unanswered Questions:**
- [ ] Question from guide not covered - needs follow-up
- [ ] Conflicting data - need clarification (3 said X, 2 said opposite)

**Emerging Questions:**
- [ ] New question discovered during interviews
- [ ] Unexpected behavior needs investigation

## 📋 Actionable Recommendations

1. **[Recommendation Title]**
   - **Why:** [Insight-based reasoning]
   - **What:** [Concrete action]
   - **Impact:** High/Medium/Low
   - **Effort:** High/Medium/Low
   - **Priority:** P0/P1/P2

2. **[Recommendation Title]**
   ...

## 🔜 Next Steps

**Immediate Actions:**
- [ ] Validate Finding X with quantitative data (analytics)
- [ ] Prototype Solution Y based on Insight Z
- [ ] Follow-up interviews for Gap A (3-5 participants)

**Longer-Term:**
- [ ] Consider Feature B (mentioned by 6/10, medium effort)
- [ ] Monitor Metric M (baseline for future comparison)

---

## 📎 Appendix: Sessions Overview

| # | Date | Participant | Role/Segment | Duration | Notes File |
|---|------|-------------|--------------|----------|------------|
| 1 | 2025-10-15 | P1 | CPO, Scale-up | 45min | session-1.txt |
| 2 | 2025-10-16 | P2 | PM, Corporate | 30min | session-2.md |
| 3 | ... | ... | ... | ... | ... |

**Total Sessions:** [X]
**Total Participants:** [Y]
**Date Range:** [Start] - [End]

**Interview Guide:** [Link]
**Raw Files:** /user_context/raw/interviews/[project]/
```

### Phase 4.5: PRD Opportunities (Optional)

**After report generation, offer to create PRD Starter Briefs for promising features.**

This phase bridges Interview Analysis → PRD Creation by preparing "PRD Starter Briefs" that give the `prd-creator` Skill a strong foundation.

#### Step 1: Identify Opportunities

From the analysis, identify potential features/solutions:

```
"Based on the insights, I see [X] potential feature opportunities:

1. **[Feature Name]** (High Impact/Medium Effort)
   - Solves Pain Point: [Reference from analysis]
   - Backed by: [Insight #X] (High Confidence, 7/10)
   - Quote: "[...]" - P3

2. **[Feature Name]** (Medium Impact/Low Effort)
   - Addresses: [Job to be Done]
   - Backed by: [Insight #Y] (Medium Confidence, 4/10)

3. **[Feature Name]** (High Impact/High Effort)
   - Strategic opportunity from Cross-Cutting Theme Z
   - Backed by: [Multiple insights]

Want to create PRD Starter Briefs for any of these?"
```

**Impact/Effort Matrix:**
- **High Impact/Low Effort** → Quick Wins (P0)
- **High Impact/Medium Effort** → Strategic (P0-P1)
- **High Impact/High Effort** → Big Bets (P1-P2)
- **Medium Impact/Low Effort** → Nice to Have (P1-P2)

#### Step 2: User Selection (Interactive!)

Ask user which opportunities to develop:

```
"Which features should we create PRD Starter Briefs for?
- All 3?
- Just the Quick Wins (#2)?
- Let's discuss each first?

I'll create starter briefs TOGETHER with you - you can add your thoughts,
constraints, scope ideas, etc."
```

**IMPORTANT:** Interactive process! Don't just auto-generate.

#### Step 3: Create Starter Briefs (Collaboratively)

For each selected feature, create a PRD Starter Brief TOGETHER with the user:

**Process:**
1. **Draft from Analysis**
   - Problem Statement (from Pain Points)
   - User Personas (from Participants)
   - Success Metrics (proposed from Insights)
   - Initial Scope (what's in/out)
   - Supporting Evidence (quotes, frequency)

2. **User Input Loop**
   ```
   "I've drafted a starter brief for [Feature X].

   Before I save it, feedback:
   - Problem Statement resonant?
   - Missing any constraints? (technical, business, time)
   - Scope boundaries clear?
   - Any must-have context for PRD creation?"
   ```

3. **Refine Together**
   - User adds technical constraints
   - User clarifies scope boundaries
   - User adds strategic context
   - User suggests success metrics adjustments

4. **Save Starter Brief**
   Location: `/outputs/interviews/[project]/[feature-name]-starter-brief.md`

**PRD Starter Brief Template:**

```markdown
---
type: prd-starter-brief
feature: [Feature Name]
analysis_ref: /outputs/interviews/[project]/[project]-analysis.md
insight_refs: [1, 3, 5]  # Which insights from analysis
priority: P0/P1/P2
impact: High/Medium/Low
effort: High/Medium/Low
confidence: High/Medium/Low
participants: X/Y  # How many mentioned this
created: YYYY-MM-DD
status: draft
---

# PRD Starter Brief: [Feature Name]

## Problem Statement

**User Pain:**
[Concretely formulated from Pain Points - 2-3 sentences]

**Current Situation:**
[How users work around this today]

**Business Impact:**
[Why this matters - revenue, retention, efficiency]

---

## User Personas (from Interviews)

**Primary User:** [Role, Company Type, Segment]
- Characteristics: [Key traits from interviews]
- Context: [When they encounter this problem]
- Quote: "[Evidence]" - P[X]

**Secondary User:** [If applicable]
- [Brief description]

---

## Success Metrics (Proposed)

**Primary Metric:**
- [Measurable outcome] - Target: [X]
- Baseline: [Current state if known]

**Secondary Metrics:**
- [Metric 2] - Target: [Y]
- [Metric 3] - Target: [Z]

**How to Measure:**
[Analytics setup, tracking plan, validation method]

---

## Scope (Initial)

### ✅ In Scope (v1)
- [Core capability 1]
- [Core capability 2]
- [Core capability 3]

### 🔮 Future Scope (v2+)
- [Enhancement 1]
- [Enhancement 2]

### ❌ Explicitly Out of Scope
- [Edge case 1]
- [Feature X that was requested but not core]
- [Technical complexity Y to avoid now]

---

## Key Supporting Evidence

**From Analysis:** `/outputs/interviews/[project]/[project]-analysis.md`

### High-Confidence Insights
1. **[Insight Title]** (7/10 participants)
   - Finding: [1 sentence]
   - Quote: "[Evidence]" - P[X]

2. **[Insight Title]** (5/10 participants)
   - Finding: [1 sentence]
   - Quote: "[Evidence]" - P[Y]

### Pain Points Addressed
- **[Pain Point]** (Severity: High, 8/10 mentioned)
  - Current workaround: [How they cope]
  - Impact: [Business/user cost]

---

## Constraints & Context

**Technical Constraints:**
[User-added: Stack, APIs, integrations, performance]

**Business Constraints:**
[User-added: Budget, timeline, resources, compliance]

**Strategic Context:**
[User-added: How this fits company strategy, OKRs, roadmap]

**Dependencies:**
[User-added: Other features, systems, teams]

---

## Open Questions

**For PRD Development:**
- [ ] [Question about scope]
- [ ] [Question about technical approach]
- [ ] [Question about stakeholder alignment]

**For Design/Engineering:**
- [ ] [Technical feasibility question]
- [ ] [UX design question]

---

## Next Steps

✅ **Ready for `prd-creator` Skill**

**To create PRD:**
```
"Create PRD from starter brief: /outputs/interviews/[project]/[feature]-starter-brief.md"
```

**Recommended PRD Type:** [Lean/Traditional/Hybrid] (based on scope/complexity)

**Stakeholders to Involve:**
- Design: [For UX/UI]
- Engineering: [For technical feasibility]
- [Other teams as needed]

---

**Created from Interview Analysis:** [Date]
**Analysis:** `/outputs/interviews/[project]/[project]-analysis.md`
```

#### Step 4: Confirm & Bridge to PRD Creation

After creating starter briefs:

```
"✅ PRD Starter Briefs created:

1. /outputs/interviews/[project]/feature-a-starter-brief.md (P0)
2. /outputs/interviews/[project]/feature-b-starter-brief.md (P1)

These briefs are 80% done - perfect foundation for PRD creation!

Next steps:
- Use `prd-creator` Skill to turn briefs into full PRDs
- Command: 'Create PRD from starter brief: [path]'

Want to start with Feature A now?"
```

---

### Phase 5: Review & Iterate

1. **Show Report to User**
   - Highlight: Top 3 insights, confidence levels, gaps

2. **Feedback Loop**
   ```
   "Questions:
   - Do these insights match your gut feel?
   - Any surprises or misinterpretations?
   - Want deeper analysis on specific theme?
   - Need different format (e.g., presentation slides)?"
   ```

3. **Iterate if Needed**
   - Refine findings
   - Add missing context
   - Reframe recommendations

---

## Examples

### Example 1: Discovery Research

**Input:**
```
User: "Analyze my PM Tool interviews"
- Interview Guide: /outputs/interview-guides/pm-tool-discovery.md
- Files: 10 transcripts in /user_context/raw/interviews/pm-tool/
- Context: B2B SaaS, Scale-up PMs (50-200 employees)
```

**Process:**
1. Load guide → Goals: Understand Jira pain points, workflow inefficiencies
2. Analyze 10 transcripts → Extract insights per goal
3. Find patterns:
   - 8/10 mentioned "Jira comment chaos"
   - 6/10 mentioned "Confluence → Jira manual work"
4. Score confidence: High (frequent + consistent)
5. Generate report with quotes, recommendations

**Output:**
- `/outputs/interviews/pm-tool/pm-tool-analysis.md`
- Executive Summary: "Scale-up PMs waste 2-3h daily on Jira/Confluence manual work"
- Top Insight: "Comment management is #1 pain point (High Confidence, 8/10)"
- Recommendation: "Build Jira Comment Digest tool (High Impact, Medium Effort)"

**Phase 4.5 (PRD Opportunities):**
- Identified 2 PRD opportunities: "Jira Comment Digest" (P0), "Confluence-Jira Sync" (P1)
- User selected: "Jira Comment Digest"
- Created: `/outputs/interviews/pm-tool/comment-digest-starter-brief.md`
- User added constraints: "Must integrate with existing Jira API", "Target: <5min setup"
- Ready for `prd-creator` Skill!

### Example 2: Usability Testing

**Input:**
```
User: "Extract insights from prototype tests"
- Interview Guide: /outputs/interview-guides/checkout-flow-usability.md
- Files: 5 session notes in /user_context/raw/interviews/checkout-flow/
- Context: E-commerce checkout redesign, mobile users
```

**Process:**
1. Load guide → Test: New 3-step checkout vs. old 5-step
2. Analyze 5 sessions → UI feedback per screen
3. Find patterns:
   - 4/5 confused by payment screen layout
   - 5/5 loved progress indicator
   - 3/5 missed "Save for later" button
4. Map to goals: "Reduce cart abandonment" → Partially Answered

**Output:**
- Report with screen-by-screen feedback
- High Confidence: Progress indicator = win (keep!)
- Medium Confidence: Payment layout needs iteration (4/5 struggled)
- Recommendation: A/B test payment layout variants

---

## Configuration (Optional)

If user wants custom output format, check for:
`/outputs/interview-guides/[project-name].md` → Analysis Template section

Example template customization:
```markdown
## Analysis Configuration
focus_areas:
  - Pain Points (High Priority)
  - Jobs to be Done (Medium Priority)
  - Feature Requests (Low Priority)

confidence_threshold: Medium
quote_limit: 3 per insight
segment_analysis: true
segments: [B2B, B2C, Enterprise]
```

---

## Integration with Other Skills

**Upstream:**
- `interview-guide` Skill creates the research plan this Skill references

**Downstream:**
- `prd-creator` Skill can use **PRD Starter Briefs** for 80% head start
  - Phase 4.5 creates briefs → `prd-creator` loads them → fast PRD creation
  - Command: `"Create PRD from starter brief: /outputs/interviews/[project]/[feature]-starter-brief.md"`
- `user-stories` Skill can create tickets based on recommendations

**Cross-Reference:**
When creating interview guide, remind user:
> "After interviews, use `interview-analysis` Skill to synthesize insights!"

When analyzing interviews:
1. Reference original guide: `/outputs/interview-guides/[project].md`
2. Offer PRD Opportunities: "Want to create PRD Starter Briefs for these features?"
3. Bridge to PRD Creation: "Ready to create PRD from brief? Use `prd-creator` Skill!"

---

## Tips & Best Practices

**✅ DO:**
- **Verbatim Quotes are Evidence** → Always include for top insights
- **Frequency = Confidence** → "7/10 said X" > "Someone mentioned X"
- **Segment Analysis** → If data exists (B2B vs. B2C, roles, etc.)
- **Map to Goals** → Always tie findings back to original research goals
- **Actionable Recommendations** → "Prototype X" not "Consider exploring X maybe"
- **Highlight Gaps** → What you DIDN'T learn is as important as what you did

**❌ DON'T:**
- Ignore minority opinions (1/10 can be valid edge case!)
- Cherry-pick quotes that confirm bias
- Over-interpret anecdotal data (1 mention ≠ pattern)
- Skip confidence scoring (user needs to know certainty)
- Forget context (B2B PM ≠ B2C User, different needs!)

---

## File Structure

```
Product-Toolkit/
├── outputs/
│   └── interviews/
│       └── [project-name]/
│           ├── [project-name]-analysis.md
│           ├── feature-a-starter-brief.md  # PRD Starter Briefs
│           ├── feature-b-starter-brief.md
│           └── feature-c-starter-brief.md
└── user_context/
    └── raw/
        └── interviews/
            └── [project-name]/
                ├── session-1.txt
                ├── session-2.md
                ├── session-3.pdf
                └── ...
```

**Note:** Starter Briefs saved in SAME folder as analysis (no subfolder!) - keeps structure minimal.

---

## Troubleshooting

**Issue: Files not found**
→ Check: `/user_context/raw/interviews/[project-name]/` exists?
→ Ask user to confirm project name & file location

**Issue: No interview guide**
→ Can proceed without (create ad-hoc goals)
→ OR use `interview-guide` Skill to create one first

**Issue: Mixed formats hard to parse**
→ Ask user: "Can you provide .txt/.md versions? PDFs are trickier."
→ Use Read tool for PDFs (works but less reliable)

**Issue: Conflicting insights**
→ Flag in report: "3 said X, 2 said opposite → needs clarification"
→ Confidence: Medium or Low (uncertainty noted)

**Issue: Too many quotes**
→ Limit to 2-3 per insight (best/most representative)
→ More quotes in Appendix if needed

---

## Success Criteria

**Analysis complete when:**
- ✅ All interview files processed
- ✅ Goals from guide mapped to findings (or flagged as gaps)
- ✅ Patterns identified with frequency counts
- ✅ Confidence scored per insight
- ✅ Verbatim quotes included as evidence
- ✅ Actionable recommendations generated
- ✅ Report saved to `/outputs/interviews/[project]/`

**User should have:**
- Clear understanding of what was learned
- Confidence in findings (backed by frequency + quotes)
- Concrete next steps (recommendations)
- Awareness of gaps (what needs more research)

---

*Created with Product-Toolkit*
*Companion Skill: interview-guide*
