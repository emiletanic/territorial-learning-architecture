# TLA evaluation framework

TLA is currently an open research architecture. Evaluation should focus on whether its design patterns improve bounded decision workflows rather than presuming system-level superiority.

## Minimal comparison

A first benchmark can compare:

1. a uniform RAG + LLM workflow;
2. a workflow with compiled knowledge;
3. a TLA-style workflow using AER and CAER.

## Candidate measures

- decision latency;
- token or compute cost;
- human effort;
- source traceability;
- unnecessary escalations avoided;
- unnecessary experiments avoided;
- quality of contextual reuse decisions;
- decision quality judged by blinded reviewers where feasible.

## Important constraint

AER routing overhead must be measured. A routing mechanism that costs as much as the work it avoids defeats its purpose.

See [research/open_questions.md](../research/open_questions.md) for the current research agenda.
