# Epic Breakdown Guide

Systematic Approach: EPIC → User Stories (Frontend/Backend/System)

---

## 🎯 Breakdown Philosophy

**Core Principle:**
- **Split vertically** (preserve User Value)
- **NOT horizontally** (not by layer: Frontend/Backend/DB)
- **End-to-End Value** (every story can be deployed)

**But:** When stories become too big, split into system components.

---

## 🚀 Breakdown Process (Step-by-Step)

### Phase 1: Understand the Epic (Discovery)

**Ask the PM:**

1. **Problem/Opportunity**
   - What's the problem?
   - What's the opportunity?
   - Why now?

2. **User Context**
   - Who are the users? (Persona)
   - What's the use case?
   - What's the expected outcome?

3. **Constraints**
   - Technical Constraints? (API Limits, Legacy Systems)
   - Time Constraints? (Deadline, Runway)
   - Resource Constraints? (Team Size, Budget)

4. **Success Criteria**
   - Which metrics are we improving?
   - How do we measure success?
   - What's the Definition of Done?

**Output:**
```
Epic: [Name]
Problem: [Description]
User: [Persona]
Outcome: [Expected Impact]
Constraints: [List]
Success Criteria: [Metrics]
```

---

### Phase 2: Map the User Journey

**Step 1: Identify the Happy Path**

```
User Journey (Happy Path):
1. User does [Action 1]
   → System shows [Result 1]

2. User does [Action 2]
   → System shows [Result 2]

3. User does [Action 3]
   → System shows [Result 3]

Outcome: [User achieves goal]
```

**Step 2: Alternative Paths & Edge Cases**

```
Alternative Paths:
- What if user makes an error?
- What if API is offline?
- What if no data is present?
- What if permission is missing?
```

**Step 3: Identify User Value Points**

```
Value Points:
- [Step 1]: User can do [X] → Value: [Y]
- [Step 2]: User can do [X] → Value: [Y]
- [Step 3]: User can do [X] → Value: [Y]

→ Each Value Point = potential story!
```

---

### Phase 3: Identify System Components

**For each Value Point → System Components:**

**Frontend:**
- UI Components (Buttons, Forms, Screens)
- Client-side Logic (Validation, State Management)
- UX Flows (Navigation, Feedback)

**Backend:**
- API Endpoints (REST, GraphQL)
- Business Logic (Calculations, Rules)
- 3rd Party Integrations (Stripe, Twilio, etc.)

**Database:**
- Schema Changes (New Tables, Migrations)
- Data Models (Relationships, Constraints)
- Indexes (Performance)

**Infrastructure:**
- Deployment (Docker, CI/CD)
- Monitoring (Logs, Metrics)
- Scaling (Load Balancer, Caching)

**QA/Testing:**
- Unit Tests
- Integration Tests
- E2E Tests
- Performance Tests

---

### Phase 4: Extract Stories

**Approach 1: Vertical (Standard)**

```
Story: "As [User] I want [X] to [Y]"

Scope:
- Frontend: [Component A, Component B]
- Backend: [API Endpoint, Business Logic]
- Database: [Schema Change]

→ Story delivers End-to-End Value!
```

**Approach 2: Horizontal (only when Vertical is too big)**

```
Story 1 (MVP): "As [User] I want [X] to [Y]" (Basic Version)
  → Frontend + Backend + DB (but minimal)

Story 2 (Enhancement): "As [User] I want [X extended] to [Y]"
  → Extends Story 1

Story 3 (Enhancement): "As [User] I want [X optimized] to [Y]"
  → Optimizes Story 1
```

**Approach 3: System Components (only for very large EPICs)**

```
Story 1: "As [User] I want [X] to [Y]" (Frontend Focus)
  → Frontend + Mock Backend

Story 2: "As [User] I want [X] to [Y]" (Backend Integration)
  → Real Backend API + Integration

Story 3: "As [User] I want [X optimized] to [Y]" (Performance)
  → Caching, Optimization
```

---

### Phase 5: Dependencies & Sequencing

**Dependency Types:**

1. **Hard Dependency (BLOCKS)**
   - Story A must be done before Story B can start
   - Example: API must exist before Frontend integrates

2. **Soft Dependency (RELATES TO)**
   - Stories are related but no hard block
   - Example: Login & Registration (similar flows)

3. **Technical Dependency**
   - Infrastructure/Tech-Stack must be ready
   - Example: Stripe Integration must be set up

**Dependency Mapping:**

```
Story A: [Title]
  → BLOCKS: Story B, Story C
  → BLOCKED BY: (none)

Story B: [Title]
  → BLOCKS: Story D
  → BLOCKED BY: Story A

Story C: [Title]
  → BLOCKS: (none)
  → BLOCKED BY: Story A

Story D: [Title]
  → BLOCKS: (none)
  → BLOCKED BY: Story B
```

**Sequencing:**

```
Sprint 1:
- Story A (Foundation)

Sprint 2:
- Story B (depends on A)
- Story C (depends on A, parallel to B)

Sprint 3:
- Story D (depends on B)
```

---

## 🎯 Breakdown Patterns

### Pattern 1: CRUD Features

**Epic:** "User Account Management"

**Breakdown:**

```
Story 1: "As a user I want to register to create an account"
  → CREATE (3 Points)

Story 2: "As a user I want to edit my profile to keep my data up to date"
  → UPDATE (3 Points)

Story 3: "As a user I want to upload a profile picture to present myself"
  → UPDATE + File Upload (5 Points)

Story 4: "As a user I want to delete my account to no longer be part of the platform"
  → DELETE (3 Points)

Story 5: "As a user I want to view my profile to check my data"
  → READ (2 Points)
```

**Total:** 16 Story Points

---

### Pattern 2: Complex User Flow

**Epic:** "Checkout Flow"

**Breakdown:**

```
Story 1 (MVP): "As a user I want to add a product to my cart to buy it later"
  → Cart Management (3 Points)

Story 2: "As a user I want to view my cart to check what I'm buying"
  → Cart View (2 Points)

Story 3: "As a user I want to enter my shipping address to receive the product"
  → Address Form (3 Points)

Story 4: "As a user I want to pay with credit card to complete the purchase"
  → Payment Integration (Stripe) (8 Points)

Story 5: "As a user I want to receive an order confirmation email to confirm my purchase"
  → Email Integration (5 Points)

Story 6: "As a user I want to view my order history to see past purchases"
  → Order History (3 Points)
```

**Total:** 24 Story Points (2 Sprints)

**Dependencies:**
- Story 4 BLOCKED BY Story 3 (need address before payment)
- Story 5 BLOCKED BY Story 4 (need completed order)

---

### Pattern 3: Integration Feature

**Epic:** "Slack Integration"

**Breakdown:**

```
Story 1 (Technical): "Slack OAuth Setup to authenticate users"
  → OAuth Flow (5 Points)

Story 2: "As a user I want to connect my Slack workspace to receive notifications"
  → Connection Flow (3 Points)
  → BLOCKED BY Story 1

Story 3: "As a user I want to receive notifications in Slack to get updates"
  → Send Notifications (5 Points)
  → BLOCKED BY Story 2

Story 4: "As a user I want to choose which notifications I receive so I'm not disturbed"
  → Notification Settings (3 Points)
  → BLOCKED BY Story 3

Story 5: "As a user I want to disconnect Slack to stop receiving notifications"
  → Disconnect Flow (2 Points)
```

**Total:** 18 Story Points

---

### Pattern 4: Performance/Optimization

**Epic:** "Dashboard Performance Improvement"

**Breakdown:**

```
Story 1 (Technical): "As a user I want fast load times (<2s) so I don't have to wait"
  → Implement Caching (Redis) (8 Points)

Story 2 (Technical): "As a user I want to see large amounts of data without performance issues"
  → Implement Pagination (3 Points)

Story 3 (Technical): "As a developer I want to eliminate N+1 queries to reduce DB load"
  → Fix N+1 Queries (5 Points)

Story 4 (Technical): "As a user I want to see optimized images to improve load times"
  → Image Optimization (CDN) (5 Points)
```

**Total:** 21 Story Points

---

## 🛠️ System Component Breakdown

### Frontend Stories

**Trigger:** UI-heavy Features, Client-side Logic

**Breakdown:**

```
Story: "As a user I want [UI Feature] to [Benefit]"

Components:
- UI Component(s): [Button, Form, Modal]
- State Management: [Redux, Context API]
- API Integration: [REST Calls]
- Validation: [Client-side]
- Error Handling: [User Feedback]

Technical Notes:
- Framework: React / Vue / Native
- Styling: Tailwind / CSS Modules
- Testing: Jest, React Testing Library
```

---

### Backend Stories

**Trigger:** API, Business Logic, Integrations

**Breakdown:**

```
Story: "As a user I want [Feature] to [Benefit]"

Backend Components:
- API Endpoint: POST /api/... (REST or GraphQL)
- Business Logic: [Calculations, Rules]
- Database: [Queries, Transactions]
- 3rd Party: [Stripe, Twilio, etc.]
- Error Handling: [Status Codes, Messages]

Technical Notes:
- Framework: Node.js / Python / Ruby
- Database: PostgreSQL / MongoDB
- Testing: Jest, Supertest
```

---

### Database Stories

**Trigger:** Schema Changes, Migrations

**Breakdown:**

```
Story (Technical): "Database Migration: [Description]"

Changes:
- New Tables: [users, orders]
- New Columns: [email, created_at]
- Indexes: [email_idx for performance]
- Constraints: [UNIQUE, NOT NULL]

Migration Plan:
- Step 1: Create migration file
- Step 2: Test on Staging
- Step 3: Deploy to Production (zero-downtime)

Rollback Plan:
- Revert migration if issues
```

---

### QA/Testing Stories

**Trigger:** Complex Features, Critical Paths

**Breakdown:**

```
Story (QA): "As QA I want to test [Feature] to ensure quality"

Test Coverage:
- Unit Tests: [Functions, Components]
- Integration Tests: [API Endpoints]
- E2E Tests: [User Flows]
- Performance Tests: [Load Time, Stress Tests]

Acceptance Criteria:
- [ ] Unit Test Coverage >80%
- [ ] All E2E Tests passing
- [ ] Performance <3s page load
```

---

## 📊 Story Sizing by Components

### Frontend (UI-focused)

| Size | Description | Example |
|------|-------------|---------|
| **2** | Simple UI Change | Change text, add button |
| **3** | New Component | Simple Form, Modal |
| **5** | Complex Component | Multi-step Form, Chart |
| **8** | Feature + State Mgmt | Dashboard with API Integration |

### Backend (API-focused)

| Size | Description | Example |
|------|-------------|---------|
| **2** | Simple Endpoint | GET /api/users |
| **3** | CRUD Endpoint | POST /api/users with Validation |
| **5** | Complex Logic | Payment Processing, Business Rules |
| **8** | 3rd Party Integration | Stripe, Twilio, Complex APIs |

### Fullstack (End-to-End)

| Size | Description | Example |
|------|-------------|---------|
| **5** | Simple Feature | Login Form (Frontend + Backend + DB) |
| **8** | Standard Feature | Registration Flow with Email Verification |
| **13** | Complex Feature | **TOO BIG! Split!** |

---

## 🧩 Splitting Strategies

### Strategy 1: MVP → Enhancement

**When story is too big:**

```
Story 1 (MVP): "As a user I want [Basic X] to [Y]"
  → Minimal functional version (5 Points)

Story 2 (Enhancement): "As a user I want [X extended] to [better Y]"
  → Enhanced Version (3 Points)

Story 3 (Optimization): "As a user I want [X optimized] to [even better Y]"
  → Optimized Version (3 Points)
```

**Example:**

```
Story 1: "As a user I want to see search results to find products"
  → Basic Search (Text-Match) (5 Points)

Story 2: "As a user I want to use filters to refine search results"
  → Add Filters (Category, Price) (5 Points)

Story 3: "As a user I want to see intelligent suggestions to find things faster"
  → Add Auto-Complete (3 Points)
```

---

### Strategy 2: Path-based Splitting

**When user journey is complex:**

```
Story 1: "As a user I want [Happy Path] to [Y]"
  → Happy Path (3 Points)

Story 2: "As a user I want [Edge Case 1] to [Y]"
  → Edge Case 1 (2 Points)

Story 3: "As a user I want [Edge Case 2] to [Y]"
  → Edge Case 2 (2 Points)
```

**Example:**

```
Story 1: "As a user I want to log in with email/password to get access"
  → Happy Path (3 Points)

Story 2: "As a user I want to use 'Forgot Password' to regain access"
  → Reset Password Flow (5 Points)

Story 3: "As a user I want to use Social Login to get faster access"
  → Google/Facebook Login (8 Points)
```

---

### Strategy 3: Component-based Splitting

**Only for very large EPICs:**

```
Story 1: "As a user I want [X] to [Y]" (Frontend)
  → UI + Mock Data (3 Points)

Story 2: "As a user I want [X] to [Y]" (Backend Integration)
  → Real API Integration (5 Points)

Story 3: "As a user I want [X optimized] to [Y]" (Performance)
  → Caching, Optimization (3 Points)
```

**⚠️ Caution:** Only use when Vertical Splitting is not possible!

---

## ✅ Breakdown Checklist

**Before finalizing:**

```
✅ Every story has clear User Value
✅ Every story is INVEST-compliant
✅ Story Points estimated (max 8 Points)
✅ Dependencies identified & marked
✅ Acceptance Criteria defined (Given-When-Then)
✅ Technical Notes added
✅ Labels & Components set
✅ Epic Link set
```

---

## 🚀 Jira Batch Creation

**After Breakdown → Jira:**

```javascript
// Batch Create via jira_batch_create_issues
{
  "issues": [
    {
      "project_key": "PROD",
      "summary": "As a user I want...",
      "issue_type": "Story",
      "description": "...",
      "assignee": "user@example.com",
      "components": ["Frontend"],
      "additional_fields": {
        "parent": "PROD-100",  // Epic Link
        "customfield_10016": 5  // Story Points
      }
    },
    // ... more stories
  ]
}
```

**Output for PM:**

```
✅ Created 8 Stories in Jira (Epic: PROD-100)

Frontend (3 Stories):
- PROD-123: As a user I want... (3 Points)
- PROD-124: As a user I want... (5 Points)
- PROD-125: As a user I want... (2 Points)

Backend (3 Stories):
- PROD-126: API Endpoint for... (5 Points)
- PROD-127: Integration with... (8 Points)
- PROD-128: Validation... (3 Points)

QA (2 Stories):
- PROD-129: E2E Tests (3 Points)
- PROD-130: Performance Tests (5 Points)

Total: 34 Story Points (~2 Sprints for 1 Dev)
```

---

**Breakdown is an art. With practice, it gets better. INVEST always.**

---

*Epic Breakdown Guide for Product-Toolkit*
*Hendrik Hemken, 2025*
