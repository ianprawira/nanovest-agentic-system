# Onboarding: Nanovest Agentic System

Welcome. This guide sets up your personal Claude Code environment so you can use the
Nanovest Agentic System to draft PRDs, create tickets, summarize research, and more.

**Estimated time:** 30–45 minutes
**Prerequisites:** A laptop, a Nanovest Google Workspace account, and GitHub access.

---

## Step 1 — Install Claude Code

1. Go to [claude.ai/code](https://claude.ai/code) and install Claude Code
2. Sign in with your Anthropic account (get credentials from your lead if you don't have one)
3. Verify it works: open a terminal and type `claude --version`

---

## Step 2 — Create Your Local Nanovest Folder

This is your private workspace. Nothing here is shared automatically.

```
mkdir -p ~/Documents/Nanovest/drafts/prds
mkdir -p ~/Documents/Nanovest/drafts/research
mkdir -p ~/Documents/Nanovest/drafts/meeting-notes
mkdir -p ~/Documents/Nanovest/context
```

Then create your current sprint file:

```
touch ~/Documents/Nanovest/context/active-sprint.md
```

Open `active-sprint.md` and write a few lines about what you're working on this week —
tickets, features, priorities. Claude will read this when you ask about "this sprint."

**Local draft naming convention:** `YYYY-MM-DD-feature-name-type.md`
Example: `2026-03-15-stock-fractional-shares-prd.md`

---

## Step 3 — Clone the System Repo

```
git clone https://github.com/nanovest/NanovestAgenticSystem ~/Documents/Nanovest/system-repo
```

This gives you local access to all agent definitions, templates, and skills.
Pull regularly to stay up to date: `git pull` inside `system-repo/`.

---

## Step 4 — Set Up Your Personal CLAUDE.md

This file is your personal Claude configuration. It tells Claude who you are, where
your files live, and how you want it to behave. **It stays on your machine — never
commit it to GitHub.**

1. Copy the template:
   ```
   cp ~/Documents/Nanovest/system-repo/config/pm-claude-template.md ~/Documents/Nanovest/CLAUDE.md
   ```
2. Open `~/Documents/Nanovest/CLAUDE.md` and fill in every `[PLACEHOLDER]` field

---

## Step 5 — Configure Claude Code to See Your Files

Claude Code needs to know which directories to read from. Open (or create)
`~/.claude/settings.json` and add your Nanovest folders:

```json
{
  "additionalDirectories": [
    "~/Documents/Nanovest",
    "~/Documents/Nanovest/system-repo"
  ]
}
```

This lets Claude read your drafts, your personal CLAUDE.md, and all system templates
without you having to paste file contents manually.

---

## Step 6 — Verify Your Setup

Open a terminal in your Nanovest folder and start Claude Code:

```
cd ~/Documents/Nanovest
claude
```

Then say:

> "Read my CLAUDE.md and my active-sprint.md. Tell me what you know about my setup
> and what I'm working on."

Claude should correctly read both files and summarize your config. If it can't find them,
check that your `additionalDirectories` in Step 5 are correct.

---

## Step 7 — Test a Core Workflow

Say:

> "Help me draft a PRD brief for [any feature you have in mind]."

Claude should:
- Use the PRD template from `system-repo/prompts/prd-template.md`
- Ask you clarifying questions (goal, user, success metric)
- Save the draft to `drafts/prds/` with the correct naming format

If this works, your setup is complete.

---

## Step 8 (Optional) — Set Up Google Drive API

For seamless Drive read/write without copy-pasting, follow the guide at
`system-repo/config/drive-setup.md`. This takes ~20 additional minutes and requires
a Nanovest Google Cloud project (ask your lead for access).

**If you skip this step:** copy-paste works for all workflows. Just paste Drive content
into your Claude conversation. Everything else functions identically.

---

## Step 9 — Read the Key Docs

Before you start working, skim these:

| Doc | What it covers |
|-----|----------------|
| `AGENTS.md` | What agents exist and what they can do |
| `SKILLS.md` | Reusable patterns: PRDs, tickets, summaries |
| `PROMOTION.md` | How to move drafts from local → Drive → shared → GitHub |

---

## Quick Reference: Trigger Phrases

| What you want | What to say |
|---------------|------------|
| Save locally | Claude saves automatically to `drafts/` |
| Back up to your Drive | "Save this to my Drive" |
| Share with the team | "Share this with the team" |
| Update a system template | "Update the template" or "Commit this" |
| Read your sprint context | "What am I working on this sprint?" |

---

## Getting Help

- Read `SKILLS.md` for available patterns
- Read `PROMOTION.md` for the promotion workflow
- Ask your Product Lead if something isn't working
- File issues at the GitHub repo for system-level problems
