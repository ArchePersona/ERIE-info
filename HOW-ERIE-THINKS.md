# How ERIE Thinks

ERIE follows a deterministic-first philosophy.

Deterministic cognition happens first. Semantic reasoning happens only when deterministic investigation reaches its boundary — and then only as a policy decision, never by default.

## The progression

```text
Intent
    |
    v
Target
    |
    v
Satisfaction Criteria
    |
    v
Deterministic Evaluation
    |
    v
State
    |
    v
Only if required
    |
    v
Semantic Reasoning
```

Deterministic cognition may:

- evaluate criteria
- acquire evidence
- identify missing evidence
- determine reasoning exhaustion
- conclude that external evidence is required

The language model is **never the default reasoning engine**. It is an optional cognitive capability, invoked only when the investigation reaches a defined boundary.

## The boundary

When deterministic cognition can no longer advance the Target on its own, ERIE chooses among:

- **Continue** — deterministic reasoning is still productive
- **Wait** — the right thing is to wait for future evidence
- **Acquire evidence** — evidence exists but has not been obtained
- **Ask** — the missing information can only come from the user
- **Invoke semantic reasoning** — the deterministic boundary has been reached and nothing is missing that can be deterministically acquired
- **Resolve** — the Target's criteria are satisfied

Invoking a model is a deliberate escalation, driven by state and pressure — never the default path.

## The Piggyback Seed

When semantic reasoning is required, ERIE transfers the complete investigation state rather than the original user prompt.

The language model receives the current investigation frontier:

- the Target
- its satisfaction criteria
- satisfied criteria
- unsatisfied criteria
- missing evidence
- the current state
- pressure
- the requested cognitive operation
- the current scratch workspace

For example, when determining an employer:

```text
Target: Determine employer

Scratch:
- Acme ruled out.
- Promotion event appears relevant.
- Need employment chronology.
- HR record contradicts payroll.
```

The model does not start from scratch. It joins an existing investigation — with the candidate paths, eliminated possibilities, and unresolved contradictions already in view.

## Scratch

Every Active Target owns a temporary cognitive workspace: the Scratch workspace. It holds what is currently being considered:

- observations
- possible explanations
- candidate paths
- eliminated possibilities
- working notes
- reminders
- intermediate derivations
- unresolved contradictions
- investigation breadcrumbs
- semantic notes

Scratch is working cognition, not knowledge. It is disposable, editable, and expected to change. Nothing moves directly from the Scratch workspace into persistent knowledge — every outcome must pass deterministic validation first.

See [Cognitive Layers](COGNITIVE-LAYERS.md).

## Attention and the cognitive budget

Reasoning is expensive. Attention is finite.

Before reasoning begins, ERIE determines where the next unit of cognitive effort provides the greatest benefit. Each reasoning cycle starts from the current knowledge summary and the unresolved frontier, selects deterministic targets, and allocates a finite cognitive budget across them. The budget follows the work that produces the greatest knowledge gain — reducing the known-unknowns first.

## Honesty by construction

ERIE never guesses, never hallucinates, and never pretends a boundary does not exist.

- State is derived, never invented.
- Pressure is a property of the Target, not an excuse.
- Semantic reasoning is an escalation, not a habit.
- Placeholders are visible until evidence resolves them.
- Every conclusion remains traceable to the evidence that supports it.

## See also

- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — the organizing principle
- [Cognitive Layers](COGNITIVE-LAYERS.md) — the three layers
- [EVALUATION.md](EVALUATION.md) — how to verify this behavior
- [API.md](API.md) — the public API surface
