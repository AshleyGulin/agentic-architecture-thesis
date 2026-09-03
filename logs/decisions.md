# Decision Log

## Scope of this log

This log records adopted repository-level decisions already approved in the repository design specification. Its Evidence field gives decision provenance and rationale; it is not empirical thesis Evidence. Unresolved thesis framing, scenario, mechanism, sensing, metrics, ethics, and method choices remain Open questions and are not locked here.

## Entry schema

Every new entry must include date, context, options, Decision, rationale, Evidence or provenance, consequences, reconsideration trigger, and linked IDs. Material changes to thesis scope, ethics, or central contribution require student approval before entry.

### D-LOG-001 — Private thesis repository

- **Date:** 2026-09-02 repository working-date label.
- **Context:** The thesis needs durable, access-controlled working memory and future remote collaboration.
- **Options:** Public repository; private repository; non-repository storage.
- **Decision:** Use a private repository dedicated to the thesis.
- **Rationale:** Research notes, provisional claims, and possible participant-sensitive workflows should not default to public access; a dedicated repository also isolates thesis work from unrelated repositories.
- **Evidence/provenance:** Approved repository requirement in [design specification §§1, 7, and 9](../docs/superpowers/specs/2026-09-02-thesis-agent-design.md). This is design provenance, not thesis Evidence.
- **Consequences:** Remote publishing must verify ownership and privacy; sensitive study data may still require storage outside Git and separate ethics controls.
- **Reconsideration trigger:** A publication, collaboration, institutional, or data-governance requirement calls for a different access model and receives explicit approval.
- **Linked IDs:** None; repository-governance Decision.

### D-LOG-002 — English formal writing with clearly marked Chinese thinking notes

- **Date:** 2026-09-02 repository working-date label.
- **Context:** Formal thesis output is English, while exploratory reasoning may benefit from Chinese notes.
- **Options:** English only; Chinese only; bilingual formal documents; English formal writing plus labeled Chinese exploration.
- **Decision:** Write formal thesis and publication-ready content in English; permit clearly marked Chinese thinking notes for exploration.
- **Rationale:** This preserves exploratory fluency without silently turning an uncertain translation into an authoritative claim.
- **Evidence/provenance:** Approved convention in [design specification §2](../docs/superpowers/specs/2026-09-02-thesis-agent-design.md) and [AGENTS.md](../AGENTS.md). This is repository provenance, not thesis Evidence.
- **Consequences:** Chinese notes must retain uncertainty and be translated through review before becoming formal claims.
- **Reconsideration trigger:** Program, advisor, publication, or collaboration requirements change the formal language policy.
- **Linked IDs:** [Q0](../questions/question-tree.md#q0), [C1–C5](../claims-and-evidence/evidence-matrix.md) as documentation context; no claim status is changed.

### D-LOG-003 — Research operating system instead of a detailed annual calendar

- **Date:** 2026-09-02 repository working-date label.
- **Context:** The research direction is developing and fixed monthly tasks would encode premature commitments.
- **Options:** Detailed annual calendar; milestone-only plan; question/evidence inquiry loops with high-level stage gates.
- **Decision:** Organize progress through a research operating system of questions, evidence, inquiry loops, and four high-level stage gates rather than a detailed annual calendar.
- **Rationale:** The structure can respond to evidence and failed attempts while maintaining a durable view of progress.
- **Evidence/provenance:** Approved operating model in [design specification §§1 and 5](../docs/superpowers/specs/2026-09-02-thesis-agent-design.md). This is organizational provenance, not thesis Evidence.
- **Consequences:** Dates may be added from confirmed institutional deadlines; active next actions remain few and evidence-linked.
- **Reconsideration trigger:** Confirmed deadlines or institutional requirements make a more detailed schedule necessary.
- **Linked IDs:** [Q0–Q5](../questions/question-tree.md) and [C1–C5](../claims-and-evidence/evidence-matrix.md) organize the work; none is resolved by this Decision.

### D-LOG-004 — Hybrid on-demand agent with optional weekly review

- **Date:** 2026-09-02 repository working-date label.
- **Context:** The student needs help on request and may later benefit from a lightweight continuity check without manufactured updates.
- **Options:** On-demand only; fixed recurring reporting; hybrid on-demand work with an optional quiet weekly review.
- **Decision:** Use an on-demand Thesis Agent and keep a weekly review optional. If activated with explicit approval, it remains quiet when nothing meaningful changed and surfaces only consequential gaps, sustained stagnation, completion, failure, or a Decision requiring the student.
- **Rationale:** The hybrid model supports continuity without imposing a rigid schedule or creating administrative work for its own sake.
- **Evidence/provenance:** Approved interaction model in [design specification §8](../docs/superpowers/specs/2026-09-02-thesis-agent-design.md). This is organizational provenance, not thesis Evidence.
- **Consequences:** The weekly log [template](weekly/README.md) may be used without activating automation; activation remains a separate explicit choice.
- **Reconsideration trigger:** The cadence becomes burdensome, misses meaningful changes, or the student requests a different review pattern.
- **Linked IDs:** None; agent-operation Decision.

## Open decisions not yet adopted

The domestic scenario, boundary family or curtain, sensing approach, trajectory metrics, policy, participants, research method, success criteria, and thesis contribution remain provisional. Record a new Decision only after its required Evidence and approval are documented.
