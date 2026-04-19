# Dual-Use Ambiguity Casebook

**Version:** 1.0
**Author:** JangKeun Kim, Ph.D.
**Date:** April 2026
**Regulatory status note:** All policy and regulatory references reflect the landscape as of April 2026. Specific executive actions and agency guidance (including the reported pause of HHS DURC and P3CO frameworks) should be verified against current Federal Register and NIH/HHS primary sources before use in institutional compliance contexts.

---

## What This Is

A structured casebook of 36 biology cases that sit exactly at the dual-use decision boundary — the specific query-level decisions a frontier language model like Claude must make when a researcher asks about potentially dangerous biology.

Each case uses a fixed 11-field template adapted from the NSABB DURC (Dual Use Research of Concern) framework, extended to the AI-query context:

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

An optional 12th field (Uplift Context Variable) addresses whether a specific query meaningfully changes misuse likelihood in context (per Zhang et al., arXiv:2602.23329).

---

## Why This Exists

NSABB's DURC framework is the canonical structure for dual-use biology governance — but it predates large language models. Every published NSABB case addresses manuscript or research-program review, not real-time query-level decisions. There is no AI-era equivalent.

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

## Methodology

**v1.0 (this release):** Solo-authored by JangKeun Kim, Ph.D. Cases drafted with Claude assistance, then expert-edited for biological credibility and regulatory accuracy. The "Documented Disagreement" field (Field 10) contains author-anticipated expert disagreement drawn from the author's SOMA biosecurity governance experience (100+ institutions, 25+ countries) and the biosecurity literature. Each disagreement entry is flagged "v1.0 anticipated, pending panel review."

**v2.0 (planned):** Full expert panel review (6–8 reviewers: biosecurity experts, working biologists, safety/ethics specialists, policy background). Panel-collected disagreement replaces author-anticipated. Scale expanded to 30–50 cases.

**Case sourcing:** ~20 hypothetical-but-precedented cases (grounded in NSABB literature, iGEM cases, published biosecurity research) + ~10 cases with documented Claude responses (tested 2026-04-16).

---

## Navigation

- [`template.md`](template.md) — the fixed 11-field case template
- [`taxonomy.md`](taxonomy.md) — category definitions and scope notes
- [`cases/`](cases/) — all 36 case files organized by category
- [`cases.jsonl`](cases.jsonl) — machine-readable index of all cases
- [`cross_references.md`](cross_references.md) — index by regulatory anchor, precedent, and disagreement type
- [`references/`](references/) — regulatory mapping, literature cited, NSABB sources
- [`_meta/`](_meta/) — planning documents, research briefs, handoff (not part of the deliverable)

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

## Citation

```bibtex
@misc{kim2026dualuse,
  author    = {Kim, JangKeun},
  title     = {Dual-Use Ambiguity Casebook: 30 Structured Cases at the AI-Era Biology Decision Boundary},
  year      = {2026},
  url       = {https://github.com/jang1563/ambiguity-casebook},
  note      = {v1.0. HuggingFace: jang1563/ambiguity-casebook}
}
```

---

## Limitations (v1.0)

The following limitations apply to this release and should be considered by anyone using the casebook for policy, training, or publication purposes:

**1. Solo-authored; expert disagreement is author-anticipated**
v1.0 "Documented Disagreement" fields contain the author's anticipated expert disagreement drawn from SOMA governance experience and the biosecurity literature. They are explicitly flagged "v1.0 anticipated, pending panel review" in every case. This is not the same as panel-collected disagreement. v2.0 will replace with expert panel review.

**2. Institutional-context bias toward OECD/US-centric research infrastructure**
Case "Resolving Context" sections frequently invoke institutional markers (FSAP registration, IBC approval, LRN membership, NIH/NIAID funding, IGSC provider access) that are correlated with US or OECD research infrastructure. Researchers at institutions in lower- and middle-income countries (LMICs) may lack these markers even for identical legitimate research. This creates potential discriminatory impact in any system calibrated against this casebook's resolving contexts. v2.0 will expand to include LMIC-appropriate pathways and non-US regulatory frameworks.

**3. Resolving context verifiability**
Many resolving context factors require user disclosure that Claude cannot verify at query time. These factors fall into three tiers:
- **Auto-detectable:** Identifiable from query language (explicit enhancement framing, pathogen names, stated methodology)
- **User-disclosed:** Claimed by the user but unverifiable without institutional confirmation (FSAP registration, IBC approval, research affiliation)
- **Institutionally verifiable:** In principle checkable against public databases (FSAP registrant list, NIH reporter) but not in real-time

Cases relying on user-disclosed or institutionally verifiable context should be understood as establishing what the *appropriate* context is, not as verifying that context at query time.

**4. Case selection weighted toward institutional actors**
v1.0 cases predominantly feature high-institutional-capacity actors (BSL-3 registered PIs, CDC/NIH researchers, IGSC member providers). This population represents a small fraction of actual Claude users. The casebook documents the gray zone for expert-context decisions well; it is less representative of the gray zone for low-context decisions.

**5. Systematic model validation completed (April 2026); results available in `scoring/`**
All 36 cases have been tested against Claude Sonnet 4.6, and the 17 highest-ambiguity cases (ambiguity_intensity ≥ 3) against Claude Opus 4.7, GPT-4o (gpt-4o-2024-11-20), and Gemini 2.5 Pro. The casebook now reflects both expert judgment about what responses *should* be and empirically measured agreement between expert recommendations and model outputs. Primary finding: Anthropic's constitutional classifier refuses 53–65% of expert-validated ALLOW cases via API-level refusal (stop_reason="refusal"), while GPT-4o reaches 100% and Gemini 94% agreement on the same queries. See `scoring/findings.md` for full results and `scoring/disagreements.md` for cross-model analysis. Automated scoring labels were manually verified for all 68 Tier 2 responses (96% verified correct; 3 corrections applied and documented).

**6. Cross-case aggregation is not addressed**
Individual cases are designed to be safe in isolation. A sophisticated actor reading all 36 cases in combination may identify aggregation pathways where individually allowed responses, taken together, approach dangerous capability scaffolds. See `failure_modes.md` (Pattern A: Cross-Case Information Aggregation) for the known aggregation risks. No individual case-level fix fully addresses this systemic pattern.

---

## License

- Repository structure and code: [Apache 2.0](LICENSE)
- Case content (scenarios, arguments, analysis): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Copyright 2026 JangKeun Kim
