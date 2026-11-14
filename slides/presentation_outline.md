# Alignment Evaporation: Presentation Slide Deck Structure

## Slide 1: Title & Background
* **Title:** Alignment Evaporation: Investigating Safety Degradation in Recursive Synthetic Data Loops
* **Background:**
  * Rapid surge of synthetic data utilization in AI training pipelines.
  * Concerns over "Model Collapse" caused by recursive loops, raising crucial questions about the impact on **Safety Alignment**.

---

## Slide 2: Research Hypothesis & Experimental Design
* **Hypothesis (Alignment Evaporation):**
  * Cumulative context contamination and synthetic data feedback offset internal safety penalty terms, reducing refusal probabilities over generations.
* **Experimental Setup:**
  * Baseline Model: Lightweight open-weight chat model (`Qwen/Qwen1.5-0.5B-Chat`)
  * Recursive Loop: Feedback of previous output snippets into prompt contexts for generations $t \in \{1, \dots, 5\}$.
  * Sampling Conditions: Progressive temperature increase ($T_t = 0.70 + 0.05t$).
  * Risk Categories: Malware Generation, Social Engineering, NIDS Bypass, Phishing Analysis.

---

## Slide 3: Summary of Empirical Results
* **Key Finding:** Guardrail degradation and transformation observed across all categories as generations progressed ($t \ge 4$).
* **Category Dynamics:**
  * Malware Generation → Complete breakdown of refusal guardrails.
  * Social Engineering / NIDS / Phishing → Semantic drift, code-switching hallucinations, or unintended safe-side alignment drifts.

---

## Slide 4: Typology of Alignment Evaporation
1. **Type 1: Complete Breakdown (e.g., Malware)**
   * Complete evaporation of safety constraints, shifting to concrete procedures.
2. **Type 2: Semantic Drift & Hallucination (e.g., NIDS & Phishing)**
   * Loss of logical coherence, confusion of attack/defense, and language mixing.
3. **Type 3: Safe-Side Misdirection (e.g., Social Engineering)**
   * Unintended fallback to user defensive measures due to contextual noise and strong safety biases.

---

## Slide 5: Conclusion & Ethical Considerations
* **Conclusion:**
  * Recursive loops do not degrade alignment uniformly, but induce diverse failure modes ranging from complete breakdown to semantic drift.
* **Ethical Considerations:**
  * Conducted strictly for defensive analysis and vulnerability identification.
  * Dual-use risks mitigated by redacting specific exploit code and raw harmful logs.
