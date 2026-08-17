# Integrating ERIE

This document explains how ERIE fits into an existing AI architecture.

ERIE is a deterministic, target-centered cognitive engine — the successor to Retrieval-Augmented Generation (RAG). It is the intelligence layer between enterprise knowledge and AI generation.

```text
Enterprise Knowledge
        |
        v
      Chronos
        |
Evidence . Claims . Events . Context
        |
        v
      ERIE
        |
 Targets . Criteria . Pressure
        |
        v
 Any Language Model  (when the boundary demands it)
        |
        v
 Defensible, explainable answers
```

ERIE does not replace your application, your language model, or your knowledge sources. It supersedes the retrieval layer between them — and, beyond that, it changes what the system is trying to do: satisfy investigations rather than answer prompts.

## Replacing the retrieval layer

In a typical RAG architecture:

```text
Query -> Retriever -> Text chunks -> Prompt -> LLM -> Answer
```

With ERIE:

```text
Target -> ERIE -> Evidence . Claims . Context -> Deterministic evaluation -> LLM (only at the boundary) -> Resolved investigation
```

The difference is what the language model reasons over — and whether it is consulted at all:

- RAG feeds the model retrieved text chunks, with no structure and no provenance.
- ERIE feeds the model evidence with provenance, resolved claims, relationships, and context — and consults the model only when deterministic investigation reaches its boundary.

Your language model stays the same. The material it reasons over changes — and so does the decision about when reasoning is needed at all.

## Investigation-grounded context

An ERIE integration is organized around investigations. An investigation has an intent, satisfaction criteria, a derived state, pressure, and a deterministic next action. Deterministic evaluation comes first; semantic reasoning is invoked only at the defined boundary.

The governing constraint is straightforward:

> **Investigation may derive from supplied evidence. It may not introduce facts absent from that evidence.**

This makes the evidence boundary testable rather than merely advisory. An integrating application can verify that every claim in a result is traceable to supplied evidence with provenance.

## Provider independence

ERIE is provider-independent by design:

- any language model — ERIE does not couple you to a model vendor
- any storage backend — evidence and knowledge are not tied to a database vendor
- any retrieval implementation — retrieval providers can evolve without changing your integration

Changing a provider is an operational change, not an architectural one. You integrate against ERIE's stable public surface, not against internals.

## Traceability and explainable reasoning

Every result contains:

- the produced output
- the evidence on which the output was grounded
- the supported claims derived from that evidence

Claims remain connected to their evidence, and evidence retains its provenance. An integrating application can walk any answer back to the sources that produced it — which is exactly what is needed when an answer has to be defended.

## Contradictions are preserved, not flattened

Traditional retrieval silently collapses disagreement into a single confident answer. ERIE preserves meaningful distinctions: claims may be duplicate, refined, superseded, contradictory, or independent — and the disagreement stays visible in the result.

## The public integration surface

Applications interact with ERIE through defined interfaces organized around investigations:

- `Intent` and `Target` — why cognition exists and the persistent object of cognition
- `SatisfactionCriterion` — what it means for the Target to be satisfied
- `TargetState` — the derived state (unknown, partial, ambiguous, resolved, exhausted, reopened)
- `Pressure` — the deterministic property that drives escalation policy
- `NextCognitiveAction` — the deterministic next action (continue, wait, acquire evidence, ask, invoke semantic reasoning, resolve)
- `PiggybackSeed` — the complete investigation state transferred when semantic reasoning is invoked
- `EvidenceSet` and `InferenceResult` — the evidence grounding for each operation

```python
target = Intent("resolve employment", kind="resolve")
target.add_criterion("employer identified", kind="identity", required=True)
target.add_criterion("evidence confirmed", kind="evidence", required=True)

state = target.evaluate()

if state.next_action == "invoke_semantic_reasoning":
    seed = target.seed_for_semantic_reasoning()
    result = model.join(seed)
```

The exact network API, authentication mechanism, endpoints, and serialized schemas are supplied with API access and are authoritative for an active integration.

## Stability boundary

Integrate against documented ERIE interfaces and the deployed API schemas supplied with access — never against implementation details.

ERIE is designed so that underlying storage, retrieval, and model providers can evolve without requiring applications to change. The implementation behind the public surface is proprietary.

## Evaluation before integration

Before committing to an integration, evaluate ERIE on your own evidence: [EVALUATION.md](EVALUATION.md).

## See also

- [QUICKSTART.md](QUICKSTART.md) — from access to first investigation
- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — the organizing principle
- [How ERIE Thinks](HOW-ERIE-THINKS.md) — deterministic-first cognition and escalation
- [Cognitive Layers](COGNITIVE-LAYERS.md) — Chronos / ERIE / Scratch Pad
- [API.md](API.md) — API overview
- [FAQ.md](FAQ.md) — common questions
