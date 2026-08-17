# Target-Centered Cognition

ERIE does not organize cognition around reasoning.

ERIE organizes cognition around **Targets**.

Reasoning is one cognitive capability used to advance a Target — it is not the organizing principle of the engine. A Target is the persistent object of cognition: something that must become satisfied.

## The cognitive flow

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
Next Cognitive Action
```

## Intent

Intent is why cognition exists. Every Target begins with a purpose — investigate, resolve, verify, explain, or track. The intent is the reason the Target exists at all.

## Target

A Target is the persistent object of cognition. It represents something that must become satisfied, and it persists across reasoning cycles until it is:

- satisfied,
- abandoned, or
- archived.

A Target is not a question. A Target is a commitment.

## Satisfaction Criteria

A Target decomposes into one or more **Satisfaction Criteria**. Criteria define what it means for the Target to be satisfied.

Without criteria, "Resolved" has no meaning.

Criteria are first-class objects, not just text. Each criterion carries:

- a **kind** — what kind of satisfaction it represents (evidence, identity, temporal, consistency, completeness, constraint)
- **required** — whether the criterion must be satisfied for the Target to resolve
- **blocking** — an unsatisfied blocking criterion prevents resolution and forces escalation
- an **alternative group** — criteria in the same group are satisfied when any member is satisfied (OR); groups combine with everything else (AND)
- a **weight** — its deterministic influence on pressure
- a **derivation source** — which criterion it was derived from, when applicable
- an **evaluation method** — how the criterion is deterministically evaluated
- **provenance** — where the criterion came from, fully traceable

Criteria compose. *Launch Ready* can be expressed as *Tests Pass* AND (*Manual Review* OR *Automated Check*) AND *Legal Approved* — each of those being a first-class criterion.

## State

State is **derived** by evaluating the Target's criteria. It is never guessed.

```text
unknown      nothing is known yet
partial      some criteria satisfied
ambiguous    evidence conflicts
resolved     all required criteria satisfied
exhausted    deterministic investigation is exhausted
reopened     a resolved target became unsatisfied again
```

These are evaluations, not goals. A Target in the `exhausted` state has not failed — deterministic investigation has reached its limit, honestly reported.

## Pressure

Pressure is a property of the Target, independent of reasoning. It is derived deterministically from the criteria state: the weighted share of unresolved criteria, a bonus when evidence is missing, a bonus when a previously resolved Target reopens, and a bonus when a blocking criterion is unsatisfied.

Pressure determines the escalation policy after deterministic cognition has reached its limit:

- continue deterministic reasoning
- wait for future evidence
- acquire evidence
- ask the user
- invoke semantic reasoning

## Next Cognitive Action

From the derived state and pressure, ERIE chooses the next cognitive action deterministically:

```text
Continue
Wait
Acquire Evidence
Ask
Invoke Semantic Reasoning
Resolve
```

Semantic reasoning is invoked only at the defined boundary — and only when the investigation is missing nothing it can deterministically acquire.

## Recursive cognition

If a criterion cannot be satisfied directly, ERIE can derive a new Target.

For example, if the criterion *Identity confirmed* is unsatisfied, ERIE derives a new Target: *Determine identity*. The derived Target's criteria carry their derivation source and provenance, so the recursion is fully traceable. Derived Targets are ordinary Targets: they can be evaluated, resolved, and can themselves derive further Targets.

## Active Targets

ERIE maintains a working set of Active Targets. Each Active Target carries:

- identity
- intent
- satisfaction criteria
- current state
- pressure
- missing evidence
- next cognitive action
- its own scratch workspace

Active Targets are event-driven: they are re-evaluated when new evidence arrives, when knowledge changes, when context changes, when pressure changes, or on explicit review. Continuous background reasoning never happens — Targets wake when relevant events occur.

## See also

- [How ERIE Thinks](HOW-ERIE-THINKS.md) — deterministic-first cognition and escalation
- [Cognitive Layers](COGNITIVE-LAYERS.md) — where Targets live in the architecture
- [API.md](API.md) — the public API surface
- [README.md](README.md) — the product overview
