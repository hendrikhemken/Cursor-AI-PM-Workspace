# User Stories Templates

Ready-to-use Templates for User Stories, EPICs, Acceptance Criteria & Technical Stories.

---

## 📝 User Story Template

```markdown
# [Story Title - short & concise]

**As** [Role/Persona]
**I want** [Feature/Function]
**to** [Benefit/Goal/Outcome]

---

## Acceptance Criteria

- [ ] **Given** [Context/Precondition] **When** [Action/User Action] **Then** [Expected Outcome]
- [ ] **Given** [Context] **When** [Action] **Then** [Outcome]
- [ ] **Given** [Context] **When** [Action] **Then** [Outcome]

---

## Technical Notes

**Frontend:**
- Component: [e.g., UserProfileScreen.tsx]
- UI Libraries: [e.g., React, Tailwind]
- API Calls: GET /api/users/{id}

**Backend:**
- Endpoint: POST /api/...
- Business Logic: [Description]
- Database: [Tables/Collections]

**Infrastructure:**
- Deployment: [e.g., Docker, Vercel]
- Environment Variables: [e.g., API_KEY]

---

## Edge Cases & Error Handling

- [ ] What happens on network error?
- [ ] What about invalid data?
- [ ] What on timeout?
- [ ] What if permissions are missing?

---

## Dependencies

**Blocked by:**
- [STORY-123]: [Reason why]

**Blocks:**
- [STORY-456]: [Reason why]

**Relates to:**
- [STORY-789]: [Description]

---

## Story Points

**Estimate:** [1, 2, 3, 5, 8, 13]

**Rationale:**
- [Why this estimate?]
- [What's complex?]
- [What unknowns exist?]

---

## Labels

- `user-story`
- `frontend` / `backend` / `fullstack`
- `q4-2025` (Quarter)
- `high-priority` / `medium-priority` / `low-priority`

---

## Definition of Done

- [ ] Code written & reviewed
- [ ] Unit Tests written (>80% Coverage)
- [ ] Integration Tests (if relevant)
- [ ] Acceptance Criteria met
- [ ] UI/UX reviewed (if Frontend)
- [ ] Performance acceptable (<3s Load Time)
- [ ] Documentation updated
- [ ] Deployed to Staging
- [ ] QA Sign-off
- [ ] PO Acceptance

```

---

## 🗂️ Epic Template

```markdown
# [Epic Name]

**Vision:**
[What's the big goal of this epic? What problem are we solving?]

**Business Value:**
[Why is this important? Which metrics are we improving?]

**Target Users:**
- [Persona 1: Description]
- [Persona 2: Description]

---

## Success Criteria (Outcomes)

- [ ] [Metric 1: e.g., "User Engagement +20%"]
- [ ] [Metric 2: e.g., "Conversion Rate +10%"]
- [ ] [Metric 3: e.g., "Support Tickets -30%"]

---

## Scope (High-Level)

**In Scope:**
- [Feature 1]
- [Feature 2]
- [Feature 3]

**Out of Scope:**
- [What are we NOT doing?]
- [What comes later?]

---

## User Journey

**Happy Path:**
1. User does [Action 1]
2. System shows [Result 1]
3. User does [Action 2]
4. System shows [Result 2]
5. **Outcome:** [User achieves goal]

**Alternative Paths:**
- [Edge Case 1]
- [Edge Case 2]

---

## Technical Approach

**Architecture:**
- [Frontend Approach]
- [Backend Approach]
- [Database Changes]
- [3rd Party Integrations]

**Tech Stack:**
- Frontend: [React, Vue, Native, etc.]
- Backend: [Node.js, Python, Ruby, etc.]
- Database: [PostgreSQL, MongoDB, etc.]

---

## Dependencies & Risks

**External Dependencies:**
- [3rd Party API: e.g., Stripe, Twilio]
- [Other Teams: e.g., Platform Team]

**Risks:**
- [Risk 1: e.g., "API Rate Limits"]
- [Risk 2: e.g., "Legacy System Constraints"]

**Mitigation:**
- [How do we mitigate Risk 1?]
- [How do we mitigate Risk 2?]

---

## Timeline (High-Level)

- **Start:** [Date]
- **Target Completion:** [Date]
- **Estimated Sprints:** [2-4 Sprints]
- **Story Points (total):** [50-100 Points]

---

## Stakeholders

- **Product Owner:** [Name]
- **Engineering Lead:** [Name]
- **Designer:** [Name]
- **QA Lead:** [Name]

---

## Related Epics

- [EPIC-123]: [Description]
- [EPIC-456]: [Description]

```

---

## ✅ Acceptance Criteria Template (Given-When-Then)

### Standard Format

```markdown
**Given** [Precondition / Context]
**When** [User Action / Trigger]
**Then** [Expected Result / Outcome]
```

### Examples

**Good:**
```
✅ Given user is logged in
   When user clicks "Edit Profile"
   Then user sees form with current data

✅ Given user has 0 friends
   When user loads friends list
   Then user sees "No friends yet" message

✅ Given API is offline
   When user saves changes
   Then user sees "Connection failed" error + Retry button
```

**Bad:**
```
❌ "Form should work"
   → Too vague! WHAT should work?

❌ "User can change data"
   → Not testable! WHICH data? HOW to change?

❌ "Performance should be good"
   → Not measurable! WHAT is "good"? <3s? <5s?
```

### Make Edge Cases Explicit

```markdown
**Happy Path:**
- [ ] Given valid input When submit Then success

**Edge Cases:**
- [ ] Given empty input When submit Then validation error
- [ ] Given invalid email When submit Then "Invalid email" error
- [ ] Given network timeout When submit Then "Timeout" error + Retry
- [ ] Given 1000+ records When load Then pagination (max 50 per page)
```

---

## 🛠️ Technical Story Template

For stories that have NO direct User Value (e.g., Refactoring, Tech Debt, Infrastructure).

```markdown
# [Technical Story Title]

**Problem:**
[What's the technical problem?]

**Solution:**
[What's the solution?]

**Impact:**
[Why is this important? Performance? Maintainability? Security?]

---

## Acceptance Criteria

- [ ] [Technical Requirement 1]
- [ ] [Technical Requirement 2]
- [ ] [Tests passing]
- [ ] [Performance benchmark met]

---

## Technical Details

**Current State:**
- [Description of current state]

**Target State:**
- [Description of target state]

**Approach:**
- [Step 1]
- [Step 2]
- [Step 3]

---

## Story Points

**Estimate:** [3, 5, 8]

---

## Labels

- `tech-debt`
- `refactoring`
- `infrastructure`
- `backend` / `frontend`

```

---

## 🏷️ Labels & Components Guide

### Components (System Areas)

- `Frontend` - UI, Client-side Logic, UX
- `Backend` - API, Business Logic, Integrations
- `Database` - Schema Changes, Migrations
- `Infrastructure` - DevOps, CI/CD, Monitoring
- `QA` - Testing, E2E, Performance Tests
- `Documentation` - Docs, API Specs, Guides

### Labels (Additional Categorization)

- `user-story` / `technical-story` / `bug` / `spike`
- `high-priority` / `medium-priority` / `low-priority`
- `q4-2025` / `q1-2026` (Quarter)
- `mobile` / `web` / `api` (Platform)
- `mvp` / `nice-to-have` (Scope)

---

## 📊 Story Status Workflow

```
📝 Backlog
  ↓
📋 Ready for Dev (Refinement done, AC clear)
  ↓
👨‍💻 In Progress (Dev working)
  ↓
🧪 In Review (Code Review / QA)
  ↓
✅ Done (Deployed, Accepted by PO)
```

---

## 🎨 Jira-specific Fields

### Required Fields
- `project_key` - e.g., "PROD", "DEV", "TECH"
- `summary` - Story Title
- `issue_type` - "Story" / "Task" / "Bug"

### Optional Fields
- `description` - Full Story (with ACs, Technical Notes)
- `assignee` - Email, Name, or Account ID
- `components` - ["Frontend", "Backend"]
- `labels` - ["user-story", "q4-2025"]
- `priority` - {"name": "High"} / "Medium" / "Low"
- `parent` - Epic Key (e.g., "PROD-100")

### Custom Fields (Story Points)
- Usually `customfield_10016` or similar
- Check via `jira_search_fields "story points"`

---

**These templates are ready-to-use. Copy, paste, adapt!**

---

*Templates for Product-Toolkit User Stories Skill*
*Hendrik Hemken, 2025*
