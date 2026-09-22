# TLA evaluation framework

TLA is currently a research and design framework. Its claims must therefore be evaluated empirically rather than assumed.

## Evaluation question

The central empirical question is:

**Does TLA help a territorial problem-solving system learn faster, more transparently and more cumulatively than a conventional AI-assisted or study-to-programme process?**

## Suggested comparison

A first proof of concept should select one bounded territorial problem and compare:

- a conventional AI-assisted approach that seeks recommendations directly; and
- a TLA workflow that explicitly identifies uncertainty, designs bounded evidence-generating actions, records provenance and accumulates capabilities.

## Core metrics

### 1. Problem-to-experiment time

Time required to transform an initially broad problem into a legitimate, testable intervention.

[
T_{PE}=t_{experiment}-t_{problem}
]

### 2. Decision-critical uncertainty reduction

For each uncertainty (u_i), record decision relevance and evidential support before and after the learning cycle.

The metric should not assume that every uncertainty is probabilistic. Qualitative and ordinal scales may be appropriate for implementation, behavioural, legal or value uncertainty.

### 3. Provenance completeness

Proportion of consequential claims and decisions for which sources, assumptions, AI systems, human validations and experiment outcomes can be reconstructed.

### 4. Capability reuse

[
ReuseRate = \frac{reused\ validated\ components}{available\ validated\ components}
]

Reusable components may include datasets, workflows, models, protocols, expert networks, APIs and monitoring methods.

### 5. Reproduction rate

Share of solutions that retain acceptable performance and public value when transferred to another team, organization or context under specified conditions.

### 6. Cost of failed exploration

Resources committed to unsuccessful hypotheses before they are rejected or revised. TLA predicts that bounded micro-experiments can reduce this cost relative to premature full-scale deployment.

### 7. Human-governance integrity

Whether objectives, risk thresholds, authorization and scaling decisions remain under explicitly assigned human authority.

## Falsifiable propositions

- **P1:** A problem-first architecture can reduce time from ambiguous problem to testable intervention in high-uncertainty contexts.
- **P2:** Explicit uncertainty representation reduces premature convergence on a single AI-generated recommendation.
- **P3:** Bounded experiments reduce the expected cost of unsuccessful innovation.
- **P4:** Decision provenance improves reconstructability even when the underlying AI models are not fully interpretable.
- **P5:** Capability memory increases reuse across successive territorial problems.
- **P6:** AI-supported task decomposition and expert matching reduce coordination cost for distributed expertise.
- **P7:** Across repeated cycles, system-level improvement increasingly comes from accumulated organizational capability, not only from improvements in individual AI models.

## Status

These propositions are research hypotheses. The repository will distinguish clearly between architectural claims, illustrative examples and empirically validated results.
