# ERIE API Overview

This document describes the public API surface of ERIE at the conceptual level, for adoption and integration planning.

ERIE is a deterministic, target-centered cognitive engine. Its API is organized around investigations, not around retrieval. Retrieval is one capability within the engine; the organizing concepts are Targets, Satisfaction Criteria, State, Pressure, and the Piggyback Seed.

ERIE's implementation is proprietary. The deployed API specification supplied with access is authoritative for an active integration: it defines the endpoints, authentication, serialization, and schemas exactly as deployed.

## Access model

- ERIE is accessed through controlled API access provided by ARCHETRON.
- Credentials are issued with evaluation or commercial arrangements and are personal to the account.
- Do not share credentials. Do not include credentials in source control, logs, or reports.
- See [SECURITY.md](SECURITY.md) for reporting requirements.

## The investigation surface

### Intent

Why cognition exists. Every investigation begins with an intent — investigate, resolve, verify, explain, or track.

### Target

The persistent object of cognition. A Target represents something that must become satisfied, and it persists across reasoning cycles until satisfied, abandoned, or archived.

### SatisfactionCriterion

What it means for a Target to be satisfied. Criteria are first-class objects with a kind (evidence, identity, temporal, consistency, completeness, constraint), required/blocking semantics, alternative groups, weight, evaluation method, and provenance.

```text
kind
required
blocking
alternative_group
weight
derived_from
evaluation_method
provenance
```

### TargetState

The derived state of a Target — an evaluation, never a guess.

```text
unknown
partial
ambiguous
resolved
exhausted
reopened
```

### Pressure

A property of the Target, in [0, 9], independent of reasoning. Derived from the criteria state; determines escalation policy.

### NextCognitiveAction

The deterministic next action, chosen by policy from state and pressure.

```text
continue
wait
acquire_evidence
ask
invoke_semantic_reasoning
resolve
```

### PiggybackSeed

The complete investigation state transferred when semantic reasoning is invoked: the Target, its criteria, satisfied and unsatisfied criteria, missing evidence, current state, pressure, requested operation, and the current scratch workspace. The model joins an existing investigation rather than starting a new one.

### Scratch

The Target's temporary cognitive workspace — working cognition, never knowledge. Observations, candidate explanations, eliminated paths, and intermediate reasoning. Nothing moves from the scratch workspace into persistent knowledge without deterministic validation.

## The evidence surface

ERIE grounds every investigation in real material. The evidence surface supports that grounding:

### EvidenceReference

Provenance carried by every evidence item.

```text
source_id
location
acquired_at
```

### Evidence

Source material combined with its provenance reference. Metadata may accompany evidence, but metadata is never silently promoted into evidence.

### EvidenceSet

The ordered body of evidence supplied to an investigation. The evidence set defines what an investigation may and may not derive from.

### InferenceResult

The outcome of a reasoning operation within an investigation.

```text
output
evidence
claims
```

- `output` — the produced result
- `evidence` — the material the result was grounded on
- `claims` — assertions derived from that evidence, traceable to it

## Conceptual usage

```python
# An investigation, not a question.
target = Intent("resolve employment", kind="resolve")
target.add_criterion("employer identified", kind="identity", required=True)
target.add_criterion("evidence confirmed", kind="evidence", required=True)

# Deterministic evaluation advances the target.
state = target.evaluate()

if state.next_action == "invoke_semantic_reasoning":
    seed = target.seed_for_semantic_reasoning()
    # The model receives the complete investigation state.
    result = model.join(seed)
```

This example illustrates the public contract, not ERIE's internal implementation.

## Contract guarantees

- **Target persistence.** Investigations persist across reasoning cycles until satisfied, abandoned, or archived.
- **State is derived.** Target state is deterministically derived from satisfaction criteria, never guessed.
- **Deterministic first.** Semantic reasoning is invoked only when deterministic investigation reaches a defined boundary — never by default.
- **Evidence boundary.** Investigation may derive from supplied evidence. It may not introduce facts absent from that evidence.
- **Provenance.** Evidence and outcomes retain source, location, and acquisition context.
- **Contradiction preservation.** Disagreement is not flattened into a single confident answer.
- **Provider independence.** The surface does not depend on a particular model, storage, or retrieval provider.

## Stability boundary

Integrate against the deployed API schemas supplied with access. Do not rely on undocumented fields, behavior, or endpoints; they may change without notice. Documented concepts are designed to remain stable.

## See also

- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — the organizing principle
- [How ERIE Thinks](HOW-ERIE-THINKS.md) — deterministic-first cognition and escalation
- [Cognitive Layers](COGNITIVE-LAYERS.md) — Chronos / ERIE / Scratch
- [QUICKSTART.md](QUICKSTART.md) — first investigation end to end
- [INTEGRATION.md](INTEGRATION.md) — fitting ERIE into your architecture
- [EVALUATION.md](EVALUATION.md) — evaluating the contract behaviorally
- [FAQ.md](FAQ.md) — common questions
