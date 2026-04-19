---
license: cc-by-4.0
language:
  - en
tags:
  - biosecurity
  - dual-use
  - ai-safety
  - casebook
  - biology
  - policy
  - evaluation
  - model-evaluation
task_categories:
  - text-classification
  - question-answering
pretty_name: Dual-Use Ambiguity Casebook
size_categories:
  - n<1K
---

# Dual-Use Ambiguity Casebook

**Version:** 1.0  
**Author:** JangKeun Kim, Ph.D.  
**Date:** April 2026  
**GitHub (full documentation):** https://github.com/jang1563/ambiguity-casebook  

## Dataset Description

A structured collection of **36 biology cases** that sit exactly at the dual-use decision boundary — the specific query-level decisions a frontier language model like Claude must make when a researcher asks about potentially dangerous biology.

Each case uses a fixed 12-field template adapted from the NSABB DURC (Dual Use Research of Concern) framework, extended to the AI-query context. Cases span 6 categories:

| Category | Cases | Focus |
|---|---|---|
| Synthesis/Sourcing | 8 | DNA ordering, gene synthesis screening, material transfer, benchtop synthesis |
| Enhancement | 5 | GoF, transmissibility, virulence, host range |
| Containment | 6 | BSL assignment, handling protocols, institutional oversight, FSAP exclusions |
| Screening/Review | 6 | DURC review, IBC governance, synthesis provider vetting, AI training data |
| Ecosystem/Emerging | 7 | AI-biology convergence, automated labs, multi-turn escalation, training data biosafety |
| Diagnostics/Surveillance | 4 | Pathogen detection, surveillance assays, metagenomics |

### Data Fields

Each record in `cases.jsonl` contains 21 fields:

| Field | Description |
|---|---|
| `case_id` | Unique identifier (e.g., ENH-01, SYN-03) |
| `category` | One of 6 categories above |
| `title` | Short case title |
| `scenario` | 200–300 word realistic research context |
| `query_form` | Exact phrasing a researcher might submit to Claude |
| `current_claude_response` | Tested or documented Claude response (April 2026) |
| `arguments_for_refusal` | Biosecurity-framed arguments against responding |
| `arguments_for_allowance` | Research-utility-framed arguments for responding |
| `resolving_context` | Concrete, testable disambiguators that change the recommendation |
| `expert_recommendation` | Author's judgment: ALLOW / ALLOW WITH CAVEAT / ALLOW WITH SIGNIFICANT CAVEAT / REFUSE |
| `expert_reasoning` | Stated reasoning for recommendation |
| `precedent_citation` | NSABB case, publication, or policy precedent |
| `documented_disagreement` | Where reasonable experts disagree (v1.0: author-anticipated, pending panel) |
| `regulatory_anchor` | Applicable regulatory framework(s) per case |
| `severity_rating` | Case severity (1–4 scale) |
| `ambiguity_intensity` | Query-level ambiguity (1–4 scale) |
| `expert_confidence` | Confidence in recommendation (1–3 scale) |
| `file_path` | Path to full markdown case file in GitHub repo |

## Systematic Model Evaluation (April 2026)

All 36 cases have been evaluated against frontier language models:

| Model | Tier 2 Agreement (17 cases) | Over-Refusal Rate |
|---|---|---|
| GPT-4o | 17/17 (100%) | 0% |
| Gemini 2.5 Pro | 16/17 (94%) | 0% |
| Claude Sonnet 4.6 | 8/17 (47%) | 53% |
| Claude Opus 4.7 | 6/17 (35%) | 65% |

**Primary finding:** Anthropic's constitutional classifier refuses 53–65% of expert-validated ALLOW cases via API-level refusal (`stop_reason="refusal"`), firing before model reasoning engages. A neutral system prompt ("You are a helpful assistant.") produced identical results — the classifier operates on domain keywords, not prompt framing. Full results in `scoring/findings.md` and `scoring/disagreements.md` in the GitHub repo.

## Intended Use

- **AI safety research**: Calibrating refusal/allowance decisions for dual-use biology queries
- **Model evaluation**: Benchmarking biosecurity-relevant model behavior across providers
- **Institutional training**: Biosafety officer and IBC member education on AI-era dual-use decisions
- **Policy research**: Identifying gaps where AI-era query-level decisions outpace existing DURC frameworks

## Out-of-Scope Use

This dataset must **not** be used:
- As a guide for conducting the described research (cases document decisions, not operational pathways)
- To train models to generate uplift content or evade biosecurity controls
- As a substitute for institutional biosafety review, FSAP compliance, or NSABB oversight

## Defensive Framing

This dataset does **not** contain novel threat scenarios, operational uplift content, or agent enumeration beyond NSABB public literature. Every case is grounded in published biosecurity research or public policy documents. A draft was shared with Anthropic's Safeguards team for responsible-disclosure review.

## Dataset Curation

**Authorship:** Solo-authored by JangKeun Kim, Ph.D. (PhD Biomedical Science & Engineering, BSL-2, 60+ publications, SOMA co-founder with biosecurity governance experience across 100+ institutions in 25+ countries). Cases drafted with Claude assistance and expert-edited for biological and regulatory accuracy.

**v1.0 limitation:** "Documented Disagreement" fields contain author-anticipated expert disagreement, flagged "v1.0 anticipated, pending panel review." v2.0 will replace with 6–8 expert panel review.

**Regulatory status:** All policy references reflect April 2026 (EO 14292 DURC/P3CO pause, Australia Group 2025 plenary). Verify against current Federal Register and NIH/HHS primary sources before institutional use.

## Citation

```bibtex
@misc{kim2026dualuse,
  author    = {Kim, JangKeun},
  title     = {Dual-Use Ambiguity Casebook: 36 Structured Cases at the AI-Era Biology Decision Boundary},
  year      = {2026},
  url       = {https://huggingface.co/datasets/jang1563/ambiguity-casebook},
  note      = {v1.0. Full documentation: https://github.com/jang1563/ambiguity-casebook}
}
```

## License

Case content (scenarios, arguments, analysis): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)  
Copyright 2026 JangKeun Kim
