# Agent Roster

Defines the agents in the Nanovest Agentic System — their roles, responsibilities,
inputs, outputs, and how they interact.

---

## Design Principles

- **Single responsibility.** Each agent does one thing well.
- **Composable.** Agents can call or hand off to other agents.
- **Auditable.** Every agent decision is logged with reasoning.
- **Explainable.** Outputs should be understandable by non-technical stakeholders.

---

## Planned Agents

### 1. PM Agent — `pm-agent`
**Status:** Planned
**Files:** `agents/pm-agent/system-prompt.md`, `tools.md`, `test.md`

**Responsibility:** Assists Product Managers with specification and planning work.

**Can do:**
- Draft PRDs from a brief
- Write user stories and acceptance criteria
- Break a feature into Jira tickets
- Summarize user research or competitor analysis
- Generate release notes

**Inputs:** Feature brief, user research, meeting notes, existing docs
**Outputs:** PRD, tickets, release notes, summaries

**Tools:** File read/write, Google Drive (optional API), GitHub (read)

---

### 2. Eng Agent — `eng-agent`
**Status:** Planned
**Files:** `agents/eng-agent/system-prompt.md`, `tools.md`, `test.md`

**Responsibility:** Assists engineers with development-adjacent tasks.

**Can do:**
- Review code against a checklist
- Generate boilerplate from a spec
- Write/update technical documentation
- Summarize a PR diff in plain language
- Answer architecture questions from existing docs

**Inputs:** Code, PRs, specs, architecture docs
**Outputs:** Review comments, docs, summaries, boilerplate

**Tools:** File read/write, GitHub (read/write local clone)

---

### 3. Ops Agent — `ops-agent`
**Status:** Future

**Responsibility:** Handles recurring operational tasks across teams.

**Can do:**
- Route requests to the right team
- Generate weekly status reports from Jira/Slack
- Answer internal FAQs using company knowledge base
- Escalation detection (flagging blockers in standups)

**Inputs:** Slack messages, Jira boards, knowledge base
**Outputs:** Reports, routed tickets, FAQ answers

**Tools:** Slack, Jira, Confluence, email

---

### 4. Orchestrator — `orchestrator`
**Status:** Future

**Responsibility:** Routes incoming requests to the right agent, coordinates multi-agent workflows.

**Pattern:**
1. Receive request (Slack command, web form, API call)
2. Classify: which team / which agent handles this?
3. Dispatch to appropriate agent
4. Aggregate output if multi-agent
5. Return to requester

---

## Agent Interaction Map

```
User / Slack / Web
       │
  Orchestrator
   ┌───┴───┐
PM Agent  Eng Agent  (Ops Agent — future)
```

---

## Adding a New Agent

1. Copy the agent template above
2. Fill in: responsibility, inputs, outputs, tools
3. Create `agents/<name>/system-prompt.md`
4. Add a test case in `agents/<name>/test.md`
5. Update this file
