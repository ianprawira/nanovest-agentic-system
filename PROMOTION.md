# Promotion Workflow

How to move your work between layers — from private draft to team-visible to published.

Claude reads freely from any layer. It writes only when you explicitly say so.

---

## The Four Layers

```
[ Local Draft ]  →  [ Personal Drive ]  →  [ Shared Drive ]  →  [ GitHub ]
   (private)         (your backup)          (team-visible)     (eng-visible)
```

You control every transition. Nothing moves automatically.

---

## Layer 1: Local Draft

**What it is:** Files on your machine in `~/Documents/Nanovest/drafts/`

**Naming convention:** `YYYY-MM-DD-feature-name-type.md`
Example: `2026-03-15-stock-fractional-shares-prd.md`
- All lowercase
- Hyphens instead of spaces
- No special characters

**Claude's behavior:** Reads and writes here freely. This is your scratchpad.

---

## Layer 2: Personal Drive

**What it is:** Your private Google Drive folder — `[Your Name] Nanovest Work/`

**Naming convention:** `YYYY-MM-DD — Feature Name — Doc Type — Status`
Example: `2026-03-15 — Stock Fractional Shares — PRD — Draft`

Status values: `Draft`, `Review`, `Approved`, `Published`

**How to trigger:** Say "save this to my Drive."

**What Claude does:**
1. Converts filename to Drive convention
2. Shows you the filename and target folder: `[Your Name] Nanovest Work/Drafts/PRDs/`
3. Waits for your confirmation
4. Uploads via Drive API (if configured) or outputs formatted content with copy-paste instructions

Nothing else on the team can see this. It is your personal backup.

---

## Layer 3: Shared Drive

**What it is:** The team's shared Google Drive — `Nanovest Product Team/`

**Folder map:**
```
Products/
├── Stocks/        → PRDs/, Research/, Release Notes/
├── Crypto/        → PRDs/, Research/, Release Notes/
├── Reksa Dana/    → PRDs/, Research/, Release Notes/
└── Cross-Product/ → PRDs/, Research/, Release Notes/
Strategy/          → OKRs/, Roadmaps/, Competitive Analysis/
Operations/        → Meeting Notes/ (by quarter), Weekly Updates/, Decisions Log/
```

**Naming convention:** Same as Personal Drive, but status updates to `Review` on promotion.

**How to trigger:** Say "share this with the team."

**What Claude does:**
1. **Warns you:** "This will become visible to all ~16 PMs and Product Leads. Continue?"
2. Updates status in filename from `Draft` → `Review`
3. Shows you the new filename and target path
4. Waits for your confirmation
5. Writes to Shared Drive (via API or with copy-paste instructions)
6. Optionally drafts a Slack message to announce the doc

**Use this when:** The doc is ready for feedback, not just for backup.

---

## Layer 4: GitHub

**What it is:** The `NanovestAgenticSystem` repo. Engineers can see this.

**What belongs here:** Agent definitions, prompt templates, reusable skills, system docs.
**What does NOT belong here:** PRDs, meeting notes, research, personal drafts — those stay in Drive.

**How to trigger:** Say "update the template" or "commit this to the repo."

**What Claude does:**
1. Shows you a diff of what would change vs. the current file
2. Waits for your confirmation
3. Writes the file to your local clone of the repo
4. Provides a commit message for you to review
5. **You run the git commands** — Claude does not push automatically:
   ```
   git add [file]
   git commit -m "[message Claude provided]"
   git push
   ```

**Use this when:** A pattern or template has been refined through real use and should become
the new standard for the whole team.

---

## Promotion Rules Claude Always Follows

These are set in your personal `CLAUDE.md`. They apply in every session:

- Never promote without explicit instruction
- Always confirm filename + target folder before writing to Drive or GitHub
- Always show what will be written before writing it
- Warn about visibility when promoting to Shared Drive
- Warn about engineer visibility when promoting to GitHub
- Never push to GitHub — the PM always reviews and runs git push manually

---

## Quick Reference

| I want to... | I say... |
|---|---|
| Save a draft locally | Claude saves to `drafts/` automatically |
| Back up to my private Drive | "Save this to my Drive" |
| Share with the team | "Share this with the team" |
| Make a template official | "Update the template" or "Commit this" |
| Undo a local draft change | Ask Claude to revert, or use file history |

---

## What If I Made a Mistake?

- **Wrong file on local:** Ask Claude to revert the change, or delete/restore manually
- **Uploaded to wrong Drive folder:** Move it manually in Google Drive; tell Claude the new location
- **Pushed wrong thing to GitHub:** Use `git revert` or ask your Product Lead — do not force-push
