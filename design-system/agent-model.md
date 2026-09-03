# Provisional Agent Model

## Status

This is a design Hypothesis for structuring inquiry, not an implemented system or claim of intelligent behavior. It links [Q2](../questions/question-tree.md#q2), [Q3](../questions/question-tree.md#q3), and [Q4](../questions/question-tree.md#q4) with [C2](../claims-and-evidence/evidence-matrix.md#c2), [C3](../claims-and-evidence/evidence-matrix.md#c3), and [C4](../claims-and-evidence/evidence-matrix.md#c4).

## Provisional loop

```text
observation
  → bounded interpretation with uncertainty
  → policy choice: do nothing / ask / propose / act within consent
  → boundary action or non-action
  → observed occupant response
  → feedback and documented revision
```

Every transition must remain inspectable. The loop does not grant the agent access to intention, consent, emotion, social role, or preference unless a person communicates it through an approved channel.

## Observed features versus inferred social meaning

| Observed or directly recorded feature | Possible Interpretation to test, never an observed fact | Counterexamples or ambiguity | Policy limit |
| --- | --- | --- | --- |
| Position or path relative to a boundary | Person may be approaching, passing, avoiding, or exploring. | The route may concern an object, another person, habit, accessibility, or sensor error. | Do not move solely because a path resembles an intent category. |
| Reduced speed or pause | Person may be hesitating or waiting. | They may be reading, listening, resting, distracted, or outside the valid sensing area. | Increase uncertainty; prefer non-action or a low-attention clarification. |
| Orientation estimate | Attention or intended route may be changing. | Body, head, gaze, mobility aid, and sensor orientation may disagree. | Do not infer attention, identity, or consent from orientation. |
| Clearance or distance to people/boundary | Proximity conditions may create comfort, access, or safety concerns. | Desired distance varies by person, activity, culture, environment, and moment. | Enforce verified safety clearance but do not claim a social preference. |
| Repeated detour or reversal | A layout or action may be inconvenient, resisted, or reinterpreted. | The repeated route may be playful, incidental, object-driven, or caused by tracking error. | Surface a possible pattern and invite correction; do not optimize it away automatically. |
| Direct command, manual adjustment, stop, or reversal | A person has provided explicit interaction input. | Input may conflict across occupants or be accidental; authority may be unclear. | Honor stop immediately; resolve other conflicts through the approved consent protocol. |

## Model components

### Observation

- Use the minimum approved features and spatial resolution needed for the study.
- Record sensor confidence, missing data, timestamp, coordinate frame, and known occlusion or tracking limits.
- Avoid identity, audio, video, or sensitive attributes unless separately justified, consented to, and approved.

### Interpretation

- Keep multiple plausible interpretations with confidence or uncertainty bounds.
- Label social meaning as Interpretation; never promote it to observation through repetition.
- Include an `unknown/ambiguous` state and counterexamples from documented testing.

### Policy

- Candidate outputs are `do nothing`, `ask`, `propose`, `act within prior consent`, and `safe stop/recover`.
- Default to non-action when uncertainty, consent, authority, or safety is unresolved.
- Prevent one occupant’s inferred preference from silently overriding another person’s explicit refusal.

### Boundary action

- Use only an approved, bounded action from the [adaptive-boundary action space](adaptive-boundary.md).
- Explain the proposed spatial effect and provide time and means to refuse, stop, or reverse.
- Separate an action command from confirmation that the physical state was achieved safely.

### Occupant response and feedback

- Record observable response separately from participant-reported meaning.
- Treat refusal, interruption, manual adjustment, workaround, and reinterpretation as valid feedback, not model error by default.
- A feedback update remains a Hypothesis until repeated and evaluated under a documented method.

## Uncertainty and memory horizon

- **Uncertainty:** represent observation quality and interpretation uncertainty separately; set action-specific thresholds only through approved testing.
- **Memory horizon:** compare no memory, within-session context, and longer-term preference memory as candidates. No horizon is selected.
- **Forgetting:** expire or aggregate records according to the study’s consent and data-retention plan; do not preserve inferred social labels by default.
- **Conflict:** current explicit refusal and safety stop take priority over learned tendency or historical preference.

## Explanation, consent, and override

- Explain what was observed, what was inferred, the uncertainty, the proposed spatial effect, and how to decline.
- Obtain consent for sensing, storage, model updates, and boundary actuation as distinct choices; include bystanders and withdrawal.
- Provide a persistent manual mode plus immediate, accessible stop and reversal behavior.
- A stop must not depend on successful interpretation by the model.

## Failure modes and required response

| Failure mode | Risk | Required provisional response | Evidence to collect before deployment |
| --- | --- | --- | --- |
| Missing, noisy, or misassociated observation | Unsafe or irrelevant action. | Do nothing or stop; report uncertainty. | Sensor test records and known failure envelope. |
| Unsupported social inference | Stereotyping, coercion, or privacy harm. | Remove or constrain the inference; ask rather than assume. | Counterexamples, participant correction, and audit trail. |
| Conflicting occupant input | One person’s agency is suppressed. | Honor any stop; pause other action and request resolution under an approved protocol. | Multi-occupant scenario tests and consent rules. |
| Obstruction or mechanical fault | Collision, entrapment, blocked access, or damage. | Immediate safe stop; release/manual recovery; no autonomous retry. | Independent safety validation and recovery test. |
| Explanation or control unavailable | Occupant cannot understand or refuse. | Remain fixed/manual and signal unavailability. | Accessibility and failure-recovery evaluation. |
| Feedback drift or stale memory | Historical pattern dominates current preference. | Reduce memory weight, expire data, and prioritize current explicit input. | Longitudinal tests and retention audit. |

## Evaluation questions

- Does the loop preserve practical opportunities for anticipation, refusal, reversal, redirection, and reinterpretation?
- Can observers distinguish observation, Interpretation, policy choice, physical action, response, and feedback?
- Do fixed and direct-manual baselines perform as well or better?
- Which failures would disconfirm [C2](../claims-and-evidence/evidence-matrix.md#c2), [C3](../claims-and-evidence/evidence-matrix.md#c3), or [C4](../claims-and-evidence/evidence-matrix.md#c4)?
