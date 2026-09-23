# TLA architecture overview

The current TLA reference architecture is centered on two design patterns and three organizational memories.

## Two design patterns

- **AER — Adaptive Evidence Routing:** route a decision toward the least costly reliable evidence source that is proportionate to uncertainty, risk and reversibility.
- **CAER — Context-Aware Experience Reuse:** before reusing prior experience, compare source and target contexts and choose **Reuse**, **Adapt** or **Re-experiment**.

## Three memories

- **Evidence Memory** — original documents, data and measurements.
- **Compiled Knowledge Memory** — versioned syntheses and structured knowledge linked back to evidence.
- **Experiential Memory** — structured records of interventions and observed outcomes.

## Architecture

\`\`\`mermaid
flowchart LR
 P[Problem / decision] --> AER[AER]
 AER --> E[Evidence Memory]
 AER --> K[Compiled Knowledge]
 AER --> H[Human Expertise]
 AER --> R[Tool-assisted Reasoning]
 AER --> X{Comparable experience?}
 X --> CAER[CAER]
 CAER --> U[Reuse]
 CAER --> A[Adapt]
 CAER --> RE[Re-experiment]
 AER --> M[Micro-experiment]
 U --> D[Decision / action]
 A --> D
 RE --> M
 M --> D
 D --> EM[Experiential Memory]
\`\`\`

The complete current paper is [docs/TLA.md](../docs/TLA.md).
