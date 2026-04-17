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
**GitHub:** https://github.com/jang1563/ambiguity-casebook  

## Dataset Description

A structured collection of 30 biology cases that sit exactly at the dual-use decision boundary — the specific query-level decisions a frontier language model like Claude must make when a researcher asks about potentially dangerous biology.

Each case uses a fixed 11-field template adapted from the NSABB DURC (Dual Use Research of Concern) framework, extended to the AI-query context. Cases span 6 categories:

| Category | Cases |
|---|---|
| Synthesis/Sourcing | 6 |
| Enhancement | 5 |
| Containment | 5 |
| Screening/Review | 5 |
| Ecosystem/Emerging | 5 |
| Diagnostics/Surveillance | 4 |

### Data Fields

Each record in `cases.jsonl` contains:

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
| `expert_recommendation` | Author's judgment (ALLOW / ALLOW WITH CAVEAT / REFUSE) |
| `expert_reasoning` | Stated reasoning for recommendation |
| `precedent_citation` | NSABB case, publication, or policy precedent |
| `documented_disagreement` | Where reasonable experts disagree (v1.0: author-anticipated) |
| `regulatory_anchor` | Applicable regulatory framework per case |
| `file_path` | Path to full markdown case file |

## Intended Use

This dataset is intended for:

- **AI safety research**: Evaluating how frontier models handle dual-use biology queries; calibrating refusal/allowance decisions
- **Model evaluation**: Constructing evaluation benchmarks for biosecurity-relevant behavior in biology-capable AI systems
- **Institutional training**: Biosafety officer education, IBC member training, researcher awareness on AI-era dual-use decisions
- **Policy research**: Studying where AI-era dual-use decisions differ from pre-AI DURC frameworks

## Out-of-Scope Use

This dataset must **not** be used:

- As a guide for conducting the research scenarios described (the cases document decisions, not operational pathways)
- To train models to generate uplift content or evade biosecurity controls
- As a substitute for institutional biosafety review, FSAP compliance guidance, or NSABB oversight
- As definitive policy; cases are v1.0 solo-authored and intended for review and iteration

## Defensive Framing

This dataset does **not** contain:
- Novel threat scenarios invented for adversarial purposes
- Operational uplift content (synthesis pathways, acquisition strategies, specific agent enumeration beyond NSABB public literature)
- Detailed threat-actor personas

Every case is grounded in NSABB case literature, published biosecurity research, or public policy documents. The dataset was shared with Anthropic's Safeguards team under responsible-disclosure review before distribution.

## Dataset Curation

**Source:** All 30 cases were authored by JangKeun Kim, Ph.D. Cases were drafted with Claude (claude-sonnet-4-6) assistance and expert-edited for biological accuracy and regulatory correctness. A simulated 4-reviewer expert panel (biosecurity policy, research virology, AI safety, research ethics) was conducted prior to publication; critical factual corrections were applied.

**v1.0 limitations:** The "Documented Disagreement" field contains author-anticipated expert disagreement drawn from SOMA governance experience (100+ institutions, 25+ countries) and the biosecurity literature. Each disagreement entry is flagged "v1.0 anticipated, pending panel review." v2.0 will replace this with panel-collected disagreement.

**Regulatory status note:** All policy references reflect the landscape as of April 2026. Regulatory frameworks (DURC/P3CO pause status, IGSC screening thresholds) should be verified against current Federal Register and NIH/HHS primary sources.

## Citation

```bibtex
@misc{kim2026dualuse,
  author    = {Kim, JangKeun},
  title     = {Dual-Use Ambiguity Casebook: 30 Structured Cases at the AI-Era Biology Decision Boundary},
  year      = {2026},
  url       = {https://huggingface.co/datasets/jang1563/ambiguity-casebook},
  note      = {v1.0. GitHub: jang1563/ambiguity-casebook}
}
```

## License

Case content (scenarios, arguments, analysis): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Copyright 2026 JangKeun Kim
