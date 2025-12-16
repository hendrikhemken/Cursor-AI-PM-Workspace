# Cursor AI PM Operating System

**Build Your Personal AI-Powered PM Workspace**

*Live Workshop System for the [Live Conference](https://liveconference.co/) by [Brick Institute](https://bfrominstitute.com/)*

Created by **[Beyond 7](https://beyond7.ai)** - [Hendrik Hemken](https://linkedin.com/in/hendrikhemken) & [Sören von Sebelin](https://linkedin.com/in/soeren-von-sebelin)

---

A hands-on workshop system that helps Product Managers build their own AI operating system in Cursor:
- Create OKRs (with best practices from Wodtke + Klau)
- Write PRDs in Confluence with Jira Epic linking
- Break down EPICs into User Stories
- Weekly OKR check-ins (Monday commitments, Friday celebrations)
- Summarize Jira comment threads

**Target Audience:** Product Managers at Startups, Scale-ups & Corporates

---

## 🚀 Quick Start

**1. Prerequisites**

- [Cursor](https://cursor.com) installed
- MCP Servers configured (Confluence, Jira - optional but recommended)

**2. Setup**

```bash
# Clone this repo
git clone https://github.com/hendrikhemken/Cursor-AI-PM-Workspace.git
cd Cursor-AI-PM-Workspace

# Open in Cursor
cursor .

# On first session, Claude will auto-detect and guide you
# through context setup (5 min interactive questionnaire)
```

**Alternative (Skip Setup):**
If you prefer to dive right in, just open the folder in Cursor - you can set up context later by saying "Setup my context".

**3. Start Using**

The system activates automatically when you mention relevant keywords:

- **OKRs:** "Let's create my Q4 OKRs" → `okr-expert` skill activates
- **User Stories:** "Break down this EPIC" → `user-stories` skill activates
- **PRDs:** "Create a PRD for Feature X" → `prd-creator` skill activates

---

## ✨ Features

### 🎯 OKR Creation & Management
- **Adaptive approach** - Wodtke (Startup) vs Klau (Corporate) based on your context
- **Weekly cadence** - Monday Commitments, Friday Celebrations
- **Quality enforcement** - Outcomes > Outputs, no activity-based KRs
- **Red team review** - Catches gameable metrics before they become problems

### 📝 User Stories & Epic Breakdown
- **PRD → Stories** - Extract User Stories from Product Requirements
- **INVEST compliance** - Enforces Independent, Negotiable, Valuable, Estimable, Small, Testable
- **Jira integration** - Auto-create stories with links & dependencies
- **Platform-aware** - Separate stories for iOS/Android/Backend when needed

### 📄 PRD Creation (Confluence)
- **Modern, lean PRDs** - Feature-level instead of 150-page monsters
- **AI-assisted drafting** - 80% draft, 20% human refinement
- **Direct publishing** - Creates pages in Confluence via MCP
- **Jira Epic linking** - Bidirectional PRD ↔ Epic links

### 🔧 Productivity Tools
- **Context setup** - Interactive company/product/team context collection
- **Jira comment digest** - Summarize ticket discussions & ongoing threads
- **Skill creator** - Meta-skill for building custom Cursor skills

---

## 🛠️ MCP Server Setup (Optional but Recommended)

**For full functionality, configure these MCP servers:**

### Confluence & Jira MCP

The system integrates with Confluence (PRDs) and Jira (User Stories) via MCP servers.

**Setup:**
1. Follow [MCP Atlassian installation guide](https://github.com/QuantGeekDev/mcp-atlassian)
2. Configure with your Atlassian credentials
3. Restart Cursor

**What you get:**
- ✅ Create PRDs directly in Confluence
- ✅ Create Jira tickets from User Stories
- ✅ Link PRDs ↔ Epics bidirectionally
- ✅ Search & read existing Confluence pages

**Need help with MCP setup?** → [Book a session](#-need-help)

---

## 📚 Credits & Inspiration

This system teaches best practices from industry leaders:

### OKR Methodology
- **Christina Wodtke** - "Radical Focus" (Weekly cadence, 5/10 confidence, Monday/Friday rhythm)
  - 📖 [Buy the book on Amazon](https://www.amazon.com/Radical-Focus-SECOND-Achieving-Objectives/dp/1955469059)
  - 🌐 [eleganthack.com](https://eleganthack.com)
- **Rick Klau** - Google's OKR approach (Quarterly grading, transparency, 0.6-0.7 = success)
  - 🎥 [Watch his legendary Google Ventures talk](https://www.youtube.com/watch?v=mJB83EZtAjc)
- **Marty Cagan** - "INSPIRED" (Product Teams critique, OKR prerequisites, Feature vs Product Teams)
  - 📖 [Buy the book](https://www.svpg.com/books/inspired-how-to-create-tech-products-customers-love-2nd-edition/)
  - 🌐 [svpg.com](https://svpg.com)

### User Stories & Agile
- **Mike Cohn** - "User Stories Applied" (INVEST principles)
  - 📖 [Buy the book](https://www.mountaingoatsoftware.com/books/user-stories-applied)

**Important:** We teach these methodologies in our own words with full attribution. All content is original.

**Want to learn these frameworks properly? Buy their books - they're amazing!**

*This system does NOT replace their work - it helps you APPLY it.*

---

## 🎓 Need Help?

This system is **free & open source** - use it however you want!

**Want personalized setup for your team?**
- Cursor workshops for PMs
- MCP Server configuration & debugging
- Custom skill development for your workflows
- Team-specific adaptation (Startup vs Corporate)
- OKR coaching & implementation

👉 **[Connect on LinkedIn](https://linkedin.com/in/hendrikhemken)**

---

## 📂 Repository Structure

```
Cursor-AI-PM-Workspace/
├── README.md                    # You are here
├── CLAUDE.md                    # Main instructions for Cursor (Claude reads this)
├── INSTALLATION.md              # Detailed setup guide
├── LICENSE                      # MIT License
├── .gitignore                   # Protects your personal data
├── .claude/
│   └── skills/                  # Agent skills (auto-activate on keywords)
│       ├── okr-expert/          # OKR creation & review (Wodtke + Klau)
│       ├── okr-monday/          # Monday commitment check-ins
│       ├── okr-friday/          # Friday celebration check-ins
│       ├── prd-creator/         # PRD creation in Confluence + Jira Epic linking
│       ├── user-stories/        # Epic breakdown & User Story creation
│       ├── jira-comment-digest/ # Jira comment thread summarization
│       ├── user-context/        # Interactive context setup
│       ├── skill-creator/       # Create new Cursor skills
│       └── hook-creator/        # Create Cursor hooks
├── examples/                    # Best practice examples
│   └── okrs/                    # Example OKRs (anonymized)
├── best-practices/              # Deep-dive guides & workflows
│   └── FIGMA_MCP.md             # Figma MCP Server workflow
└── outputs/                     # Your generated deliverables (gitignored)
    ├── okrs/                    # Your OKR files
    ├── prd/                     # Your PRD drafts
    └── meeting-notes/           # Meeting notes & summaries
```

---

## 📖 How It Works

**The AI PM Operating System is your Daily PM Assistant:**

1. **Context-Aware:** Adapts to your company type (Startup vs Corporate), customer type (B2C vs B2B), team size
2. **Skill-Based:** Skills activate automatically when you mention keywords (no manual invocation)
3. **Opinionated:** Enforces best practices (INVEST, Outcomes > Outputs, no cargo cult OKRs)
4. **Proactive:** Tracks progress, reminds you of deadlines, identifies blockers
5. **Integrated:** Works directly with Confluence, Jira, Figma via MCP servers

**Example Session:**

```
You: "Let's create my Q4 2025 OKRs"

Claude: "Cool! I see you're a Solo Consultant (from your User Context).
         I'll use Wodtke's Weekly Rhythm approach.

         What's your North Star for Q4?"

You: "Sign 3 retainer clients at €3K/month MRR"

Claude: "Nice! Let me draft an Objective + Key Results...

         [drafts OKR]

         Red Team Check: This KR is gameable - could you sign
         low-quality clients. Should we add a quality gate (NPS 50+)?"

You: "Good catch! Yes, add that."

Claude: "✅ Updated. Confidence level 5/10?
         I'll create the file at /outputs/okrs/Q4-2025-OKRs.md
         and set up your weekly Monday/Friday check-ins."
```

---

## 🤝 Contributing

Found a bug? Have a feature request? Want to add a new skill?

- **Issues:** [github.com/hendrikhemken/Cursor-AI-PM-Workspace/issues](https://github.com/hendrikhemken/Cursor-AI-PM-Workspace/issues)
- **Discussions:** Share your workflows, ask questions, help others
- **Pull Requests:** Welcome! Please follow the existing structure

---

## 📜 License

MIT License - Copyright (c) 2025 Hendrik Hemken & Sören von Sebelin

See [LICENSE](LICENSE) for details.

**You are free to:**
- ✅ Use this system commercially
- ✅ Modify and distribute
- ✅ Use privately or for your team
- ✅ Fork and build on top of it

**Attribution appreciated but not required.**

---

## 🙏 Acknowledgments

Built with:
- [Cursor](https://cursor.com) - AI-powered code editor
- [MCP Servers](https://modelcontextprotocol.io/) for Confluence, Jira, Figma integration
- Wisdom from Wodtke, Klau, Cagan, Cohn & the PM community

**Special Thanks:**
- Christina Wodtke for making OKRs actually work (Weekly rhythm FTW!)
- Rick Klau for demystifying Google's OKR process
- Marty Cagan for the Product Teams critique (saved us from cargo cult OKRs)
- [Brick Institute](https://bfrominstitute.com/) & [Live Conference](https://liveconference.co/) for the workshop opportunity
- All the PMs who gave feedback during development

---

## 🎪 Live Workshop System

**This repository was created for the Live Conference by Brick Institute.**

The Live Workshop System is designed to be hands-on and practical - you'll leave with a working AI PM Operating System tailored to YOUR context.

**Workshop Goals:**
- ✅ Set up your personal AI PM workspace in Cursor
- ✅ Configure your company/product context
- ✅ Create your first OKRs with AI assistance
- ✅ Understand how to extend the system with custom skills

---

## 👨‍💻 Created by Beyond 7

**Hendrik Hemken** & **Sören von Sebelin** - Two Product Managers who got tired of context-switching between 47 different tools.

This system is our answer: **One AI assistant that actually understands PM work.**

*Connect with us:*
- 👉 [Hendrik on LinkedIn](https://linkedin.com/in/hendrikhemken)
- 👉 [Sören on LinkedIn](https://linkedin.com/in/soeren-von-sebelin)
- 🌐 [Beyond 7](https://beyond7.ai)

---

**Cursor AI PM Operating System - Because PMs deserve better tools.**

*Live Workshop System for the Live Conference by Brick Institute*
