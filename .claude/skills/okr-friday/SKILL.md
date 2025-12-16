---
name: okr-friday
description: >
  Weekly Friday Celebration check-in for OKRs. Use when user mentions "Friday", "End of week",
  "OKR Review", "Friday Wins", "Weekly Review", or at the end of each week to celebrate progress.
---

# Friday Celebration - Weekly OKR Check-in

Facilitate a **15-minute** Friday afternoon check-in to celebrate wins and capture learnings (Wodtke's Weekly OKR Cadence).

## Instructions

### 1. Identify Active OKR File
**First, read:** `/outputs/okrs/CURRENT_WEEK.md`

**Extract from front matter:**
- `quarter:` field (e.g., `Q1 2026`, `Q4 2025`)
- Convert to filename: `Q1-2026-OKRs.md`, `Q4-2025-OKRs.md`

**Main OKR file:** `/outputs/okrs/[QX-YYYY]-OKRs.md`

### 2. Identify Current Week
- What's today's date?
- Which week are we closing? (Calculate from quarter start date in CURRENT_WEEK.md)

### 3. Read Current OKRs & Monday Commitments
**Load:** `/outputs/okrs/[QX-YYYY]-OKRs.md` (from Step 1)

**Find:**
- This week's Monday Commitments
- All Key Results (current scores)
- Confidence levels from Monday

### 4. Check What Got Done
- "Let's look at what you committed to Monday..."
- "Which did you complete? Which didn't happen?"
- Mark checkboxes: `[ ]` → `[x]` for completed

### 5. Celebrate & Learn
**Ask:**
- "What are you celebrating this week?" (big & small wins!)
- "What worked this week?"
- "What didn't work?"
- "What will you do differently next week?"

**Celebrate everything:**
- Completed actions
- Progress (even 5%)
- Learning ("X doesn't work" is a win!)

### 6. Update Progress
**For EACH KR:**
- "Did this KR move forward this week? By how much?"
- Update "Current" values in the file

### 7. Update OKR File
Update `/outputs/okrs/[QX-YYYY]-OKRs.md` (the active OKR file from Step 1):

**Weekly section:**
```markdown
### Week X (Date Range)

**Monday Commitments:**
- [x] KR1: [completed action]
- [ ] KR2: [not done action]

**Confidence Update:**
[keep from Monday]

**Friday Wins & Learning:**
- 🎉 [Win 1]
- 🎉 [Win 2]
- 📚 Learned: [Learning 1]
- ⚠️ [Blocker if any]
```

**KR section (top of file):**
- Update "Current" values for each KR

### 8. Update CURRENT_WEEK.md
**IMPORTANT:** Update `/outputs/okrs/CURRENT_WEEK.md` with:

- Mark completed checkboxes [x]
- Update "Current Progress" for each KR
- Prepare for next week (move to Week N+1 if next week starts)

**This keeps the current week view accurate!**

### 9. Summarize & Close
**Provide:**
- 2-3 key wins highlighted
- 1-2 key learnings captured
- "Great week! See you Monday!"

**Keep it SHORT - 15 min max!**

---

## Example

**User:** "Friday Wins!"

**You:**
```
Happy Friday! 🎉 Let's celebrate - 15 min!

We're closing Week 3 (Nov 4-8) of Q4 2025.

**Monday's Commitments:**
- KR1: Follow-up to Client A, pricing call with Client B
- KR2: Write 3 LinkedIn posts, engage 10 competitor posts
- KR3: Send NPS survey, start case study outline
- KR4: Finalize workshop deck, outreach 5 warm leads

**What got done? What didn't?**

[User responds, you mark checkboxes...]

**Let's celebrate - what are your WINS this week?**

[User responds...]

🎉 Awesome wins:
- Client A proposal sent (KR1 progress!)
- 3 LinkedIn posts published (KR2 commitment crushed!)
- Case study outline started (KR3 moving!)

**What did you LEARN this week?**

[User responds...]

📚 Key learnings:
- Demos in proposals convert better than text
- LinkedIn posts on Tuesday get 2x engagement
- Need simpler NPS tool (current one too clunky)

**Did any KRs move forward numerically?**

[User responds...]

Progress updates:
- KR1: €2K → €3K MRR (Client X signed!)
- KR2: 2 → 4 calls (2 more booked!)
- KR3: NPS survey ready
- KR4: Workshop deck 80% done

✅ Updated!

**Great week!** Key wins: Client X signed (€3K MRR!), 4 discovery calls, LinkedIn momentum!

Enjoy your weekend - see you Monday! 🚀
```

---

## File Reference

**Determine active OKR file:**
1. Read `CURRENT_WEEK.md` → extract `quarter:` from front matter
2. Construct filename: `Q1 2026` → `Q1-2026-OKRs.md`

**Update (2 files!):**
1. `/outputs/okrs/[QX-YYYY]-OKRs.md` (main OKR file - archive of all weeks)
   - Weekly section (checkboxes + Wins & Learning)
   - KR section (Current values)
2. `/outputs/okrs/CURRENT_WEEK.md` (current week only - Single Source of Truth!)
   - Mark checkboxes complete
   - Update progress

**CRITICAL:** Both files must be updated every Friday!

**Never:**
- ❌ Change target numbers
- ❌ Edit OKRs themselves
- ❌ Skip weeks
- ❌ Forget to update CURRENT_WEEK.md!

---

*Friday Celebration Skill - Wodtke's Weekly Cadence*
