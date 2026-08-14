# Evaluating ERIE

ERIE is designed to make evidence-grounded intelligence measurable.

A useful evaluation should test the relationship between evidence and output rather than scoring only fluency or apparent correctness.

## Suggested evaluation dimensions

### Grounding

Provide a bounded evidence set and ask questions whose answers are fully supported, partially supported, and unsupported.

Evaluate whether the output stays within what the supplied evidence permits.

### Unsupported claims

Ask for information that is plausible but absent from the evidence.

A grounded system should not convert plausibility into fact.

### Provenance

Inspect whether supporting evidence retains enough provenance to identify its source, location, and acquisition context.

### Evidence isolation

Run the same question against materially different evidence sets.

The permissible result should follow the supplied evidence rather than hidden assumptions or unrelated knowledge.

### Contradiction

Supply evidence containing disagreement or conflicting observations.

Evaluate whether the disagreement remains visible instead of being silently collapsed into a single confident answer.

### Traceability

Inspect whether claims in a result can be associated with the evidence used to support them.

### Repeatability

Repeat equivalent tests under controlled inputs and compare whether evidence selection, claims, and conclusions remain meaningfully consistent.

## Comparative benchmarking

When comparing ERIE with another system, use the same source material, questions, and evaluation criteria for both systems.

Useful measurements include:

- supported claims produced
- unsupported claims produced
- claims with identifiable supporting evidence
- preservation of source provenance
- behavior when evidence is insufficient
- behavior when evidence conflicts
- sensitivity to changes in the supplied evidence

The objective is not to determine which system writes the most persuasive answer.

The objective is to determine which system most faithfully represents what the evidence supports.
