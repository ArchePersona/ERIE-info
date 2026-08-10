# ERIE

**Epistemic Reasoning & Investigation Engine**

ERIE is an evidence-first intelligence engine for applications that need answers they can inspect, trace, and defend.

Most AI systems are very good at producing an answer. ERIE is concerned with the harder question:

> **What does the available evidence actually support?**

ERIE organizes disconnected information into evidence with provenance, resolves that information into structured knowledge, and provides a reasoning surface designed to keep conclusions grounded in the available evidence.

**Evidence first. Reasoning second. Generation last.**

## Overview

ERIE gives applications a reusable evidence and reasoning foundation while preserving context that ordinary retrieval can lose:

- where information came from
- where it existed within its source
- when it was acquired
- which evidence supports or conflicts with a claim
- which claims were derived from that evidence
- how claims relate, contradict, refine, duplicate, or supersede one another

ERIE is not a chatbot, search product, or domain-specific application. It is infrastructure that other applications can build on.

SHERLOCK, for example, is an investigation application built on ERIE. ERIE itself remains domain-agnostic.

## External model

From an integrating application's perspective, ERIE separates retrieval, evidence, knowledge, and reasoning:

```text
Sources
   |
   v
Evidence + Provenance
   |
   v
Structured Knowledge
   |
   +---- claims
   +---- relationships
   +---- contradictions
   +---- provenance
   |
   v
Evidence-Grounded Reasoning
   |
   v
Grounded Result + Supporting Evidence + Claims
```

The implementation behind that surface is proprietary. Consumers interact with ERIE through defined interfaces rather than depending on internal implementation details.

## Evidence

Evidence is the factual boundary ERIE reasons against.

An evidence record contains source material together with a stable reference describing its provenance. A reference identifies:

- `source_id` — the originating source
- `location` — where the evidence exists within that source
- `acquired_at` — when it was acquired

Metadata may accompany evidence, but metadata is not silently promoted into evidence.

Evidence used for a reasoning operation is supplied as an ordered `EvidenceSet`, keeping the material supporting a result explicit and inspectable.

## Knowledge

ERIE can transform evidence into structured knowledge rather than treating retrieved documents as the final reasoning substrate.

Conceptually, that process can include artifact analysis, claim extraction, claim resolution, relationship discovery, provenance association, and decision recording.

Claim resolution is designed to preserve meaningful distinctions such as duplicate, refined, superseded, contradictory, and independent claims instead of silently flattening disagreement.

The result is a knowledge layer whose claims and relationships remain connected to their evidence and provenance.

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

See the [Integration Overview](docs/INTEGRATION.md) for the public conceptual interface.

## Evaluating ERIE

ERIE is intended to be evaluated by behavior, not by how convincing generated prose sounds.

Useful tests include grounding, unsupported-claim detection, provenance preservation, evidence isolation, contradiction handling, traceability, repeatability, and provider independence.

The central evaluation question is simple:

> **Does the system faithfully represent what the evidence supports?**

See [Evaluating ERIE](docs/EVALUATION.md) for a comparative evaluation framework.

## API access

ERIE is closed-source proprietary software. The implementation repository is not public.

Evaluation and commercial integration are provided through controlled API access. API credentials, endpoint-specific documentation, and current request/response schemas are supplied with access so evaluators work against the deployed interface rather than documentation that may drift from it.

## Documentation

Public documentation is indexed in [`docs/`](docs/README.md).

These documents describe ERIE's supported external concepts and behavioral boundaries. The deployed API specification supplied with access is authoritative for an active integration.

## Relationship to ARCHETRON

ERIE is one component of ARCHETRON. Its responsibility is evidence, structured knowledge, and evidence-grounded reasoning. Other components handle concerns such as execution observation, operational telemetry, governance, attention, and application-specific behavior.

Those responsibilities are intentionally separate.

## Repository policy

This repository contains public ERIE information and documentation. It does not contain ERIE's proprietary implementation.

- [License](LICENSE)
- [Security Policy](SECURITY.md)
- [Contribution Policy](CONTRIBUTING.md)

## Status

ERIE is under active development. Public documentation describes supported external concepts and behavioral guarantees without exposing proprietary implementation details.

## Licensing

ERIE is proprietary software. Publication of this repository does not grant a license to ERIE software, source code, APIs, models, or other proprietary technology.

Evaluation access and commercial licensing are available directly from ARCHETRON. See [LICENSE](LICENSE) for the terms governing the materials in this repository.
