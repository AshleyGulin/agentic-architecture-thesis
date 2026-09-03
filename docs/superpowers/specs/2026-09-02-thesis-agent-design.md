# Agentic Architecture Thesis Agent — Design Specification

## 1. Purpose

Create a private GitHub repository named `agentic-architecture-thesis` that functions as both a thesis knowledge base and the durable memory of a long-running thesis agent.

The repository will support an architecture thesis about agentic architecture, adaptive architectural boundaries, human trajectories, and human–architecture co-adaptation. It must preserve research context across conversations, expose gaps between claims and evidence, and turn the next useful research actions into a small number of GitHub Issues.

The system is not a fixed annual calendar. The student expects to graduate in May 2027, but the research direction is still developing. Progress will therefore be organized through research questions, iterative inquiry loops, evidence, and stage gates rather than a detailed month-by-month plan.

## 2. Working Language

- Formal thesis material and content intended for later publication will be written in English.
- Exploratory thinking notes may be written in Chinese.
- Core documents may contain a clearly marked `Chinese thinking notes` section when informal reasoning needs to remain close to the formal text.
- The agent must not silently translate an uncertain Chinese idea into an authoritative English claim. It must preserve uncertainty and label the statement appropriately.

## 3. Thesis Framing at Repository Creation

The initial framing is provisional:

- **Domain:** agentic architecture and human–architecture co-adaptation.
- **Architectural primitive:** an adaptive boundary rather than a wall alone.
- **Candidate materialization:** curtain or another soft, continuously adjustable boundary.
- **Primary behavioral signal:** human trajectory, expanded to include movement, distance, orientation, hesitation, dwell, and route choice.
- **Candidate context:** a compact domestic environment with a primary occupant and changing social presence.
- **Central concern:** how an adaptive boundary learns from spatial behavior and changes spatial affordances without over-controlling occupants.

These statements are hypotheses and framing decisions, not established findings.

## 4. Repository Architecture

```text
agentic-architecture-thesis/
├── README.md
├── AGENTS.md
├── state/
│   ├── current-state.md
│   └── research-memory.md
├── questions/
│   └── question-tree.md
├── claims-and-evidence/
│   └── evidence-matrix.md
├── research/
│   ├── literature-map.md
│   ├── bibliography.md
│   ├── precedents.md
│   └── reading-notes/
├── design-system/
│   ├── scenario.md
│   ├── adaptive-boundary.md
│   ├── agent-model.md
│   └── trajectory-metrics.md
├── experiments/
│   ├── experiment-index.md
│   └── experiment-template.md
├── writing/
│   ├── thesis-framing.md
│   ├── research-questions.md
│   ├── argument-outline.md
│   └── glossary.md
├── logs/
│   ├── decisions.md
│   └── weekly/
├── .github/
│   └── ISSUE_TEMPLATE/
└── docs/superpowers/specs/
```

`README.md` is an orientation dashboard, not the complete knowledge base. It links to the current thesis position, active research questions, current experiments, and next actions.

`state/current-state.md` is the shortest reliable handoff document. It records the present direction, active work, blockers, decisions required from the student, and no more than three recommended next actions.

`state/research-memory.md` contains only durable information worth carrying across sessions. It distinguishes supported findings from hypotheses and avoids duplicating reading notes.

## 5. Research Operating Model

### 5.1 Question Tree

Research is organized from a core question into dependent questions:

```text
Core question
├── Why must the boundary adapt?
├── What can the agent perceive?
├── What can the boundary change?
├── How do occupants negotiate with it?
└── How is architectural value evaluated?
```

Each active question may connect to a hypothesis, required evidence, current evidence, design implication, and next test.

### 5.2 Research Loop

The basic unit of progress is an inquiry loop:

```text
observe → frame a question → make or simulate → test → interpret → revise
```

The duration is not fixed. A loop may be a desk study, a precedent comparison, a simulation, or a full-scale prototype experiment.

Experiments receive stable identifiers such as `EXP-001`. Failed and inconclusive experiments remain documented because they constrain later claims.

### 5.3 Evidence Matrix

Every central thesis claim is tracked against:

- evidence required;
- evidence currently available;
- evidence quality or limitation;
- unresolved gap;
- next useful action.

The agent must use the evidence matrix to distinguish progress in knowledge from completion of administrative tasks.

### 5.4 Stage Gates

Only four high-level gates are maintained:

1. **Frame locked:** the problem, context, research question, and intended contribution can be stated clearly.
2. **System demonstrated:** sensing, agent policy, adaptive boundary, and occupant response form an observable loop.
3. **Evidence sufficient:** the main claims are supported, revised, or explicitly limited by research evidence.
4. **Thesis defensible:** writing, design work, and experimental evidence form a coherent argument suitable for examination before May 2027.

Dates may be added later by working backward from confirmed institutional deadlines.

## 6. Thesis Agent

### 6.1 Role

The Thesis Agent is a persistent research collaborator whose memory is stored in the repository rather than hidden in a single conversation. It helps the student recover context, evaluate research gaps, synthesize new material, and decide the next useful action.

### 6.2 Startup Sequence

At the beginning of each substantial task, the agent reads, in order:

1. `AGENTS.md`;
2. `state/current-state.md`;
3. `questions/question-tree.md`;
4. `claims-and-evidence/evidence-matrix.md`;
5. the latest decision and weekly logs relevant to the request;
6. the specific research, design, experiment, or writing documents involved.

It should not load every file when a targeted read is sufficient.

### 6.3 Classification of New Information

Before committing new material to durable memory, the agent classifies it as one or more of:

- **Source:** bibliographic or precedent material that can be traced.
- **Evidence:** an observation or result with a documented method and provenance.
- **Interpretation:** a reasoned reading of sources or evidence.
- **Hypothesis:** a proposition that remains to be tested.
- **Decision:** an adopted direction and its rationale.
- **Open question:** an unresolved matter that affects the research.

The label must remain visible wherever confusing the categories could overstate certainty.

### 6.4 Actions

Within an approved task, the agent may:

- update the relevant Markdown document;
- update the evidence matrix and question tree;
- record a decision with its rationale;
- create or update a small number of GitHub Issues;
- refresh `state/current-state.md` at the end of meaningful work;
- recommend up to three prioritized next actions.

Major reframing must be proposed to the student before being adopted as a decision.

### 6.5 Guardrails

The agent must:

- never invent sources, citations, observations, participants, or experiment results;
- distinguish preference and speculation from supported conclusions;
- avoid presenting a moving curtain or technical mechanism as architectural contribution without explaining its spatial consequences;
- check for an existing document or Issue before creating a duplicate;
- preserve existing content and use additive edits or reviewed replacements;
- record the reason for consequential changes in `logs/decisions.md`;
- keep the active Issue set small and avoid pre-populating a year of speculative tasks;
- surface contradictions and missing evidence;
- request student judgment when a choice changes thesis scope, ethics, or research direction.

## 7. GitHub Work Model

Markdown files preserve knowledge and argument. GitHub Issues represent actionable work only.

Initial Issue templates will cover:

- reading or source review;
- research question or framing work;
- precedent analysis;
- experiment;
- writing or synthesis;
- decision required.

Each Issue should identify its purpose, related question or claim, expected output, completion evidence, and linked documents. Labels will describe work type and state of knowledge. Milestones will correspond to the four stage gates, not calendar months.

Repository creation and initial content will occur without modifying the unrelated existing repository `AshleyGulin/-`.

## 8. Agent Interaction Model

The operating mode is hybrid:

- **On demand:** the student can ask the agent to ingest a source, develop a question, plan or review an experiment, synthesize evidence, update writing, or assess current state.
- **Lightweight recurring review:** once repository setup is complete, an optional weekly heartbeat may inspect progress. It should remain quiet when nothing meaningful has changed and notify only when it finds a consequential gap, sustained stagnation, completion, failure, or a decision requiring the student.

The recurring review is not a detailed schedule and does not manufacture work merely to produce an update.

## 9. Safety and Failure Handling

- Remote writes must target the private `AshleyGulin/agentic-architecture-thesis` repository only.
- Before updating an existing remote file, the current version and blob identifier must be read.
- Conflicting edits stop the write and are reported for review.
- Partial setup must be documented in `state/current-state.md` with the remaining action clearly stated.
- When a source cannot be verified, it remains an unverified lead and cannot enter the bibliography as confirmed evidence.

## 10. Initial Success Criteria

Initial setup is complete when:

- the private GitHub repository exists under `AshleyGulin`;
- the repository structure and core Markdown documents are present;
- current framing is captured without overstating certainty;
- `AGENTS.md` defines the startup sequence, information taxonomy, actions, and guardrails;
- the question tree and evidence matrix contain useful initial entries;
- Issue templates and the four stage-gate milestones are available where supported;
- a small first set of Issues reflects immediate research needs;
- a fresh agent can read the repository and accurately summarize the thesis state and next actions without relying on this conversation.

## 11. Verification

After setup, verification will include:

1. confirming repository privacy and ownership;
2. listing remote files to verify structure;
3. reading back core files from GitHub;
4. checking that no file in `AshleyGulin/-` changed;
5. testing a cold-start prompt against the repository handoff documents;
6. checking all initial Issues for a linked question, claim, or concrete output.
