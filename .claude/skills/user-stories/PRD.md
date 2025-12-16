# PRD → User Stories Workflow

Systematically convert Product Requirements Documents (Confluence, Google Docs, Notion) into User Stories.

---

## 🎯 Workflow Overview

**Input:** Product Requirements Document (PRD)
**Output:** Series of User Stories (INVEST-compliant, ready for Jira)

**Supported Formats:**
- ✅ Confluence Page (Copy-paste or URL)
- ✅ Google Docs (URL or export)
- ✅ Markdown Files (.md)
- ✅ Notion Pages (export)
- ✅ Plain Text / Chat Description

---

## 🚀 Workflow (Step-by-Step)

### Phase 1: Receive PRD Input

**Ask the PM:**

```
"Cool! Let's turn the PRD into User Stories.

How would you like to give me the PRD?

1. Confluence URL (if accessible)
2. Copy-paste the content here
3. Markdown File (.md export)
4. Screenshot of the PRD
5. Just describe it to me in chat

What works best?"
```

**Input Options:**

#### Option 1: Confluence URL
```
User: "https://yourcompany.atlassian.net/wiki/spaces/PROD/pages/123456/Feature-X"

→ Use WebFetch (if public or authenticated)
→ Extract content
```

#### Option 2: Copy-Paste
```
User: [Copies Confluence content directly]

→ Parse the pasted content
→ Handle Confluence-specific formatting
```

#### Option 3: Markdown File
```
User: "Here's the PRD: /path/to/prd.md"

→ Read File
→ Parse Markdown Structure
```

#### Option 4: Screenshot
```
User: [Screenshot of Confluence Page]

→ OCR / Image-to-Text (Claude can read images!)
→ Parse extracted text
```

#### Option 5: Chat Description
```
User: "The feature should... [description]"

→ Conduct structured interview
→ Build PRD structure in chat
```

---

### Phase 2: PRD Analysis & Understanding Structure

**What you need to extract from the PRD:**

#### 1. Problem Statement
```
❓ What problem are we solving?
❓ Why is this important?
❓ What's the opportunity?
```

#### 2. Target Users
```
❓ Who are the users? (Persona)
❓ What's their current pain point?
❓ What's the expected outcome?
```

#### 3. Features & Requirements
```
❓ What are the Must-Have features?
❓ What are Nice-to-Have features?
❓ What is explicitly OUT OF SCOPE?
```

#### 4. Success Criteria
```
❓ How do we measure success? (Metrics)
❓ What's the Definition of Done?
❓ What Acceptance Criteria exist?
```

#### 5. Constraints & Dependencies
```
❓ Technical Constraints? (API Limits, Legacy)
❓ Time Constraints? (Deadline, Launch Date)
❓ External Dependencies? (3rd Party APIs, other teams)
```

#### 6. User Journey / Use Cases
```
❓ What's the Happy Path?
❓ What Alternative Paths exist?
❓ What Edge Cases?
```

---

### Phase 3: PRD Parsing (Confluence-specific)

**Recognize Confluence Structure:**

#### Typical PRD Structure in Confluence:

```markdown
# [Feature Name]

## Problem Statement
[Description of the problem]

## Target Users
- User Persona 1
- User Persona 2

## Requirements
### Must-Have
- Requirement 1
- Requirement 2

### Nice-to-Have
- Requirement 3

## User Flows
1. User does X
2. System shows Y
3. User does Z

## Success Metrics
- Metric 1: Target
- Metric 2: Target

## Technical Considerations
[Tech Stack, APIs, etc.]

## Out of Scope
- Feature X (for later)
```

**Your Task:**
1. Parse the structure (Headings, Lists, Tables)
2. Extract Requirements & Features
3. Identify User Value Points
4. Map to potential User Stories

---

### Phase 4: Map Requirements → User Stories

**Mapping Logic:**

#### 1. Feature-based Mapping (Standard)

```
PRD Requirement:
"Users should be able to export their data as CSV"

→ Story:
"As a user I want to export my data as CSV
to analyze it in Excel"
```

#### 2. User Journey-based Mapping

```
PRD User Flow:
1. User uploads file
2. System validates file
3. System shows preview
4. User confirms
5. System processes

→ Stories:
Story 1: "As a user I want to upload files..."
Story 2: "As a user I want to see a preview..."
Story 3: "As a user I want to see processing status..."
```

#### 3. Epic vs. Story Decision

```
PRD Feature: "Complete Payment Integration"

→ Too big for one story!
→ Create Epic + breakdown into Stories

Epic: "Payment Integration"
├── Story 1: "As a user I want to pay with credit card..."
├── Story 2: "As a user I want to see payment status..."
└── Story 3: "As a user I want to receive invoice via email..."
```

---

### Phase 5: Write User Stories

**For each identified story:**

```markdown
# Story Title

**As** [Persona from PRD]
**I want** [Feature/Capability]
**to** [Business Value / Outcome from PRD]

---

## Acceptance Criteria

(Extracted from PRD Requirements)

- [ ] Given [Context] When [Action] Then [Expected Outcome]
- [ ] Given [Context] When [Action] Then [Outcome]
- [ ] Given [Context] When [Action] Then [Outcome]

---

## Technical Notes

(Extracted from PRD Technical Section)

**Frontend:**
- [UI Components from PRD]

**Backend:**
- [API Requirements from PRD]
- [3rd Party Integrations]

**Database:**
- [Data Model from PRD]

---

## Edge Cases

(Extracted from PRD Use Cases / Edge Cases)

- [ ] Edge Case 1
- [ ] Edge Case 2

---

## PRD Reference

**Source:** [Confluence Page URL / Title]
**Section:** [Which section of PRD]
**Original Requirement:** "[Quote from PRD]"

---

## Story Points

[Estimate based on Complexity from PRD]
```

---

### Phase 6: INVEST Check (Quality Gate)

**For EVERY story:**

```
✅ Independent? Can be implemented on its own?
✅ Negotiable? Details still negotiable?
✅ Valuable? User Value from PRD clear?
✅ Estimable? Enough info to estimate?
✅ Small? Max 8 Story Points?
✅ Testable? Acceptance Criteria clear?

If NO → Revise the story!
```

---

### Phase 7: Output & Jira Creation

**Output for PM:**

```
📋 PRD Analysis: [PRD Title]

Identified:
- 🎯 Problem: [Brief summary]
- 👥 Users: [Personas]
- 📊 Success Metrics: [Metrics from PRD]

Stories created: 8

Frontend (3):
- Story 1: As [User] I want... (3 Points)
- Story 2: As [User] I want... (5 Points)
- Story 3: As [User] I want... (2 Points)

Backend (3):
- Story 4: As [User] I want... (5 Points)
- Story 5: As [User] I want... (3 Points)
- Story 6: As [User] I want... (8 Points)

QA (2):
- Story 7: E2E Tests for... (3 Points)
- Story 8: Performance Tests... (5 Points)

Total: 34 Story Points (~2 Sprints for 1 Dev)

Should I create the stories in Jira? (Project: PROD)
```

**When User says "Yes":**
→ Batch Create via `jira_batch_create_issues`
→ Optional: Create Epic first (if appropriate)
→ Link Stories to Epic

---

## 🔍 Confluence-specific Parsing Tips

### Recognize Confluence Markup

**Headings:**
```
h1. Main Heading
h2. Sub Heading
h3. Sub-sub Heading
```

**Lists:**
```
* Bullet Point
# Numbered List
```

**Tables:**
```
|| Header 1 || Header 2 ||
| Cell 1 | Cell 2 |
```

**Macros:**
```
{info}
This is an info box
{info}

{warning}
This is a warning
{warning}
```

**Code Blocks:**
```
{code:java}
System.out.println("Hello");
{code}
```

### Common Confluence PRD Patterns

**Pattern 1: User Story Format already in PRD**
```
Confluence Content:
"As a user, I want to export data so that I can analyze it"

→ Already in User Story Format!
→ Copy & enhance with AC, Technical Notes
```

**Pattern 2: Requirements List**
```
Confluence Content:
Requirements:
- System shall allow file upload (max 10MB)
- System shall validate file format
- System shall show preview

→ Map to Stories:
Story 1: "As a user I want to upload files (max 10MB)..."
Story 2: "As a user I want to see validation feedback..."
Story 3: "As a user I want to see a preview..."
```

**Pattern 3: Epic-level PRD**
```
Confluence Content:
"Complete Checkout Flow Implementation"

→ Too big!
→ Create Epic + breakdown into Stories (see BREAKDOWN.md)
```

---

## 📊 PRD Quality Check

**Before creating stories:**

```
✅ PRD is complete?
   → Problem, Users, Requirements, Success Criteria present?

✅ Requirements are clear?
   → Not too vague ("system should be fast")

✅ User Value recognizable?
   → Not just technical specs

✅ Success Metrics defined?
   → How do we measure success?

✅ Scope clear?
   → What's IN, what's OUT?
```

**If PRD is incomplete:**

```
⚠️ "Hey, the PRD is a bit thin.

Missing:
- Success Metrics (how do we measure success?)
- Edge Cases (what happens on error?)
- Technical Constraints (API limits?)

Should I still write stories
or do you want to complete the PRD first?"
```

---

## 🎯 Output Formats

### Format 1: Inline (Chat)

```
Story 1:
───────
As [User] I want [X] to [Y]

Acceptance Criteria:
- [ ] Given... When... Then...

Story Points: 3
───────

Story 2:
───────
...
```

### Format 2: Markdown File

```
File: /outputs/user-stories/PRD-Feature-X-Stories.md

Contains:
- All Stories
- PRD Reference
- Story Mapping (PRD Requirement → Story)
```

### Format 3: Jira Direct

```
→ Batch Create in Jira
→ PRD Link in Story Description
→ PRD Section as Label/Component
```

---

## 🚨 Common Pitfalls

### ❌ Pitfall 1: PRD too vague

**Problem:**
```
PRD: "System should have good UX"
```

**Fix:**
```
Ask:
- What is "good UX" specifically?
- Which user actions?
- Which outcomes?
```

---

### ❌ Pitfall 2: Tech Spec instead of User Value

**Problem:**
```
PRD: "Implement REST API with OAuth2"
```

**Fix:**
```
Ask:
- Why do we need this?
- What can the user do with it?
- What's the value?

→ Story: "As a user I want to securely access my data (via OAuth2)..."
```

---

### ❌ Pitfall 3: Epic-level PRD

**Problem:**
```
PRD: "Complete Social Network Implementation"
(100+ Stories)
```

**Fix:**
```
→ "This is an EPIC-level PRD!

Should I:
1. Create Epic + breakdown into Stories (see BREAKDOWN.md)
2. Identify MVP phase (what's first?)
3. Focus only on Core Features for Sprint 1?"
```

---

### ❌ Pitfall 4: Missing Acceptance Criteria

**Problem:**
```
PRD has no ACs, only "User can upload file"
```

**Fix:**
```
→ Generate ACs based on standard edge cases:

- [ ] Given valid file When upload Then success
- [ ] Given file >10MB When upload Then "Too large" error
- [ ] Given invalid format When upload Then "Invalid format" error
- [ ] Given network error When upload Then retry option
```

---

## 🔗 PRD → Stories Mapping Examples

### Example 1: Simple Feature PRD

**PRD (Confluence):**
```
# Feature: Export Data

## Problem
Users can't export their data for external analysis.

## Requirements
- Export as CSV
- Include all user data (last 12 months)
- Email download link if >1000 records
- Immediate download if <1000 records

## Success Metrics
- Export feature used by 30% of users
- <2s export time for <1000 records
```

**Stories:**

```
Story 1:
"As a user I want to export my data as CSV
to analyze it in Excel"

Acceptance Criteria:
- [ ] Given <1000 records When export Then immediate download
- [ ] Given >1000 records When export Then email with download link
- [ ] Given export clicked When download ready Then CSV includes all fields

Technical Notes:
- Backend: GET /api/export?format=csv
- Async job for >1000 records
- Email template: "Your export is ready"

Story Points: 5

PRD Reference: Confluence Page "Feature: Export Data" → Requirements Section
```

---

### Example 2: Complex Flow PRD

**PRD (Confluence):**
```
# Feature: Multi-Step Onboarding

## User Flow
1. User signs up
2. User verifies email
3. User completes profile (name, photo, bio)
4. User selects preferences
5. User sees personalized dashboard

## Requirements
- Email verification required
- Profile completion optional (can skip)
- Preferences: categories, notifications
- Dashboard shows relevant content based on preferences
```

**Stories:**

```
Story 1: "As a new user I want to register..."
Story 2: "As a new user I want to verify my email..."
Story 3: "As a new user I want to complete my profile..."
Story 4: "As a new user I want to set preferences..."
Story 5: "As a new user I want to see a personalized dashboard..."

Total: 5 Stories (~15-20 Story Points)
```

---

## 📚 Best Practices

### 1. PRD as Single Source of Truth

```
✅ Link every story back to the PRD
✅ Quote original Requirements in Story Description
✅ Track PRD Changes → update Stories
```

### 2. Conversational Parsing

```
✅ Show the PM what you extracted
✅ Ask when unclear
✅ Confirm interpretation

❌ NOT: Blindly create stories without asking
```

### 3. Incremental Refinement

```
✅ First Pass: Quick Stories (Titles + Basic AC)
✅ Second Pass: Refine ACs, Technical Notes
✅ Third Pass: INVEST Check, Story Points

❌ NOT: Expect perfect stories on first try
```

### 4. PRD Quality Feedback

```
✅ Give feedback when PRD has gaps
✅ Suggest improvements
✅ Help PM write better PRDs

Example:
"⚠️ PRD is missing Success Metrics - how do we measure success?
   Should I suggest standard metrics? (Engagement, Conversion, etc.)"
```

---

## 🎨 Tone & Style

**Conversational, not robotic:**

```
❌ NOT:
"PRD parsed. 8 stories extracted. Creating in Jira."

✅ INSTEAD:
"Cool! I've gone through the PRD.

Found:
- Problem: Users can't export data
- Target: 30% Adoption
- 3 Must-Have Features, 2 Nice-to-Have

I'll create 5 stories from this (Frontend + Backend + QA).

Should I get started? 🚀"
```

---

## 🧪 Testing Checklist

**Before releasing to PM:**

```
✅ All stories have User Value (not just tech specs)
✅ All stories are INVEST-compliant
✅ Acceptance Criteria are testable (Given-When-Then)
✅ Technical Notes are present (Frontend/Backend/DB)
✅ PRD Reference is linked (traceability)
✅ Story Points estimated (realistic)
✅ Dependencies identified (if any)
```

---

**PRD → Stories is an art. With practice, it gets better. User Value First. INVEST always.**

---

*PRD Workflow for Cursor AI PM Operating System User Stories Skill*
*Beyond 7, 2025*
