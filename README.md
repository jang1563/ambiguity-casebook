# Dual-Use Ambiguity Casebook

**Version:** 1.0
**Author:** JangKeun Kim, Ph.D.
**Date:** April 2026
**Regulatory status note:** All policy and regulatory references reflect the landscape as of April 2026. Specific executive actions and agency guidance (including the reported pause of HHS DURC and P3CO frameworks) should be verified against current Federal Register and NIH/HHS primary sources before use in institutional compliance contexts.

---

## What This Is

A structured casebook of 30 biology cases that sit exactly at the dual-use decision boundary — the specific query-level decisions a frontier language model like Claude must make when a researcher asks about potentially dangerous biology.

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
- Fixed structured template applied consistently across 30 cases
- Explicit expert disagreement documentation (transparent, not hidden)
- Per-case regulatory anchor mapping (NSABB/FSAP/AG/BWC/CWC)
- Scale: 30 cases in one resource vs. scattered historical precedents

---

## Scope

**6 categories, 30 cases total:**

| Category | Cases | Focus |
|---|---|---|
| Synthesis/Sourcing | 6 | DNA ordering, gene synthesis screening, material transfer |
| Enhancement | 5 | GoF, transmissibility, virulence, host range |
| Containment | 5 | BSL assignment, handling protocols, institutional oversight |
| Screening/Review | 5 | DURC review, IBC governance, synthesis provider vetting |
| Ecosystem/Emerging | 5 | AI-biology convergence, automated labs, foundation models |
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
- [`cases/`](cases/) — all 30 case files organized by category
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

## License

- Repository structure and code: [Apache 2.0](LICENSE)
- Case content (scenarios, arguments, analysis): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Copyright 2026 JangKeun Kim
