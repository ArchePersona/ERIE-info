# ERIE

> **The Successor to RAG**

Retrieval-Augmented Generation (RAG) solved an important problem: giving language models better context.

ERIE starts where RAG stops.

RAG retrieves documents.

ERIE conducts deterministic investigations.

RAG assembles context.

ERIE constructs understanding.

RAG begins with retrieval.

ERIE begins with purpose.

ERIE is a deterministic, target-centered cognitive engine that organizes cognition around persistent **Targets** rather than transient reasoning episodes. Semantic reasoning is one capability within the engine—not the architecture itself.

---

# The Cognitive Model

```
Intent
    |
    v
Target
    |
    v
Satisfaction Criteria
    |
    v
Deterministic Investigation
    |
    v
State
    |
    v
Semantic Reasoning (only if required)
    |
    v
Resolution
```

### Three Cognitive Layers

- **Chronos** remembers.
- **ERIE** investigates.
- **Scratch** thinks.

Deterministic cognition happens first. Semantic models are invoked only when deterministic investigation reaches its boundary.

---

# What ERIE preserves from RAG

ERIE keeps the part of RAG that worked — grounding answers in real material — and replaces the part that did not: treating retrieved text as the end of cognition.

- **Evidence with provenance.** Every piece of material carries where it came from, where it exists within its source, and when it was acquired.
- **Structured knowledge, not text chunks.** Claims, relationships, events, and contradictions are resolved and preserved — disagreement is not silently flattened into a single confident answer.
- **A testable evidence boundary.** Investigation may derive from supplied evidence. It may not introduce facts absent from that evidence. The constraint is enforceable, not advisory.
- **Explainable results.** Every investigation returns its outcome together with the evidence it was grounded on and the claims derived from it.

RAG finds text. ERIE establishes what the available evidence actually supports — and keeps working until the investigation is satisfied.

# Purposeful investigation

Most AI systems retrieve information.

ERIE investigates.

An investigation in ERIE is not a single question-and-answer exchange. It is a persistent object of cognition with a purpose, satisfaction criteria, a derived state, and a deterministic next action. It continues across reasoning cycles until its criteria are satisfied — or it is deliberately abandoned or archived.

State is never guessed. It is deterministically derived from the satisfaction criteria: unknown, partial, ambiguous, resolved, exhausted, or reopened. Pressure and the next cognitive action follow from that derivation — continue, wait, acquire evidence, ask, invoke semantic reasoning, or resolve.

See [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) and [How ERIE Thinks](HOW-ERIE-THINKS.md).

# The cognitive budget

Reasoning is expensive. Attention is finite.

ERIE does not treat all knowledge equally. Each reasoning cycle receives a finite cognitive budget, allocated deterministically toward the targets that produce the greatest knowledge gain. The unresolved frontier, requested nouns, and evolving knowledge compete for attention — and attention favors work that reduces what is unknown.

# Where ERIE fits

ERIE sits between your knowledge sources and your AI application. It is the intelligence layer that turns raw material into purposeful, evidence-grounded investigation:

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

ERIE is infrastructure, not an application. It is domain-agnostic and provider-independent: it works with any language model, any storage backend, and any retrieval implementation.

## Principles

- Evidence first.
- Reasoning always.
- Deterministic by structure.
- Probabilistic by judgment.

**ERIE answers. Better.**

# Status

ERIE v1.0.2 is platform complete and currently verified at **4,843 automated tests** across **307 source files** — ruff clean, mypy strict, pytest passing.

The architecture has matured through two complementary subsystems:

- **Chronos v1** — persistent knowledge (world model, ontology, noun and event ledgers, evidence, provenance, evolution, materialization, placeholders, cognitive processors).
- **ERIE 001-004** — purposeful investigation (finite cognitive attention, target-centered cognition, first-class satisfaction criteria, the cognitive Scratch workspace).

See [ROADMAP.md](ROADMAP.md) for direction.

# Documentation

- [QUICKSTART.md](QUICKSTART.md) — from access to your first investigation
- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — the organizing principle
- [How ERIE Thinks](HOW-ERIE-THINKS.md) — deterministic-first cognition and escalation
- [Cognitive Layers](COGNITIVE-LAYERS.md) — Chronos / ERIE / Scratch
- [INTEGRATION.md](INTEGRATION.md) — fitting ERIE into your architecture
- [API.md](API.md) — the public API overview
- [EVALUATION.md](EVALUATION.md) — how to evaluate ERIE
- [FAQ.md](FAQ.md) — frequently asked questions
- [ROADMAP.md](ROADMAP.md) — product direction

Historical engineering documentation remains available under [archive/](archive/README.md) for reference.

# Obtaining access

ERIE is closed-source proprietary software. Evaluation access and commercial licensing are provided through controlled API access from VOLSHi.

API credentials, endpoint-specific documentation, and current request/response schemas are supplied with access, so evaluators work against the deployed interface rather than documentation that may drift from it.

# Relationship to ARCHETRON

ERIE is a technology within ARCHETRON, the technology ecosystem built by VOLSHi. ERIE's responsibility within the ecosystem is evidence, structured knowledge, and evidence-grounded investigation.

# Repository policy

This repository contains public ERIE product information and documentation. It does not contain ERIE's proprietary implementation.

- [License](LICENSE.md)
- [Security Policy](SECURITY.md)
- [Contribution Policy](CONTRIBUTING.md)
