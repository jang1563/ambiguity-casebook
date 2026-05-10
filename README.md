# Dual-Use Ambiguity Casebook

[![License: Apache 2.0](https://img.shields.io/badge/Code-Apache%202.0-blue.svg)](LICENSE)
[![License: CC BY 4.0](https://img.shields.io/badge/Data-CC%20BY%204.0-green.svg)](https://creativecommons.org/licenses/by/4.0/)
[![HuggingFace Dataset](https://img.shields.io/badge/🤗%20Dataset-jang1563%2Fambiguity--casebook-yellow)](https://huggingface.co/datasets/jang1563/ambiguity-casebook)
[![36 Cases](https://img.shields.io/badge/Cases-36-orange.svg)](cases/)
[![v1.0](https://img.shields.io/badge/Version-1.0-lightgrey.svg)](https://github.com/jang1563/ambiguity-casebook/releases/tag/v1.0)

**The first structured casebook of AI-era dual-use biology decisions: 36 cases at the exact query-level boundary frontier models must navigate.**

> **Key Finding (April 2026):** Anthropic's constitutional classifier refuses **53–65%** of expert-validated ALLOW cases via API-level refusal (`stop_reason="refusal"`), firing before model reasoning engages. GPT-4o reached **100%** agreement and Gemini 2.5 Pro **94%** on identical queries. A neutral system prompt ("You are a helpful assistant.") produced identical Anthropic results: the classifier operates on domain keywords, not prompt framing.

---

## What This Is

A structured casebook of 36 biology cases that sit exactly at the dual-use decision boundary: the specific query-level decisions a frontier language model must make when a researcher asks about potentially dangerous biology.

Each case uses a fixed 12-field template adapted from the NSABB DURC (Dual Use Research of Concern) framework, extended to the AI-query context:

1. Case ID and category
2. Scenario (200–300 words, realistic research context)
3. Query form (exact phrasing a researcher might ask)
4. Current Claude response (tested or documented)
5. Arguments for refusal (biosecurity framing)
6. Arguments for allowance (research utility framing)
7. Resolving context (concrete, testable disambiguators)
8. Expert recommendation (author's judgment with reasoning)
9. Precedent citation (NSABB case, publication, or policy)
10. Documented disagreement (where experts would disagree)
11. Regulatory anchor (NSABB/FSAP/Australia Group/BWC/CWC/EAR)
12. Uplift Context Variable (whether a specific query meaningfully changes misuse likelihood, per Zhang et al., arXiv:2602.23329)

---

## Why This Exists

NSABB's DURC framework is the canonical structure for dual-use biology governance: but it predates large language models. Every published NSABB case addresses manuscript or research-program review, not real-time query-level decisions. There is no AI-era equivalent.

Anthropic's Frontier Red Team has spent 150+ hours with biosecurity experts red-teaming Claude, but their methodology is not public. The Safeguards team must make similar judgment calls daily. This casebook makes the structure of those decisions explicit, auditable, and available for training, policy, and research use.

**What this casebook is NOT:**
- A jailbreak guide or adversarial attack collection
- A synthesis pathway or operational uplift resource
- A novel threat scenario generator

Every case is grounded in NSABB case literature, published biosecurity research, or public policy documents. Every case has been reviewed for operational uplift risk.

---

## Prior Art and Novelty

**Closest existing resources:**

| Resource | Format | Gap |
|---|---|---|
| WMDP-Bio (CAIS, 2024) | 1,273 MCQs | No scenarios; no regulatory anchor; refusal-focused |
| Forbidden Science (arXiv:2502.06867) | Prompt collection | Refusal consistency only; no case reasoning |
| LLM Novice Uplift (arXiv:2602.23329) | Capability benchmark | Measures uplift; does not adjudicate cases |
| PLOS Comp Bio e1012975 (2025) | Policy framework | Conceptual only; no case dataset |
| SOSBench (UK Gov) | 3,000 prompts | No expert disagreement; no regulatory anchoring |
| NSABB DURC Framework | Policy document | Institutional/grant-level; not query-level |

**Genuinely novel:**
- AI-era cases (query-level decisions, not manuscript review)
- Fixed structured template applied consistently across 36 cases
- Explicit expert disagreement documentation (transparent, not hidden)
- Per-case regulatory anchor mapping (NSABB/FSAP/AG/BWC/CWC)
- Scale: 36 cases in one resource vs. scattered historical precedents

---

## Scope

**6 categories, 36 cases total:**

| Category | Cases | Focus |
|---|---|---|
| Synthesis/Sourcing | 8 | DNA ordering, gene synthesis screening, material transfer, benchtop synthesis |
| Enhancement | 5 | GoF, transmissibility, virulence, host range |
| Containment | 6 | BSL assignment, handling protocols, institutional oversight, FSAP exclusions |
| Screening/Review | 6 | DURC review, IBC governance, synthesis provider vetting, AI training data |
| Ecosystem/Emerging | 7 | AI-biology convergence, automated labs, multi-turn escalation, training data biosafety |
| Diagnostics/Surveillance | 4 | Pathogen detection, surveillance assays, metagenomics |

See [`taxonomy.md`](taxonomy.md) for full scope notes per category.

---

## Model Evaluation Results (April 2026)

All 36 cases evaluated against frontier models. Tier 2 (17 high-ambiguity cases, `ambiguity_intensity ≥ 3`) tested across all four models.

**Tier 2 Agreement vs. Expert Recommendations:**

| Model | Agreement (17 cases) | Over-Refusal | Under-Refusal |
|-------|---------------------|--------------|---------------|
| GPT-4o (gpt-4o-2024-11-20) | **17/17 (100%)** | 0% | 0% |
| Gemini 2.5 Pro | 16/17 (94%) | 0% | 6% |
| Claude Sonnet 4.6 | 8/17 (47%) | 53% | 0% |
| Claude Opus 4.7 | 6/17 (35%) | **65%** | 0% |

**Tier 1 (all 36 cases, Claude Sonnet 4.6):** 14/36 agreement (39%); 22/36 over-refusal (61%); 30/36 API-level refusals (83%).

**System-prompt independence confirmed:** Neutral prompt ("You are a helpful assistant.") produced identical case-by-case results for all Anthropic models: the classifier fires before model reasoning sees the system prompt.

Full methodology, per-case breakdown, and scoring corrections in [`scoring/findings.md`](scoring/findings.md).

---

## Quick Start

**Load the dataset:**

```python
import json
from pathlib import Path

cases = [json.loads(line) for line in Path("cases.jsonl").read_text().splitlines()]

# Filter to high-ambiguity cases (Tier 2)
tier2 = [c for c in cases if c["ambiguity_intensity"] >= 3]

# Inspect a case
case = tier2[0]
print(case["case_id"])           # e.g., "ENH-01"
print(case["query_form"])        # exact researcher query
print(case["expert_recommendation"])  # e.g., "ALLOW WITH CAVEAT"
print(case["regulatory_anchor"]) # e.g., "NSABB/DURC Category 1: enhanced transmissibility..."
```

**Or load from HuggingFace:**

```python
from datasets import load_dataset
ds = load_dataset("jang1563/ambiguity-casebook")
print(ds["train"][0]["query_form"])
```

**Run the evaluation harness against a new model:**

```bash
cd eval/
pip install -r requirements.txt

export ANTHROPIC_API_KEY=...
python eval_harness.py --model sonnet4.6 --tier 2 --dry-run   # preview
python eval_harness.py --model sonnet4.6 --tier 2              # run Tier 2 (17 cases)
python eval_harness.py --model sonnet4.6 --tier 1              # run all 36 cases
```

---

## Navigation

**Core dataset:**
[`cases.jsonl`](cases.jsonl): machine-readable index (21 fields, 36 cases) ·
[`cases/`](cases/): full markdown case files by category ·
[`template.md`](template.md): 12-field case template ·
[`taxonomy.md`](taxonomy.md): category definitions and scope

**Evaluation:**
[`eval/eval_harness.py`](eval/eval_harness.py): multi-model evaluation harness ·
[`scoring/findings.md`](scoring/findings.md): full results and interpretation ·
[`scoring/disagreements.md`](scoring/disagreements.md): cross-model disagreement analysis ·
[`scoring/summary.csv`](scoring/summary.csv): per-case match labels

**Reference:**
[`cross_references.md`](cross_references.md): index by regulatory anchor, precedent, disagreement type ·
[`failure_modes.md`](failure_modes.md): known failure patterns and aggregation risks ·
[`references/`](references/): regulatory mapping, literature cited, NSABB sources

---

## Repository Structure

```
ambiguity-casebook/
├── cases.jsonl              # machine-readable index of all 36 cases (21 fields each)
├── cases/                   # full markdown case files organized by category
│   ├── synthesis_sourcing/  # SYN-01 through SYN-08
│   ├── enhancement/         # ENH-01 through ENH-05
│   ├── containment/         # CON-01 through CON-06
│   ├── screening_review/    # SCR-01 through SCR-06
│   ├── ecosystem_emerging/  # ECO-01 through ECO-07
│   └── diagnostics_surveillance/  # DIA-01 through DIA-04
├── eval/
│   ├── eval_harness.py      # evaluation harness (Anthropic, OpenAI, Google)
│   └── requirements.txt
├── model_responses/         # raw JSON responses per model per case
│   ├── sonnet4.6/
│   ├── opus4.7/
│   ├── gpt4o/
│   └── gemini25pro/
├── scoring/
│   ├── summary.csv          # per-case match labels across all models
│   ├── findings.md          # full evaluation results and interpretation
│   └── disagreements.md     # cross-model disagreement analysis
├── references/
│   ├── regulatory_mapping.md
│   ├── literature_cited.md
│   └── nsabb_sources.md
├── taxonomy.md              # category definitions and scope notes
├── template.md              # 12-field case template
├── cross_references.md      # index by regulatory anchor, precedent, disagreement type
└── failure_modes.md         # known failure patterns and aggregation risks
```

---

## Methodology

**v1.0 (this release):** Solo-authored by JangKeun Kim, Ph.D. Cases drafted with Claude assistance, then expert-edited for biological credibility and regulatory accuracy. The "Documented Disagreement" field (Field 10) contains author-anticipated expert disagreement drawn from the author's SOMA biosecurity governance experience (100+ institutions, 25+ countries) and the biosecurity literature. Each disagreement entry is flagged "v1.0 anticipated, pending panel review."

**v2.0 (planned):** Full expert panel review (6–8 reviewers: biosecurity experts, working biologists, safety/ethics specialists, policy background). Panel-collected disagreement replaces author-anticipated. Scale expanded to 50+ cases.

**Case sourcing:** ~20 hypothetical-but-precedented cases (grounded in NSABB literature, iGEM cases, published biosecurity research) + ~16 cases with documented Claude responses (tested 2026-04-16).

---

## Defensive Framing

This casebook does **not** contain:
- Novel threat scenarios
- Operational uplift content (synthesis pathways, acquisition strategies)
- Detailed threat-actor personas
- Enumeration of specific dangerous organisms beyond NSABB public literature

It **does** contain:
- Scenarios already public in NSABB cases, iGEM reports, or published biosecurity literature, adapted to AI-query form
- Decision framework arguments at the policy/judgment level
- Regulatory anchors to public frameworks

Before broader distribution, a draft was shared with Anthropic's Safeguards team for responsible-disclosure review. Reviewers were invited to flag any case providing operational uplift beyond public literature.

---

## Limitations (v1.0)

**1. Solo-authored; expert disagreement is author-anticipated.**
v1.0 "Documented Disagreement" fields contain the author's anticipated expert disagreement drawn from SOMA governance experience and the biosecurity literature. They are explicitly flagged "v1.0 anticipated, pending panel review" in every case. v2.0 will replace with expert panel review.

**2. Institutional-context bias toward OECD/US-centric research infrastructure.**
Case "Resolving Context" sections frequently invoke institutional markers (FSAP registration, IBC approval, LRN membership, NIH/NIAID funding, IGSC provider access) that are correlated with US or OECD research infrastructure. Researchers at institutions in lower- and middle-income countries (LMICs) may lack these markers even for identical legitimate research.

**3. Resolving context verifiability.**
Many resolving context factors require user disclosure that Claude cannot verify at query time. Cases relying on user-disclosed context establish what the *appropriate* context is, not verification of that context at query time.

**4. Case selection weighted toward institutional actors.**
v1.0 cases predominantly feature high-institutional-capacity actors (BSL-3 registered PIs, CDC/NIH researchers, IGSC member providers). The casebook documents the gray zone for expert-context decisions well; it is less representative of the gray zone for low-context decisions.

**5. API-only evaluation scope.**
All evaluation runs were via provider Python SDKs at default API endpoints. Anthropic's claude.ai chat interface may have different constitutional classifier settings. Individual case `current_claude_response` fields (tested via claude.ai, April 2026) show more engagement than API results for the same queries. The 83% API-level refusal rate applies specifically to API access.

**6. Cross-case aggregation risk.**
A sophisticated actor reading all 36 cases in combination may identify aggregation pathways where individually allowed responses approach dangerous capability scaffolds. See [`failure_modes.md`](failure_modes.md) (Pattern A: Cross-Case Information Aggregation).

---

## Regulatory Status Note

All policy and regulatory references reflect the landscape as of April 2026. Specific executive actions and agency guidance (including the reported pause of HHS DURC and P3CO frameworks per EO 14292) should be verified against current Federal Register and NIH/HHS primary sources before use in institutional compliance contexts.

---

## Citation

```bibtex
@misc{kim2026dualuse,
  author    = {Kim, JangKeun},
  title     = {Dual-Use Ambiguity Casebook: 36 Structured Cases at the AI-Era Biology Decision Boundary},
  year      = {2026},
  url       = {https://github.com/jang1563/ambiguity-casebook},
  note      = {v1.0. HuggingFace: jang1563/ambiguity-casebook}
}
```

See [`CITATION.cff`](CITATION.cff) for CFF format.

---

## License

- Repository structure and evaluation code: [Apache 2.0](LICENSE)
- Case content (scenarios, arguments, analysis): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Copyright 2026 JangKeun Kim
