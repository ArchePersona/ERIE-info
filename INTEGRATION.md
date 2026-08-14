# Integrating ERIE

This document explains how ERIE fits into an existing AI architecture.

ERIE is an evidence-first reasoning engine that replaces traditional Retrieval-Augmented Generation (RAG). It is the intelligence layer between enterprise knowledge and AI generation.

```text
Enterprise Knowledge
        |
        v
      ERIE
        |
Evidence . Claims . Context
        |
        v
 Any Language Model
        |
        v
 Better Answers
```

ERIE does not replace your application, your language model, or your knowledge sources. It replaces the retrieval layer between them.

## Replacing the retrieval layer

In a typical RAG architecture:

```text
Query -> Retriever -> Text chunks -> Prompt -> LLM -> Answer
```

With ERIE:

```text
Query -> ERIE -> Evidence . Claims . Context -> Prompt -> LLM -> Answer + Evidence + Claims
```

The difference is what the language model reasons over:

- RAG feeds the model retrieved text chunks, with no structure and no provenance.
- ERIE feeds the model evidence with provenance, resolved claims, relationships, and context — and returns the answer together with the evidence and claims that support it.

Your language model stays the same. The material it reasons over changes.

## Evidence-grounded context

ERIE's reasoning contract accepts a prompt together with an EvidenceSet — an ordered body of evidence.

The governing constraint is straightforward:

> **Reasoning may derive from supplied evidence. It may not introduce facts absent from that evidence.**

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

Applications interact with ERIE through defined interfaces:

- `RetrievalRequest` — a query, a result limit, and optional filters; returns candidate evidence with provenance
- `EvidenceSet` — the ordered body of evidence supplied to a reasoning operation
- `InferenceRequest` — a prompt together with an EvidenceSet, establishing the factual boundary for the operation
- `InferenceResult` — the output, the evidence it was grounded on, and the derived claims

```python
request = RetrievalRequest(
    query="What does the available evidence support?",
    limit=10,
)

result = engine.run(request)

print(result.output)
print(result.evidence)
print(result.claims)
```

The exact network API, authentication mechanism, endpoints, and serialized schemas are supplied with API access and are authoritative for an active integration.

## Stability boundary

Integrate against documented ERIE interfaces and the deployed API schemas supplied with access — never against implementation details.

ERIE is designed so that underlying storage, retrieval, and model providers can evolve without requiring applications to change. The implementation behind the public surface is proprietary.

## Evaluation before integration

Before committing to an integration, evaluate ERIE on your own evidence: [EVALUATION.md](EVALUATION.md).

## See also

- [QUICKSTART.md](QUICKSTART.md) — from access to first result
- [API.md](API.md) — API overview
- [FAQ.md](FAQ.md) — common questions
