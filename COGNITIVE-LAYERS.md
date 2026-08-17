# Cognitive Layers

ERIE's architecture separates cognition into three explicit layers. Each owns a different kind of cognitive work, and the layers are never confused for one another.

```text
Chronos remembers.
ERIE investigates.
Scratch Pad thinks.
```

Together they provide:

- persistent knowledge
- purposeful investigation
- temporary working thought

## Chronos remembers

Chronos is the persistent knowledge layer. It is the canonical memory of the system: what exists, what happened, what is still unknown.

Chronos owns:

- the world model and ontology
- the noun ledger — everything that exists
- the event ledger — what happened
- evidence with provenance
- knowledge maturity (1-9)
- evolution, materialization, and refinement
- the unresolved frontier — what is known to be unknown

Chronos preserves what is known. It never forgets, never discards a noun, and never treats speculation as knowledge. Knowledge in Chronos is deterministic, immutable, and fully traceable.

## ERIE investigates

ERIE is the purposeful investigation layer. It pursues what is unknown.

ERIE owns:

- Targets — the persistent objects of cognition
- Intent — why cognition exists
- Satisfaction Criteria — what satisfaction means
- derived state — never guessed
- pressure — independent of reasoning
- the deterministic next cognitive action

ERIE organizes cognition around Targets, not around reasoning. Reasoning is one capability used to advance a Target — invoked deterministically first, and escalated to semantic reasoning only at the defined boundary.

## Scratch Pad thinks

The Scratch Pad is the working cognition layer. Every Active Target owns one.

The Scratch Pad holds what is currently being considered:

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

The Scratch Pad is **not** knowledge. It is not truth. It is not persistent memory. It is disposable, editable, and expected to change. It exists only while it contributes to an investigation.

## The boundaries

The separation is enforced, not aspirational:

- Chronos never consumes Scratch Pad entries directly.
- Nothing moves directly from speculation into persistent knowledge.
- Every outcome must pass deterministic validation before it becomes knowledge in Chronos.
- Verified outcomes are candidates — never knowledge on their own.

The lifecycle of an observation:

```text
Observation
    |
    v
Scratch Pad
    |
    v
Evaluated
    |
    +-- Discard
    |
    +-- Verified
             |
             v
      Deterministic validation
             |
             v
          Chronos
```

When a Target resolves, its Scratch Pad is discarded, archived for debugging, or summarized into provenance. It is never treated as memory.

## Why three layers

Confusing working thought with knowledge is the failure mode of most AI systems — the model's confident speculation becomes indistinguishable from established fact.

ERIE separates them structurally:

| Layer | Owns | Is it knowledge? |
|---|---|---|
| Chronos | persistent knowledge, evidence, history, identity | yes |
| ERIE | Targets, Criteria, State, Pressure, Next Action | no — it pursues |
| Scratch Pad | temporary working cognition | no — it thinks |

This is what makes ERIE's answers defensible: at every step, the system knows which layer produced the claim, what evidence supports it, and whether it has been validated.

## See also

- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — the investigation layer
- [How ERIE Thinks](HOW-ERIE-THINKS.md) — deterministic-first escalation
- [README.md](README.md) — the product overview
