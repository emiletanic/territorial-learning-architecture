# Adaptive Evidence Routing (AER)

AER is a TLA design pattern for deciding **how much additional evidence a decision actually needs and which evidence route should be used next**.

## Reference routing policy

A deliberately simple starting policy is:

1. If available knowledge is sufficient relative to risk and reversibility, decide and record the justification.
2. If comparable prior experience exists, invoke CAER before reusing it.
3. If recent and traceable compiled knowledge is sufficient, use it.
4. If a precise or recent fact is missing, query Evidence Memory through RAG or equivalent search.
5. If hypotheses still need comparison, invoke more costly reasoning or tools.
6. If the uncertainty depends on specialist expertise or institutional judgment, escalate to the appropriate human actor.
7. If the required information does not yet exist, design a bounded micro-experiment.
8. Stop when additional information is no longer likely to change the decision enough to justify its cost or delay.

## Design principle

AER is useful only if the cost of routing remains lower than the resources it saves. Trivial or already well-documented decisions should be able to bypass most of the mechanism.

## Open implementation questions

- How should uncertainty be estimated in different domains?
- What constitutes "sufficient" evidence?
- How should risk and reversibility affect routing?
- How can calibrated confidence, abstention and verification mechanisms contribute?
- When is routing overhead too expensive?

AER is intentionally not specified as a single optimal algorithm. The repository welcomes alternative routing policies and comparative implementations.
