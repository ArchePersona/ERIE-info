# ERIE Roadmap

ERIE is an evidence-first reasoning engine that replaces traditional Retrieval-Augmented Generation (RAG).

## Current status

ERIE v1.0.2 is platform complete. The engine, runtime, and platform are implemented and verified; public application interfaces and reference adapters are in place.

ERIE is under active development, and public documentation describes supported external concepts and behavioral guarantees without exposing proprietary implementation details.

## Direction

Development is application-driven: ERIE evolves when a consuming application identifies a genuine platform capability gap, not through speculative framework expansion.

Expected work includes:

- evaluation access expansion for new adopters
- integration documentation driven by real integrations
- additional reference adapters
- consumer-driven platform capabilities
- performance improvements and bug fixes

No architectural redesign is planned.

## Stability commitment

- Public interfaces are stable. Integrations are made against documented interfaces and deployed API schemas.
- Bug fixes, contract repairs, and performance improvements do not break existing integrations.
- Breaking changes are reserved for deliberate major releases and are not currently planned.

## How to influence the roadmap

ERIE evolves through demonstrated consumer need. Evaluation access is the primary channel: run the evaluation suite in [EVALUATION.md](EVALUATION.md) on your own evidence, and route integration requests to the repository owner.

## See also

- [README.md](README.md)
- [QUICKSTART.md](QUICKSTART.md)
- [INTEGRATION.md](INTEGRATION.md)
- [FAQ.md](FAQ.md)
