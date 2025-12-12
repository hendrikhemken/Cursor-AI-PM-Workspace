# Installation Guide - Product Toolkit

**Get started in 5 minutes!**

Created by the **Product Brothers** - [Hendrik Hemken](https://linkedin.com/in/hendrikhemken) & [Sören von Sebelin](https://linkedin.com/in/soeren-von-sebelin)

---

## 🎯 What You'll Get

After installation, you'll have:
- ✅ OKR creation & weekly check-ins (Wodtke + Klau best practices)
- ✅ PRD writing assistance (Confluence integration)
- ✅ User Story breakdown (Jira integration)
- ✅ Interview guides & analysis
- ✅ LinkedIn content creation
- ✅ Your personal PM assistant that knows YOUR context

---

## 📋 Prerequisites

**Required:**
- [Claude Code](https://docs.claude.com/en/docs/claude-code) installed
- macOS, Linux, or Windows with WSL

**Optional (but recommended):**
- Git (for easy updates)
- MCP Servers configured (Confluence, Jira, Figma)

---

## 🚀 Installation Options

Choose the option that works best for you:

### **Option A: Git Clone** (Recommended for Developers)

**Pros:** Easy updates via `git pull`, full version control
**Cons:** Requires Git knowledge

```bash
# 1. Clone the repository
git clone https://github.com/hendrikhemken/product-ai-toolkit.git

# 2. Navigate into the directory
cd product-ai-toolkit

# 3. Open in Claude Code
claude
```

**Done! Skip to [First-Time Setup](#-first-time-setup)**

---

### **Option B: Download ZIP** (For Non-Technical Users)

**Pros:** No Git needed, simple download
**Cons:** Manual updates (download new ZIP when updates are released)

**Steps:**

1. **Download the latest release:**
   - Go to [GitHub Releases](https://github.com/hendrikhemken/product-ai-toolkit/releases/latest)
   - Click **"Download ZIP"** or **"Source code (zip)"**

2. **Extract the ZIP file:**
   - macOS: Double-click the ZIP file
   - Windows: Right-click → Extract All
   - Linux: `unzip product-ai-toolkit.zip`

3. **Move to a permanent location:**
   ```bash
   # Example (adjust to your preference):
   mv product-ai-toolkit ~/Documents/Product-Toolkit
   cd ~/Documents/Product-Toolkit
   ```

4. **Open in Claude Code:**
   ```bash
   claude
   ```

   **First session:** Claude auto-detects you're new and guides you through context setup (5 min).

   **Alternative (Manual):** Copy `user_context/COMPANY_CONTEXT.template.md` to `user_context/COMPANY_CONTEXT.md` and edit manually.

**Done! Continue to [First-Time Setup](#-first-time-setup)**

---

## 🎬 First-Time Setup

When you open the Product Toolkit for the **first time**, Claude will greet you:

```
Hey! 👋 Welcome to the Product Toolkit!

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
- Context is saved to `user_context/COMPANY_CONTEXT.md` (gitignored)
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

Claude: [Displays your COMPANY_CONTEXT.md]
```

**All working? 🎉 You're ready to go!**

---

## 🔌 Optional: MCP Server Setup

For **full functionality** (Confluence PRDs, Jira tickets, Figma imports), set up MCP servers:

### **Confluence & Jira MCP**

```bash
# Install mcp_docker server
# Full guide: https://github.com/QuantGeekDev/mcp-atlassian

# Add to your Claude Code MCP config:
# ~/.config/claude-code/mcp.json (macOS/Linux)
# %APPDATA%\claude-code\mcp.json (Windows)
```

**What you get:**
- ✅ Create PRDs directly in Confluence
- ✅ Create Jira tickets from User Stories
- ✅ Link PRDs ↔ Epics bidirectionally
- ✅ Search & read existing pages

**Need help?** [Connect with us on LinkedIn](https://linkedin.com/in/hendrikhemken) - we offer setup workshops!

---

## 🔄 Updating the Toolkit

### **If you used Git Clone (Option A):**

```bash
# Navigate to your toolkit directory
cd ~/path/to/product-ai-toolkit

# Pull latest changes
git pull origin main

# Restart Claude Code
```

**Your COMPANY_CONTEXT.md is safe!** (It's gitignored and won't be overwritten)

---

### **If you used ZIP Download (Option B):**

1. Download the [latest release](https://github.com/hendrikhemken/product-ai-toolkit/releases/latest)
2. Extract the new ZIP
3. **IMPORTANT:** Copy your `user_context/COMPANY_CONTEXT.md` from the old folder to the new one
4. Delete the old folder, use the new one

**Pro Tip:** Consider switching to Git Clone for easier updates!

---

## 🆘 Troubleshooting

### **"Claude doesn't recognize the toolkit"**

**Solution:**
- Make sure you opened Claude Code **in the toolkit directory**
- Run `pwd` (macOS/Linux) or `cd` (Windows) to verify location
- Should show: `/path/to/product-ai-toolkit`

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
- Or edit `user_context/COMPANY_CONTEXT.md` directly

---

### **"MCP servers not working"**

**Solution:**
- Verify MCP config: `~/.config/claude-code/mcp.json`
- Restart Claude Code after adding MCP servers
- Check MCP server logs for errors
- See our [MCP Setup Guide](./best-practices/FIGMA_MCP.md) for details

---

### **"Git permission denied"**

**Solution:**
```bash
# If using HTTPS (recommended):
git remote set-url origin https://github.com/hendrikhemken/product-ai-toolkit.git

# If using SSH (requires SSH key setup):
git remote set-url origin git@github.com:hendrikhemken/product-ai-toolkit.git
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

- **Issues:** [GitHub Issues](https://github.com/hendrikhemken/product-ai-toolkit/issues)
- **Discussions:** [GitHub Discussions](https://github.com/hendrikhemken/product-ai-toolkit/discussions)
- **LinkedIn:** [Hendrik](https://linkedin.com/in/hendrikhemken) | [Sören](https://linkedin.com/in/soeren-von-sebelin)

**Want personalized setup?**
- Claude Code workshops for PM teams
- Custom skill development
- MCP server configuration & debugging

👉 Reach out on LinkedIn!

---

## 🎉 Welcome to the Product Toolkit!

**You're now part of the PM community building better tools together.**

*Created by the Product Brothers - Because PMs deserve better tools.*

**Now go create some amazing OKRs! 🚀**
