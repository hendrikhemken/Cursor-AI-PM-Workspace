# PRD Templates
*Ready-to-use Product Requirements Document Templates*

---

## Template Overview

| Template | Use Case | Length | Effort | Audience |
|----------|----------|--------|--------|----------|
| **Lean PRD** | Agile Teams, MVP, Fast Iteration | 1-3 Pages | 1-2 Days | Small-Medium Teams |
| **Traditional PRD** | Waterfall, Regulated Industries | 10-30 Pages | 2-6 Weeks | Large Enterprises |
| **Amazon PR/FAQ** | Strategic Initiatives, Executive Decisions | 5-10 Pages | 4-8 Weeks | Leadership, Customer-Obsessed Orgs |
| **Hybrid Agile PRD** | Scale-Ups, Cross-Functional Teams | 5-10 Pages | 1-2 Weeks | Medium-Large Teams (10-50) |

---

## Template 1: Lean PRD ✅ (DEFAULT)

**When to use:**
- ✅ Agile/Scrum Environment
- ✅ Small-Medium Feature (2 weeks - 3 months)
- ✅ Startup or small team (2-20 people)
- ✅ MVP or Early-Stage
- ✅ Fast iteration desired

**Length:** 1-3 pages
**Creation time:** 1-2 days (with 3-5 iterations)
**Review Stakeholders:** 5-10 people

---

### Lean PRD Template

```markdown
---
title: [Feature Name] - PRD
space_key: [SPACE]
status: Draft
author: [PM Name]
created: [YYYY-MM-DD]
last_updated: [YYYY-MM-DD]
epic_link: [JIRA-XXX]
---

# [Feature Name] - Product Requirements Document

**Status:** 🟡 Draft
**Owner:** [PM Name]
**Target Release:** Q[X] 202[X]
**Epic:** [JIRA-XXX](link)

---

## 📋 Executive Summary

[1-2 paragraphs: What are we building, why, for whom]

**TL;DR:** [15-word summary]

---

## 🎯 Problem Statement

**Problem:**
[Specific problem in 2-3 sentences]

**Impact:**
- **Quantitative:** [Metrics/Data]
  - Example: "35% of users abandon upload → 20k DAU lost"
- **Qualitative:** [User Quotes]
  - Example: "I can't upload multiple videos at once!" - User Quote

**Vision:**
[What does the world look like when problem is solved?]

---

## 👥 User Personas & Use Cases

### Primary Persona: [Name]

| Attribute | Details |
|-----------|---------|
| **Role** | [e.g., Content Creator] |
| **Goals** | [What do they want to achieve?] |
| **Pain Points** | [Current frustrations] |
| **Tech Proficiency** | [Low/Medium/High] |
| **Quote** | "[Direct quote from research]" |

### Use Case: [Title]

**As** [User Type]
**I want** [Action]
**to** [Benefit]

**Happy Path:**
1. [Step 1]
2. [Step 2]
3. [Step 3]

**Edge Cases:**
- [Edge Case 1]
- [Edge Case 2]

---

## 📊 Success Metrics

| Metric | Baseline | Target | Timeframe | Method |
|--------|----------|--------|-----------|--------|
| [KPI 1] | [Current] | [Goal] | Q[X] 202[X] | [How to measure?] |
| [KPI 2] | [Current] | [Goal] | Q[X] 202[X] | [How to measure?] |
| [KPI 3] | [Current] | [Goal] | Q[X] 202[X] | [How to measure?] |

**Example:**
| Metric | Baseline | Target | Timeframe | Method |
|--------|----------|--------|-----------|--------|
| Upload Success Rate | 85% | 95% | Q2 2025 | Analytics Dashboard |
| Avg Upload Time | 45s | <15s | Q2 2025 | Performance Monitoring |
| User Satisfaction (NPS) | 42 | >70 | Q3 2025 | Quarterly Survey |

---

## ⚙️ Features & Requirements

### Must-Have (P0) ✅
- **[Feature 1]:** [Description]
  - Acceptance Criteria: [Specific, testable]
- **[Feature 2]:** [Description]
  - Acceptance Criteria: [Specific, testable]

### Should-Have (P1) 🔵
- **[Feature 3]:** [Description]

### Nice-to-Have (P2) 🟢
- **[Feature 4]:** [Description]

### OUT of Scope ❌
- ❌ **[Feature X]:** [Why out of scope?]
- ❌ **[Feature Y]:** [Why out of scope?]

---

## 🛠️ Technical Considerations

**Architecture:**
- [High-Level Approach]

**Dependencies:**
- [System/Team Dependencies]

**Constraints:**
- **Performance:** [e.g., "<2s Load Time for 95% users"]
- **Security:** [Requirements]
- **Scalability:** [e.g., "100k concurrent users"]
- **Accessibility:** [WCAG 2.1 compliance]

**Assumptions:**
- [Key Assumption 1]
- [Key Assumption 2]

**Risks:**
| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| [Risk 1] | High/Med/Low | High/Med/Low | [Plan] |

---

## 📅 Timeline & Milestones

**Phase 1 - MVP** (Q[X] 202[X])
- [Core Features]
- **Milestone:** [Deliverable]

**Phase 2 - Enhancement** (Q[X] 202[X])
- [Additional Features]
- **Milestone:** [Deliverable]

**Phase 3 - Scale** (Q[X] 202[X])
- [Optimization]
- **Milestone:** [Deliverable]

---

## 🔗 Related Links

- **Epic:** [JIRA-XXX](link)
- **Design:** [Figma/Sketch Link]
- **User Research:** [Research Doc]
- **Roadmap:** [Product Roadmap]
- **Tech Spec:** [Engineering Doc]

---

## 📝 Open Questions

- [ ] [Question 1]
- [ ] [Question 2]
- [ ] [Question 3]

---

## 📜 Changelog

| Date | Author | Changes |
|------|--------|---------|
| 202[X]-[MM]-[DD] | [Name] | Initial Draft |
| 202[X]-[MM]-[DD] | [Name] | Added Success Metrics |
| 202[X]-[MM]-[DD] | [Name] | Stakeholder Feedback incorporated |

```

---

## Template 2: Traditional PRD

**When to use:**
- ⚠️ Waterfall or highly regulated industry (Finance, Healthcare, Government)
- ⚠️ Large Feature (3+ months)
- ⚠️ High Risk, High Investment
- ⚠️ >50 Stakeholders
- ⚠️ Compliance/Legal Requirements

**Length:** 10-30 pages
**Creation time:** 2-6 weeks
**Review Stakeholders:** 20-50+ people

---

### Traditional PRD Template

```markdown
---
title: [Product/Feature Name] - Product Requirements Document
space_key: [SPACE]
status: Draft
author: [PM Name]
version: 1.0
created: [YYYY-MM-DD]
last_updated: [YYYY-MM-DD]
approval_required: [Legal, Compliance, Security, Executive]
---

# [Product/Feature Name] - Product Requirements Document

**Document Control**

| Attribute | Details |
|-----------|---------|
| **Version** | 1.0 |
| **Status** | Draft / In Review / Approved |
| **Owner** | [PM Name] |
| **Approvers** | [List of Stakeholders] |
| **Classification** | Confidential / Internal |
| **Target Release** | [Date] |

---

## Table of Contents

1. Executive Summary
2. Background & Strategic Context
3. Market Analysis
4. Problem Statement
5. User Personas & Scenarios
6. Product Vision & Objectives
7. Functional Requirements
8. Non-Functional Requirements
9. User Experience & Design
10. Technical Architecture
11. Integration & Dependencies
12. Security & Compliance
13. Success Metrics & KPIs
14. Timeline & Resource Planning
15. Budget & ROI Analysis
16. Risk Management
17. Go-to-Market Strategy
18. Appendices

---

## 1. Executive Summary

**Purpose:**
[High-Level Overview: What, Why, For Whom, When]

**Strategic Alignment:**
[How does this align with Company Strategy/OKRs?]

**Business Impact:**
- **Revenue Opportunity:** [€X Million]
- **Cost Savings:** [€X Million]
- **Market Share:** [X% increase]
- **Customer Acquisition:** [X new customers]

**Investment Required:**
- **Development:** [€X / X FTE Months]
- **Marketing:** [€X]
- **Operations:** [€X]

**Recommendation:**
[Approve / Reject / Further Study]

---

## 2. Background & Strategic Context

### Company Strategy
[How does this product fit into overall company strategy?]

### Market Opportunity
[Market Size, Growth Rate, Trends]

### Competitive Landscape
[Who are the competitors? What do they do?]

### Strategic Rationale
[Why now? Why us?]

---

## 3. Market Analysis

### Target Market Segments

| Segment | Size | Growth | Attractiveness | Priority |
|---------|------|--------|----------------|----------|
| [Segment 1] | [X Users] | [X% YoY] | High/Med/Low | P0/P1/P2 |

### Competitive Analysis

| Competitor | Product | Strengths | Weaknesses | Market Share |
|------------|---------|-----------|------------|--------------|
| [Comp 1] | [Product] | [List] | [List] | [X%] |

### Market Trends
- [Trend 1]
- [Trend 2]

---

## 4. Problem Statement

**Problem Overview:**
[Comprehensive Problem Description]

**Quantitative Evidence:**
- [Metric 1]: [Data]
- [Metric 2]: [Data]
- [Market Research]: [Findings]

**Qualitative Evidence:**
- User Interviews: [Summary]
- Customer Feedback: [Quotes]
- Support Tickets: [Analysis]

**Business Impact of NOT Solving:**
- Revenue Loss: [€X]
- Customer Churn: [X%]
- Competitive Disadvantage: [Description]

---

## 5. User Personas & Scenarios

### Persona 1: [Name]

**Demographics:**
- Age: [Range]
- Location: [Geo]
- Income: [Range]
- Education: [Level]

**Psychographics:**
- Goals: [List]
- Motivations: [List]
- Frustrations: [List]
- Behaviors: [List]

**Technology Profile:**
- Devices: [List]
- Software: [List]
- Tech Proficiency: [Level]

**User Journey:**
[Detailed Journey Map]

**Pain Points:**
[Detailed Pain Point Analysis]

**User Quotes:**
> "[Direct Quote from Research]"

---

## 6. Product Vision & Objectives

### Vision Statement
[Inspiring Vision: What does the world look like in 3-5 years?]

### Product Objectives

| Objective | Description | Success Criteria | Owner |
|-----------|-------------|------------------|-------|
| [Obj 1] | [Detail] | [Measurable] | [Team] |

### Strategic Goals Alignment

| Company Goal | Product Contribution | Impact |
|--------------|---------------------|--------|
| [Goal 1] | [How PRD supports] | [Metric] |

---

## 7. Functional Requirements

### 7.1 Core Features

#### Feature 1: [Name]

**Description:**
[Detailed Description]

**User Stories:**
- As a [user], I want to [action], so that [benefit]
- As a [user], I want to [action], so that [benefit]

**Functional Specifications:**
1. The system **shall** [requirement]
2. The system **shall** [requirement]
3. The system **shall** [requirement]

**Acceptance Criteria:**
- **Given** [context]
- **When** [action]
- **Then** [expected outcome]

**Priority:** P0 / P1 / P2

**Dependencies:**
[List of Dependencies]

**Assumptions:**
[Key Assumptions]

---

### 7.2 Secondary Features

[Repeat structure for each feature]

---

## 8. Non-Functional Requirements

### 8.1 Performance

| Requirement | Specification | Method |
|-------------|---------------|--------|
| Page Load Time | <2 seconds (95th percentile) | Lighthouse, RUM |
| API Response Time | <200ms (average) | APM Tools |
| Concurrent Users | 100,000+ | Load Testing |
| Uptime | 99.95% annually | SLA Monitoring |

### 8.2 Security

**Authentication:**
- [Requirements]

**Authorization:**
- [Requirements]

**Data Protection:**
- Encryption at Rest: [Standard]
- Encryption in Transit: [Standard]
- PII Handling: [GDPR/CCPA Compliance]

**Compliance:**
- [GDPR]
- [HIPAA]
- [SOC 2]
- [ISO 27001]

### 8.3 Scalability

**Horizontal Scaling:**
[Requirements]

**Vertical Scaling:**
[Requirements]

**Database Scaling:**
[Strategy]

### 8.4 Accessibility

**Standards:**
- WCAG 2.1 Level AA compliance
- Keyboard Navigation
- Screen Reader Support

**Testing:**
[Accessibility Testing Plan]

### 8.5 Usability

**Response Time:**
- User-initiated actions: <1s feedback

**Error Handling:**
- Clear error messages
- Recovery paths

**Internationalization:**
- Languages: [List]
- Localization: [Strategy]

---

## 9. User Experience & Design

### 9.1 User Flows

[Detailed User Flow Diagrams]

### 9.2 Wireframes

[Link to Figma/Sketch]

### 9.3 Design Principles

[Guiding Design Principles]

### 9.4 UI Components

[Component Library Reference]

---

## 10. Technical Architecture

### 10.1 System Architecture

[High-Level Architecture Diagram]

### 10.2 Technology Stack

| Layer | Technology | Rationale |
|-------|------------|-----------|
| Frontend | [Tech] | [Why] |
| Backend | [Tech] | [Why] |
| Database | [Tech] | [Why] |
| Infrastructure | [Tech] | [Why] |

### 10.3 Data Model

[Entity Relationship Diagram]

### 10.4 API Design

[API Specifications / OpenAPI Spec]

---

## 11. Integration & Dependencies

### 11.1 Internal Integrations

| System | Integration Type | Dependency | Owner |
|--------|------------------|------------|-------|
| [System 1] | [API/Event/Batch] | [Critical/High/Med] | [Team] |

### 11.2 External Integrations

| Service | Purpose | SLA | Cost |
|---------|---------|-----|------|
| [Service 1] | [Purpose] | [Uptime] | [€/month] |

### 11.3 Dependencies

[Critical Path Dependencies]

---

## 12. Security & Compliance

### 12.1 Security Requirements

[Detailed Security Specs]

### 12.2 Compliance Requirements

| Regulation | Requirement | Implementation | Validation |
|------------|-------------|----------------|------------|
| GDPR | [Req] | [How] | [Method] |

### 12.3 Data Privacy

**Data Collection:**
[What data is collected, why, how]

**Data Retention:**
[Retention policies]

**User Rights:**
[Right to Access, Delete, Portability]

---

## 13. Success Metrics & KPIs

### 13.1 Business Metrics

| Metric | Baseline | Target | Timeframe | Measurement |
|--------|----------|--------|-----------|-------------|
| Revenue | [€X] | [€Y] | [Date] | [Method] |
| Customer Acquisition | [X] | [Y] | [Date] | [Method] |
| Market Share | [X%] | [Y%] | [Date] | [Method] |

### 13.2 Product Metrics

| Metric | Baseline | Target | Timeframe | Measurement |
|--------|----------|--------|-----------|-------------|
| DAU | [X] | [Y] | [Date] | Analytics |
| Engagement Rate | [X%] | [Y%] | [Date] | Analytics |
| NPS | [X] | [Y] | [Date] | Survey |

### 13.3 Technical Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Uptime | 99.95% | Monitoring |
| Error Rate | <0.1% | APM |
| Page Load | <2s | RUM |

---

## 14. Timeline & Resource Planning

### 14.1 Project Phases

| Phase | Duration | Deliverables | Resources |
|-------|----------|--------------|-----------|
| Discovery | [X weeks] | [List] | [Team] |
| Design | [X weeks] | [List] | [Team] |
| Development | [X weeks] | [List] | [Team] |
| Testing | [X weeks] | [List] | [Team] |
| Launch | [X weeks] | [List] | [Team] |

### 14.2 Milestones

[Gantt Chart / Timeline]

### 14.3 Resource Allocation

| Role | FTE | Duration | Cost |
|------|-----|----------|------|
| PM | 1.0 | [X months] | [€] |
| Engineering | 5.0 | [X months] | [€] |
| Design | 2.0 | [X months] | [€] |
| QA | 2.0 | [X months] | [€] |

---

## 15. Budget & ROI Analysis

### 15.1 Development Costs

| Category | Cost |
|----------|------|
| Personnel | [€X] |
| Infrastructure | [€X] |
| Third-Party Services | [€X] |
| **Total** | **[€X]** |

### 15.2 Ongoing Costs

| Category | Monthly | Annual |
|----------|---------|--------|
| Infrastructure | [€X] | [€Y] |
| Services | [€X] | [€Y] |
| **Total** | **[€X]** | **[€Y]** |

### 15.3 Revenue Projections

| Year | Revenue | Cost | Profit | ROI |
|------|---------|------|--------|-----|
| Y1 | [€X] | [€Y] | [€Z] | [X%] |
| Y2 | [€X] | [€Y] | [€Z] | [X%] |
| Y3 | [€X] | [€Y] | [€Z] | [X%] |

### 15.4 Break-Even Analysis

[Analysis]

---

## 16. Risk Management

### 16.1 Risk Register

| Risk | Impact | Likelihood | Mitigation | Owner |
|------|--------|------------|------------|-------|
| [Risk 1] | High/Med/Low | High/Med/Low | [Strategy] | [Name] |
| [Risk 2] | High/Med/Low | High/Med/Low | [Strategy] | [Name] |

### 16.2 Contingency Plans

[Detailed Contingency Plans]

---

## 17. Go-to-Market Strategy

### 17.1 Launch Strategy

[Launch Plan]

### 17.2 Marketing & Positioning

[Marketing Strategy]

### 17.3 Sales Enablement

[Sales Materials, Training]

### 17.4 Customer Support

[Support Plan]

---

## 18. Appendices

### Appendix A: Research Data
[Detailed Research Findings]

### Appendix B: Competitive Analysis
[Deep Competitive Research]

### Appendix C: Technical Specifications
[Detailed Tech Specs]

### Appendix D: Legal & Compliance Documents
[Contracts, Compliance Docs]

---

## Document Approval

| Stakeholder | Role | Approval | Date | Signature |
|-------------|------|----------|------|-----------|
| [Name] | [Role] | ✅ / ⏳ / ❌ | [Date] | [Signature] |

---

## Changelog

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Name] | Initial Draft |
| 1.1 | [Date] | [Name] | Stakeholder Feedback |
| 2.0 | [Date] | [Name] | Final Approval |

```

---

## Template 3: Amazon PR/FAQ

**When to use:**
- 🚀 Major Strategic Initiative
- 🚀 Customer Obsession Culture
- 🚀 Evaluating multiple solution approaches
- 🚀 Executive-Level Decision needed
- 🚀 Significant Investment required

**Length:** 5-10 pages
**Creation time:** 4-8 weeks (10+ drafts typical!)
**Review Process:** 5+ review meetings with stakeholders

---

### Amazon PR/FAQ Template

```markdown
---
title: [Product Name] - PR/FAQ
space_key: [SPACE]
status: Draft
author: [PM Name]
created: [YYYY-MM-DD]
last_updated: [YYYY-MM-DD]
draft_version: [X]
---

# [Product Name] - Press Release & FAQ

**Status:** 🟡 Draft [X] / In Review / Approved
**Owner:** [PM Name]
**Target Launch:** [Date]

---

## Part 1: Press Release (Customer-Facing)

### [PRODUCT NAME] - [HEADLINE]

**[CITY, DATE]** – [Company Name] today announced [Product Name], [one-sentence description].

---

### Summary (1 Paragraph)

[Product Name] is [brief description]. It [solves problem] for [customer segment] by [approach/innovation]. Starting [date], customers can [action].

---

### Problem (1 Paragraph - Customer Perspective)

For years, [customer segment] have struggled with [problem]. This has led to [negative consequence]. Customers have told us: "[direct customer quote highlighting pain]."

---

### Solution (1 Paragraph - How Product Solves)

[Product Name] solves this by [simple explanation]. Now customers can [benefit 1], [benefit 2], and [benefit 3]. "[Customer quote about solution value]," said [fictional customer name].

---

### How It Works (1-2 Paragraphs - Simple Explanation)

Getting started is simple:
1. [Step 1]
2. [Step 2]
3. [Step 3]

[Product Name] uses [technology/approach] to ensure [key benefit]. Unlike alternatives, [differentiation].

---

### Customer Testimonial (Fictional but Realistic)

"[Product Name] has completely changed how we [activity]," said [fictional customer name], [title] at [fictional company]. "We've seen [specific result] in just [timeframe]. It's exactly what we needed."

---

### Availability & Pricing

[Product Name] is available starting [date] at [pricing model]. For more information, visit [URL] or contact [email].

---

### About [Company]

[Standard company boilerplate]

---

## Part 2: FAQ (Internal - Stakeholder-Facing)

### External FAQs (Customer-Oriented)

#### Q1: Who is this for?

**A:** [Target customer segment description with use cases]

---

#### Q2: How much does it cost?

**A:** [Pricing model explanation with rationale]

---

#### Q3: How is this different from [Competitor X]?

**A:** [Competitive differentiation - honest assessment]

---

#### Q4: What if I already use [Alternative Solution]?

**A:** [Migration path, compatibility, or positioning]

---

#### Q5: How does it work technically?

**A:** [High-level technical explanation for non-technical audience]

---

#### Q6: Is my data secure?

**A:** [Security & privacy assurances with specifics]

---

#### Q7: When will it be available in [Region/Language]?

**A:** [Rollout plan]

---

### Internal FAQs (Stakeholder-Oriented)

#### Q1: What is the market size and opportunity?

**A:** [Market analysis with data]
- Total Addressable Market (TAM): [€X]
- Serviceable Addressable Market (SAM): [€Y]
- Serviceable Obtainable Market (SOM): [€Z]
- Growth Rate: [X% CAGR]

---

#### Q2: What are the economics? What is the P&L impact?

**A:**

| Metric | Year 1 | Year 2 | Year 3 |
|--------|--------|--------|--------|
| Revenue | [€X] | [€Y] | [€Z] |
| Costs | [€A] | [€B] | [€C] |
| Profit | [€X-A] | [€Y-B] | [€Z-C] |
| ROI | [X%] | [Y%] | [Z%] |

**Assumptions:** [Key assumptions]

---

#### Q3: What dependencies exist? What is required to deliver?

**A:**

**Critical Dependencies:**
- Engineering: [X FTE for Y months]
- Design: [X FTE for Y months]
- Infrastructure: [Requirements]
- Partnerships: [Which partners needed]

**Timeline:**
- MVP: [Date]
- Beta: [Date]
- GA: [Date]

---

#### Q4: Who are the competitors and what do they offer?

**A:**

| Competitor | Product | Strengths | Weaknesses | Our Advantage |
|------------|---------|-----------|------------|---------------|
| [Comp 1] | [Product] | [List] | [List] | [Why we're better] |

---

#### Q5: What is our moat? Why can't competitors replicate this?

**A:**
- [Moat 1]: [Explanation]
- [Moat 2]: [Explanation]
- [Moat 3]: [Explanation]

**Barriers to Entry:** [What makes this hard to copy]

---

#### Q6: What are the top 3 risks and how do we mitigate them?

**A:**

1. **[Risk 1]** (Likelihood: High/Med/Low, Impact: High/Med/Low)
   - **Mitigation:** [Strategy]
   - **Contingency:** [Plan B]

2. **[Risk 2]** (Likelihood: High/Med/Low, Impact: High/Med/Low)
   - **Mitigation:** [Strategy]
   - **Contingency:** [Plan B]

3. **[Risk 3]** (Likelihood: High/Med/Low, Impact: High/Med/Low)
   - **Mitigation:** [Strategy]
   - **Contingency:** [Plan B]

---

#### Q7: What are the top 3 reasons this could fail?

**A:**
1. **[Failure Reason 1]:** [Explanation + Prevention]
2. **[Failure Reason 2]:** [Explanation + Prevention]
3. **[Failure Reason 3]:** [Explanation + Prevention]

**Validation Plan:** [How we'll test assumptions before full launch]

---

#### Q8: What technical challenges exist?

**A:**
- [Challenge 1]: [Technical complexity + approach]
- [Challenge 2]: [Technical complexity + approach]
- [Challenge 3]: [Technical complexity + approach]

**Technical Risks:** [Assessment]

---

#### Q9: What is the Go-to-Market strategy?

**A:**

**Target Segments:**
- Primary: [Segment] ([X% of TAM])
- Secondary: [Segment] ([Y% of TAM])

**Distribution Channels:**
- [Channel 1]: [Strategy]
- [Channel 2]: [Strategy]

**Marketing:**
- Launch: [Approach]
- Ongoing: [Strategy]

**Sales:**
- [Sales approach]

---

#### Q10: What metrics define success?

**A:**

**North Star Metric:** [Primary Success Indicator]

**Supporting Metrics:**

| Metric | Baseline | 6 Months | 12 Months | 24 Months |
|--------|----------|----------|-----------|-----------|
| [Metric 1] | [X] | [Y] | [Z] | [A] |
| [Metric 2] | [X] | [Y] | [Z] | [A] |
| [Metric 3] | [X] | [Y] | [Z] | [A] |

---

#### Q11: What is the pricing rationale?

**A:**
- **Pricing Model:** [Model + Justification]
- **Competitive Comparison:** [How we compare]
- **Customer Value:** [Value delivered vs. price]
- **Margin Analysis:** [Economics]

---

#### Q12: What are the regulatory/compliance considerations?

**A:**
- [Regulation 1]: [Requirement + Plan]
- [Regulation 2]: [Requirement + Plan]
- [Compliance Timeline]: [When compliant]

---

#### Q13: How does this align with company strategy?

**A:**

| Company OKR | Product Contribution | Impact |
|-------------|---------------------|--------|
| [OKR 1] | [How product helps] | [Metric] |

---

#### Q14: What are we NOT doing (and why)?

**A:**

Out of Scope (for now):
- ❌ [Feature X]: [Reason - e.g., "Not validated with customers yet"]
- ❌ [Market Y]: [Reason - e.g., "Too small, focus on core first"]
- ❌ [Capability Z]: [Reason - e.g., "Technical complexity not worth ROI"]

**Future Consideration:** [What might come later]

---

#### Q15: What feedback have we received so far?

**A:**

**Customer Research:**
- Interviews: [X customers, key findings]
- Surveys: [X responses, insights]
- Beta Feedback: [Summary if applicable]

**Internal Feedback:**
- Engineering: [Concerns + resolutions]
- Sales: [Concerns + resolutions]
- Support: [Concerns + resolutions]

---

## Iteration History

| Draft | Date | Key Changes | Reviewers |
|-------|------|-------------|-----------|
| 1 | [Date] | Initial draft | [Names] |
| 2 | [Date] | Pricing model revised based on finance feedback | [Names] |
| X | [Date] | [Changes] | [Names] |

---

## Next Steps

- [ ] Review Meeting 1: [Date] with [Stakeholders]
- [ ] Review Meeting 2: [Date] with [Stakeholders]
- [ ] Executive Approval: [Date]
- [ ] Development Kickoff: [Date]

```

---

## Template 4: Hybrid Agile PRD

**When to use:**
- 🔄 Medium-Large Team (10-50 people)
- 🔄 Complex Feature with Cross-Functional Collaboration
- 🔄 Agile methodology, but more structure needed
- 🔄 Remote/Distributed Teams
- 🔄 Balance between Speed and Clarity

**Length:** 5-10 pages
**Creation time:** 1-2 weeks
**Review Stakeholders:** 10-20 people

---

### Hybrid Agile PRD Template

```markdown
---
title: [Feature Name] - Product Requirements
space_key: [SPACE]
status: Living Document
author: [PM Name]
created: [YYYY-MM-DD]
last_updated: [YYYY-MM-DD]
epic_link: [JIRA-XXX]
sprint: [Current Sprint]
---

# [Feature Name] - Product Requirements

**Status:** 🟢 Active Development
**Owner:** [PM Name]
**Epic:** [JIRA-XXX](link)
**Current Sprint:** Sprint [X]
**Target Release:** Q[X] 202[X]

---

## 📋 Document Status

| Section | Status | Last Updated |
|---------|--------|--------------|
| Problem & Vision | ✅ Complete | [Date] |
| User Stories | 🟡 In Progress | [Date] |
| Design | 🔵 Not Started | [Date] |
| Technical Spec | 🟡 In Progress | [Date] |

**Next Review:** [Date]

---

## 🎯 Vision & Problem

### Vision Statement

[1-2 sentences: What does success look like?]

### Problem Statement

**Problem:**
[Specific Problem]

**Who Has This Problem:**
- [User Type 1] ([X% of users])
- [User Type 2] ([Y% of users])

**Impact:**
- Quantitative: [Metrics]
- Qualitative: [User Quotes]

**Current Workarounds:**
[What do users do currently? Why doesn't it work?]

---

## 👥 User Personas

### Persona 1: [Name]

**Profile:**
- Role: [Title]
- Goals: [Top 3 Goals]
- Pain Points: [Top 3 Frustrations]
- Quote: "[User Quote]"

**User Journey:**
[Current State vs. Future State]

---

## 📊 Success Metrics

**North Star:** [Primary Metric]

| Metric | Baseline | Target | Sprint Goal | Measurement |
|--------|----------|--------|-------------|-------------|
| [Metric 1] | [X] | [Y] | [Sprint Z: A] | [How] |
| [Metric 2] | [X] | [Y] | [Sprint Z: B] | [How] |

**Leading Indicators:**
[Early signals that predict success]

---

## 🗂️ Feature Themes & Epics

### Theme: [High-Level Theme]

**Epic 1:** [Epic Name] ([JIRA-XXX](link))
- **Goal:** [What does this epic achieve?]
- **User Stories:** [X stories]
- **Story Points:** [X points]
- **Status:** [Not Started / In Progress / Done]

**Epic 2:** [Epic Name] ([JIRA-XXX](link))
- **Goal:** [What does this epic achieve?]
- **User Stories:** [X stories]
- **Story Points:** [X points]
- **Status:** [Not Started / In Progress / Done]

---

## 📝 User Stories (Top Priority)

### Sprint [Current]: In Progress

#### Story 1: [JIRA-XXX] - [Title]

**User Story:**
As [User Type]
I want [Action]
to [Benefit]

**Acceptance Criteria:**
- [ ] Given [Context] When [Action] Then [Outcome]
- [ ] Given [Context] When [Action] Then [Outcome]
- [ ] Given [Context] When [Action] Then [Outcome]

**Story Points:** [X]
**Status:** [To Do / In Progress / In Review / Done]
**Assignee:** [Name]
**Sprint:** Sprint [X]

**Technical Notes:**
- [Implementation detail]
- [Dependency]

**Design:**
[Link to Figma/Sketch]

---

### Sprint [Next]: Planned

[Repeat structure for upcoming stories]

---

### Backlog: Prioritized

[List of future stories with priority]

---

## 🎨 User Experience & Design

### User Flows

[Link to detailed flows]

**Key Flows:**
1. [Flow 1]: [Description]
2. [Flow 2]: [Description]

### Wireframes & Mockups

[Embedded images or links]

**Design Status:**
- [ ] Low-Fidelity Wireframes
- [ ] High-Fidelity Mockups
- [ ] Interactive Prototype
- [ ] Design System Components

### Design Decisions

| Decision | Rationale | Alternatives Considered |
|----------|-----------|------------------------|
| [Decision 1] | [Why] | [What we didn't choose] |

---

## 🛠️ Technical Architecture

### System Components

[High-Level Architecture Diagram]

### APIs & Integrations

| API | Purpose | Owner | Status |
|-----|---------|-------|--------|
| [API 1] | [Purpose] | [Team] | [Ready / In Dev / Planned] |

### Data Model

[Key entities and relationships]

### Technical Constraints

- Performance: [Requirements]
- Security: [Requirements]
- Scalability: [Requirements]

### Open Technical Questions

- [ ] [Question 1]
- [ ] [Question 2]

---

## 🔗 Dependencies & Risks

### Internal Dependencies

| Dependency | Type | Team | Impact | Status |
|------------|------|------|--------|--------|
| [Dep 1] | Blocking / High / Med | [Team] | [Impact] | [Status] |

### External Dependencies

| Service | Purpose | SLA | Risk |
|---------|---------|-----|------|
| [Service 1] | [Purpose] | [Uptime] | High/Med/Low |

### Risks

| Risk | Impact | Likelihood | Mitigation | Owner |
|------|--------|------------|------------|-------|
| [Risk 1] | High/Med/Low | High/Med/Low | [Plan] | [Name] |

---

## 📅 Roadmap & Timeline

### Phase 1: MVP (Sprint [X-Y])

**Goal:** [What's delivered]

**Features:**
- ✅ [Feature 1] (Done)
- 🟡 [Feature 2] (In Progress - Sprint X)
- 🔵 [Feature 3] (Planned - Sprint Y)

**Milestone:** [Date]

---

### Phase 2: Enhancement (Sprint [X-Y])

**Goal:** [What's delivered]

**Features:**
- 🔵 [Feature 4]
- 🔵 [Feature 5]

**Milestone:** [Date]

---

## ⚙️ Scope Management

### In Scope (This Release)

✅ [Feature 1]
✅ [Feature 2]
✅ [Feature 3]

### Out of Scope (Future Releases)

❌ [Feature X]: [Why out of scope - e.g., "Phase 2"]
❌ [Feature Y]: [Why out of scope - e.g., "Not validated yet"]

### Nice-to-Have (If Time Permits)

🟢 [Feature Z]: [Conditional on sprint capacity]

---

## 🔗 Related Links

- **Jira Epic:** [JIRA-XXX](link)
- **Jira Board:** [Sprint Board](link)
- **Design:** [Figma](link)
- **Tech Spec:** [Engineering Doc](link)
- **User Research:** [Research Findings](link)
- **Analytics Dashboard:** [Metrics](link)

---

## 💬 Open Questions & Decisions

### Open Questions

- [ ] [Question 1] (Owner: [Name], Due: [Date])
- [ ] [Question 2] (Owner: [Name], Due: [Date])

### Recent Decisions

| Date | Decision | Rationale | Decider |
|------|----------|-----------|---------|
| [Date] | [What was decided] | [Why] | [Who] |

---

## 📜 Changelog (Recent Sprints)

| Sprint | Date | Changes | Author |
|--------|------|---------|--------|
| Sprint X | [Date] | Initial Draft | [Name] |
| Sprint X+1 | [Date] | Added Stories 1-5 based on refinement | [Name] |
| Sprint X+2 | [Date] | Updated AC for Story 3 per eng feedback | [Name] |

---

## 🗣️ Feedback & Comments

[Space for stakeholder comments during review]

**Latest Feedback:**
- [Date] - [Stakeholder]: [Comment]
- [Date] - [Stakeholder]: [Comment]

```

---

## Template Selection Guide

**Quick Decision Tree:**

```
START → Small Team (<10)?
  ├─ YES → MVP/Early-Stage?
  │   ├─ YES → **Lean PRD** ✅
  │   └─ NO → Complex Feature?
  │       ├─ YES → **Hybrid Agile PRD**
  │       └─ NO → **Lean PRD** ✅
  └─ NO → Large Team (>50)?
      ├─ YES → Regulated Industry?
      │   ├─ YES → **Traditional PRD**
      │   └─ NO → Strategic Initiative?
      │       ├─ YES → **Amazon PR/FAQ**
      │       └─ NO → **Hybrid Agile PRD**
      └─ NO → Medium Team (10-50)?
          └─ **Hybrid Agile PRD**
```

**When in Doubt:**
→ Start with **Lean PRD** ✅
→ Add structure if needed (KISS Principle!)

---

*PRD Templates for Cursor AI PM Operating System*
*Beyond 7, 2025*
