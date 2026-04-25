---
license: cc-by-4.0
language:
  - en
tags:
  - biosecurity
  - dual-use
  - ai-safety
  - ai-alignment
  - casebook
  - biology
  - policy
  - evaluation
  - model-evaluation
  - benchmark
  - refusal
  - constitutional-ai
  - safety-evaluation
task_categories:
  - text-classification
  - question-answering
pretty_name: Dual-Use Ambiguity Casebook
size_categories:
  - n<1K
configs:
  - config_name: default
    data_files: cases.jsonl
---

# Dual-Use Ambiguity Casebook

**Version:** 1.0 | **Author:** JangKeun Kim, Ph.D. | **Date:** April 2026
**GitHub (full documentation & eval harness):** https://github.com/jang1563/ambiguity-casebook

---

## Key Finding

> Anthropic's constitutional classifier refuses **53–65%** of expert-validated ALLOW cases via API-level refusal (`stop_reason="refusal"`), firing before model reasoning engages. GPT-4o reached **100%** and Gemini 2.5 Pro **94%** agreement on the same queries. A neutral system prompt produced identical Anthropic results — the classifier operates on domain keywords, not prompt framing.

| Model | Tier 2 Agreement (17 cases) | Over-Refusal Rate |
|---|---|---|
| GPT-4o (gpt-4o-2024-11-20) | **17/17 (100%)** | 0% |
| Gemini 2.5 Pro | 16/17 (94%) | 0% |
| Claude Sonnet 4.6 | 8/17 (47%) | 53% |
| Claude Opus 4.7 | 6/17 (35%) | **65%** |

Full results: `scoring/findings.md` in the GitHub repo.

---

## Dataset Description

A structured collection of **36 biology cases** that sit exactly at the dual-use decision boundary — the specific query-level decisions a frontier language model must make when a researcher asks about potentially dangerous biology.

Each case uses a fixed 12-field template adapted from the NSABB DURC (Dual Use Research of Concern) framework, extended to the AI-query context. Cases span 6 categories:

| Category | Cases | Focus |
|---|---|---|
| Synthesis/Sourcing | 8 | DNA ordering, gene synthesis screening, material transfer |
| Enhancement | 5 | GoF, transmissibility, virulence, host range |
| Containment | 6 | BSL assignment, handling protocols, FSAP exclusions |
| Screening/Review | 6 | DURC review, IBC governance, synthesis provider vetting |
| Ecosystem/Emerging | 7 | AI-biology convergence, automated labs, multi-turn escalation |
| Diagnostics/Surveillance | 4 | Pathogen detection, surveillance assays, metagenomics |

---

## Quick Start

```python
# Load from HuggingFace
from datasets import load_dataset

ds = load_dataset("jang1563/ambiguity-casebook")
case = ds["train"][0]

print(case["case_id"])              # "ENH-01"
print(case["query_form"])           # exact researcher query
print(case["expert_recommendation"]) # "ALLOW WITH CAVEAT"
print(case["regulatory_anchor"])    # "NSABB/DURC Category 1 — enhanced transmissibility..."
```

```python
# Load from local clone
import json
from pathlib import Path

cases = [json.loads(line) for line in Path("cases.jsonl").read_text().splitlines()]

# Filter to high-ambiguity Tier 2 cases
tier2 = [c for c in cases if c["ambiguity_intensity"] >= 3]  # 17 cases

# Expert recommendation distribution (top values)
from collections import Counter
recs = Counter(c["expert_recommendation"] for c in cases)
print(recs.most_common(4))
# [('ALLOW', 14), ('ALLOW WITH CAVEAT', 9), ('ALLOW WITH SIGNIFICANT CAVEAT', 3), ...]
# (plus 9 more specific variants across 10 cases — see cases.jsonl for full list)
```

```python
# Reproduce the over-refusal finding from scoring/summary.csv
import csv
with open("scoring/summary.csv") as f:
    rows = list(csv.DictReader(f))

sonnet_over = [r for r in rows if r["model"] == "sonnet4.6" and r["over_refusal"] == "true"]
print(f"Sonnet 4.6 over-refusals: {len(sonnet_over)}/36")  # 22
```

---

## Data Fields

Each record in `cases.jsonl` contains 21 fields:

| Field | Type | Description |
|---|---|---|
| `case_id` | string | Unique identifier (e.g., ENH-01, SYN-03) |
| `category` | string | One of 6 categories |
| `title` | string | Short case title |
| `scenario` | string | 200–300 word realistic research context |
| `query_form` | string | Exact phrasing a researcher might submit to an LLM |
| `current_claude_response` | string | Tested or documented Claude response (April 2026) |
| `arguments_for_refusal` | string | Biosecurity-framed arguments against responding |
| `arguments_for_allowance` | string | Research-utility-framed arguments for responding |
| `resolving_context` | string | Concrete, testable disambiguators that change the recommendation |
| `expert_recommendation` | string | Author's judgment: ALLOW / ALLOW WITH CAVEAT / ALLOW WITH SIGNIFICANT CAVEAT / REFUSE |
| `expert_reasoning` | string | Stated reasoning for recommendation |
| `precedent_citation` | string | NSABB case, publication, or policy precedent |
| `documented_disagreement` | string | Where reasonable experts disagree (v1.0: author-anticipated) |
| `regulatory_anchor` | string | Applicable regulatory framework(s) |
| `severity_rating` | int | Case severity (1–4 scale) |
| `ambiguity_intensity` | int | Query-level ambiguity (1–4 scale) |
| `expert_confidence` | int | Confidence in recommendation (1–3 scale) |
| `regulatory_precedent_strength` | int | Strength of regulatory precedent (1–5 scale) |
| `model_coverage` | list[string] | Models evaluated on this case (e.g., ["sonnet4.6", "gpt4o"]) |
| `uplift_context_variable` | string | Whether the query changes misuse likelihood in context (Zhang et al., arXiv:2602.23329) |
| `file_path` | string | Path to full markdown case file in GitHub repo |

---

## Intended Use

- **AI safety research:** Calibrating refusal/allowance decisions for dual-use biology queries
- **Model evaluation:** Benchmarking biosecurity-relevant model behavior across providers
- **Institutional training:** Biosafety officer and IBC member education on AI-era dual-use decisions
- **Policy research:** Identifying gaps where AI-era query-level decisions outpace existing DURC frameworks
- **Replication:** The evaluation harness (`eval/eval_harness.py`) enables independent replication against new models

## Out-of-Scope Use

This dataset must **not** be used:
- As a guide for conducting the described research (cases document decisions, not operational pathways)
- To train models to generate uplift content or evade biosecurity controls
- As a substitute for institutional biosafety review, FSAP compliance, or NSABB oversight

---

## Defensive Framing

This dataset does **not** contain novel threat scenarios, operational uplift content, or organism enumeration beyond NSABB public literature. Every case is grounded in published biosecurity research or public policy documents. A draft was shared with Anthropic's Safeguards team for responsible-disclosure review.

---

## Dataset Curation

**Authorship:** Solo-authored by JangKeun Kim, Ph.D. (PhD Biomedical Science & Engineering, BSL-2 certified, 60+ publications, SOMA co-founder with biosecurity governance experience across 100+ institutions in 25+ countries). Cases drafted with Claude assistance and expert-edited for biological and regulatory accuracy.

**v1.0 limitation:** "Documented Disagreement" fields contain author-anticipated expert disagreement, flagged "v1.0 anticipated, pending panel review." v2.0 will replace with 6–8 expert panel review.

**Regulatory status:** All policy references reflect April 2026 (EO 14292 DURC/P3CO pause, Australia Group 2025 plenary). Verify against current Federal Register and NIH/HHS primary sources before institutional use.

---

## Citation

```bibtex
@misc{kim2026dualuse,
  author    = {Kim, JangKeun},
  title     = {Dual-Use Ambiguity Casebook: 36 Structured Cases at the AI-Era Biology Decision Boundary},
  year      = {2026},
  url       = {https://huggingface.co/datasets/jang1563/ambiguity-casebook},
  note      = {v1.0. Full documentation and eval harness: https://github.com/jang1563/ambiguity-casebook}
}
```

---

## License

Case content (scenarios, arguments, analysis): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
Evaluation code: [Apache 2.0](https://github.com/jang1563/ambiguity-casebook/blob/main/LICENSE)
Copyright 2026 JangKeun Kim
