# User Stories Best Practices Guide

INVEST Principles, Best Practices, Good vs. Bad Examples, Common Mistakes.

---

## 🎯 INVEST Principles

**Every User Story MUST be INVEST-compliant:**

### **I - Independent**

**Rule:** Story can be implemented on its own, without waiting for other stories.

**✅ Good:**
```
Story A: "As a user I want to edit my profile to keep my data up to date"
Story B: "As a user I want to upload a profile picture to present myself"

→ Both stories are independent of each other
```

**❌ Bad:**
```
Story A: "As a user I want to complete step 1 of registration"
Story B: "As a user I want to complete step 2 of registration"

→ Story B depends completely on Story A!
→ Fix: One story "As a user I want to register to..."
```

**Exceptions:**
- Technical Dependencies are OK (but mark them explicitly!)
- Set BLOCKED BY relationships in Jira

---

### **N - Negotiable**

**Rule:** Implementation details can still be discussed.

**✅ Good:**
```
"As a user I want to receive notifications to stay informed about updates"

→ HOW the notifications look can still be discussed
→ Push? Email? In-App? → Negotiable!
```

**❌ Bad:**
```
"As a user I want to receive push notifications with a red badge and sound 'ding.mp3'"

→ Too specific! No room for negotiation.
```

**Rule of Thumb:**
- Story = **WHAT** (negotiable)
- Acceptance Criteria = **HOW** (more concrete, but still negotiable)
- Implementation = **EXACT** (not negotiable)

---

### **V - Valuable**

**Rule:** Story delivers User Value or Business Value.

**✅ Good (User Value):**
```
"As a user I want to cancel my order to correct mistakes"

→ Clear User Value: User can fix errors
```

**✅ Good (Business Value):**
```
"As an admin I want to see analytics to make data-driven decisions"

→ Clear Business Value: Better Decisions
```

**❌ Bad (Activity-based, no Value):**
```
"As a developer I want to implement a REST API"

→ That's NOT Value, that's an Activity!
→ Fix: "As a user I want to export my data (via API) to use it in other tools"
```

**Technical Stories:**
- Sometimes there are Technical Stories without direct User Value
- Allowed for: Refactoring, Tech Debt, Infrastructure
- **BUT:** Always explain Business Impact! ("Performance +50%", "Improved maintainability")

---

### **E - Estimable**

**Rule:** Team can estimate Story Points.

**✅ Good:**
```
"As a user I want to change my email address to stay reachable when switching providers"

Acceptance Criteria:
- Given user is logged in When user changes email Then confirmation email sent
- Given user clicks confirmation link Then email updated

→ Team can estimate: 3-5 Story Points
```

**❌ Bad:**
```
"As a user I want a better experience"

→ Too vague! What does "better" mean?
→ Team cannot estimate!
```

**If not estimable:**
- **Create a Spike Story** (Time-boxed Research)
- After Spike: Write real stories

**Spike Example:**
```
Spike: "Research: How do we integrate Payment Provider X?"
Time-box: 4 hours
Output: Technical Approach Doc + Story Points Estimate
```

---

### **S - Small**

**Rule:** Story fits in one sprint (max 8 Story Points).

**✅ Good:**
```
"As a user I want to upload a profile picture to present myself"

→ 3 Story Points (0.5-1 day)
→ Fits easily in a sprint
```

**❌ Bad:**
```
"As a user I want to use a complete social network"

→ That's an EPIC, not a Story!
→ 100+ Story Points!
```

**Sizing Guide:**
- **1-2 Points:** Trivial (hours)
- **3-5 Points:** Standard (0.5-2 days) ← Sweet Spot!
- **8 Points:** Maximum (2-3 days)
- **13+ Points:** TOO BIG! Split!

**If too big:**
- Split into smaller stories
- Split vertically (preserve User Value!)
- Not horizontally (layer-based)

---

### **T - Testable**

**Rule:** Clear Acceptance Criteria = testable.

**✅ Good:**
```
Acceptance Criteria:
- [ ] Given user uploaded 5MB image When submit Then success
- [ ] Given user uploaded 20MB image When submit Then "File too large" error
- [ ] Given user uploaded .exe file When submit Then "Invalid format" error

→ 100% testable! QA knows exactly what to test.
```

**❌ Bad:**
```
Acceptance Criteria:
- [ ] Upload should work

→ Not testable! WHAT does "work" mean?
→ Which edge cases?
```

**Given-When-Then Format:**
```
Given [Precondition]
When [User Action]
Then [Expected Result]
```

---

## 🚫 Common Mistakes (and how to avoid them)

### ❌ Mistake 1: Activity-based Stories

**Bad:**
```
"As a developer I want to build an API"
"Implement User Authentication"
"Create Database Schema"
```

**Why Bad:**
- No User Value
- No Outcome
- Developer perspective, not User perspective

**Fix:**
```
"As a user I want to log in with email & password to securely access my account"

Technical Notes:
- Backend: JWT Authentication
- Database: Users Table with hashed passwords
- Frontend: Login Form
```

---

### ❌ Mistake 2: Stories too big

**Bad:**
```
"As a user I want to use all social features"

→ 50+ Story Points
→ Multiple sprints
```

**Fix:**
```
Split into smaller stories:
- Story 1: "As a user I want to add friends"
- Story 2: "As a user I want to create posts"
- Story 3: "As a user I want to like posts"
- Story 4: "As a user I want to comment"
```

---

### ❌ Mistake 3: Vague Acceptance Criteria

**Bad:**
```
Acceptance Criteria:
- [ ] Feature should work well
- [ ] Performance should be OK
- [ ] User should be satisfied
```

**Fix:**
```
Acceptance Criteria:
- [ ] Given user loads dashboard When <1000 records Then page loads in <2s
- [ ] Given user loads dashboard When >1000 records Then pagination (50/page)
- [ ] Given API offline When load Then "Connection Error" + Retry button
```

---

### ❌ Mistake 4: Horizontal Splitting (Layer-based)

**Bad:**
```
Story 1: "Frontend for User Registration"
Story 2: "Backend for User Registration"
Story 3: "Database for User Registration"

→ No story delivers standalone Value!
→ User can only use it when all 3 stories are done!
```

**Fix (Vertical Splitting):**
```
Story 1: "As a user I want to register to create an account"
  → Includes: Frontend + Backend + Database
  → Delivers complete User Value!
```

**If story too big for vertical split:**
- MVP version first (Basic Registration)
- Then enhancement stories (Social Login, Email Verification, etc.)

---

### ❌ Mistake 5: Tech Stack in Story Title

**Bad:**
```
"As a user I want to retrieve my data via GraphQL API"
```

**Why Bad:**
- Tech Stack is an Implementation Detail
- Should be negotiable!

**Fix:**
```
Title: "As a user I want to export my data to use it in other tools"

Technical Notes:
- Implementation: GraphQL API (or REST, to be decided)
```

---

### ❌ Mistake 6: Missing Dependencies

**Bad:**
```
Story A: "As a user I want to make payments"
Story B: "As a user I want to use Stripe as payment provider"

→ Story A cannot be implemented without B!
→ But no explicit dependency!
```

**Fix:**
```
Story B: "As a user I want to use Stripe as payment provider"
  → BLOCKS: Story A

Story A: "As a user I want to make payments"
  → BLOCKED BY: Story B
```

---

## ✅ Best Practices

### 1. User Value First

**Always ask:** "What value does the user get from this?"

```
❌ "Implement Caching"
✅ "As a user I want fast load times (<2s) so I don't have to wait"

Technical Notes:
- Solution: Redis Caching
```

---

### 2. Split Vertically (not horizontally)

**Vertical Slicing:**
- Every story delivers End-to-End Value
- Frontend + Backend + Database in one story (if needed)

**Horizontal Slicing (AVOID):**
- Story per Layer (Frontend, Backend, DB)
- No story delivers standalone Value

---

### 3. Define Definition of Done (DoD)

**Team-wide DoD:**
```
- [ ] Code written & reviewed
- [ ] Unit Tests (>80% Coverage)
- [ ] Acceptance Criteria met
- [ ] Deployed to Staging
- [ ] QA Sign-off
- [ ] PO Acceptance
```

**Every story must meet DoD to be considered "Done"!**

---

### 4. Use Personas

**Generic:**
```
"As a user I want to receive notifications"
```

**With Persona:**
```
"As a Power User (30-45 years old, active daily) I want to receive configurable notifications so I'm not disturbed by unimportant updates"

→ Gives more context!
→ Helps with design decisions!
```

---

### 5. Outcome over Output

**Output-focused (BAD):**
```
"Ship 5 Features"
"Deploy to Production"
```

**Outcome-focused (GOOD):**
```
"Increase User Engagement by 20%"
"Reduce Support Tickets by 30%"
"Improve NPS from 7 to 8"
```

---

### 6. Technical Spikes for Uncertainty

**When the team cannot estimate:**
- Create a Spike Story
- Time-box (e.g., 4 hours)
- Output: Technical Approach Doc

**Spike Example:**
```
Spike: "Research: How to integrate Payment Provider X?"

Acceptance Criteria:
- [ ] Technical Approach documented
- [ ] Risks identified
- [ ] Story Points estimate for implementation

Time-box: 4 hours
```

**After Spike:** Write real Implementation Stories

---

## 🎨 Good vs. Bad Examples

### Example 1: User Registration

**❌ BAD:**
```
Title: "Implement User Authentication"

Description:
- Create JWT tokens
- Hash passwords
- Store in database
```

**Why Bad:**
- Activity-based (not user-centric)
- No User Value visible
- Tech Stack in the foreground

**✅ GOOD:**
```
Title: "As a user I want to register to create an account"

Description:
As a new user I want to register with email & password,
to save my data and access it again later.

Acceptance Criteria:
- [ ] Given user on /register When email + password entered Then account created
- [ ] Given email already exists When submit Then "Email already registered"
- [ ] Given password <8 characters When submit Then "Password too short"
- [ ] Given successful registration When submit Then auto-login + redirect to dashboard

Technical Notes:
- Backend: JWT Authentication, bcrypt for passwords
- Database: Users Table (email, hashed_password, created_at)
- Frontend: Registration Form with validation

Story Points: 5
```

---

### Example 2: Export Feature

**❌ BAD:**
```
Title: "Build Export API"

Description:
- Create REST endpoint
- Support CSV format
```

**Why Bad:**
- Developer perspective
- No User Value
- Too vague (which data? which use cases?)

**✅ GOOD:**
```
Title: "As a user I want to export my data as CSV to analyze it in Excel"

Description:
As a user I want to export all my data (transactions from the last 12 months)
as a CSV file to analyze it in Excel or other tools.

Acceptance Criteria:
- [ ] Given user on /export When click "Export CSV" Then download CSV file
- [ ] Given 1000+ records When export Then async job + email with download link
- [ ] Given <1000 records When export Then immediate download
- [ ] Given CSV downloaded When open Then all fields included (date, amount, category, notes)

Technical Notes:
- Backend: GET /api/export?format=csv
- Async Job for >1000 records (Bull Queue)
- CSV Format: date,amount,category,notes
- Email Template: "Your export is ready!"

Edge Cases:
- [ ] User has 0 records → Empty CSV with headers
- [ ] User has special characters in notes → CSV escaping

Story Points: 5
```

---

### Example 3: Performance Improvement

**❌ BAD:**
```
Title: "Implement Caching"

Description:
- Add Redis
- Cache API responses
```

**Why Bad:**
- Tech Solution, not Problem
- No measurable Outcome

**✅ GOOD:**
```
Title: "As a user I want fast load times (<2s) so I don't have to wait"

Description:
Current: Dashboard loads in 8-10s with 1000+ records.
Target: Dashboard loads in <2s.

Problem: N+1 Queries + no caching.

Acceptance Criteria:
- [ ] Given user loads dashboard When <1000 records Then page loads in <2s
- [ ] Given user loads dashboard When >1000 records Then page loads in <3s
- [ ] Given cache hit When load Then <500ms response time

Technical Notes:
- Solution: Redis Caching (TTL: 5 min)
- Fix N+1 queries (use JOIN)
- Add pagination (50 records/page)

Story Points: 8
```

---

## 🧪 INVEST Check Cheatsheet

**Before committing to Jira:**

```
Story: "As [Role] I want [Feature] to [Benefit]"

✅ Independent? Can story be implemented on its own?
✅ Negotiable? Details still negotiable?
✅ Valuable? User or Business Value clear?
✅ Estimable? Team can estimate Story Points?
✅ Small? Max 8 Story Points?
✅ Testable? Acceptance Criteria clear & testable?

If NO to any point → Revise the story!
```

---

## 📚 Further Reading

### Recommended Books
- **"User Story Mapping"** - Jeff Patton
- **"User Stories Applied"** - Mike Cohn
- **"The Lean Startup"** - Eric Ries (Outcome-focused Thinking)

### Recommended Articles
- Atlassian Guide to User Stories
- Martin Fowler: UserStory
- Roman Pichler: 10 Tips for Writing Good User Stories

---

**INVEST is not negotiable. Quality first. User Value first.**

---

*User Stories Best Practices Guide for Cursor AI PM Operating System*
*Beyond 7, 2025*
