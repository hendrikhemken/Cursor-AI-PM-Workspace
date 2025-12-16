# Best Practices Guides

This directory contains best practices guides for Cursor features and patterns used in the AI PM Operating System.

---

## Available Guides

### MCP Server Integration
- **FIGMA_MCP.md** - Figma MCP Server integration
  - Workflow patterns
  - Configuration examples
  - Integration best practices

---

## Quick Start

### For AI PM Operating System Skills

Your current implementation uses Agent Skills (in `.claude/skills/`):
- SKILL.md = Combined agent definition + system prompt
- Triggers on keyword patterns

**Key Templates Available in Skills:**
- OKR templates (`okr-expert/TEMPLATES.md`)
- PRD templates (`prd-creator/TEMPLATES.md`)
- User Story templates (`user-stories/TEMPLATES.md`)

---

## Key Insights

### Skill Architecture
- **Simple**: YAML front matter + Markdown format
- **Composable**: Skills can reference other skill files
- **Context-Aware**: Adapts based on user context in CLAUDE.md

### Component Breakdown
| Component | Purpose | Location |
|-----------|---------|----------|
| Skills | Specialized agents for PM tasks | `.claude/skills/` |
| Templates | Reusable formats for outputs | Inside skill folders |
| Best Practices | Deep-dive methodology guides | Inside skill folders |
| Examples | Real-world anonymized examples | `examples/` |

### Best Practices Summary
1. Single responsibility per skill
2. Detailed output specifications
3. Comprehensive documentation
4. Clear naming conventions (kebab-case)
5. Context injection from CLAUDE.md

---

## File Locations

```
/best-practices/
├── README.md (this file)
└── FIGMA_MCP.md (MCP integration guide)
```

---

## Next Steps for AI PM Operating System

### Current State
- Skills in `.claude/skills/` (9 skills)
- SKILL.md format (self-contained)
- Keyword-based triggers

### Available Skills

| Skill | Purpose |
|-------|---------|
| `okr-expert` | OKR creation with Wodtke + Klau best practices |
| `okr-monday` | Monday commitment check-ins |
| `okr-friday` | Friday celebration check-ins |
| `prd-creator` | PRD creation in Confluence |
| `user-stories` | Epic breakdown & User Story creation |
| `jira-comment-digest` | Summarize Jira ticket discussions |
| `user-context` | Interactive context setup |
| `skill-creator` | Create new custom skills |
| `hook-creator` | Create automation hooks |

---

## Tips

- Use skill templates for consistent outputs
- Follow existing patterns in skill files
- Document output formats thoroughly
- Test skills with different contexts

---

**Maintained for:** Cursor AI PM Operating System
**Updated:** 2025-12
**Status:** Production Ready

*Live Workshop System by Beyond 7*
