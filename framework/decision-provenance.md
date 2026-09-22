# Decision provenance in TLA

## Operational justifiability

TLA distinguishes **mechanistic interpretability** from **operational justifiability**.

Mechanistic interpretability concerns the internal computational mechanisms by which an AI model produces an output. For contemporary foundation models, complete mechanistic understanding may be unavailable to operators and may not be a realistic requirement for every supporting use.

Operational justifiability asks a different question: **can the institution reconstruct why it relied on a recommendation and challenge the path that led to the decision?**

TLA therefore treats provenance as a first-class system requirement.

## Minimum provenance record

For a consequential AI-assisted decision, the record should preserve, where applicable:

1. the original problem statement;
2. the public objective and decision owner;
3. the data and documentary sources used;
4. the assumptions made;
5. the uncertainties identified;
6. alternative hypotheses or options considered;
7. the AI systems, model versions and relevant configurations used;
8. significant prompts, transformations or analytical steps where preservation is proportionate;
9. human interventions and validations;
10. experiments authorized and their safeguards;
11. observed outcomes;
12. residual uncertainty;
13. the reason for the final institutional decision;
14. any conditions for review, expiration, reproduction or scale-up.

## Principle

TLA does not claim that provenance makes an opaque model internally transparent. It makes the **decision process reconstructable**, and therefore more auditable, contestable and learnable.
