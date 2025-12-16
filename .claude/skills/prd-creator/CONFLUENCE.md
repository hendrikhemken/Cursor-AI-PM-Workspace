# Confluence Workflows for PRDs
*Confluence MCP Integration - Page Creation, Updates & Jira Linking*

---

## 🛠️ Available MCP Tools

**Confluence Page Management:**
- `confluence_create_page` - Create new page
- `confluence_update_page` - Update existing page
- `confluence_get_page` - Read page content
- `confluence_get_page_children` - Get child pages
- `confluence_search` - Search pages
- `confluence_add_label` - Add labels
- `confluence_add_comment` - Add comment
- `confluence_delete_page` - Delete page (CAUTION!)

**Jira Integration:**
- `jira_create_issue` - Create Epic/Story
- `jira_update_issue` - Update issue
- `jira_search` - Search issues

**All tools are native MCP Tools** - directly usable, no Python scripts needed!

---

## 📝 Workflow 1: Create New PRD

### Step 1: Prepare Markdown Draft

**Input from PM:**
- Space Key (e.g., "PROD", "DEV", "TEAM")
- Title (e.g., "Multi-Video Upload - PRD")
- Parent Page ID (optional, if part of a larger initiative)

**Prepare Markdown:**
```markdown
# Multi-Video Upload - PRD

**Status:** Draft
**Owner:** Jane Doe
**Target Release:** Q2 2025

## Problem Statement
[Content...]

## Success Metrics
[Content...]
```

---

### Step 2: Markdown → Confluence HTML Conversion

**Important:** Confluence uses Storage Format (HTML), not Markdown!

**Conversion Rules:**

| Markdown | Confluence HTML |
|----------|-----------------|
| `# Heading` | `<h1>Heading</h1>` |
| `## Heading` | `<h2>Heading</h2>` |
| `**bold**` | `<strong>bold</strong>` |
| `*italic*` | `<em>italic</em>` |
| `[Link](url)` | `<a href="url">Link</a>` |
| Code Block | `<ac:structured-macro ac:name="code">...</ac:structured-macro>` |
| Table | `<table>...</table>` |

**✅ MCP Tool converts automatically** Markdown → HTML!

**Tip:** Write in Markdown, the tool handles the conversion.

---

### Step 3: Create Confluence Page

**→ Use the `confluence_create_page` tool**

**Parameters:**
- `space_key`: "PROD" (the Confluence Space Key)
- `title`: "Multi-Video Upload - PRD"
- `content`: Markdown content (automatically converted to HTML)
- `parent_id`: "123456789" (optional - if part of a page hierarchy)

**Example Content:**
```markdown
# Multi-Video Upload - PRD

**Status:** 🟡 Draft
**Owner:** Jane Doe
**Target Release:** Q2 2025
**Epic:** PROD-123

---

## 📋 Executive Summary

Multi-Video Upload allows creators to batch-upload multiple videos
simultaneously, reducing upload time by 70% and increasing creator
satisfaction.

[... rest of PRD content ...]
```

**Response contains:**
- `id`: Page ID (for future updates - important to save!)
- `title`: Page Title
- `_links.webui`: URL to share with team

**→ Save the Page ID** for later updates!

---

### Step 4: Add Labels

**→ Use `confluence_add_label` for each label**

**Recommended Labels:**

**Category Labels:**
- `prd` (always!)

**Timeline Labels:**
- `q1-2025`, `q2-2025`, `q3-2025`, `q4-2025`

**Feature Labels:**
- `feature-multi-upload`, `feature-analytics`, etc.

**Status Labels:**
- `status-draft`, `status-in-review`, `status-approved`, `status-archived`

**Team Labels:**
- `team-platform`, `team-growth`, `team-infra`

**Example Label Set:**
```
→ confluence_add_label(page_id, "prd")
→ confluence_add_label(page_id, "q2-2025")
→ confluence_add_label(page_id, "feature-multi-upload")
→ confluence_add_label(page_id, "status-draft")
→ confluence_add_label(page_id, "team-platform")
```

---

### Step 5: Create Epic in Jira & Link

**Optional: Create Epic in Jira**

**→ Use `jira_create_issue` tool**

**Parameters:**
- `project_key`: "PROD"
- `issue_type`: "Epic"
- `summary`: "Multi-Video Upload"
- `description`: Link to PRD + Summary
- `additional_fields`: Labels, etc.

**Epic Description Example:**
```markdown
Product Requirements Document:
https://company.atlassian.net/wiki/spaces/PROD/pages/987654321

## Summary
Batch video upload feature enabling creators to upload multiple
videos simultaneously.

## Success Metrics
- Upload Success Rate: 85% → 95%
- Avg Upload Time: 45s → <15s

See PRD for full details.
```

**→ Response contains:**
- `key`: Epic Key (e.g., "PROD-123")

---

### Step 6: Update PRD with Epic Link

**→ Use `confluence_update_page` tool**

**Parameters:**
- `page_id`: The Page ID from Step 3
- `title`: "Multi-Video Upload - PRD" (can stay the same)
- `content`: Updated content with Epic Link
- `version_comment`: "Added Epic Link" (important for Changelog!)

**Updated Content Example:**
```markdown
# Multi-Video Upload - PRD

**Status:** 🟡 Draft
**Owner:** Jane Doe
**Target Release:** Q2 2025
**Epic:** [PROD-123](https://company.atlassian.net/browse/PROD-123)

[... rest of content ...]
```

**→ Version Comment documents changes** (appears in Page History)

---

### Step 7: Output for PM

```
✅ PRD successfully created in Confluence!

📄 PRD: https://company.atlassian.net/wiki/spaces/PROD/pages/987654321
🎯 Epic: PROD-123 (https://company.atlassian.net/browse/PROD-123)

Labels:
- prd
- q2-2025
- feature-multi-upload
- status-draft
- team-platform

Next Steps:
1. Share PRD with stakeholders (Design, Engineering)
2. Gather feedback & iterate
3. Update status: Draft → In Review → Approved
4. Derive User Stories from PRD (via user-stories skill)
```

---

## 🔄 Workflow 2: Update Existing PRD

### Use Case: Incorporate Stakeholder Feedback

**Step 1: Read Page**

**→ Use `confluence_get_page` tool**

**Parameters:**
- `page_id`: "987654321"
- `convert_to_markdown`: true (for easier editing)
- `include_metadata`: true (for labels, version, etc.)

**Response contains:**
- `markdown`: Page content as Markdown
- `version.number`: Current version (e.g., 3)
- `metadata.labels`: Current labels

---

**Step 2: Update Content**

**→ Use `confluence_update_page` tool**

**Parameters:**
- `page_id`: "987654321"
- `title`: "Multi-Video Upload - PRD" (can stay the same)
- `content`: Updated content with stakeholder feedback
- `version_comment`: "Added Design Feedback: Updated wireframes, clarified edge cases"

**Important:**
- `version_comment` documents changes (Changelog!)
- Version Number auto-increments
- Page History tracked automatically

---

## 🔍 Workflow 3: Search PRD (when Page ID unknown)

### Use Case: User says "Update the Multi-Upload PRD"

**Step 1: Search**

**→ Use `confluence_search` tool**

**Parameters:**
- `query`: "Multi-Video Upload PRD"
- `limit`: 5 (max results)

**Response contains:**
- `results`: Array of found pages
  - `id`: Page ID
  - `title`: Page Title
  - `space.key`: Space Key
  - `url`: Page URL

**Step 2: Ask PM which page is meant**

```
I found 2 PRDs:

1. Multi-Video Upload - PRD (PROD Space)
2. Video Upload Optimization - PRD (TECH Space)

Which one do you want to update?
```

---

## 🏗️ Workflow 4: Hierarchical Structure (Parent/Child Pages)

### Use Case: PRD with Sub-Pages (e.g., Design Spec, Tech Spec)

**Structure:**
```
📄 Multi-Video Upload - PRD (Parent)
  ├─ 🎨 Design Spec (Child)
  ├─ 🛠️ Technical Spec (Child)
  └─ 📊 User Research Findings (Child)
```

**Create Parent Page:**

**→ Use `confluence_create_page` for Parent**

**Parameters:**
- `space_key`: "PROD"
- `title`: "Multi-Video Upload - PRD"
- `content`: [PRD Content]

**→ Save the `parent_id` from the Response!**

**Create Child Pages:**

**→ Use `confluence_create_page` for each Child**

**Design Spec:**
- `space_key`: "PROD"
- `title`: "Multi-Video Upload - Design Spec"
- `content`: [Design Content]
- `parent_id`: [Parent Page ID from above]

**Technical Spec:**
- `space_key`: "PROD"
- `title`: "Multi-Video Upload - Technical Spec"
- `content`: [Tech Content]
- `parent_id`: [Parent Page ID from above]

**Benefit:**
- Hierarchical organization
- PRD remains "Landing Page"
- Details in sub-pages
- Navigation easier

---

## 📊 Workflow 5: Get Child Pages

### Use Case: "Show me all sub-docs for the PRD"

**→ Use `confluence_get_page_children` tool**

**Parameters:**
- `parent_id`: "987654321"
- `include_content`: false (only titles, no full content)
- `limit`: 25 (max results)

**Response contains:**
- `results`: Array of child pages
  - `id`: Page ID
  - `title`: Page Title

**Example Output:**
```
Found 2 child pages:
1. Multi-Video Upload - Design Spec (ID: 111111111)
2. Multi-Video Upload - Technical Spec (ID: 222222222)
```

---

## 💬 Workflow 6: Add Comments

### Use Case: Stakeholder Feedback as Comment

**→ Use `confluence_add_comment` tool**

**Parameters:**
- `page_id`: "987654321"
- `content`: Comment text (Markdown supported)

**Example Comment:**
```markdown
**Engineering Feedback:**

The proposed upload architecture looks good, but we need to clarify:
- Max file size per video?
- Total batch size limit?
- Concurrent upload streams (sequential vs. parallel)?

Please add to Technical Considerations section.
```

**When to use:**
- Document stakeholder feedback
- Track open questions
- Review comments
- @Mentions for notifications

---

## 🔗 Integration: Confluence ↔ Jira

### Best Practice: Two-Way Linking

**Confluence PRD:**
```markdown
**Epic:** [PROD-123](https://company.atlassian.net/browse/PROD-123)
```

**Jira Epic Description:**
```markdown
📄 **Product Requirements Document:**
https://company.atlassian.net/wiki/spaces/PROD/pages/987654321

## Summary
[Brief Summary from PRD]

See PRD for full details, metrics, and requirements.
```

**Benefit:**
- Single Source of Truth (PRD in Confluence)
- Easy Navigation (Jira → PRD, PRD → Jira)
- Context for Developers
- PRD remains "Landing Page" for feature

---

## 📁 Confluence Space Organization

### Recommended Structure

```
📁 PROD (Space)
  ├─ 📂 Product Requirements (Parent Page)
  │   ├─ 📄 Multi-Video Upload - PRD
  │   ├─ 📄 Advanced Search - PRD
  │   └─ 📄 User Profile V2 - PRD
  ├─ 📂 User Research
  │   └─ [Research Docs]
  ├─ 📂 Design
  │   └─ [Design Specs]
  └─ 📂 Technical Specs
      └─ [Tech Docs]
```

**Why:**
- Clear hierarchy
- Easy discovery
- Consistent naming
- Team knows where things are

---

## 🚨 Common Mistakes & How to Avoid

### Mistake 1: Missing Version Comment

**Problem:**
```
→ confluence_update_page without version_comment
```

**Impact:**
- No changelog
- Unclear what was changed
- Poor traceability

**Solution:**
```
→ ALWAYS use version_comment:
  "Added Success Metrics section per stakeholder feedback"
  "Updated wireframes based on Design review"
  "Clarified edge cases from Engineering feedback"
```

---

### Mistake 2: Forgetting Labels

**Problem:**
PRD without labels → hard to find, categorize

**Solution:**
Always add at minimum:
- `prd`
- `status-[x]` (draft/in-review/approved)
- `q[x]-202[x]` (timeline)

---

### Mistake 3: Missing or Broken Jira Link

**Problem:**
```markdown
**Epic:** PROD-123
```

**Impact:**
- No clickable link
- Poor UX

**Solution:**
```markdown
**Epic:** [PROD-123](https://company.atlassian.net/browse/PROD-123)
```

**→ Always use full URL with Markdown link!**

---

### Mistake 4: Wrong or Non-existent Space Key

**Problem:**
```
→ confluence_create_page with space_key="PRODUKTMANAGEMENT"
→ Space doesn't exist → ERROR
```

**Solution:**
1. Ask PM: "Which space? (e.g., 'PROD', 'DEV')"
2. When unsure: Search existing pages to identify
3. Confirm before creating

---

### Mistake 5: Lost Page ID

**Problem:**
```
→ confluence_create_page called
→ Page ID NOT saved
→ Later: "What was that Page ID again?" 😱
```

**Solution:**
```
→ ALWAYS save Page ID from Response!
→ Output to PM: "Page ID: 987654321 (for future updates)"
```

---

## 💡 Pro Tips

### Tip 1: Use Version History

Confluence automatically tracks versions.

**Check Version History:**
→ Page → "..." Menu → "Page History"

**Restore old version:**
→ Page History → "Restore" at desired version

**→ That's why version_comments are so important!**

---

### Tip 2: @Mentions for Notifications

**In Comments:**
```markdown
@jane.doe Can you review the Success Metrics section?
@john.smith Engineering feasibility check needed for Phase 2.
```

**Impact:**
- Email Notification to mentioned person
- Increases Visibility
- Faster Feedback Loop

---

### Tip 3: Confluence Macros for Rich Content

**Table of Contents:**
```html
<ac:structured-macro ac:name="toc" />
```

**Status Badge:**
```html
<ac:structured-macro ac:name="status">
  <ac:parameter ac:name="title">Draft</ac:parameter>
  <ac:parameter ac:name="colour">Yellow</ac:parameter>
</ac:structured-macro>
```

**Jira Issue Macro:**
```html
<ac:structured-macro ac:name="jira">
  <ac:parameter ac:name="key">PROD-123</ac:parameter>
</ac:structured-macro>
```

**→ Ask me if you need specific macros!**

---

### Tip 4: Search Uses CQL (Confluence Query Language)

**Advanced Search Examples:**

**Simple Text Search:**
```
query: "Multi-Video Upload PRD"
```

**CQL Search:**
```
query: 'space="PROD" AND label="prd" AND label="q2-2025"'
```

**Common CQL Patterns:**
- `title ~ "Upload"` → Title contains "Upload"
- `label = "prd"` → Has label "prd"
- `space = "PROD"` → In Space PROD
- `created >= "2025-01-01"` → Created after date
- `type = "page"` → Only Pages (not Blog Posts)

**→ CQL is powerful for complex queries!**

---

### Tip 5: Markdown is Automatically Converted

**You write:**
```markdown
# Heading
**Bold** and *italic*
- Bullet points
[Links](https://example.com)
```

**MCP Tool automatically converts to:**
```html
<h1>Heading</h1>
<p><strong>Bold</strong> and <em>italic</em></p>
<ul><li>Bullet points</li></ul>
<p><a href="https://example.com">Links</a></p>
```

**→ Just write Markdown, the tool handles the rest!**

---

## 📋 Confluence PRD Checklist

**Before publishing:**

- [ ] **Title:** Clear & Descriptive (Feature Name - PRD)
- [ ] **Space:** Correctly chosen (e.g., PROD, DEV)
- [ ] **Parent Page:** Set (if part of larger initiative)
- [ ] **Content:** Complete & formatted
- [ ] **Labels:** At minimum `prd`, `status-[x]`, `q[x]-202[x]`
- [ ] **Epic Link:** Included in PRD (Jira Epic URL)
- [ ] **Jira Epic:** Created & linked back to PRD
- [ ] **Version Comment:** Describes changes (on updates)
- [ ] **Status Badge:** Draft / In Review / Approved (optional)
- [ ] **Stakeholders:** Notified (via @Mentions or Share)
- [ ] **Page ID:** Saved for future updates

---

## 🔄 Complete PRD Creation Flow (Summary)

**Step-by-Step:**

1. **Prepare Markdown Content** (PRD draft)
2. **→ confluence_create_page** (space_key, title, content)
3. **→ Save Page ID** from response
4. **→ confluence_add_label** (multiple calls for all labels)
5. **→ jira_create_issue** (Epic with PRD Link) [optional]
6. **→ confluence_update_page** (add Epic Link to PRD)
7. **→ Output URL & Page ID** to PM
8. **→ Notify Stakeholders** (share URL or @mentions)

**That's it! PRD is live, linked, labeled & ready. 🚀**

---

**You're now ready to manage PRDs in Confluence like a pro!**

**Key Takeaways:**
- ✅ MCP Tools are native
- ✅ Markdown is automatically converted
- ✅ Always save Page ID
- ✅ Version Comments are mandatory
- ✅ Labels for discoverability
- ✅ Two-Way Linking (Confluence ↔ Jira)

---

*Confluence Workflows for Cursor AI PM Operating System*
*Beyond 7, 2025*
