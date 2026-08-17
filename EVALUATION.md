# Evaluating ERIE

ERIE is a deterministic, target-centered cognitive engine — the successor to Retrieval-Augmented Generation (RAG).

It is evaluated by behavior, not by how convincing generated prose sounds. The point of evaluation is to test the relationship between evidence and outcome — not to score fluency.

The central evaluation question is:

> **Does the system faithfully represent what the evidence supports?**

## Evaluating investigations

ERIE organizes cognition around investigations. Beyond answer quality, evaluate the investigation itself:

- **State derivation.** Is the investigation's state deterministically derived from its satisfaction criteria? Unknown, partial, ambiguous, resolved, exhausted, and reopened must never be guessed.
- **Criteria satisfaction.** Does an investigation resolve only when all required criteria are satisfied? Does a blocking criterion prevent resolution while unsatisfied?
- **Escalation discipline.** Is semantic reasoning invoked only at the deterministic boundary, never by default? Does the system acquire evidence or ask before escalating?
- **Pressure.** Does pressure drive escalation deterministically, independent of reasoning?
- **Scratch.** Does working cognition stay out of persistent knowledge? Do verified outcomes pass deterministic validation before becoming knowledge?
- **Piggyback seeds.** When semantic reasoning is invoked, does the model receive the complete investigation state rather than starting from scratch?

See [How ERIE Thinks](HOW-ERIE-THINKS.md).

## Evaluation dimensions

### Evidence grounding

Provide a bounded evidence set and ask questions whose answers are fully supported, partially supported, and unsupported. Evaluate whether the output stays within what the supplied evidence permits.

### Unsupported-claim detection

Ask for information that is plausible but absent from the evidence. A grounded system should not convert plausibility into fact.

### Provenance

Inspect whether supporting evidence retains enough provenance to identify its source, location, and acquisition context.

### Evidence isolation

Run the same question against materially different evidence sets. The permissible result should follow the supplied evidence rather than hidden assumptions or unrelated knowledge.

### Contradiction handling

Supply evidence containing disagreement or conflicting observations. Evaluate whether the disagreement remains visible instead of being silently collapsed into a single confident answer.

### Traceability

Inspect whether claims in a result can be associated with the evidence used to support them.

### Repeatability

Repeat equivalent tests under controlled inputs and compare whether evidence selection, claims, and conclusions remain meaningfully consistent.

### Explainability

Evaluate whether a result can be understood: why this evidence was used, what claims were derived, and how the output follows from the evidence.

## Benchmarking ERIE against RAG

When comparing ERIE with another system, use the same source material, questions, and evaluation criteria for both systems.

Useful measurements include:

- supported claims produced
- unsupported claims produced
- claims with identifiable supporting evidence
- preservation of source provenance
- behavior when evidence is insufficient
- behavior when evidence conflicts
- sensitivity to changes in the supplied evidence

A RAG pipeline is scored on the same questions, with the same material. The comparison answers one question:

> Which system most faithfully represents what the evidence supports?

The objective is not to determine which system writes the most persuasive answer.

## Making the evaluation pass or fail on grounding

The single most decisive test: take a set of claims, remove the evidence that supports one of them, and ask again. A grounded system's answer changes. A system that generates over retrieved text may continue asserting the claim regardless.

Repeat the pattern across:

- missing evidence
- conflicting evidence
- revised evidence
- evidence from different sources on the same subject

## What evaluation does not measure

Answer quality alone is not the product. Fluency, apparent confidence, and surface correctness are expected of any modern model. ERIE's value is in what sits underneath the answer: evidence, provenance, traceability, and a testable boundary between supported and unsupported.

## See also

- [QUICKSTART.md](QUICKSTART.md) — running your first evaluation
- [How ERIE Thinks](HOW-ERIE-THINKS.md) — what to verify about escalation
- [Target-Centered Cognition](TARGET-CENTERED-COGNITION.md) — what an investigation is
- [INTEGRATION.md](INTEGRATION.md) — where ERIE fits in your architecture
- [FAQ.md](FAQ.md) — common questions
