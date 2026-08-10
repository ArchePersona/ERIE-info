# ERIE Integration Overview

This document describes ERIE from the perspective of an application or evaluator. It intentionally does not document ERIE's proprietary internal implementation.

## Core concepts

### RetrievalRequest

A retrieval request describes the information an application wants ERIE to locate.

Conceptually it contains:

```text
query
limit
filters
```

### EvidenceReference

Every evidence item carries provenance through a reference containing:

```text
source_id
location
acquired_at
```

### Evidence

Evidence combines source material with its provenance reference. Additional metadata may describe acquisition details, but metadata is kept distinct from the evidence itself.

### EvidenceSet

An EvidenceSet is the ordered body of evidence supplied to a reasoning operation.

### InferenceRequest

A reasoning request combines:

```text
prompt
evidence
```

The supplied EvidenceSet establishes the factual boundary for that reasoning operation.

### InferenceResult

A reasoning result conceptually contains:

```text
output
evidence
claims
```

The evidence identifies the material on which the result was grounded. Claims represent assertions derived from that evidence.

## Conceptual usage

```python
request = RetrievalRequest(
    query="What does the available evidence support?",
    limit=10,
)

result = engine.run(request)

for evidence in result.evidence:
    print(evidence.reference.source_id)
    print(evidence.reference.location)

for claim in result.claims:
    print(claim)
```

The exact network API, authentication mechanism, endpoints, and serialized schemas are supplied with API access and should be treated as the authoritative integration specification.

## Stability boundary

Consumers should integrate against documented ERIE interfaces and deployed API schemas rather than relying on implementation details.

ERIE is designed so that underlying storage, retrieval, model, and other providers can evolve without requiring applications to understand ERIE's internals.
