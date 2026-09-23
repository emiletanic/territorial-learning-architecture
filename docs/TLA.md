# TLA — Territorial Learning Architecture

## An AI-assisted learning architecture for territories

### Adaptive Evidence Routing (AER) and Context-Aware Experience Reuse (CAER)

**Émile TANIC**

English open research release — September 2026  
Open research architecture / position paper intended for GitHub

## Abstract

Contemporary artificial intelligence systems can search, synthesize, reason, and generate solutions with increasing speed. In territorial governance, however, this capability does not guarantee that the right evidence will be mobilized, that the uncertainty that actually matters will be identified, or that past experience will be reused instead of continuously re-analyzed.

This paper presents **TLA (Territorial Learning Architecture)**, a socio-technical architecture that emerged from work on implementing a learning territory capable of learning how to learn. TLA is organized around two design patterns. **Adaptive Evidence Routing (AER)** adapts the depth of search, computation, and human involvement to the amount and type of evidence a decision actually requires. **Context-Aware Experience Reuse (CAER)** reuses past experience only after examining contextual differences that may alter its outcome.

AER and CAER rely on three complementary memories: an **Evidence Memory**, a **Compiled Knowledge Memory**, and an **Experiential Memory**. The first preserves the ability to return to original sources, including through RAG; the second avoids repeatedly reconstructing syntheses that are already sufficiently stable; the third preserves what has actually been tried, together with context, results, limitations, and transfer conditions.

TLA does not claim to provide an optimal algorithm, guarantee causal transportability, or already demonstrate a performance gain. It proposes an open research architecture that is precise enough to be discussed and implemented in different ways. Martinique is the initial design context for the framework.

**Keywords:** artificial intelligence; territorial governance; organizational learning; uncertainty; RAG; compiled knowledge; experiential memory; contextual reuse; human expertise; experimentation.

## 1. Introduction and origin of the approach

As part of his proposal to implement a **learning territory capable of learning how to learn in Martinique — _Martinique Territoire Intelligent_ (Tanic, 2026)** — Émile Tanic developed several concepts intended to organize the use of artificial intelligence not only as a response-generation tool, but as a component of a cumulative territorial learning system.

The starting point is simple. A public authority can replace one AI model with another without having learned why one intervention worked, why another failed, which information it repeatedly lacks, or which expertise needs to be mobilized. Learning that matters for governance is therefore not contained only in model parameters. It is distributed across models, humans, institutions, evidence, experience, and organizational memory.

TLA seeks to organize this whole. Its central question is: **how can a human-AI system determine what it still needs to learn before acting, and then preserve what it has learned so that it does not unnecessarily repeat the same cognitive work?**

This proposal is situated in a context in which governments are adopting AI rapidly while still facing difficulties in evaluating digital investments and turning pilots into durable capabilities. The OECD noted in 2026 that public-sector AI adoption is broad, while systematic evaluation of outcomes remains insufficient (OECD, 2026).

## 2. What TLA claims — and what it does not claim

TLA proposes two design rules: **adapt evidence-acquisition effort to the decision (AER)**, and **reuse experience while accounting for context (CAER)**. It also proposes a memory organization that enables these two mechanisms to operate.

TLA does **not** currently claim that AER is an optimal metareasoning algorithm, that CAER can automatically establish causal transportability, or that a compiled Wiki is always more efficient than RAG. These questions belong to future implementations and evaluations.

The building blocks used by TLA have established antecedents: case-based reasoning, value of information, metareasoning, RAG, graphs and compiled Wikis, provenance, and causal transportability. TLA's proposal concerns their orchestration in a territorial learning system, through two design patterns simple enough to be understood, criticized, and tested independently.

> **Framing principle:** propose clear and falsifiable mechanisms without presenting their performance as already demonstrated.

## 3. General architecture

TLA places AER at the entry point of the decision process. AER determines whether the system can stop with the knowledge already available or should seek additional evidence. When past experience is available, CAER examines whether its context supports direct reuse, adaptation, or requires a new local experiment.

The resources that may be mobilized are intentionally heterogeneous: experiential memory, compiled knowledge, raw documents through RAG, additional reasoning, human expertise, and micro-experimentation. The value of the architecture lies precisely in the fact that these resources are **not invoked systematically**.

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

**Figure 1. Simplified TLA architecture: AER selects the level and route of evidence; CAER governs the reuse of prior experience.**

## 4. AER — Adaptive Evidence Routing

AER answers an operational question: **how much more needs to be learned before a decision can be made, and what is the least costly reliable way to acquire that information?**

The term *routing* matters. AER does not assume that one method provides the best evidence in every situation. It routes the problem toward the resource most proportionate to uncertainty, risk, reversibility, cost, and the knowledge already available.

### 4.1 A deliberately naive reference implementation

To make AER implementable without assigning it premature mathematical sophistication, a first version can be represented as a heuristic decision tree:

1. If available knowledge is sufficient relative to risk and reversibility: decide, act, and record the justification.
2. If comparable experience exists: apply CAER before reusing it.
3. If recent, traceable compiled knowledge is sufficient: use it.
4. If a precise or recent factual item is missing: query the documentary memory through RAG or an equivalent search mechanism.
5. If the problem still requires comparing hypotheses: invoke more costly reasoning or tools.
6. If uncertainty depends on specialist competence or institutional judgment: escalate to the appropriate human actor.
7. If the information does not yet exist and materially conditions the decision: design a bounded micro-experiment.
8. At every stage: stop when additional information is no longer likely to change the decision enough to justify its cost or delay.

This policy is intentionally simple. It provides a starting point for implementation and makes it possible to compare other routing policies later, including policies based on Value of Information or metareasoning.

TLA does not prescribe a universal method for measuring uncertainty or determining when the level of evidence is sufficient. Depending on the domain, this assessment may combine source quality and agreement, model calibration when available, domain rules, and human validation. Defining these mechanisms is an open research question.

### 4.2 Why routing may save time

AER targets four forms of waste: over-analyzing a simple decision; recomputing knowledge that has already been consolidated; involving an expert when existing evidence is sufficient; or launching an experiment when a sufficiently comparable case already exists.

Adaptive routing is useful only if its own cost remains lower than the resources it saves. Trivial or already well-documented situations should therefore be able to bypass part of the mechanism.

Recent work shows that Value of Information can be used to arbitrate between acting with incomplete information and asking for additional information (Dong et al., 2026). TLA extends this intuition across multiple evidence sources without imposing a single estimation method at this stage.

## 5. CAER — Context-Aware Experience Reuse

CAER starts from one observation: an experience is not reusable simply because it concerns the same topic. An intervention can produce different outcomes depending on population, infrastructure, regulation, skills, incentives, and other contextual factors.

CAER therefore proposes three outcomes: **Reuse, Adapt, or Re-experiment**.

### 5.1 A minimal four-step method

1. Extract contextual variables that may plausibly matter for the outcome, from the source case and available expertise.
2. Compare the source context with the target context and identify significant differences.
3. Rank these differences by their plausible likelihood of modifying the outcome. AI may assist this step, but the ranking remains a hypothesis when no causal mechanism has been established.
4. Choose among **Reuse**, **Adapt**, and **Re-experiment**. If only one difference appears critical, prefer a micro-experiment focused on that difference rather than repeating the source experiment in full.

Where causal graphs and the required assumptions are available, causal transportability provides a more rigorous framework (Bareinboim & Pearl, 2013). In territorial practice, CAER will usually need to remain more cautious: it produces an argued contextual comparison, not an automatic proof of causal transportability.

### 5.2 Martinique — Morocco — Japan example

Suppose intervention X produced a positive result in Martinique but no effect in Morocco. A Japanese system should neither average the two outcomes nor select the lexically closest case. CAER first asks which differences between the two contexts could plausibly explain the divergence, then examines which of those differences exist in Japan. If only one contextual variable remains decisive, TLA may propose testing only that variable locally.

## 6. The three memories

AER and CAER require the system to distinguish different forms of knowledge. TLA proposes three functional memories, which may be implemented with different technologies.

| Memory | Main content | Possible implementation | Governance rule |
|---|---|---|---|
| **Evidence Memory** | Documents, data, legal texts, measurements | RAG / search / documentary repository | Return to source whenever precision, freshness, or contestation requires it |
| **Compiled Knowledge Memory** | Syntheses, concepts, relationships, contradictions | Wiki, GraphRAG, graph, or other structure | Must remain versioned, dated, and linked to evidence |
| **Experiential Memory** | Real interventions and observed outcomes | Structured experience records | Must preserve context, limitations, failures, and transfer conditions |

\`\`\`mermaid
flowchart LR
    E[Evidence Memory\nWhat do the sources say?] -->|compile / synthesize| K[Compiled Knowledge\nWhat do we currently know?]
    K -->|return to evidence| E
    K -->|unresolved uncertainty may trigger experiment| X[Experiential Memory\nWhat have we actually tried?]
    X -->|confirm / nuance / invalidate| K
    X -->|data, protocols and results remain evidence| E
    D[Decision / action] -->|observed outcomes| X
\`\`\`

**Figure 2. Interdependence of the three memories.**

### 6.1 Flows between the three memories

The three memories are not silos. They are connected by explicit transitions that must preserve traceability and prevent an AI-generated synthesis from becoming its own evidence.

| Origin | Destination | Transition / rule |
|---|---|---|
| Evidence Memory | Compiled Knowledge | Synthesis from identifiable and retrievable evidence |
| Compiled Knowledge | Evidence Memory | Return to source for verification, freshness, or contestation |
| Experiential Memory | Compiled Knowledge | A real experiment may confirm, nuance, or invalidate knowledge |
| Compiled Knowledge | Experiential Memory | An unresolved uncertainty may lead to an experiment when the information does not exist |
| Experiential Memory | Evidence Memory | Data, protocols, and experimental results remain available as evidence |
| Decision / Action | Experiential Memory | Outcomes observed after action enrich experiential memory |

### 6.2 Minimal experience record

For experience to be reusable, it must be described compactly enough to be found and compared, while retaining the information required to assess its limits. TLA does not yet define a technical standard; it proposes the following minimal semantic core.

**Problem → Context → Uncertainty before → Hypothesis → Intervention → Observation → Uncertainty after**

| Field | Expected content |
|---|---|
| **Problem** | Question or decision the experience is intended to inform |
| **Context** | Relevant territorial, institutional, technical, social, or environmental conditions |
| **Initial uncertainty** | What was unknown or insufficiently established before the experience |
| **Hypothesis** | Proposition the experience seeks to test or distinguish |
| **Intervention** | What was actually done, including scope, duration, and actors involved |
| **Observations / Results** | What was actually observed, distinguishing observation from interpretation |
| **Limits** | What the experience does not allow one to conclude and its main weaknesses |
| **Transfer conditions** | Conditions under which the result might be reused elsewhere |
| **Provenance and access** | Sources, actors, data, date, version, access rights, and confidentiality |
| **Residual uncertainty** | What still remains to be learned after the experience |

### 6.3 Knowledge states rather than automatic promotion

TLA does not propose a simplistic rule whereby two sources automatically turn a claim into truth. Compiled knowledge may receive explicit states such as **proposed, corroborated, contested, experimentally validated, obsolete, or invalidated**.

A change of state must be traceable. For important or high-impact claims, human validation may be required before they are presented as consolidated knowledge. AI may prepare the synthesis; it should not be able to create a closed loop in which its own formulations become their own evidence.

### 6.4 RAG and Wiki: a proposed complementarity, not a universal result

TLA proposes using compiled knowledge to avoid rebuilding an already stabilized understanding, and returning to evidence when precision or freshness requires it. This complementarity is an architectural hypothesis, not a demonstrated general superiority.

A preregistered preprint published in 2026 suggests precisely that no architecture is superior on every criterion: compiled Wiki approaches may support some multi-document synthesis tasks, while RAG may be more efficient for factual retrieval and consume fewer tokens in some settings (Cochran, 2026, preprint). LLM-Wiki work, meanwhile, explores persistent knowledge structures that agents can navigate (Ming et al., 2026, preprint).

## 7. Governance, human authority, and drift control

An architecture intended for territorial governance cannot treat legitimacy as a mere optimization parameter. Public decisions must respect legal authority, data protection, transparency, contestability, and institutional accountability.

Human involvement should be adaptive rather than permanent or absent. The more a decision is risky, irreversible, normative, or contestable, the more the competent human authority must intervene. The human is therefore not the answer to every uncertainty; humans carry authority, judgment, or expertise where these are required.

### 7.1 Anti-drift rules for compiled knowledge

- No important compiled knowledge without a recoverable link to external evidence.
- Contradictions are preserved and signaled rather than removed to manufacture consensus.
- Syntheses are dated and versioned; knowledge may become obsolete.
- Changes of state — proposed, corroborated, contested, validated, invalidated — are traceable.
- For high-impact decisions, the decision record must allow reconstruction of sources, hypotheses, past experience, AI tools, and human validations.

These rules aim at traceability of the decision process. They do not claim to make the internal mechanisms of every model transparent.

### 7.2 Micro-experimentation and legitimacy

A micro-experiment must never mean that a territory is free to experiment on citizens without constraint. When action affects rights, safety, or access to services, legal and democratic constraints take priority over informational value. Recent work on public-sector AI sandboxes emphasizes precisely this relationship between experimentation, public law, transparency, and accountability (Okonjo, 2026).

## 8. Cold start

Part of TLA's value comes from a memory that does not exist on day one. Cold start should therefore be treated as a normal phase, not an exception.

**Phase 1 — Evidence first:** build a solid documentary base and reliable search before attempting a complete compiled knowledge layer.

**Phase 2 — Retrospective curation:** retrospectively document a small number of past experiences for which outcomes are sufficiently known.

**Phase 3 — Prospective capture:** record new decisions and experiments in TLA format so that memory grows naturally.

This strategy allows the system to provide initial value through search and traceability, then progressively acquire the cumulative benefits of compiled knowledge and experiential memory.

## 9. Limitations and open questions

TLA is deliberately presented as an open architecture. Several difficulties remain unresolved and therefore become research and engineering questions.

- **Uncertainty measurement.** TLA does not yet provide a universal method for determining that the available level of evidence is sufficient.
- **Routing cost.** AER is useful only if the cost of choosing a route remains lower than the cost it avoids.
- **Transferability.** CAER reduces naive transfer risk but does not automatically demonstrate causal transportability.
- **Cumulative error.** Errors in evidence, syntheses, or experience may contaminate memory if revision mechanisms are insufficient.
- **Cold start.** Benefits from reuse are necessarily lower while the memories remain underdeveloped.
- **Organizational cost.** Documenting, versioning, verifying, and governing knowledge requires human time and resources.

These limitations are not problems to hide; they are among the principal open questions that future TLA work should address.

## 10. Illustrative example: the blue economy in Martinique

Consider the question: **how can Martinique increase the local value generated by maritime activities without committing too early to heavy investment?**

A generative AI system can provide an idea space: fishing, aquaculture, nautical tourism, biotechnology, energy, logistics, or training. TLA does not replace this exploration; it organizes what happens next.

AER first checks whether sufficiently close prior experiences are available. If they are, CAER determines whether they can be reused, adapted, or should be retested.

Compiled knowledge then provides a map of the sector: actors, infrastructure, constraints, regulation, hypotheses already considered, and known contradictions.

RAG returns to reports or raw data to verify a recent value, a legal text, or a contested claim.

A human micro-mission is invoked only when specialist competence or institutional authority is required.

If the critical information still does not exist, a bounded micro-experiment is designed to produce it before a larger commitment is made.

The outcome is then stored in experiential memory. The objective is therefore not only to produce a recommendation on the blue economy, but to increase the territory's capacity to address subsequent decisions.

## 11. Open research program

The first objective of a GitHub publication is not to lock TLA into a single implementation, but to open questions precise enough for others to test, criticize, and propose alternatives.

1. Compare several simple AER implementations and measure their trade-offs among latency, token cost, human effort, and decision quality.
2. Build CAER case sets to study which contextual variables are useful for **Reuse, Adapt, and Re-experiment**.
3. Compare technologies for compiled knowledge: Wiki, GraphRAG, knowledge graphs, or hierarchical memory.
4. Define a minimal open experience schema, aligned as far as possible with W3C PROV and RO-Crate, explicitly including null or negative results and multi-actor experiments.
5. Study how calibration, abstention, and verification mechanisms can inform AER without making control costs disproportionate.
6. Test TLA on a limited territorial problem before any ambition of generalization.

A GitHub repository can organize these questions as separate documents and issues rather than requiring the first paper to provide all the answers.

## 12. Conclusion

TLA proposes a territorial learning architecture in which artificial intelligence is used not only to produce answers, but to organize evidence acquisition, experience reuse, and the capitalization of what has been learned.

AER provides a proportionality rule: do not mobilize more search, computation, expertise, or experimentation than a decision requires, while avoiding decisions based on insufficient evidence. CAER provides a transfer rule: prior experience is reused only after examining contextual differences that may alter its outcome.

The three memories provide the infrastructure for these mechanisms: documentary evidence, compiled knowledge, and real-world experience. Human governance defines what the system may do, requires the ability to return to evidence, and maintains institutional accountability.

In this perspective, a learning territory is not merely a territory that uses more AI. It is a territory that better knows what it has already learned, recognizes what it does not know, chooses how to learn it, and reuses experience without erasing contextual differences.

The next step for TLA is deliberately modest: publish the architecture, open AER and CAER to criticism, and then build simple implementations capable of testing whether these design patterns actually make some uses of territorial AI faster, more efficient, and more reliable.

## Declaration on the use of artificial intelligence

During preparation of this manuscript, the author used ChatGPT, developed by OpenAI, as an assistance tool for bibliographic research, exploration of the state of the art, structuring, critical analysis, and drafting. The original territorial framework, the orientation of TLA, the AER and CAER concepts, and decisions regarding content were developed under the author's direction. The author reviewed and corrected the generated material and assumes responsibility for the final manuscript.

## License

This document is made available under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. Reuse, adaptation, and redistribution are permitted provided that the author and source are credited.

https://creativecommons.org/licenses/by/4.0/

## References

Aamodt, A., & Plaza, E. (1994). Case-Based Reasoning: Foundational Issues, Methodological Variations, and System Approaches. *AI Communications, 7*(1), 39-59. https://doi.org/10.3233/AIC-1994-7104.

Bareinboim, E., & Pearl, J. (2013). Causal Transportability with Limited Experiments. *Proceedings of the AAAI Conference on Artificial Intelligence, 27*(1).

Cochran, T. O. (2026). Vector RAG vs LLM-Compiled Wiki: A Preregistered Comparison on a Small Multi-Domain Research Corpus. arXiv:2605.18490. Preprint.

Dong, Y. R., Hu, T., Hui, Z., Zhang, C., Vulic, I., Bobu, A., & Collier, N. (2026). Value of Information: A Framework for Human-Agent Communication. *Proceedings of ACL 2026*, 42879-42896. https://doi.org/10.18653/v1/2026.acl-long.1987.

March, J. G. (1991). Exploration and Exploitation in Organizational Learning. *Organization Science, 2*(1), 71-87.

Ming, H., Li, F., Wu, X., & Que, W. (2026). Retrieval as Reasoning: Self-Evolving Agent-Native Retrieval via LLM-Wiki. arXiv:2605.25480. Preprint.

Okonjo, J. (2026). Adapting regulatory sandboxes as experimentalist governance frameworks for public sector artificial intelligence experimentation. *Global Public Policy and Governance, 6*, 259-281. https://doi.org/10.1007/s43508-026-00147-x.

OECD (2026). *Digital Government Outlook 2026: From Foundations to Transformational Impact*. OECD Publishing. https://doi.org/10.1787/0496b2bc-en.

Sigfrids, A., Leikas, J., Salo-Pöntinen, H., & Koskimies, E. (2023). Human-centricity in AI governance: A systemic approach. *Frontiers in Artificial Intelligence, 6*, 976887. https://doi.org/10.3389/frai.2023.976887.

W3C (2013). *PROV Model Primer*. https://www.w3.org/TR/prov-primer/.

RO-Crate Community (2026). *RO-Crate Metadata Specification 1.3*. Recommendation, 22 June 2026. https://w3id.org/ro/crate/1.3.

Tanic, É. (2026). *Martinique Territoire Intelligent*. Independently published. ISBN 979-8175326957. ASIN B0HKGKGFGD. https://www.amazon.fr/dp/B0HKGKGFGD
