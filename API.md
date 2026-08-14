# ERIE API Overview

This document describes the public API surface of ERIE at the conceptual level, for adoption and integration planning.

ERIE's implementation is proprietary. The deployed API specification supplied with access is authoritative for an active integration: it defines the endpoints, authentication, serialization, and schemas exactly as deployed.

## Access model

- ERIE is accessed through controlled API access provided by ARCHETRON.
- Credentials are issued with evaluation or commercial arrangements and are personal to the account.
- Do not share credentials. Do not include credentials in source control, logs, or reports.
- See [SECURITY.md](SECURITY.md) for reporting requirements.

## Conceptual surface

### RetrievalRequest

Describes the information an application wants ERIE to locate.

```text
query
limit
filters
```

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

The ordered body of evidence supplied to a reasoning operation. The evidence set defines what a reasoning operation may and may not derive from.

### InferenceRequest

A reasoning request combining a prompt and an EvidenceSet.

```text
prompt
evidence
```

### InferenceResult

The result of a reasoning operation.

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

This example illustrates the public contract, not ERIE's internal implementation.

## Contract guarantees

- **Evidence boundary.** Reasoning may derive from supplied evidence. It may not introduce facts absent from that evidence.
- **Provenance.** Evidence retains source, location, and acquisition context.
- **Contradiction preservation.** Claims may be duplicate, refined, superseded, contradictory, or independent; disagreement is not flattened.
- **Provider independence.** The surface does not depend on a particular model, storage, or retrieval provider.

## Stability boundary

Integrate against the deployed API schemas supplied with access. Do not rely on undocumented fields, behavior, or endpoints; they may change without notice. Documented concepts are designed to remain stable.

## See also

- [QUICKSTART.md](QUICKSTART.md) — first requests end to end
- [INTEGRATION.md](INTEGRATION.md) — fitting ERIE into your architecture
- [EVALUATION.md](EVALUATION.md) — evaluating the contract behaviorally
- [FAQ.md](FAQ.md) — common questions
