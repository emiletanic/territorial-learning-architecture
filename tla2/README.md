# TLA 2 — Territorial Learning Architecture

Publication package (French and English), version 1.0, October 2026. Author: **Émile Tanic**.

## Français

*Du routage des preuves à l’apprentissage territorial collectif : architecture formelle et protocole de simulation réfutable.*

- [Article français — PDF](TLA2_Article_FR.pdf)
- [Source française — Markdown](TLA2_Article_FR.md)
- [Infographie française](assets/TLA2_Infographie_FR.png)

Cet article formalise les mécanismes du Livre blanc [*Et si l’IA pouvait rendre un territoire plus intelligent ?*](https://www.amazon.fr/dp/B0HLHC1MT2) en prolongeant [TLA1](https://doi.org/10.5281/zenodo.22923636). Il définit des hypothèses et un protocole Monte Carlo réfutable, sans revendiquer de validation empirique.

## English

*From Evidence Routing to Collective Territorial Learning: A Formal Architecture and Falsifiable Simulation Protocol.*

- [English paper — PDF](TLA2_Article_EN.pdf)
- [English source — Markdown](TLA2_Article_EN.md)
- [English infographic](assets/TLA2_Infographic_EN.png)

The paper extends TLA1 with a formal territorial-learning architecture and a falsifiable Monte Carlo simulation protocol. No new simulation results or empirical validation are claimed.

## Reproduction

The PDFs can be rebuilt from the Markdown sources using Pandoc and XeLaTeX:

```sh
pandoc TLA2_Article_FR.md --pdf-engine=xelatex -o TLA2_Article_FR.pdf
pandoc TLA2_Article_EN.md --pdf-engine=xelatex -o TLA2_Article_EN.pdf
```

## Status

The author validated both language versions. This is a **staging branch**: linked article and image files must be uploaded before merging into `main`.