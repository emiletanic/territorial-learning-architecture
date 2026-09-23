# Context-Aware Experience Reuse (CAER)

CAER is a TLA design pattern for deciding whether a past experience should be **reused, adapted, or re-experimented** in a new context.

Semantic similarity is not enough. The same intervention can produce different outcomes under different regulatory, social, infrastructural, demographic, economic or organizational conditions.

## Minimal four-step method

1. **Extract candidate contextual variables** that may plausibly matter for the outcome.
2. **Compare source and target contexts** and identify significant differences.
3. **Rank contextual differences** by their plausible likelihood of modifying the outcome. AI may assist, but this ranking remains a hypothesis when no causal mechanism has been established.
4. Choose among:
   - **Reuse** — the result appears sufficiently transferable.
   - **Adapt** — reuse the experience with explicit contextual adjustment.
   - **Re-experiment** — run a new local test, preferably focused only on the critical difference.

## Important boundary

CAER does **not** automatically establish causal transportability.

Where explicit causal graphs and the required assumptions are available, formal transportability methods may provide a stronger basis. Otherwise CAER should be treated as a structured contextual comparison.

## Example

If intervention X succeeds in Martinique but not in Morocco, a Japanese system should not average the two outcomes or select the lexically closest report. It should ask which contextual differences could plausibly explain the divergence, then determine which of those differences exist in Japan.

If only one difference remains critical, a targeted micro-experiment may be preferable to repeating the full intervention.
