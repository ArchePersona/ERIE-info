# ERIE Quick Start

This guide takes you from requesting access to your first grounded result. It is written for adoption, not architecture.

## Prerequisites

- An AI application that currently uses a language model
- Knowledge sources your application answers from
- A desire for answers that can be inspected, traced, and defended

You do not need to change your language model. ERIE works with any model provider.

## Step 1 — Request access

ERIE is closed-source proprietary software. Access is provided through controlled evaluation and commercial arrangements with ARCHETRON.

Contact the repository owner to request evaluation access.

## Step 2 — Receive your access package

With access you receive:

- API credentials
- Endpoint documentation
- Current request/response schemas
- Access terms

These materials are authoritative for your integration. Documentation in this repository describes ERIE's public concepts; the deployed API specification governs the running service.

## Step 3 — Make your first retrieval request

Retrieval finds candidate evidence with provenance. Conceptually:

```python
request = RetrievalRequest(
    query="What does the available evidence support?",
    limit=10,
)

result = engine.run(request)

for evidence in result.evidence:
    print(evidence.reference.source_id)
    print(evidence.reference.location)
```

The exact request shape, authentication, and endpoint are defined by the API specification supplied with your access.

## Step 4 — Make your first reasoning request

Reasoning accepts a prompt together with an ordered body of evidence — an EvidenceSet — and returns a result that contains the output, the evidence it was grounded on, and the claims derived from that evidence:

```python
request = InferenceRequest(
    prompt="Summarize what the evidence supports about the incident.",
    evidence=evidence_set,
)

result = engine.run(request)

print(result.output)
print(result.evidence)
print(result.claims)
```

The governing constraint: reasoning may derive from supplied evidence. It may not introduce facts absent from that evidence.

## Step 5 — Inspect the result

A grounded result is inspectable:

- `output` — the produced answer
- `evidence` — the material the answer was grounded on, with provenance
- `claims` — the assertions derived from that evidence

Every claim should be traceable back to supporting evidence. If it is not, treat that as a defect.

## Step 6 — Evaluate before you integrate

Before wiring ERIE into production, run the evaluation suite in [EVALUATION.md](EVALUATION.md): grounding, unsupported-claim detection, provenance preservation, evidence isolation, contradiction handling, traceability, and repeatability.

## Step 7 — Integrate

Once evaluation passes, see [INTEGRATION.md](INTEGRATION.md) for how ERIE replaces the retrieval layer in your existing architecture, and [API.md](API.md) for the public API surface.

## What's next

- [INTEGRATION.md](INTEGRATION.md) — fitting ERIE into your architecture
- [EVALUATION.md](EVALUATION.md) — evaluating ERIE against RAG
- [API.md](API.md) — API overview
- [FAQ.md](FAQ.md) — common questions
