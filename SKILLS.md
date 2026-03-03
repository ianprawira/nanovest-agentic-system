# Skills & Reusable Patterns

Recipes and patterns Claude should follow when working in this system.
Add new skills here as they are developed and validated.

---

## Skill: Write a PRD

**When to use:** Product team needs a feature specification.

**Pattern:**
1. Clarify: goal, target user, success metric, constraints
2. Structure: Problem → Proposed Solution → User Stories → Acceptance Criteria → Out of Scope
3. Keep it actionable — engineering should be able to estimate from it
4. Flag regulatory or compliance implications (OJK, data privacy)

**Template location:** `prompts/prd-template.md`

---

## Skill: Create a Jira Ticket from a PRD

**When to use:** A PRD is approved and needs to be broken into dev tickets.

**Pattern:**
1. Read the PRD acceptance criteria
2. Group by: Frontend, Backend (Java), Mobile (Android/RN)
3. For each ticket: Summary, Description, Acceptance Criteria, Story Points estimate
4. Flag dependencies between tickets

**Template location:** `prompts/ticket-template.md`

---

## Skill: Write Release Notes

**When to use:** A release is ready for internal or public communication.

**Pattern:**
1. Summarize changes in plain language (not technical jargon)
2. Group: New Features → Improvements → Bug Fixes
3. If customer-facing: get product review before publishing
4. Indonesian context: consider dual-language if audience includes non-English speakers

**Template location:** `prompts/release-notes-template.md`

---

## Skill: Summarize a Meeting / Document

**When to use:** Long meeting transcript, Confluence page, or doc needs distillation.

**Pattern:**
1. Extract: Key decisions, Action items (owner + deadline), Open questions
2. Keep to 1 page max
3. Use bullet points, not prose

**Template location:** `prompts/meeting-summary-template.md`

---

## Skill: Agent Scaffolding

**When to use:** Building a new agent in the system.

**Pattern:**
1. Define: name, responsibility, inputs, outputs
2. Write the system prompt in `agents/<name>/system-prompt.md`
3. Define the tool list the agent can use
4. Write a test case with a sample input and expected output
5. Add the agent to AGENTS.md

---

## Skill: Code Review Checklist (Java Backend)

**When to use:** Reviewing Java backend PRs.

**Checklist:**
- [ ] Business logic matches ticket AC
- [ ] No hardcoded credentials or config
- [ ] Error handling covers edge cases
- [ ] Unit tests cover happy path + at least one failure case
- [ ] No breaking changes to existing API contracts
- [ ] Logging is meaningful (not noisy)

---

## Skill: Code Review Checklist (Android / React Native)

**When to use:** Reviewing mobile PRs.

**Checklist:**
- [ ] UI matches design (Figma)
- [ ] Works on both low-end and high-end devices (test matrix)
- [ ] No blocking main thread operations
- [ ] Navigation handled correctly (back stack, deep links)
- [ ] API error states handled and shown to user
- [ ] Analytics events fired correctly

---

## Skill: Promote a Draft

**When to use:** Moving work from local → personal Drive → shared Drive → GitHub.

**Pattern:** See `skills/promote-draft.md` for the full step-by-step workflow.

Quick reference:
- "Save this to my Drive" → personal Drive backup
- "Share this with the team" → Shared Drive (warn: team-visible)
- "Update the template" / "Commit this" → GitHub (warn: engineer-visible, PM pushes manually)

---

## Adding New Skills
When a workflow is repeated 2+ times, codify it here.
Format: Name → When to use → Pattern or steps → Template location (if applicable).
