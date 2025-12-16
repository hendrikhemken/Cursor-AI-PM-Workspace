# OKR Templates

Ready-to-use templates for OKR creation and tracking.

---

## [QX-YYYY]-OKRs.md (Main OKR File)

This is the **main archive** containing all weeks and full OKR details.

**Naming Convention:** `Q1-2026-OKRs.md`, `Q4-2025-OKRs.md`, etc.

```markdown
---
quarter: [QX YYYY]  # e.g., Q1 2026, Q4 2025
period: [Start Date] - [End Date]
duration: [X] weeks
type: company
owner: [Name]
approach: Wodtke (Weekly Rhythm) / Klau (Quarterly Grading)
confidence: X/10
status: active
created: YYYY-MM-DD
last_updated: YYYY-MM-DD
---

# [QX YYYY] OKRs - [Company Name]
*[Duration] weeks to [Goal]*

---

## 🎯 OBJECTIVE

**"[Inspirational, time-bound objective]"**

**Why this focus:**
- [Reason 1]
- [Reason 2]

**Success means:**
- [Success criteria 1]
- [Success criteria 2]

---

## 📊 KEY RESULTS

### KR1: [Title]
**Target:** [Measurable target]

- **Start:** [Starting value]
- **Target:** [End value by date]
- **Confidence:** X/10
- **Why:** [Why this matters]

**Current:** [X] | Target: [Y]

---

### KR2: [Title]
**Target:** [Measurable target]

- **Start:** [Starting value]
- **Target:** [End value by date]
- **Confidence:** X/10
- **Why:** [Why this matters]

**Current:** [X] | Target: [Y]

---

### KR3: [Title]
**Target:** [Measurable target]

- **Start:** [Starting value]
- **Target:** [End value by date]
- **Confidence:** X/10
- **Why:** [Why this matters]

**Current:** [X] | Target: [Y]

---

## 🔄 Weekly Cadence (Wodtke Style)

### Monday Commitments (15 min)
**"What are we doing THIS WEEK for these OKRs?"**

- Update confidence level (0.0-1.0) for each KR
- Pick 1-3 concrete actions per KR
- Write down commitments

### Friday Celebrations (15 min)
**"What did we accomplish? What did we learn?"**

- Mark wins (even small ones!)
- Update progress on KRs
- Learning: What's working? What's not?
- Adjust next week's approach

**Without weekly cadence → OKRs die!** (Wodtke's #1 Rule)

---

## 📅 Weekly Tracking

### Week 1 ([Date Range])

**Monday Commitments:**
- [ ] KR1: [concrete action]
- [ ] KR2: [concrete action]
- [ ] KR3: [concrete action]

**Confidence Update:**
- KR1: X/10 → __/10
- KR2: X/10 → __/10
- KR3: X/10 → __/10

**Friday Wins & Learning:**
- 🎉 [Win 1]
- 📚 [Learning 1]

---

### Week 2 ([Date Range])

[...repeat for all weeks...]

---

## 📈 End-of-Quarter Grading ([End Date])

**Final Scores:**
- KR1: __.__
- KR2: __.__
- KR3: __.__

**Overall Score:** __.__ / 1.0

**Wodtke Grading:**
- 0.6-0.7 = SUCCESS! 🎉
- 0.8-1.0 = Too conservative (sandbagging)
- 0.0-0.4 = Missed (but learned!)

**Retrospective:**
- What worked?
- What didn't?
- What did we learn?
- What's next for [Next Quarter]?

---

## 🚨 Critical Reminders

### Wodtke's 5 Deadly Mistakes (AVOID!)
1. ❌ **Set & Forget** → Weekly tracking is NON-NEGOTIABLE!
2. ❌ **Goal-of-Week Whiplash** → Don't change OKRs mid-quarter!
3. ❌ **Too Many OKRs** → 1 Objective, 3-5 KRs max!
4. ❌ **Micromanaging** → Trust yourself, focus on outcomes
5. ❌ **All at Once** → Start with pilot, iterate!

### Red Team Check
**Ask yourself weekly:**
- Can I game these KRs? (If YES → add quality gates!)
- Can I achieve this without business impact? (If YES → rewrite!)
- Am I measuring activities or outcomes? (Outcomes only!)

### OKRs ≠ Performance Review
**Remember:**
- OKRs = Stretch goals (designed to sometimes fail)
- Performance = Job expectations (must hit)
- NEVER conflate them or you'll sandbag immediately!

---

*Full OKR File Template*
```

---

## CURRENT_WEEK.md (Lightweight Current Week View)

This is the **Single Source of Truth for the current week** - automatically loaded in every session via `@import`.

**Location:** `/outputs/okrs/CURRENT_WEEK.md`

**Purpose:**
- Lightweight view (50 lines vs 300 lines!)
- Always visible in Claude's context
- Updated every Monday (commitments) & Friday (wins)
- Keeps User and Claude aligned on weekly focus

```markdown
---
week: [number]
period: [date range]
quarter: [QX YYYY]  # CRITICAL: This links to the main OKR file!
owner: [Name]
updated: YYYY-MM-DD
---

# Current Week OKRs - [Company Name]
*Week X of Y - QZ 2025*

---

## 🎯 This Week's Commitments

**Focus:** [One-line focus statement for the week]

- [ ] **KR1:** [Concrete action 1]
- [ ] **KR1:** [Concrete action 2]
- [ ] **KR2:** [Concrete action 1]
- [ ] **KR2:** [Concrete action 2]
- [ ] **KR3:** [Concrete action 1]

---

## 📊 Current Progress

### KR1: [Title]
**Progress:** [X] / [Y] ([%])
**Confidence:** X/10 [↑/↓/=] (was Y/10)
**Status:** [One-line status note - what's happening this week?]

### KR2: [Title]
**Progress:** [X] / [Y] ([%])
**Confidence:** X/10 [↑/↓/=] (was Y/10)
**Status:** [One-line status note]

### KR3: [Title]
**Progress:** [X] / [Y] ([%])
**Confidence:** X/10 [↑/↓/=] (was Y/10)
**Status:** [One-line status note]

---

## 💡 Quick Reference

**Objective:** "[Objective]"
**Overall Confidence:** X.X/10 (Perfect Wodtke zone!)
**This Week's North Star:** [What's the ONE thing that matters most?]

---

*Updated every Monday (Commitments) & Friday (Wins/Learning)*
*Full OKRs: /outputs/okrs/[QX-YYYY]-OKRs.md*
```

---

## Usage Notes

### When okr-expert Creates OKRs

**Creates 2 files:**
1. `/outputs/okrs/[QX-YYYY]-OKRs.md` (main archive, all weeks – e.g., `Q1-2026-OKRs.md`)
2. `/outputs/okrs/CURRENT_WEEK.md` (Week 1 initialized, `quarter:` field links to main file)

### When okr-monday Updates (Every Monday)

**Determines active file from CURRENT_WEEK.md, then updates 2 files:**
1. `/outputs/okrs/[QX-YYYY]-OKRs.md` (Week X section)
2. `/outputs/okrs/CURRENT_WEEK.md` (new commitments, move to Week X+1)

### When okr-friday Updates (Every Friday)

**Determines active file from CURRENT_WEEK.md, then updates 2 files:**
1. `/outputs/okrs/[QX-YYYY]-OKRs.md` (mark checkboxes, add wins/learning)
2. `/outputs/okrs/CURRENT_WEEK.md` (mark checkboxes, update progress)

---

## File Relationship

```
[QX-YYYY]-OKRs.md (Archive)     ← e.g., Q1-2026-OKRs.md
    ↓
CURRENT_WEEK.md (View)          ← quarter: field points to active file
    ↓
Claude's Context (@import in CLAUDE.md)
    ↓
Proactive OKR-Awareness in Sessions
```

**Key Principle:** Single Source of Truth
- Main data lives in `[QX-YYYY]-OKRs.md` (named by quarter)
- CURRENT_WEEK.md is a **derived view** (current week only)
- `quarter:` field in CURRENT_WEEK.md determines which main file is active
- Both updated in sync by Skills (Monday/Friday)

---

*OKR Templates - Product-Toolkit*
*Based on Wodtke & Klau Best Practices*
