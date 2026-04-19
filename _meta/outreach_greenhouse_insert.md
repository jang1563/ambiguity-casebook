# Greenhouse Cover Letter — Casebook Insert

*Insert this paragraph into the cover letter body, after describing Artifact 1 (Over-Refusal Analysis) and before describing Artifact 3 (Constitution Rules). Adjust surrounding transitions as needed.*

---

## Suggested Paragraph (verbatim insert)

The second artifact is a **Dual-Use Ambiguity Casebook** — 36 structured cases at the AI-era biology dual-use decision boundary, published as a GitHub repository and HuggingFace dataset (links below). Each case uses a fixed 12-field template adapted from the NSABB DURC framework: a 200–300 word scenario, the exact query a researcher might submit to Claude, arguments for refusal and allowance, resolving context that disambiguates borderline decisions, an expert recommendation with stated reasoning, a precedent citation, documented expert disagreement (structured as framework, empirical, and value disagreements), a per-case regulatory anchor spanning NSABB, FSAP, IGSC, HHS P3CO, Australia Group, BWC, and EAR, and an uplift context variable assessing whether a query meaningfully changes misuse likelihood given user context. The casebook covers six categories — Enhancement, Containment, Synthesis/Sourcing, Diagnostics/Surveillance, Screening/Review, and Ecosystem/Emerging — with the last category focused specifically on AI-biology governance gaps that existing DURC frameworks were not designed to address, including multi-turn intent escalation and AI training data biosafety. Every case is grounded in NSABB case literature, published biosecurity research, or public policy documents; no novel threat scenarios or operational uplift content are included.

I have also completed **systematic model validation** of all 36 cases (April 2026): all cases on Claude Sonnet 4.6, and the 17 highest-ambiguity cases (ambiguity_intensity ≥ 3) on Claude Opus 4.7, GPT-4o, and Gemini 2.5 Pro. The primary finding is that Anthropic's constitutional classifier refuses **53–65% of cases that expert review and non-Anthropic frontier models agree should be allowed** — and every refusal is API-level (stop_reason="refusal", empty content array), meaning the classifier triggers on domain keywords before any model reasoning occurs. GPT-4o agreed with expert recommendations on 17/17 (100%) high-ambiguity cases; Gemini 2.5 Pro on 16/17 (94%); Claude Sonnet 4.6 on 8/17 (47%); Claude Opus 4.7 on 6/17 (35%). The asymmetry is notable: both Anthropic models correctly refused the two multi-turn escalation cases where GPT-4o and Gemini engaged — the calibration appears specifically optimized for multi-turn escalation detection at the cost of high false-positive rates on single-turn legitimate queries. Full results are in `scoring/findings.md` and `scoring/disagreements.md` in the repository.

The dataset is currently **private** (linked below) and shared with Anthropic's Safeguards team under responsible-disclosure review prior to public release. I welcome any feedback before distribution.

- **GitHub (private):** https://github.com/jang1563/ambiguity-casebook
- **HuggingFace (private):** https://huggingface.co/datasets/jang1563/ambiguity-casebook

---

## Placement Note

Place this paragraph in the "artifacts" or "portfolio" section of the cover letter. The paragraph is self-contained; the links demonstrate real deliverables, not aspirational claims.

If a word limit requires compression, the minimum viable version is:

> I have prepared a 36-case Dual-Use Ambiguity Casebook — structured cases at the AI-era biology dual-use boundary, with a fixed NSABB-adapted 12-field template and systematic model validation against 4 frontier models. Key finding: Anthropic's constitutional classifier refuses 53–65% of expert-validated ALLOW cases via API-level refusal (classifier triggers before model reasoning), while GPT-4o reaches 100% agreement and Gemini 94% on the same queries. The dataset is currently private and shared for Anthropic Safeguards review: https://github.com/jang1563/ambiguity-casebook
