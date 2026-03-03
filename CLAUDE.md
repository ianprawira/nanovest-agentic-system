# Nanovest Agentic System — Claude Code Context

## What This Is
An internal agentic system for Nanovest (multi-asset investment app, Indonesia).
Primary users: Product and Engineering teams. Scope may expand company-wide.

Goal: Help teams work more effectively through AI agents — writing specs, creating tickets,
reviewing code, generating docs, synthesizing research, and automating operational workflows.

## Tech Stack
- **Backend:** Java (primary)
- **Mobile:** React Native (current), migrating to Native Android
- **AI agents:** Claude API / Anthropic SDK
- **Domain:** Fintech, investment, Indonesian market

## Workflow Style
**Collaborative.** Claude proposes, Brian approves, then Claude executes.

- Before making significant changes, present the plan and wait for approval
- Use `EnterPlanMode` for any multi-step or architectural task
- Ask clarifying questions early rather than making assumptions
- One task at a time — complete and confirm before moving on

## Conventions

### General
- Keep solutions simple. Don't over-engineer.
- Don't add features, comments, or refactors beyond what was asked
- Prefer editing existing files over creating new ones
- Delete unused code — don't leave dead code or backwards-compat shims

### File Organization
- Team context and active project work live in `teams/`
- All system internals live in `system/`:
  - `system/agents/` — agent definitions (`system-prompt.md`, `tools.md`, `test.md`)
  - `system/prompts/` — shared templates (PRDs, tickets, release notes, summaries)
  - `system/skills/` — reusable patterns and workflows
  - `system/docs/` — architecture and system documentation
  - `system/config/` — configuration templates and onboarding

### Knowledge Flow
Work moves deliberately between four layers — never automatically:
```
[ Local Draft ]  →  [ Personal Drive ]  →  [ Shared Drive ]  →  [ GitHub ]
   (private)         (personal backup)      (team-visible)     (eng-visible)
```
See `PROMOTION.md` for the full workflow and trigger phrases.

### Per-User Configuration
Each PM has a personal `CLAUDE.md` in `~/Documents/Nanovest/CLAUDE.md`.
It configures their local paths, Drive folder IDs, and domain context.
Template: `system/config/pm-claude-template.md`. **Never commit a personal CLAUDE.md to GitHub.**

### Promotion Rules (enforce in every session)
- Never write to Shared Drive without explicit "share this with the team"
- Never write to GitHub without explicit "update the template" or "commit this"
- Always confirm filename and target folder before writing anywhere
- Never run `git push` — the PM always reviews and pushes manually

### Agent Development
- Each agent should have a clear, single responsibility
- Agent inputs and outputs should be explicitly typed
- Prefer composing small agents over building one large orchestrator
- Log agent decisions for auditability

## Key Constraints
- All outputs touching financial data must be clearly marked as non-advice
- Respect Indonesian regulatory context (OJK) in any customer-facing content
- Do not hardcode credentials — use environment variables

## How to Add to This File
Update CLAUDE.md when:
- A new team or domain is added to scope
- A new tech component is introduced
- A significant architectural decision is made
