# ERIE FAQ

## What is ERIE?

ERIE is the **Epistemic Reasoning & Investigation Engine** — an evidence-first reasoning engine that replaces traditional Retrieval-Augmented Generation (RAG). It organizes enterprise knowledge into evidence with provenance, resolves that evidence into structured knowledge, and reasons over it so answers can be inspected, traced, and defended.

**ERIE answers. Better.**

## Why does ERIE exist?

Because retrieved text is not evidence. Traditional AI systems are good at producing confident language, but the answer is only as trustworthy as the retrieval that fed it. ERIE exists to close the gap between what an answer sounds like and what the available evidence actually supports.

## How is ERIE different from RAG?

RAG retrieves similar text, stuffs it into a prompt, and generates. ERIE replaces the retrieval layer with structured, evidence-first reasoning: evidence with provenance, resolved claims and relationships, preserved contradictions, a testable evidence boundary, and results that return the output together with the evidence and claims that support it.

See [EVALUATION.md](EVALUATION.md) for how to measure the difference.

## Does ERIE replace my language model?

No. ERIE is provider-independent and works with any language model. It feeds the model structured, provenance-bound evidence instead of retrieved text — the model produces better, defensible answers.

## Does ERIE replace my application?

No. ERIE is infrastructure. It sits between your knowledge sources and your AI application, replacing the retrieval layer. Applications consume ERIE through its public API.

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
- [INTEGRATION.md](INTEGRATION.md)
- [EVALUATION.md](EVALUATION.md)
- [API.md](API.md)
- [ROADMAP.md](ROADMAP.md)
