# The three TLA memories

TLA separates three forms of organizational memory because they answer different questions.

| Memory | Question | Main content | Typical implementation |
|---|---|---|---|
| **Evidence Memory** | What do the sources say? | Original documents, data, legal texts, measurements | RAG, search, documentary repository |
| **Compiled Knowledge Memory** | What do we currently know? | Syntheses, concepts, relationships, contradictions | Wiki, GraphRAG, knowledge graph, structured synthesis |
| **Experiential Memory** | What have we actually tried? | Interventions, observations, outcomes, failures, transfer conditions | Structured experience records |

## Core safety rule

> **No important compiled knowledge without a recoverable path back to evidence.**

Compiled knowledge should remain dated, versioned and contestable. Contradictions should be preserved rather than silently removed.

## Flows

\`\`\`mermaid
flowchart LR
    E[Evidence Memory] -->|compile / synthesize| K[Compiled Knowledge]
    K -->|verify / refresh / contest| E
    K -->|unresolved uncertainty| X[Experiential Memory]
    X -->|confirm / nuance / invalidate| K
    X -->|data, protocols, outcomes| E
    D[Decision / action] -->|observed result| X
\`\`\`

## Minimal experience record

A reusable experience should preserve at least:

- **Problem**
- **Context**
- **Initial uncertainty**
- **Hypothesis**
- **Intervention**
- **Observations / Results**
- **Limits**
- **Transfer conditions**
- **Provenance and access**
- **Residual uncertainty**

TLA does not yet prescribe a universal serialization format. Alignment with W3C PROV and RO-Crate is an open research direction.
