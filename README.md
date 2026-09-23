# TLA — Territorial Learning Architecture

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22923636.svg)](https://doi.org/10.5281/zenodo.22923636)

### An open research architecture for AI-assisted territorial learning

> **A learning territory should know what it has already learned, recognize what it does not know, choose how to learn it, and reuse experience without erasing contextual differences.**

TLA is a socio-technical architecture for AI-assisted territorial governance and problem solving. It originated in the *Martinique Territoire Intelligent* work and is now proposed as an open research architecture that can be discussed, implemented and tested in other contexts.

TLA is organized around two design patterns:

- **AER — Adaptive Evidence Routing:** determine how much additional evidence a decision actually needs, then route the problem toward the least costly reliable source of that evidence.
- **CAER — Context-Aware Experience Reuse:** reuse past experience only after examining contextual differences that may alter its outcome; choose among **Reuse**, **Adapt**, and **Re-experiment**.

## Core architecture

\`\`\`mermaid
flowchart LR
    P[Territorial problem / decision] --> AER[AER: What evidence is still missing?]
    AER --> E[Evidence Memory]
    AER --> K[Compiled Knowledge]
    AER --> H[Human Expertise]
    AER --> R[Tool-assisted Reasoning]
    AER --> X{Comparable experience?}
    X -->|Yes| CAER[CAER]
    CAER --> U[Reuse]
    CAER --> A[Adapt]
    CAER --> RE[Re-experiment]
    AER --> M[Micro-experiment]
    E --> D[Decision / public action]
    K --> D
    H --> D
    R --> D
    U --> D
    A --> D
    RE --> M
    M --> D
    D -->|Observed outcome| EM[Experiential Memory]
\`\`\`

## Three complementary memories

| Memory | Main question | Typical implementation |
|---|---|---|
| **Evidence Memory** | What do the sources say? | RAG, search, documentary repository |
| **Compiled Knowledge Memory** | What do we currently know? | Wiki, GraphRAG, knowledge graph, structured synthesis |
| **Experiential Memory** | What have we actually tried? | Structured experience records |

**Safety principle:** no important compiled knowledge without a recoverable path back to evidence.

## What TLA claims — and what it does not

TLA proposes design rules and an architecture. It does **not** currently claim that AER is an optimal metareasoning algorithm, that CAER automatically establishes causal transportability, or that any one memory technology is universally superior.

The purpose of this repository is to make the architecture explicit enough to be criticized, implemented in different ways, and tested.

## Research paper

The complete English paper is available in Markdown:

- [TLA — Territorial Learning Architecture](docs/TLA.md)

Focused documents:

- [Adaptive Evidence Routing (AER)](docs/AER.md)
- [Context-Aware Experience Reuse (CAER)](docs/CAER.md)
- [The three memories](docs/memories.md)
- [Governance and drift control](docs/governance.md)
- [Open research questions](research/open_questions.md)

## Initial design context

TLA emerged from the proposal for a **learning territory capable of learning how to learn in Martinique**, developed in:

**Tanic, É. (2026). _Martinique Territoire Intelligent_. Independently published. ISBN 979-8175326957. ASIN B0HKGKGFGD.**

https://www.amazon.fr/dp/B0HKGKGFGD

Martinique is the initial design context, not the boundary of the architecture.

## Contributing

Criticism, alternative formulations, reference implementations, case studies and proposals for evaluating AER or CAER are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

Open questions are tracked as GitHub Issues.

## Citation

A machine-readable citation is provided in [CITATION.cff](CITATION.cff).

Suggested citation:

> Tanic, É. (2026). *TLA — Territorial Learning Architecture: An AI-Assisted Learning Architecture for Territories*. Open research architecture. https://doi.org/10.5281/zenodo.22923636

## License

Text, diagrams and documentation are released under **Creative Commons Attribution 4.0 International (CC BY 4.0)**. See [LICENSE](LICENSE).

---

**Status:** open research architecture. The design patterns are proposed for discussion and testing; their performance is not presented as already demonstrated.
