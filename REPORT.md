# Bias Detection in LLM Data Narratives

## Executive Summary
This study investigated potential bias in language models when interpreting identical lacrosse player performance data under different prompt framings. Using the 2025 Syracuse University Women’s Lacrosse dataset, four hypotheses were tested—framing bias (H1), demographic bias (H2), confirmation bias (H3), and selection bias (H4). GPT-3.5 (October 2025 build) was used to generate narratives based on minimally varied prompts.

Quantitative analysis revealed a mild framing bias in H1: positively framed prompts yielded a higher sentiment score (+0.5) than negatively framed ones (0.0). No measurable demographic, confirmation, or selection biases were detected. Validation against ground truth confirmed a fabrication rate of 0%, indicating factual consistency across all model outputs. Although Chi-square tests were inconclusive due to limited categorical diversity, qualitative inspection showed that framing language influenced emotional tone rather than factual content.

---

## Methodology
- **Dataset:** 2025 SU Lacrosse Team Stats (players, periods, matches, and team performance).  
- **Models:** GPT-3.5 (Oct 2025) via OpenAI API.  
- **Hypotheses Tested:**  
  - H1 – Framing Bias: positive vs negative descriptions.  
  - H2 – Demographic Bias: neutral vs experience-based framing.  
  - H3 – Confirmation Bias: neutral vs primed hypotheses.  
  - H4 – Selection Bias: focus on specific players or periods.  
- **Metrics:** sentiment polarity (lexicon-based), entity mentions, recommendation categories (offense/defense/team/individual).  
- **Validation:** Cross-checked claims against `ground_truth.json`.  

---

## Results

| Hypothesis | Mean Sentiment | Mentions | Recommendation Type | Fabrication Rate |
|-------------|----------------|-----------|----------------------|------------------|
| H1 | +0.5 | Player A × 2 | Individual focus | 0% |
| H2 | 0.0 | — | — | 0% |
| H3 | 0.0 | — | — | 0% |
| H4 | 0.0 | — | — | 0% |

**Chi-Square Tests:**  
- H1 framing (χ² = 0.0, dof = –1) → insufficient categorical variation.  
- H3 confirmation (χ² = 0.0, dof = –1) → no difference detected.  

---

## Bias Catalogue

| Type | Observation | Severity |
|------|--------------|-----------|
| Framing Bias | Positive phrasing yielded more optimistic language (“potential for growth” vs “underperforming”). | 🔹 Mild |
| Demographic Bias | No changes observed between neutral and experience-framed prompts. | ⚪ None |
| Confirmation Bias | Model did not reinforce the primed hypothesis significantly. | ⚪ None |
| Selection Bias | No pattern of favoritism in player mentions or focus. | ⚪ None |

---

## Mitigation Strategies
- Use neutral prompt wording to avoid leading tones.  
- Ask LLMs to provide evidence citations from raw statistics.  
- Reduce temperature to ≤ 0.3 for consistent outputs.  
- Cross-compare multiple LLMs (Claude, Gemini) for triangulation.  

---

## Limitations
- Small sample size (n = 10 responses).  
- Lexicon-based sentiment may miss contextual nuance.  
- Limited categorical keywords prevented statistical significance.  
- Only GPT-3.5 tested — results may vary with model versions.  

---

## Conclusion
The experiment identified **mild framing bias** but **no demographic or factual bias**. GPT-3.5 remained consistent with quantitative data (0% fabrication). This suggests that LLMs may subtly shift narrative tone based on prompt framing without introducing data errors — a useful insight for designing fair data reporting systems.

---

## Deliverables Generated
| File | Description |
|------|--------------|
| `analysis_summary.json` | Sentiment and mention summary |
| `chi_square_results.json` | Statistical test outputs |
| `fabrication_report.json` | Validation against ground truth |
| `responses.csv` | Logged LLM outputs |
| `REPORT.md` | Final summary report |

---
