---
name: interview-guide
description: Creates user interview guides for product research (Discovery, Validation, Usability Testing). Use when user mentions "user interview", "interview guide", "create interview guide", "user research", "discovery interviews", "validation interviews", "usability testing", "customer conversations", or needs to prepare research sessions with users.
---

# Interview Guide Creation

## Instructions

1. **Clarify Research Goal**
   - Ask: Discovery (explore problems), Validation (test concepts), or Usability (test designs)?
   - Define specific research questions (NOT vague "understand users")
   - Example: "Why do users switch to competitor product X?"

2. **Identify Target Participants**
   - Who? (Persona, role, context)
   - How many? (5-15 for Discovery typical)
   - B2B or B2C? (affects approach & incentives)

3. **Choose Framework**
   - Discovery: Mom Test + JTBD
   - Validation: Concept Testing Framework
   - Usability: Think-Aloud Protocol

4. **Generate Interview Guide**
   - 4-Part Structure: Introduction → Warm-up → Main Questions → Wrap-up
   - Story-based questions ("Tell me about the last time you...")
   - Include Probes Bank

5. **Add Logistics**
   - Duration estimate (30-90 min depending on phase)
   - Roles (Moderator, Notetaker, Observer)
   - Materials needed
   - Consent script

6. **Output as Markdown File**
   - Save to `/outputs/interview-guides/`
   - Filename: `[Date]-[Topic]-Interview-Guide.md`
   - Include YAML front matter

---

## Phase-Specific Approaches

### Discovery Phase (Exploratory/Generative)
**Goal:** Problem understanding, opportunity identification, empathy building
**Duration:** 30-60 min
**Focus:** Problem space, NOT solutions
**Sample Size:** 5-15 participants (patterns emerge after ~5 interviews)

**Structure:**
- Introduction (5-10 min) - Rapport, Purpose, Consent
- Warm-up (5 min) - Background, easy questions
- Main Questions (30-40 min) - Story-based exploration
- Wrap-up (5 min) - "What else should I have asked?"

**Question Types:**
- "Describe a typical day with [context]"
- "Tell me about the last time you experienced [problem]"
- "What are your biggest frustrations with...?"
- "If you could change one thing, what would it be?"

**DON'Ts:**
- ❌ "What features do you want?" (Users are bad feature designers)
- ❌ Show solutions
- ❌ "Would you use X?" (hypothetical, unreliable)
- ❌ Jump to solutions too quickly

**Deliverables:** User Personas, Journey Maps, Problem Statements, Opportunity Areas

---

### Validation Phase (Concept Testing)
**Goal:** Test assumptions, validate problem-solution fit, prioritize features
**Duration:** 45-60 min
**Materials:** Mid-fidelity prototypes (NOT hi-fi!)

**Question Types:**
- "Walk me through what you see here"
- "What problem do you think this solves?"
- "How does this compare to your current approach?"
- "What would need to change for you to adopt this?"
- "Rate the likelihood that this replaces your current solution (1-10)"

**DO's:**
- ✅ Show concepts in real workflow context
- ✅ Have them compare to current solutions
- ✅ Test multiple variations
- ✅ Focus on Desirability AND Value

**DON'Ts:**
- ❌ "Would you use this?" (poor predictor)
- ❌ Use the word "validate" with users
- ❌ Test only one concept
- ❌ Over-design before validation

---

### Usability Testing Phase (Evaluative)
**Goal:** Assess how well designs work, identify usability issues
**Duration:** 30-60 min
**Method:** Think-Aloud Protocol

**Two Variants:**
- **Concurrent Think-Aloud (CTA):** Users verbalize DURING task completion
  - Pro: More complete
  - Con: Affects performance
- **Retrospective Think-Aloud (RTA):** Users explain AFTER tasks
  - Pro: Less interference
  - Con: Details get lost

**Best Practices:**
- Show demo video beforehand
- Give specific realistic tasks
- Frequently remind to think aloud
- When silent, prompt: "What are you thinking right now?"
- **DO NOT** interrupt or help
- Observe speech patterns (hesitation, frustration)
- Combine with post-task interview

**DON'Ts:**
- ❌ Lead to answers
- ❌ Interrupt flow
- ❌ Judge or correct
- ❌ Ask hypotheticals during tasks

---

## Core Frameworks

### Mom Test (Rob Fitzpatrick)
**The golden rule for unbiased interviews**

**3 Principles:**
1. **Talk about their life, NOT your idea**
2. **Ask about specifics in the PAST** (not opinions about future)
3. **Talk less, listen more**

**✅ RIGHT:**
- "Tell me about the last time you used Netflix – what happened?"
- "How do you solve this problem today?"
- "What alternatives have you tried?"

**❌ WRONG:**
- "Would you use Feature X?" (hypothetical)
- "How often do you use Netflix?" (generalized)
- "What do you think of this idea?" (biased)

**Why it works:** Stories are based on real memories with real context, not idealizations or socially desirable answers.

---

### JTBD Framework (Jobs-to-be-Done)
**For Software Adoption & Switching Behavior**

**Core Concept:** Users "hire" products to make progress toward goals. Focus on motivations, NOT features.

**Purchase Timeline (mapped backwards):**
```
Purchase ← Decision ← Active Looking ← Passive Looking ← First Thought
```

**Key Questions:**
- "When did you first realize you needed [category]?"
- "What was going on in your life at that time?"
- "What alternatives did you consider?"
- "What parameters did you compare?"
- "What was the final trigger for the purchase?"

**Duration:** 60-90 min for deep exploration
**Target Participants:** Users who RECENTLY started/stopped using product (not "want to buy"!)

**Focus:** Switching moments – "What made you switch?"

---

### Funnel Technique
**Structured question strategy: Broad → Specific → Deep**

**4 Steps:**
1. **Start broad:** "Tell me about a typical workday"
2. **Move to topic:** "How do you manage projects?"
3. **Get specific:** "What happens when deadlines change?"
4. **Go deep:** "Tell me more about that frustration"

**Why it works:** Establishes context before going deep. Avoids "cold start" with overly specific questions.

---

### Five Whys Technique
**Reach root causes through 5x "Why?"**

**Best Practices:**
- Explain technique BEFOREHAND (otherwise feels like interrogation)
- Use softer alternatives: "How so?" "Tell me more"
- Drill down to Level 3 (Patterns) or Level 4 (Mental Models)

**Example:**
```
Q: "Why do you use this app?"
A: "To track expenses"

Q: "Why track expenses?"
A: "To stay on budget"

Q: "Why is the budget important?"
A: "Saving for a house"

Q: "Why a house?"
A: "Family stability"
```
**Root Cause:** Family security (NOT expense tracking!)

---

## Probes Bank (Ready-to-Use)

**Essential Probes (always have these ready!):**
- "Tell me more about that"
- "Why is that important to you?"
- "Can you give me an example?"
- "Help me understand this better"
- "What do you mean by [term]?"
- "What happened next?"
- "How did that make you feel?"

**The most critical rule:**
🔥 **Endure 10-20 seconds of silence after answers** → Participants often fill it with deeper insights!

---

## Bias Avoidance (Top 6)

### 1. Confirmation Bias
**Problem:** Interpreting for pre-beliefs
**Solution:** Open mind, seek multiple perspectives, play devil's advocate

### 2. Leading Questions
**❌ Wrong:** "Didn't you find that easy?"
**✅ Right:** "How would you rate that on a scale of 1-10?"

### 3. Social Desirability Bias
**Problem:** Users answer to please
**Solution:** Explicitly state "no right/wrong", keep purpose vague

### 4. Politeness Bias
**Problem:** Positive answers to avoid conflict
**Solution:** Downplay your own expertise ("I'm not the designer"), neutral setting

### 5. Framing Effect
**Problem:** Question wording influences answers
**Solution:** Standardized neutral phrasing, A/B-test questions in pilot

### 6. Sponsor Bias
**Problem:** Research sponsor known → biased answers
**Solution:** Generic descriptions ("We're researching project management" instead of "We're building Tool X")

---

## Interview Guide Template

Use this template for all guides:

```markdown
---
research_goal: [Discovery/Validation/Usability]
target_participants: [Who will be interviewed?]
session_duration: [30/45/60/90 min]
interviewer: [Name]
notetaker: [Name]
observers: [Names, max 3 total]
date: [YYYY-MM-DD]
framework: [Mom Test / JTBD / Think-Aloud]
---

# Interview Guide: [Title]

## Research Questions
1. [Specific question 1 - NOT "understand users"]
2. [Specific question 2]
3. [Specific question 3]

## Target Participants
- **Who:** [Persona, Role, Context]
- **Screener Criteria:** [Behavior-based, NOT just demographics]
- **Sample Size:** [5-15 for Discovery typical]
- **Incentive:** [$50-100 B2C / $100-300+ B2B]

---

## Introduction (5-10 min)

### Consent & Recording
"Thanks for joining! This session helps us [Purpose - keep VAGUE, don't reveal hypotheses].

May I record this? Your data will be anonymized and used internally only. You can stop at any time or skip any question.

[WAIT FOR EXPLICIT YES]"

### Rapport Building
"Tell me a bit about yourself – what do you do professionally / in your free time?"

[GOAL: 2-3 min casual conversation before getting serious]

---

## Warm-up (5 min)

**Background Questions (easy to answer):**
- [Clarify role/responsibilities]
- [Establish context]
- [No difficult/deep questions yet!]

**Example:**
- "How long have you been in this role?"
- "What does a typical day look like for you?"

---

## Main Questions (30-40 min)

### [Topic 1: Name]
**Core Question (story-based!):**
"Tell me about the last time [specific past event]"

**Probes:**
- "What happened next?"
- "Why was that important to you?"
- "Can you give me an example?"
- [Endure 10-20 seconds of silence!]

---

### [Topic 2: Name]
**Core Question:**
[...]

**Probes:**
[...]

---

### [Topic 3: Name]
**Core Question:**
[...]

**Probes:**
[...]

---

## Wrap-up (5 min)

### Critical Question
"What else should I have asked? What's important that we didn't discuss?"

🔥 **→ Endure 15-20 seconds of SILENCE – they often add valuable insights!**

### Thank & Next Steps
"Thank you so much for your time and openness! We'll follow up in [timeframe] with results / an update."

[Pay incentive if applicable]

---

## Logistics

**Roles:**
- **Moderator:** [Name] - Leads conversation, asks questions, takes NO detailed notes themselves
- **Notetaker:** [Name] - Verbatim transcripts, timestamps
- **Observers:** [Names] - Max 3 total, silent, for holistic impressions

**Materials Needed:**
- [ ] Interview Guide printed
- [ ] Consent Form
- [ ] Recording Setup (Zoom / Audio Recorder)
- [ ] Backup Recording Device
- [ ] Probes Bank visible for Moderator
- [ ] [Prototypes/Materials if Validation/Usability]

**Timing:**
- [ ] 30-min buffer before/after session
- [ ] Max 3-4 sessions/day/moderator (avoid burnout)

**Post-Session:**
- [ ] Immediate debrief with team (5-10 min)
- [ ] Backup recording
- [ ] Structure notes within 24h
```

---

## Logistics Checklist

### Preparation Timeline (4-6 weeks)

**Week 1-2: Strategy & Guide**
- [ ] Conduct stakeholder interviews
- [ ] Formulate specific research questions
- [ ] Create first interview guide
- [ ] **Pilot with 1-2 people** (reveals problems!)

**Week 3: Recruitment**
- [ ] Book 30% more participants than needed (for no-shows!)
- [ ] Create screener (<10 questions, behavior-focused)
- [ ] Choose platform: User Interviews, Respondent, Ethnio
- [ ] Set incentives (B2C $50-100, B2B $100-300+)

**Week 4: Team Briefing & Materials**
- [ ] Clearly assign roles (Moderator/Notetaker/Observer)
- [ ] Acquire & test tools
- [ ] Prepare consent forms
- [ ] Review final guide with team

### Roles (clearly assign!)

**Moderator:**
- Leads conversation
- Asks questions
- Takes **NO** extensive notes themselves (splits attention!)
- Maintains rapport
- Avoids Top 5 mistakes (see below)

**Notetaker (1-2 people):**
- Verbatim transcripts
- Timestamps for important moments
- Paraphrase with meaning-preservation
- Direct quotes verbatim when impactful
- Include context (notes standalone understandable)

**Observer (1-2 Stakeholders, MAX 3 total):**
- Silent during session
- Holistic impressions
- No interruptions
- Contribute to post-session debrief

### Materials Checklist

**Essential:**
- [ ] Interview Guide printed
- [ ] Probes Bank visible for Moderator
- [ ] Recording Setup (Zoom with transcription / Audio Recorder)
- [ ] Backup Recording Device (Smartphone)
- [ ] Consent Form

**Optional (depending on phase):**
- [ ] Prototypes (Validation/Usability)
- [ ] Task Sheets (Usability)
- [ ] Laptop + Screen Share Setup
- [ ] Beverages (if in-person)

### Session Best Practices

**Timing:**
- [ ] 30-min buffer between sessions (moderator refocus!)
- [ ] Max 3-4 sessions/day/moderator
- [ ] Don't schedule too many sessions in a row (burnout!)

**During Session:**
- [ ] Get recording permission (EXPLICITLY!)
- [ ] Endure silence (10-20 sec after answers)
- [ ] Don't multitask
- [ ] If diverging: guide back to guide
- [ ] Use probes for superficial answers

**Post-Session:**
- [ ] Immediate 5-10 min team debrief (impressions fresh!)
- [ ] Backup recording
- [ ] Structure notes within 24h
- [ ] Mark key quotes & timestamps

---

## B2B vs. B2C Considerations

### B2B Interviews

**Characteristics:**
- Smaller, harder to reach population
- Higher incentives: **$100-$300+/hour** (1.5x hourly rate)
- Longer lead times (2-4 weeks planning)
- Understand organizational hierarchy
- Multi-stakeholder decision-making

**Interview Focus:**
- **Understand roles:** User ≠ Purchaser ≠ Decision-Maker
- **Workflows:** Business-process-fit critical
- **Buying Process:** Multi-stakeholder, budget approvals
- **Contextual Inquiry:** Essential (in work environment!)
- **Interview BOTH:** End Users AND Decision-Makers

**Recruitment:**
- Use sales team relationships
- LinkedIn outreach
- Industry events
- Existing customer base

---

### B2C Interviews

**Characteristics:**
- Larger population
- Easier recruitment
- Lower incentives: **$50-$100**
- Individual decision-making
- Faster turnaround

**Interview Focus:**
- Personal needs & pain points
- Emotions & motivations
- Usage context (where/when/how)
- Social influences
- Habits & routines

**Recruitment:**
- User Interviews Platform
- Social Media Ads
- Intercept Surveys
- Existing User Base

---

## Top 5 Facilitator Mistakes (Avoid!)

### 1. Insufficient Rapport-Building
**Problem:** Cold start, user doesn't open up
**Solution:** 5-10 min warm-up mandatory, establish personal connection

### 2. Not Enough Probing
**Problem:** Superficial answers, no depth
**Solution:** Keep Probes Bank visible, endure 10-20 sec silence

### 3. Multitasking During Interview
**Problem:** Splits attention, loses rapport
**Solution:** Use recording OR notetaker, NOT both yourself

### 4. Poorly Managed Observers
**Problem:** Too many people, interruptions, user feels uncomfortable
**Solution:** Max 3 observers, clarify roles beforehand, silent rule

### 5. Leading Questions
**Problem:** Biased answers, only confirms pre-beliefs
**Solution:** Stay neutral, keep purpose vague, "no right/wrong"

---

## Remote vs. In-Person

### Remote Interviews
**Advantages:**
- ✅ Lower costs (no travel)
- ✅ Geographic flexibility
- ✅ Easier recording (Zoom transcription)
- ✅ More sessions/day possible

**Disadvantages:**
- ❌ Tech dependency (internet issues)
- ❌ Harder to read non-verbal cues
- ❌ Less natural rapport
- ❌ Distractions in home office

**Best Practices:**
- Zoom/Teams with built-in transcription
- Backup recording (OBS Studio)
- Screen share for prototypes
- Camera ON for both sides

---

### In-Person Interviews
**Advantages:**
- ✅ Better rapport
- ✅ Easier to observe non-verbal cues
- ✅ Natural context (work environment!)
- ✅ Less tech dependency

**Disadvantages:**
- ❌ Higher costs (travel, location)
- ❌ Geographically limited
- ❌ More complex setup
- ❌ Fewer sessions/day

**Best Practices:**
- In natural work environment if possible
- Audio recorder + backup (smartphone)
- Provide beverages
- Quiet, neutral room

---

## Example: Discovery Interview Guide

```markdown
---
research_goal: Discovery
target_participants: Product Managers in Scale-ups (50-200 employees)
session_duration: 60 min
interviewer: Hendrik
notetaker: TBD
date: 2025-10-25
framework: Mom Test + JTBD
---

# Interview Guide: PM Tool Pain Points Discovery

## Research Questions
1. What are the biggest frustrations for PMs in their daily work?
2. What workarounds do they currently use?
3. Where is the biggest time sink?

## Target Participants
- **Who:** Product Managers, Scale-ups (50-200 employees)
- **Screener:** Works daily with Jira/Confluence, min. 2 years PM experience
- **Sample Size:** 10 interviews
- **Incentive:** $100 (B2B)

---

## Introduction (5 min)

"Thanks for joining! We're researching how Product Managers organize their daily work – nothing to sell, just learning.

May I record this? Everything stays anonymous, for internal analysis only.

Tell me briefly about yourself – what do you do, how long have you been a PM?"

---

## Warm-up (5 min)

- "How big is your team?"
- "What tools do you currently use?"
- "How long have you been in this role?"

---

## Main Questions (40 min)

### Typical Workflow
**Question:**
"Describe a typical workday – from morning to evening. What do you do?"

**Probes:**
- "What happens when an urgent bug comes up?"
- "How do you coordinate with the dev team?"
- "Where do you spend most of your time?"

---

### Last Frustration
**Question:**
"Tell me about the last time you were really frustrated in your product work – what happened?"

**Probes:**
- "What would you have needed to avoid that?"
- "How did you solve it?"
- "How often does something like this happen?"
- [Endure 15 sec silence!]

---

### Tools & Workarounds
**Question:**
"Tell me about the last time a tool let you down – what were you trying to do, what happened?"

**Probes:**
- "What alternatives have you tried?"
- "What makes a tool indispensable for you?"
- "What workarounds have you developed?"

---

### Jira Comment Chaos (Specific Pain Point)
**Question:**
"How do you handle Jira comments? Tell me about the last time you had to search for important info in comments."

**Probes:**
- "How long did that take?"
- "What was frustrating about it?"
- "How would you ideally solve this?"

---

## Wrap-up (5 min)

"What else should I have asked? What's important for your product work that we didn't discuss?"

[20 sec SILENCE]

"Awesome, thanks for your openness! I'll follow up in 2 weeks with insights from all interviews."

---

## Logistics

**Roles:**
- Moderator: Hendrik
- Notetaker: TBD
- Observers: None (1:1 better for openness)

**Materials:**
- [ ] Interview Guide printed
- [ ] Zoom Recording + Transcription
- [ ] Backup Audio (Smartphone)
- [ ] Probes Bank in front of me
- [ ] Consent Form

**Post-Session:**
- [ ] 5 min notes review
- [ ] Backup recording
- [ ] Extract key quotes
```

---

## Analysis Configuration (Optional)

**Add this section to interview guide if you want custom analysis output:**

```markdown
## Analysis Configuration
*For use with interview-analysis Skill*

**Input Location:**
- Raw files: `/user_context/raw/interviews/[project-name]/`
- Expected formats: .txt, .md, .pdf

**Analysis Focus:**
focus_areas:
  - Pain Points (High Priority)
  - Jobs to be Done (Medium Priority)
  - Feature Requests (Low Priority)

**Settings:**
- confidence_threshold: Medium (only report Medium+ confidence insights)
- quote_limit: 3 per insight (max verbatim quotes)
- segment_analysis: false (or true if tracking B2B vs. B2C, roles, etc.)

**Expected Participants:** [Number, e.g., 10]
**Segments (if applicable):** [e.g., "B2B Enterprise, B2B Scale-up, B2C"]
```

**Why useful:**
- Guides `interview-analysis` Skill on what to prioritize
- Sets expectations for output format
- Defines segments if needed (B2B vs. B2C, roles, etc.)

---

## Next Steps After Guide Creation

1. **Pilot with 1-2 People**
   - Test all questions
   - Check timing
   - Identify confusing wording
   - Adjust before real sessions

2. **Recruit Participants**
   - Use screener
   - Book 30% more than needed
   - Send confirmation 24h before

3. **Brief Team**
   - Roles clear
   - Observer rules
   - Test tools

4. **Create Interview Folders**
   - Input: `/user_context/raw/interviews/[project-name]/`
   - Output: `/outputs/interviews/[project-name]/`

5. **Run Sessions**
   - Follow guide (but stay flexible!)
   - Use probes
   - Endure silence
   - Save transcripts/notes to input folder

6. **Synthesize Findings**
   - **Use Skill:** `interview-analysis` (automated synthesis!)
   - OR manual: Affinity Mapping, Thematic Analysis
   - Output: `/outputs/interviews/[project-name]/[project]-analysis.md`

---

## Integration with Other Skills

**Downstream:**
- **`interview-analysis` Skill** - Analyzes interview outputs against this guide
  - References research goals from this guide
  - Maps findings to questions
  - Generates synthesis report

**Workflow:**
1. Create guide with `interview-guide` Skill → `/outputs/interview-guides/`
2. Run interviews → Save to `/user_context/raw/interviews/[project]/`
3. Analyze with `interview-analysis` Skill → `/outputs/interviews/[project]/`

---

*Based on Nielsen Norman Group, Teresa Torres, Rob Fitzpatrick (Mom Test), JTBD Framework, IDEO*
*Created with Product-Toolkit*
*Companion Skill: interview-analysis*
