# Installation Guide - Cursor AI PM Operating System

**Get started in 5 minutes!**

*Live Workshop System for the [Live Conference](https://liveconference.co/) by [Brick Institute](https://bfrominstitute.com/)*

Created by **[Beyond 7](https://beyond7.ai)** - [Hendrik Hemken](https://linkedin.com/in/hendrikhemken) & [Sören von Sebelin](https://linkedin.com/in/soeren-von-sebelin)

---

## 🎯 What You'll Get

After installation, you'll have:
- ✅ OKR creation & weekly check-ins (Wodtke + Klau best practices)
- ✅ PRD writing assistance (Confluence integration)
- ✅ User Story breakdown (Jira integration)
- ✅ Your personal PM assistant that knows YOUR context

---

## 📋 Prerequisites

**Required:**
- [Cursor](https://cursor.com) installed
- macOS, Linux, or Windows

**Optional (but recommended):**
- Git (for easy updates)
- MCP Servers configured (Confluence, Jira, Figma)

---

## 🚀 Installation Options

Choose the option that works best for you:

### **Option A: Git Clone** (Recommended)

**Pros:** Easy updates via `git pull`, full version control
**Cons:** Requires Git knowledge

```bash
# 1. Clone the repository
git clone https://github.com/hendrikhemken/Cursor-AI-PM-Workspace.git

# 2. Navigate into the directory
cd Cursor-AI-PM-Workspace

# 3. Open in Cursor
cursor .
```

**Done! Skip to [First-Time Setup](#-first-time-setup)**

---

### **Option B: Download ZIP** (For Non-Technical Users)

**Pros:** No Git needed, simple download
**Cons:** Manual updates (download new ZIP when updates are released)

**Steps:**

1. **Download the latest release:**
   - Go to [GitHub Releases](https://github.com/hendrikhemken/Cursor-AI-PM-Workspace/releases/latest)
   - Click **"Download ZIP"** or **"Source code (zip)"**

2. **Extract the ZIP file:**
   - macOS: Double-click the ZIP file
   - Windows: Right-click → Extract All
   - Linux: `unzip Cursor-AI-PM-Workspace.zip`

3. **Move to a permanent location:**
   ```bash
   # Example (adjust to your preference):
   mv Cursor-AI-PM-Workspace ~/Documents/AI-PM-Workspace
   cd ~/Documents/AI-PM-Workspace
   ```

4. **Open in Cursor:**
   - Open Cursor
   - File → Open Folder → Select the extracted folder

   **First session:** Claude auto-detects you're new and guides you through context setup (5 min).

   **Alternative (Manual):** Edit the **User Context** section at the bottom of `CLAUDE.md` directly.

**Done! Continue to [First-Time Setup](#-first-time-setup)**

---

## 🎬 First-Time Setup

When you open the AI PM Operating System for the **first time**, Claude will greet you:

```
Hey! 👋 Welcome to the AI PM Operating System!

I'm your daily PM assistant — built by PMs for PMs.

Before we dive in:
I need your context! Takes 5 minutes and unlocks full support.

Want me to start the setup? 🚀
```

**Just say "Yes" or "Let's go!"**

---

## 📝 Context Setup (5 Minutes)

The `user-context` skill will guide you through an interactive setup:

**You'll be asked about:**
1. **Company Info** - Name, industry, company type (Startup/Scale-up/Corporate)
2. **Product Info** - What you're building, customer type (B2C/B2B)
3. **Team Info** - Team size, your role, decision-making style
4. **Strategic Context** - North Star Metric, current quarter focus
5. **Tech Stack** - Tools you use (Jira, Confluence, Figma, etc.)

**Why this matters:**
- Claude adapts OKR approach based on company size (Wodtke for Startups, Klau for Corporates)
- PRD templates adjust to B2B vs B2C
- User Stories consider your tech stack
- Everything is personalized to YOUR workflow

**Your data stays local!**
- Context is saved in the **User Context** section of `CLAUDE.md`
- Never shared, never uploaded
- Update anytime by editing the file or saying "Update my context"

---

## ✅ Verify Installation

After setup, test that everything works:

**1. Try creating OKRs:**
```
You: "Let's create my Q4 2025 OKRs"

Claude: "Cool! I see you're a [Your Company Type].
         I'll use [Wodtke/Klau] approach..."
```

**2. Try creating a PRD:**
```
You: "Help me write a PRD for user authentication"

Claude: "Great! What's the problem this feature solves?"
```

**3. Check your context:**
```
You: "Show me my company context"

Claude: [Displays your User Context from CLAUDE.md]
```

**All working? 🎉 You're ready to go!**

---

## 🔌 Optional: MCP Server Setup

For **full functionality** (Confluence PRDs, Jira tickets, Figma imports), set up MCP servers:

### **Confluence & Jira MCP**

```bash
# Install mcp_docker server
# Full guide: https://github.com/QuantGeekDev/mcp-atlassian

# Add to your Cursor MCP config:
# Settings → MCP Servers → Add Server
```

**What you get:**
- ✅ Create PRDs directly in Confluence
- ✅ Create Jira tickets from User Stories
- ✅ Link PRDs ↔ Epics bidirectionally
- ✅ Search & read existing pages

**Need help?** [Connect with us on LinkedIn](https://linkedin.com/in/hendrikhemken) - we offer setup workshops!

---

## 🔄 Updating the System

### **If you used Git Clone (Option A):**

```bash
# Navigate to your workspace directory
cd ~/path/to/Cursor-AI-PM-Workspace

# Pull latest changes
git pull origin main

# Restart Cursor
```

**Your User Context in CLAUDE.md is safe!** (Won't be overwritten by updates)

---

### **If you used ZIP Download (Option B):**

1. Download the [latest release](https://github.com/hendrikhemken/Cursor-AI-PM-Workspace/releases/latest)
2. Extract the new ZIP
3. **IMPORTANT:** Copy your **User Context** section from the old `CLAUDE.md` to the new one
4. Delete the old folder, use the new one

**Pro Tip:** Consider switching to Git Clone for easier updates!

---

## 🆘 Troubleshooting

### **"Cursor doesn't recognize the system"**

**Solution:**
- Make sure you opened Cursor **in the workspace directory**
- Check that the folder contains `CLAUDE.md` at the root level
- Try closing and reopening Cursor

---

### **"Skills don't activate automatically"**

**Solution:**
- Skills activate on keywords (e.g., "OKR", "PRD", "User Stories")
- Try explicit triggers: "Let's create OKRs" or "Help me write a PRD"
- Check that `.claude/skills/` folder exists with skill definitions

---

### **"Context setup didn't start"**

**Solution:**
- Manually trigger: Say "Setup my context" or "Getting started"
- Or edit the **User Context** section in `CLAUDE.md` directly

---

### **"MCP servers not working"**

**Solution:**
- Verify MCP config in Cursor Settings
- Restart Cursor after adding MCP servers
- Check MCP server logs for errors
- See our [MCP Setup Guide](./best-practices/FIGMA_MCP.md) for details

---

### **"Git permission denied"**

**Solution:**
```bash
# If using HTTPS (recommended):
git remote set-url origin https://github.com/hendrikhemken/Cursor-AI-PM-Workspace.git

# If using SSH (requires SSH key setup):
git remote set-url origin git@github.com:hendrikhemken/Cursor-AI-PM-Workspace.git
```

---

## 💡 Next Steps

**After installation:**

1. **Complete Context Setup** - Let Claude interview you (5 min)
2. **Create Your First OKRs** - Say "Let's create my Q4 OKRs"
3. **Explore Skills** - Try "What can you help me with?"
4. **Join the Community** - Star the repo, share feedback, contribute!

---

## 📚 Learn More

- **[README.md](./README.md)** - Overview & features
- **[CLAUDE.md](./CLAUDE.md)** - Full system instructions (how it all works)
- **[best-practices/](./best-practices/)** - Deep-dive guides
- **[examples/](./examples/)** - Real-world OKR examples

---

## 🤝 Need Help?

**Got stuck? We're here!**

- **Issues:** [GitHub Issues](https://github.com/hendrikhemken/Cursor-AI-PM-Workspace/issues)
- **Discussions:** [GitHub Discussions](https://github.com/hendrikhemken/Cursor-AI-PM-Workspace/discussions)
- **LinkedIn:** [Hendrik](https://linkedin.com/in/hendrikhemken) | [Sören](https://linkedin.com/in/soeren-von-sebelin)

**Want personalized setup?**
- Cursor workshops for PM teams
- Custom skill development
- MCP server configuration & debugging

👉 Reach out on LinkedIn!

---

## 🎪 Live Workshop System

**This guide is part of the Live Conference workshop by Brick Institute.**

During the workshop, we'll walk through this installation together. If you're reading this later, follow the steps above and reach out if you get stuck!

---

## 🎉 Welcome to the AI PM Operating System!

**You're now part of the PM community building better tools together.**

*Created by Beyond 7 - Because PMs deserve better tools.*

**Now go create some amazing OKRs! 🚀**
