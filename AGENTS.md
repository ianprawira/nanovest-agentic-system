# Claude Roles

Describes how Claude is configured for each role at Nanovest.
Each role has a dedicated system prompt in `agents/<role>/system-prompt.md`
that shapes Claude's defaults, tone, and task focus for that user type.

---

## PM Role — `agents/pm-agent/`

For Product Managers working on specs, tickets, research, and planning.

**What Claude helps with:**
- Drafting PRDs from a brief or meeting notes
- Writing user stories and acceptance criteria
- Breaking a feature into Jira tickets
- Summarizing user research or competitor analysis
- Generating release notes

**Key files:**
- `agents/pm-agent/system-prompt.md` — Claude instructions for PM sessions
- `prompts/prd-template.md`, `ticket-template.md`, etc. — output templates

---

## Eng Role — `agents/eng-agent/`

For Engineers working on implementation, review, and documentation.

**What Claude helps with:**
- Reviewing code against a checklist
- Summarizing PR diffs in plain language
- Drafting or updating technical documentation
- Answering architecture questions from existing docs
- Generating boilerplate from a spec

**Key files:**
- `agents/eng-agent/system-prompt.md` — Claude instructions for Eng sessions

---

## Adding a New Role

1. Create `agents/<role>/system-prompt.md`
2. Add relevant output templates to `prompts/`
3. Update this file
