# ERIE FAQ

## What is ERIE?

ERIE is the **Epistemic Reasoning & Investigation Engine** — a deterministic, target-centered cognitive engine and the successor to Retrieval-Augmented Generation (RAG). It organizes cognition around persistent Targets rather than transient reasoning episodes: an investigation has intent, satisfaction criteria, a derived state, pressure, and a deterministic next action.

**ERIE answers. Better.**

## Why does ERIE exist?

Because retrieved text is not evidence — and answering a prompt is not the same as satisfying an investigation. Traditional AI systems are good at producing confident language, but the answer is only as trustworthy as the retrieval that fed it. ERIE exists to close the gap between what an answer sounds like and what the available evidence actually supports — and to keep working until the investigation is satisfied.

## How is ERIE different from RAG?

RAG was the previous evolutionary step: it gave language models better context. ERIE is the successor. RAG retrieves documents and generates; ERIE conducts deterministic investigations. RAG assembles context; ERIE constructs understanding. RAG begins with retrieval; ERIE begins with purpose.

ERIE keeps the part of RAG that worked — grounding answers in real material — and replaces the part that did not: treating retrieved text as the end of cognition.

See [EVALUATION.md](EVALUATION.md) for how to measure the difference.

## What is target-centered cognition?

ERIE organizes cognition around Targets, not reasoning. A Target is a persistent object of cognition with intent, satisfaction criteria, a derived state, pressure, and a next cognitive action. Reasoning is one capability used to advance a Target — it is not the organizing principle of the engine. See [TARGET-CENTERED-COGNITION.md](TARGET-CENTERED-COGNITION.md).

## Does ERIE replace my language model?

No. ERIE is provider-independent and works with any language model. The model is never the default reasoning engine: ERIE evaluates deterministically first and consults the model only when deterministic investigation reaches its boundary.

## What are the three cognitive layers?

Chronos remembers, ERIE investigates, and the Scratch Pad thinks. Chronos is persistent knowledge; ERIE is purposeful investigation; the Scratch Pad is temporary working cognition. Nothing moves directly from speculation into persistent knowledge — every outcome must pass deterministic validation. See [COGNITIVE-LAYERS.md](COGNITIVE-LAYERS.md).

## Does ERIE replace my application?

No. ERIE is infrastructure. It sits between your knowledge sources and your AI application, superseding the retrieval layer. Applications consume ERIE through its public API.

## Is ERIE open source?

No. ERIE is closed-source proprietary software. This repository contains public product documentation only — no implementation, no source code, no private APIs.

## How do I obtain access?

Evaluation and commercial access are provided through controlled API access from ARCHETRON. Contact the repository owner to request access. Credentials, endpoint documentation, and current schemas are supplied with access.

## What does access include?

API credentials, endpoint-specific documentation, current request/response schemas, and access terms. The deployed API specification is authoritative for an active integration.

## Can ERIE invent facts?

No. ERIE's governing constraint is that reasoning may derive from supplied evidence but may not introduce facts absent from that evidence. The evidence boundary is testable.

## Which providers are supported?

ERIE is provider-independent. Model, storage, and retrieval providers can change without changing the integration.

## How do I evaluate ERIE before adopting it?

Run the evaluation suite in [EVALUATION.md](EVALUATION.md): grounding, unsupported-claim detection, provenance preservation, evidence isolation, contradiction handling, traceability, repeatability, and explainability — on your own evidence.

## How do I report a bug or a vulnerability?

This repository is documentation only. For documentation corrections, see [CONTRIBUTING.md](CONTRIBUTING.md). For security issues, follow [SECURITY.md](SECURITY.md) and report privately.

## Where is the historical documentation?

Historical engineering documentation is archived under [archive/](archive/README.md) and remains accessible for reference.

## See also

- [QUICKSTART.md](QUICKSTART.md)
- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md)
- [How ERIE Thinks](HOW-ERIE-THINKS.md)
- [Cognitive Layers](COGNITIVE-LAYERS.md)
- [INTEGRATION.md](INTEGRATION.md)
- [EVALUATION.md](EVALUATION.md)
- [API.md](API.md)
- [ROADMAP.md](ROADMAP.md)
