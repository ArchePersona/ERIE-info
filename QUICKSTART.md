# ERIE Quick Start

This guide takes you from requesting access to your first investigation. It is written for adoption, not architecture.

## Prerequisites

- An AI application that currently uses a language model
- Knowledge sources your application investigates
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

## Step 3 — Define the investigation

An ERIE call is an investigation, not a question. An investigation begins with an intent and satisfaction criteria:

```python
target = Intent("resolve employment", kind="resolve")
target.add_criterion("employer identified", kind="identity", required=True)
target.add_criterion("evidence confirmed", kind="evidence", required=True)
```

Criteria define what it means for the investigation to be satisfied. Without criteria, "Resolved" has no meaning.

See [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md).

## Step 4 — Evaluate deterministically first

ERIE evaluates the criteria deterministically before anything else:

```python
state = target.evaluate()
```

The state is derived, never guessed: unknown, partial, ambiguous, resolved, exhausted, or reopened. From the state and pressure, ERIE chooses the next cognitive action deterministically — continue, wait, acquire evidence, ask, invoke semantic reasoning, or resolve.

## Step 5 — Escalate only at the boundary

Semantic reasoning is invoked only when deterministic investigation reaches its boundary — and only as a policy decision, never by default. When it is invoked, the model receives the complete investigation state through a Piggyback Seed: the target, its criteria, satisfied and unsatisfied criteria, missing evidence, state, pressure, the requested operation, and the current scratch workspace.

The model does not start from scratch. It joins an existing investigation.

See [How ERIE Thinks](HOW-ERIE-THINKS.md).

## Step 6 — Inspect the outcome

A grounded outcome is inspectable:

- the produced result
- the evidence it was grounded on, with provenance
- the claims derived from that evidence

Every claim should be traceable back to supporting evidence. If it is not, treat that as a defect.

## Step 7 — Evaluate before you integrate

Before wiring ERIE into production, run the evaluation suite in [EVALUATION.md](EVALUATION.md): grounding, unsupported-claim detection, provenance preservation, evidence isolation, contradiction handling, traceability, repeatability, and explainability — on your own evidence.

## Step 8 — Integrate

Once evaluation passes, see [INTEGRATION.md](INTEGRATION.md) for how ERIE fits into your existing architecture, and [API.md](API.md) for the public API surface.

## What's next

- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — the organizing principle
- [How ERIE Thinks](HOW-ERIE-THINKS.md) — deterministic-first cognition and escalation
- [Cognitive Layers](COGNITIVE-LAYERS.md) — Chronos / ERIE / Scratch
- [INTEGRATION.md](INTEGRATION.md) — fitting ERIE into your architecture
- [EVALUATION.md](EVALUATION.md) — evaluating ERIE
- [API.md](API.md) — API overview
- [FAQ.md](FAQ.md) — common questions
