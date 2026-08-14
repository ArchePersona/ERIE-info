# ERIE

**Epistemic Reasoning & Investigation Engine**

**ERIE answers. Better.**

ERIE is an evidence-first reasoning engine that replaces traditional Retrieval-Augmented Generation (RAG).

---

## The problem

Modern AI systems are very good at producing confident language.

The problem is not the quality of the prose. The problem is what sits underneath it.

When an application answers from retrieved text, the answer is only as trustworthy as the retrieval that fed it — and retrieval is lossy. It loses where information came from. It loses when it was true. It loses how pieces of information relate, conflict, or supersede one another. Most importantly, it loses the boundary between what the evidence actually supports and what the model simply generated.

The result is an answer that sounds right and cannot be defended.

ERIE exists to close that gap.

## Why ERIE

Most AI systems retrieve information.

ERIE investigates.

ERIE organizes disconnected enterprise knowledge into evidence with provenance, resolves that evidence into structured knowledge, and reasons over it — so every answer can be walked back to the evidence and sources that produced it.

That makes ERIE's answers inspectable, traceable, and defensible.

## How ERIE is different from RAG

Traditional RAG retrieves similar text, stuffs it into a prompt, and generates.

ERIE replaces that retrieval layer with structured, evidence-first reasoning:

- **Evidence with provenance.** Every piece of material carries where it came from, where it exists within its source, and when it was acquired.
- **Structured knowledge, not text chunks.** Claims, relationships, and contradictions are resolved and preserved — disagreement is not silently flattened into a single confident answer.
- **A testable evidence boundary.** Reasoning may derive from supplied evidence. It may not introduce facts absent from that evidence. The constraint is enforceable, not advisory.
- **Explainable results.** Every result returns the output, the evidence it was grounded on, and the claims derived from it.

RAG finds text. ERIE establishes what the available evidence actually supports.

## The product narrative

ERIE is the intelligence layer between enterprise knowledge and AI generation:

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

ERIE is provider-independent. It does not replace your language model — it makes any language model answer better, because the model reasons over structured, provenance-bound evidence instead of retrieved text.

## Where ERIE fits

ERIE sits between your knowledge sources and your AI application, replacing the traditional retrieval layer:

```text
Sources -> ERIE -> Evidence . Claims . Context -> Your LLM -> Defensible answers
```

ERIE is infrastructure, not an application. It is domain-agnostic and designed to be embedded into applications that need answers they can inspect, trace, and defend.

## Principles

- Evidence first.
- Reasoning always.
- Deterministic by structure.
- Probabilistic by judgment.

**ERIE answers. Better.**

## Evaluating ERIE

ERIE is evaluated by behavior, not by how convincing generated prose sounds.

Useful tests include evidence grounding, unsupported-claim detection, provenance preservation, evidence isolation, contradiction handling, traceability, repeatability, and explainability.

The central evaluation question is simple:

> **Does the system faithfully represent what the evidence supports?**

See [EVALUATION.md](EVALUATION.md) for the full evaluation framework, including how to benchmark ERIE against a RAG pipeline.

## Quick start

1. Request evaluation access through the repository owner or ARCHETRON.
2. Receive your credentials, endpoint specification, and request/response schemas.
3. Send your first retrieval and reasoning requests.
4. Inspect the results: output, supporting evidence, and claims.
5. Run the evaluation suite from [EVALUATION.md](EVALUATION.md).

See [QUICKSTART.md](QUICKSTART.md) for step-by-step guidance.

## Documentation

- [QUICKSTART.md](QUICKSTART.md) — from access to first grounded result
- [INTEGRATION.md](INTEGRATION.md) — how ERIE fits into an existing AI architecture
- [EVALUATION.md](EVALUATION.md) — how to evaluate ERIE against RAG
- [API.md](API.md) — the public API overview
- [FAQ.md](FAQ.md) — frequently asked questions
- [ROADMAP.md](ROADMAP.md) — product direction

Historical engineering documentation remains available under [archive/](archive/README.md) for reference.

## Obtaining access

ERIE is closed-source proprietary software. Evaluation access and commercial licensing are provided through controlled API access from ARCHETRON.

API credentials, endpoint-specific documentation, and current request/response schemas are supplied with access, so evaluators work against the deployed interface rather than documentation that may drift from it.

## Repository policy

This repository contains public ERIE product information and documentation. It does not contain ERIE's proprietary implementation.

- [License](LICENSE.md)
- [Security Policy](SECURITY.md)
- [Contribution Policy](CONTRIBUTING.md)
