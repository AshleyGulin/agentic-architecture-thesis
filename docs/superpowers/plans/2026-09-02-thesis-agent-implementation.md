# Thesis Agent Repository Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a private `AshleyGulin/agentic-architecture-thesis` GitHub repository that gives a long-running Thesis Agent durable research memory, evidence-aware workflows, and a small actionable task queue.

**Architecture:** GitHub Markdown is the source of truth for research context, while Issues hold only actionable work. `AGENTS.md` defines the agent contract; `state/current-state.md`, the question tree, and the evidence matrix provide a compact cold-start path. Repository creation occurs through the signed-in GitHub page because the installed GitHub connector does not expose repository creation; all later supported writes and read-back checks use the connector.

**Tech Stack:** GitHub private repository, GitHub Issues and milestones, Markdown, YAML Issue forms, Git, Codex GitHub connector.

**Spec:** `docs/superpowers/specs/2026-09-02-thesis-agent-design.md`

## Global Constraints

- Remote writes target only `AshleyGulin/agentic-architecture-thesis`; `AshleyGulin/-` remains unchanged.
- Formal thesis material is English; exploratory Chinese notes are clearly marked.
- Claims, evidence, interpretations, hypotheses, decisions, and open questions remain distinguishable.
- The active task queue contains at most three immediate research actions at initial setup.
- No source, citation, observation, participant, or experiment result may be invented.
- Existing remote content is read before replacement; conflicts stop the write.
- The repository is private.

---

### Task 1: Create and verify the private remote repository

**Files:**
- Preserve: `docs/superpowers/specs/2026-09-02-thesis-agent-design.md`
- Preserve: `docs/superpowers/plans/2026-09-02-thesis-agent-implementation.md`

**Interfaces:**
- Consumes: authenticated GitHub account `AshleyGulin` and approved name `agentic-architecture-thesis`.
- Produces: private repository `AshleyGulin/agentic-architecture-thesis` with default branch `main` and an initial README commit.

- [ ] **Step 1: Re-check repository availability**

Use the GitHub connector to search the linked account for the exact full name `AshleyGulin/agentic-architecture-thesis`.

Expected: no existing repository. If one exists, read its visibility and root contents and stop before creating or replacing anything.

- [ ] **Step 2: Create the repository through GitHub**

In the signed-in GitHub page, create:

```text
Owner: AshleyGulin
Repository name: agentic-architecture-thesis
Description: A living research repository and persistent agent memory for a thesis on adaptive architectural boundaries and human–architecture co-adaptation.
Visibility: Private
Initialize: Add a README
Default branch: main
```

- [ ] **Step 3: Verify repository identity and privacy**

Read the new repository using the connector.

Expected:

```text
repository_full_name = AshleyGulin/agentic-architecture-thesis
visibility = private
default_branch = main
permissions.push = true
```

- [ ] **Step 4: Confirm the unrelated repository is untouched**

Read the root tree or latest commit of `AshleyGulin/-` and retain its identifier for the final comparison.

- [ ] **Step 5: Record the remote setup locally**

Run:

```powershell
git remote add origin https://github.com/AshleyGulin/agentic-architecture-thesis.git
git remote -v
```

Expected: both fetch and push URLs name only the thesis repository.

- [ ] **Step 6: Commit the plan**

Run:

```powershell
git add docs/superpowers/plans/2026-09-02-thesis-agent-implementation.md
git commit -m "docs: plan thesis agent repository setup"
```

Expected: one new local commit containing only the implementation plan.

### Task 2: Create the agent contract and cold-start state

**Files:**
- Create: `README.md`
- Create: `AGENTS.md`
- Create: `state/current-state.md`
- Create: `state/research-memory.md`

**Interfaces:**
- Consumes: the thesis framing and agent rules in the design specification.
- Produces: a documented startup sequence and a compact handoff that a fresh agent can use without this conversation.

- [ ] **Step 1: Write `README.md` as an orientation dashboard**

Include these exact sections:

```markdown
# Agentic Architecture Thesis
## Working thesis
## Current status
## Research operating system
## Repository map
## Immediate next actions
## Working language
```

The working thesis must describe the adaptive boundary, trajectory signals, human–architecture co-adaptation, and the non-coercive agency concern as provisional framing.

- [ ] **Step 2: Validate the README scope**

Run:

```powershell
rg -n "Working thesis|Current status|Research operating system|Repository map|Immediate next actions|Working language" README.md
```

Expected: all six headings occur once; detailed research notes are linked rather than duplicated.

- [ ] **Step 3: Write `AGENTS.md`**

Define:

```text
Mission
Startup sequence
Information taxonomy
Allowed actions
Required end-of-task updates
Source and evidence rules
Major-decision approval rule
Duplication and conflict checks
Maximum of three recommended next actions
Cold-start completion checklist
```

The startup sequence must read `state/current-state.md`, `questions/question-tree.md`, `claims-and-evidence/evidence-matrix.md`, relevant recent logs, and task-specific files.

- [ ] **Step 4: Write the state documents**

`state/current-state.md` contains:

```markdown
# Current State
## One-sentence position
## Active inquiry
## Current evidence
## Active experiment
## Decisions needed
## Blockers
## Next three actions
## Last updated
```

`state/research-memory.md` contains separate tables for supported findings, hypotheses, interpretations, decisions, and open questions. Initial entries must be labeled provisional unless the repository contains traceable evidence.

- [ ] **Step 5: Run a cold-start completeness check**

Run:

```powershell
$required = @('README.md','AGENTS.md','state/current-state.md','state/research-memory.md')
$missing = $required | Where-Object { -not (Test-Path -LiteralPath $_) }
if ($missing) { throw "Missing: $($missing -join ', ')" }
rg -n "Source|Evidence|Interpretation|Hypothesis|Decision|Open question" AGENTS.md state/research-memory.md
```

Expected: no missing files and every information class appears.

- [ ] **Step 6: Commit the cold-start layer**

Run:

```powershell
git add README.md AGENTS.md state
git commit -m "feat: add thesis agent memory and operating contract"
```

### Task 3: Build the research reasoning layer

**Files:**
- Create: `questions/question-tree.md`
- Create: `claims-and-evidence/evidence-matrix.md`
- Create: `writing/thesis-framing.md`
- Create: `writing/research-questions.md`
- Create: `writing/argument-outline.md`
- Create: `writing/glossary.md`

**Interfaces:**
- Consumes: provisional thesis framing and the information taxonomy in `AGENTS.md`.
- Produces: linked questions, hypotheses, claims, evidence gaps, and a provisional argument that later research can revise.

- [ ] **Step 1: Write the question tree**

Start with this provisional core question:

```text
How can an adaptive architectural boundary learn from occupants' spatial behavior and alter spatial affordances while preserving occupants' capacity to negotiate, resist, or reinterpret its actions?
```

Create branches for need, perception, action space, human negotiation, and architectural evaluation. For every branch include `Status`, `Why it matters`, `Current hypothesis`, `Evidence needed`, and `Next test`.

- [ ] **Step 2: Write the evidence matrix**

Use columns:

```text
ID | Claim or hypothesis | Type | Evidence needed | Current evidence | Limitations | Related question | Next action | Status
```

Seed entries for fixed boundaries and changing relations, trajectory as a signal, soft boundaries as negotiable interventions, agent over-control, and architectural contribution. Set `Current evidence` to `Not yet documented` unless a traceable source is already in the repository.

- [ ] **Step 3: Validate uncertainty language**

Run:

```powershell
rg -n "Provisional|Hypothesis|Not yet documented|Evidence needed|Limitations" questions claims-and-evidence writing
```

Expected: provisional framing is explicit and unsupported claims are not presented as findings.

- [ ] **Step 4: Write the four thesis writing documents**

- `thesis-framing.md`: problem, context, gap, proposition, intended contribution, scope, non-goals, and Chinese thinking notes.
- `research-questions.md`: one provisional primary question, dependent questions, operational terms, and revision criteria.
- `argument-outline.md`: a claim-evidence-design implication skeleton rather than final chapter prose.
- `glossary.md`: agentic architecture, adaptive boundary, affordance, trajectory, proxemics, agency negotiation, co-adaptation, and architectural agency.

- [ ] **Step 5: Verify cross-links**

Run:

```powershell
rg -n "question-tree.md|evidence-matrix.md|thesis-framing.md|research-questions.md|argument-outline.md|glossary.md" README.md questions claims-and-evidence writing
```

Expected: README links to the reasoning layer; question and evidence documents link to each other.

- [ ] **Step 6: Commit the reasoning layer**

Run:

```powershell
git add questions claims-and-evidence writing README.md
git commit -m "feat: add thesis questions and evidence framework"
```

### Task 4: Add research, design, experiment, and decision workflows

**Files:**
- Create: `research/literature-map.md`
- Create: `research/bibliography.md`
- Create: `research/precedents.md`
- Create: `research/reading-notes/README.md`
- Create: `design-system/scenario.md`
- Create: `design-system/adaptive-boundary.md`
- Create: `design-system/agent-model.md`
- Create: `design-system/trajectory-metrics.md`
- Create: `experiments/experiment-index.md`
- Create: `experiments/experiment-template.md`
- Create: `logs/decisions.md`
- Create: `logs/weekly/README.md`

**Interfaces:**
- Consumes: question identifiers and evidence gaps from Task 3.
- Produces: focused templates and provisional design descriptions that feed evidence back into the matrix.

- [ ] **Step 1: Create the research templates**

The reading-note template records citation, source link, access date, research relevance, method, findings, limitations, useful concepts, candidate quotations with page numbers, interpretation, related questions, and follow-up.

The precedent template distinguishes project facts, source, architectural operation, sensing, action, human agency, evaluation, relevance, and transfer risk.

- [ ] **Step 2: Create provisional design-system documents**

Document the compact domestic scenario, adaptive boundary action space, agent observation/action/feedback loop, and candidate trajectory metrics. Mark unselected scenarios, sensors, mechanisms, and metrics as hypotheses or open questions rather than commitments.

- [ ] **Step 3: Create experiment records**

`experiment-template.md` contains:

```text
Experiment ID
Related question and claim
Hypothesis
Independent and dependent variables
Configuration
Participants or simulated agents
Procedure
Measures
Ethics and privacy
Raw evidence location
Observations
Results
Limitations
Decision or next experiment
```

`experiment-index.md` reserves identifiers beginning with `EXP-001` but does not invent completed experiments.

- [ ] **Step 4: Create decision and weekly logs**

Decision entries record date, context, options, decision, rationale, evidence, consequences, and reconsideration trigger. Weekly entries record work performed, evidence added, changed interpretations, failed attempts, decisions, open questions, and no more than three next actions.

- [ ] **Step 5: Validate template provenance fields**

Run:

```powershell
rg -n "Source|Citation|Related question|Evidence|Limitations|Decision|Next" research design-system experiments logs
```

Expected: every workflow can trace new information to a source, question, claim, or decision.

- [ ] **Step 6: Commit the workflow layer**

Run:

```powershell
git add research design-system experiments logs README.md state
git commit -m "feat: add research and experiment workflows"
```

### Task 5: Configure actionable GitHub work

**Files:**
- Create: `.github/ISSUE_TEMPLATE/reading.yml`
- Create: `.github/ISSUE_TEMPLATE/framing.yml`
- Create: `.github/ISSUE_TEMPLATE/precedent.yml`
- Create: `.github/ISSUE_TEMPLATE/experiment.yml`
- Create: `.github/ISSUE_TEMPLATE/writing.yml`
- Create: `.github/ISSUE_TEMPLATE/decision.yml`
- Create: `.github/ISSUE_TEMPLATE/config.yml`

**Interfaces:**
- Consumes: question IDs, claim IDs, stage gates, and completion-evidence rules.
- Produces: structured Issue forms, four stage-gate milestones, labels, and three immediate Issues.

- [ ] **Step 1: Write Issue forms**

Every form requires:

```text
Purpose
Related question or claim
Expected repository output
Completion evidence
Relevant links or sources
```

Specialized forms add method and variables for experiments, bibliographic metadata for readings, and options/consequences for decisions.

- [ ] **Step 2: Validate all Issue forms**

Run:

```powershell
$forms = Get-ChildItem .github/ISSUE_TEMPLATE/*.yml
if ($forms.Count -ne 7) { throw "Expected 7 issue configuration files" }
rg -n "name:|description:|body:|validations:|required: true" .github/ISSUE_TEMPLATE
```

Expected: six actionable forms plus `config.yml`; required fields are enforced.

- [ ] **Step 3: Commit Issue forms**

Run:

```powershell
git add .github/ISSUE_TEMPLATE
git commit -m "feat: add thesis research issue forms"
```

- [ ] **Step 4: Create labels**

Create only the initial labels:

```text
type:reading
type:framing
type:precedent
type:experiment
type:writing
type:decision
knowledge:hypothesis
knowledge:evidence
status:blocked
agent:attention
```

If the connector cannot create a missing label directly, create it through GitHub when assigning it to an initial Issue. Do not replace existing repository labels wholesale.

- [ ] **Step 5: Create stage-gate milestones**

Create `Frame locked`, `System demonstrated`, `Evidence sufficient`, and `Thesis defensible` without speculative due dates. Use the GitHub page if milestone creation is not exposed by the connector.

- [ ] **Step 6: Create exactly three immediate Issues**

Create:

1. `Compare three candidate domestic scenarios for the adaptive boundary`
2. `Define observable indicators of spatial negotiation from trajectory data`
3. `Build the initial literature map for adaptive environments, proxemics, and human–agent negotiation`

Each Issue must link to a question or claim, identify a Markdown output, state completion evidence, and use the appropriate stage-gate milestone. Do not invent deadlines.

- [ ] **Step 7: Verify the actionable queue**

List open Issues through the connector.

Expected: exactly three initial research Issues created by this setup, each with a type label, stage-gate milestone where supported, and concrete output.

### Task 6: Publish, read back, and test agent continuity

**Files:**
- Modify: `state/current-state.md`
- Modify: `README.md`

**Interfaces:**
- Consumes: the complete local repository, remote repository, and three initial Issues.
- Produces: synchronized remote content and evidence that a new agent can recover the thesis state safely.

- [ ] **Step 1: Update current state after setup**

Record repository initialization, current provisional framing, the three open Issues, no active experiment, outstanding student decisions, and the last-updated date. Link Issue numbers after they exist.

- [ ] **Step 2: Run the complete local structure check**

Run:

```powershell
$required = @(
  'README.md','AGENTS.md','state/current-state.md','state/research-memory.md',
  'questions/question-tree.md','claims-and-evidence/evidence-matrix.md',
  'research/literature-map.md','research/bibliography.md','research/precedents.md',
  'design-system/scenario.md','design-system/adaptive-boundary.md',
  'design-system/agent-model.md','design-system/trajectory-metrics.md',
  'experiments/experiment-index.md','experiments/experiment-template.md',
  'writing/thesis-framing.md','writing/research-questions.md',
  'writing/argument-outline.md','writing/glossary.md','logs/decisions.md'
)
$missing = $required | Where-Object { -not (Test-Path -LiteralPath $_) }
if ($missing) { throw "Missing: $($missing -join ', ')" }
rg -n "invented citation|confirmed finding|content pending|details pending" README.md AGENTS.md state questions claims-and-evidence research design-system experiments writing logs
```

Expected: no missing files, no unresolved implementation placeholders, and no language that falsely claims evidence.

- [ ] **Step 3: Commit final state**

Run:

```powershell
git add README.md state/current-state.md
git commit -m "docs: record initial thesis agent state"
git status --short --branch
```

Expected: clean local working tree.

- [ ] **Step 4: Publish local commits without overwriting the remote initializer**

Read the remote `main` head first. Incorporate the initial remote README commit into the local history or publish the local tree through connector Git-data operations using that remote commit as parent. Never force-update `main`.

Expected: remote `main` advances by fast-forward and contains both the spec and implementation plan.

- [ ] **Step 5: Read back critical remote files**

Use the connector to fetch:

```text
README.md
AGENTS.md
state/current-state.md
questions/question-tree.md
claims-and-evidence/evidence-matrix.md
experiments/experiment-template.md
```

Expected: remote contents match the committed local versions.

- [ ] **Step 6: Perform the cold-start test**

Using only `AGENTS.md` and the files in its startup sequence, produce a test summary containing:

```text
one-sentence thesis position
current evidence status
largest unresolved research gap
active experiment
decisions needed from the student
next three actions
```

Expected: the summary is accurate without using the original ChatGPT conversation and does not turn hypotheses into findings.

- [ ] **Step 7: Verify isolation**

Re-read the root tree or latest commit identifier of `AshleyGulin/-`.

Expected: it matches the identifier captured in Task 1.

- [ ] **Step 8: Configure optional weekly review only with explicit approval**

If the student asks to activate it, create a weekly heartbeat that reads the repository state, remains silent when unchanged, and notifies only for a consequential evidence gap, sustained stagnation, completion, failure, or a decision requiring the student. Otherwise leave scheduling unconfigured.

- [ ] **Step 9: Report completion**

Provide the private repository link, summarize the cold-start test, list the three open Issues, and state whether the optional weekly review remains off or is active.
