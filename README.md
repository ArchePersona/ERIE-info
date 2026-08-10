# ERIE

**Epistemic Reasoning & Investigation Engine**

ERIE is an evidence-first intelligence engine for applications that need answers they can inspect, trace, and defend.

Most AI systems are very good at producing an answer. ERIE is concerned with the harder question:

> **What does the available evidence actually support?**

ERIE organizes disconnected information into evidence with provenance, then provides a reasoning surface designed to keep conclusions grounded in that evidence.

**Evidence first. Reasoning second. Generation last.**

## What ERIE does

ERIE gives applications a reusable evidence and reasoning foundation.

It is designed to preserve the context that ordinary retrieval can lose:

- where information came from
- where it existed within its source
- when it was acquired
- which evidence supports a result
- which claims were derived from that evidence

ERIE is not a chatbot, search product, or domain-specific application. It is infrastructure that other applications can build on.

SHERLOCK, for example, is an investigation application built on ERIE. ERIE itself remains domain-agnostic.

## External model

From an integrating application's perspective, ERIE is deliberately simple:

```text
Question / Retrieval Request
            |
            v
     Relevant Evidence
            |
            v
   Evidence-Grounded Reasoning
            |
            v
 Grounded Result + Supporting Evidence + Claims
```

The implementation behind that surface is proprietary. Consumers interact with ERIE through defined interfaces rather than depending on its internal implementation.

## Evidence

Evidence is the fundamental unit ERIE reasons over.

An evidence record contains the source material together with a stable reference describing its provenance. A reference identifies:

- `source_id` — the originating source
- `location` — where the evidence exists within that source
- `acquired_at` — when it was acquired

Metadata may accompany evidence, but metadata is not silently promoted into evidence.

Evidence used for a reasoning operation is supplied as an ordered `EvidenceSet`, keeping the material supporting a result explicit and inspectable.

## Reasoning

ERIE's reasoning contract accepts a prompt together with an evidence set.

The result contains:

- the produced output
- the evidence on which the output was grounded
- the supported claims derived from that evidence

The governing constraint is straightforward:

> **Reasoning may derive from supplied evidence. It may not introduce facts absent from that evidence.**

This makes the evidence boundary testable rather than merely advisory.

## Retrieval

ERIE can accept a retrieval request containing:

- a query
- a result limit
- optional filters

Retrieval returns candidate evidence with provenance. Retrieval finds evidence; it does not decide what that evidence means.

## Integration surface

ERIE is designed as a provider-independent engine. Applications consume a stable engine surface rather than coupling themselves to a particular model, database, or retrieval implementation.

A typical interaction is conceptually:

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

This example illustrates the public contract rather than ERIE's internal implementation.

## Evaluating ERIE

ERIE is intended to be evaluated by behavior, not by how convincing generated prose sounds.

Useful tests include:

**Grounding** — Does the result remain within the supplied evidence?

**Unsupported claims** — Does the system introduce facts that cannot be traced to the evidence set?

**Provenance** — Can supporting information be traced back to its source and location?

**Evidence isolation** — Does changing the supplied evidence change the permissible conclusions accordingly?

**Traceability** — Can claims be connected to the evidence from which they were derived?

**Provider independence** — Can underlying providers change without changing the application's conceptual contract with ERIE?

These properties make ERIE suitable for comparative benchmarking against other evidence, retrieval, and reasoning systems.

## API access

ERIE is closed-source proprietary software. The implementation repository is not public.

Evaluation and commercial integration are provided through controlled API access. API credentials, endpoint-specific documentation, and current request/response schemas are supplied with access so that evaluators work against the deployed interface rather than documentation that may drift from it.

## Relationship to ARCHETRON

ERIE is one component of ARCHETRON. Its responsibility is evidence and evidence-grounded reasoning. Other components handle concerns such as execution observation, operational telemetry, governance, attention, and application-specific behavior.

Those responsibilities are intentionally separate.

## Status

ERIE is under active development. Public documentation describes the supported external concepts and behavioral guarantees without exposing proprietary implementation details.

## Licensing

ERIE is proprietary software. All rights reserved. Commercial licensing and evaluation access are available directly from ARCHETRON.
