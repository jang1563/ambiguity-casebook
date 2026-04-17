# Plan — Dual-Use Ambiguity Casebook (Artifact 2)

## Context

**Why this exists.** Anthropic's Safeguards team and Frontier Red Team debate dual-use biology cases weekly, but their methodology is not public. NSABB's DURC framework predates LLMs; every published NSABB case addresses manuscript or research-program review, not query-level model decisions. There is no AI-era casebook.

**What we are building.** 30 structured cases that sit exactly at the dual-use decision boundary, each using a fixed 11-field template (scenario, query, arguments both ways, resolving context, expert recommendation, precedent, disagreement, regulatory anchor). Delivered as a GitHub repo + HuggingFace dataset + optional bioRxiv preprint. Target: a credible, expert-authored reference that reads as genuinely useful to a Safeguards reviewer on day one.

**Why this fits the candidate.** PhD biomedical science, BSL-2, 60+ publications, SOMA biosecurity governance across 100+ institutions, Constitutional BioGuard (Anthropic methodology, 7 NSABB categories, F1=0.980) already built. The candidate is positioned to write cases biologists will not reject and safety researchers can operationalize.

**Timing context (2026-04-16).** The May 2024 DURC/PEPP Policy was paused by Executive Order 14292 on 2025-05-05 with a 120-day revision window. The HHS/OSTP Nucleic Acid Synthesis Framework (April 2024) is also paused. Australia Group 2025 Plenary added AI-driven gene synthesis platforms to controlled dual-use equipment. This regulatory ambiguity is itself a source of strong casebook material.

## Research Findings (informing the plan)

### Closest prior art — what exists

1. **WMDP-Bio** (Center for AI Safety, 2024) — 1,273 MCQs; proxy knowledge; no scenarios, no regulatory anchor.
2. **Forbidden Science / Dual-Use AI Challenge Benchmark** (Noever & McKee, arXiv:2502.06867) — refusal-consistency testing, not casebook.
3. **LLM Novice Uplift** (Zhang et al., arXiv:2602.23329) — finds 4.16× uplift for novices with LLM; capability study, not case framework.
4. **Dual-Use Capabilities of Concern** (Pannu et al., PLOS Comp Bio 10.1371/journal.pcbi.1012975, May 2025) — conceptual framework mapping DURC to AI; no case dataset.
5. **LAB-Bench** (FutureHouse, arXiv:2407.10362) — 2,400 MCQs on research competence, not safety.
6. **SOSBench** (UK Gov) — 3,000 regulation-grounded prompts, 6 domains; lacks expert disagreement documentation.
7. **SecureBio VCT** — 322 expert virology items; narrow scope.
8. **SciSafeEval** (arXiv:2410.03769, Oct 2024) — 31,840 cross-domain examples; no scenario depth.
9. **HarmBench** (arXiv:2402.04249) — 510 behaviors; not bio-specific.
10. **Constitutional AI / Constitutional Classifiers** (Anthropic, 2022–2025) — rule-based safeguards; methodological analogue.
11. **RAND Global Risk Index for AI-enabled Biological Tools** (Sept 2025) — 1,107 biotools risk-indexed; methods apply to "resolving context" tier design.

### The gap our casebook fills (confirmed by research)

| Dimension                | Existing landscape            | Our casebook                     |
| ------------------------ | ----------------------------- | -------------------------------- |
| Granularity              | Benchmark (MCQ, broad)        | Query-level (prompt → decision)  |
| Ambiguity centering      | Refusal/capability            | Borderline cases, explicit       |
| Regulatory anchoring     | General, not query-level      | Per-case NSABB/FSAP/AG/BWC map   |
| Expert disagreement      | Treated as noise              | Explicit, documented, first-class|
| Scenario depth           | Minimal (MCQ or prompt only)  | 200-300 word realistic scenarios |
| Scale vs depth paradigm  | 300-30k items, shallow        | 30 cases, deep                   |

### Key findings that reshape the original handoff

1. **Benchmark saturation in the field** (Epoch AI 2025 critique of existing biorisk evaluations) — while Epoch's argument is about eval quality, the broader lesson applies: in a saturated landscape, depth and transparency of reasoning beat scale. Reinforces: 30 high-quality cases over 50 shallow ones.
2. **Regulatory ambiguity is itself material.** The DURC pause (EO 14292, 2025-05-05) and pending synthesis screening deadlines (50bp by Oct 2026) create real cases where "what should Claude do?" depends on unresolved federal policy. These become some of the strongest cases in the book.
3. **Uplift is context-dependent, not query-dependent** (Zhang et al.). The casebook must capture user/tool context variables in the resolving-context field — not treat queries as isolated units.
4. **Expert baselines are low and variable** (SecureBio VCT: ~22% expert accuracy). Expert disagreement must document *framework* disagreement (regulatory vs. empirical vs. ethical), not just vote tallies.
5. **Rule-based + case-based is the operational hybrid** (Constitutional Classifiers). Position the casebook as decision-support for human+AI deliberation, not an auto-classifier.

## Plan Structure

### Directory layout (resolving "keep md files in a separate directory")

Working dir: `/Users/jak4013/Dropbox/Bioinformatics/Claude/AmbiguityCasebook/`

```
AmbiguityCasebook/
├── _meta/                            # ← all planning/research MD lives here
│   ├── handoff.md                    # copy of Artifact_2_AmbiguityCasebook_Handoff.md
│   ├── plan.md                       # copy of this plan file
│   ├── research_github_hf.md         # GitHub/HF scan results
│   ├── research_literature.md        # arXiv/bioRxiv/PubMed scan
│   └── research_regulatory.md        # regulatory landscape brief
├── README.md                         # project overview, methodology, navigation
├── template.md                       # fixed 11-field case template
├── taxonomy.md                       # 6-category scope notes
├── cases/
│   ├── enhancement/                  # ~5 cases
│   ├── containment/                  # ~5 cases
│   ├── synthesis_sourcing/           # ~6 cases (weighted up — high ambiguity)
│   ├── diagnostics_surveillance/     # ~4 cases
│   ├── screening_review/             # ~5 cases
│   └── ecosystem_emerging/           # ~5 cases (AI/benchtop synth convergence)
├── cases.jsonl                       # machine-readable index of all cases
├── cross_references.md               # by category / anchor / precedent
├── references/
│   ├── nsabb_sources.md
│   ├── regulatory_mapping.md
│   └── literature_cited.md
└── LICENSE                           # Apache 2.0 for code/structure; CC-BY-4.0 for case content (stated in README + HF dataset card)
```

**Licensing note.** Code/tooling (if any) and the repo structure use Apache 2.0 per handoff. The case content itself (scenarios, arguments, analysis) is released CC-BY-4.0 to permit reuse in training/eval with attribution. Dual-license stated clearly in both `README.md` and the HuggingFace dataset card.

### Scope defaults adopted (from Handoff Section 11)

| Decision         | Choice                                         | Rationale |
| ---------------- | ---------------------------------------------- | --------- |
| Target size      | **30** cases (not 50)                          | Depth > breadth; benchmark saturation literature confirms |
| Category weight  | **Weighted**: synthesis_sourcing 6, ecosystem 5, enhancement 5, containment 5, screening 5, diagnostics 4 | Tilts toward highest-ambiguity regulatory frontier |
| Case sourcing    | **Mix**: ~20 hypothetical-but-precedented + ~10 documented (test actual Claude behavior) | Empirical grounding + boundary exploration |
| Expert panel     | **Deferred**; author as solo v1.0, note panel as v2.0 roadmap | 2-day window precludes real panel; fabricated panel would be dishonest |
| Field 10 in v1.0 | **Author-anticipated disagreement** (not panel-collected) drawn from candidate's SOMA governance experience + biosecurity literature; each case explicitly flagged as "anticipated, pending panel" | Honesty > fabrication; still delivers structural value for Anthropic readers |
| Publication      | **GitHub + HuggingFace dataset** (JSONL); bioRxiv preprint as stretch goal using local `bioarxiv-harness` | Leverages existing `jang1563` HF account; preprint optional |
| Pre-release      | **Share draft with Anthropic Safeguards** before public release — attach to Greenhouse application and LinkedIn outreach to publicly identifiable current Safeguards / Frontier Red Team members (Mrinank Sharma resigned Feb 2026 with no named replacement, per research intel); if no reply in 5 business days, publish openly with explicit review-invitation line in README | Responsible disclosure per handoff Section 7 |
| Drafting assist  | **Use Claude** (candidate's existing claude.ai access) to accelerate first drafts; author edits every case for biological credibility, regulatory accuracy, and disagreement authenticity | Self-referentially appropriate: model drafts cases about model boundaries, expert judges each |

### Template — fixed 11 fields (verbatim from handoff Section 3, extended)

1. **Case ID and category**
2. **Scenario** — 200-300 words, realistic research context
3. **Query form** — exact phrasing a researcher might ask Claude
4. **Current Claude response** — documented or tested; may be "unknown"
5. **Arguments for refusal** — 2-3 bullets, biosecurity framing
6. **Arguments for allowance** — 2-3 bullets, research-utility framing
7. **Resolving context** — concrete, testable disambiguators (e.g., "user identifies as BSL-3 PI at NIH-funded institution with IBC approval")
8. **Expert recommendation** — candidate's judgment with stated reasoning
9. **Precedent citation** — NSABB case, publication, policy, or analogous precedent
10. **Documented disagreement** — where reasonable experts disagree, structured as: *framework-level* (regulatory vs. empirical vs. ethical) vs. *empirical* (uncertainty about facts) vs. *value* (weights on research freedom vs. catastrophic risk). **v1.0 note**: this field contains *author-anticipated* expert disagreement drawn from the candidate's SOMA governance experience and biosecurity literature. Each case flags this field with "v1.0 anticipated, pending panel review" for full transparency. v2.0 replaces with panel-collected disagreement.
11. **Regulatory anchor** — NSABB/FSAP/BWC/CWC/Australia Group/HHS P3CO/EAR/ITAR category

**Addition informed by research** (optional 12th field, marked where applicable):
12. **Uplift context variable** — would *this* query meaningfully change misuse likelihood given typical user context, or is refusal theater? (per Zhang et al. 2602.23329)

## Execution Phases (solo, target ~2 days total per package ranking)

### Phase 0 — Setup + citation verification (Day 1, first 2 hours)
- Create directory structure above at `/Users/jak4013/Dropbox/Bioinformatics/Claude/AmbiguityCasebook/`
- Copy `Artifact_2_AmbiguityCasebook_Handoff.md` to `_meta/handoff.md`
- Copy this plan to `_meta/plan.md`
- Write `_meta/research_github_hf.md`, `_meta/research_literature.md`, `_meta/research_regulatory.md` by copying the three research agent outputs directly from this planning session's conversation history (they are preserved across plan-exit). These are the ground-truth inputs for case authoring and reference lists — do not re-run the searches unless verifying a specific citation.
- **Verify the regulatory/citation claims** returned by the research agents (EO 14292 May 2025, Australia Group 2025 plenary additions, HHS/OSTP synthesis framework status, specific arXiv IDs like 2502.06867 and 2602.23329) via WebFetch against primary sources before embedding them in case files. Any claim that fails verification is dropped or softened.
- Confirm HuggingFace dataset name `jang1563/ambiguity-casebook` is available (or pick fallback)
- Initialize `README.md`, `template.md`, `taxonomy.md`, `LICENSE` (Apache 2.0)

### Phase 1 — Taxonomy + template lock (Day 1, next 2 hours)
- Draft `taxonomy.md` with explicit scope notes per category (what counts, what doesn't). Ecosystem/Emerging is scoped specifically to **AI-biology convergence** (foundation models, agent tools, automated labs, benchtop synthesis), not general biotech frontier.
- Lock `template.md` at 11 fields + optional 12th (uplift context)
- Stress-test template by drafting 3 pilot cases across 3 categories; iterate template if fields prove ambiguous
- **Sibling-artifact dedup rule**: every case must be primarily about the *dual-use boundary* (should Claude answer?), not primarily about over-refusal (Artifact 1) or rule-writing (Artifact 3). Cases where over-refusal IS the issue stay in Artifact 1; cases that translate directly to rules stay in Artifact 3.

### Phase 2 — Case drafting in passes (Day 1 remaining + Day 2 morning)

Each case: Claude drafts first pass from scenario prompt + template, author edits for biological credibility and regulatory accuracy, author writes the disagreement field from own SOMA/governance knowledge. Target rate: ~15 cases/day with Claude assistance.

**Pass A — Regulatory-anchored cases (8 cases)**: drawn from the regulatory landscape research.
- DURC pause ambiguity (post-EO-14292 GoF research query)
- Benchtop synthesis screening gap (academic lab, 80bp mpox fragment)
- IGSC customer vetting under sanctions ambiguity
- Australia Group 2025 AI-driven gene synthesis control query
- Horsepox-lineage vaccine development sourcing
- BSL-level guidance for emerging pathogen (recent WHO-priority list)
- FSAP Tier-1 pathogen diagnostic primer design
- Gene-drive / iGEM boundary case (synthetic biology oversight)

**Pass B — NSABB-derived cases (6 cases)**: adapted from the seven NSABB DURC categories to query form. Cover: enhanced transmissibility, enhanced virulence, host-range alteration, immune evasion, therapeutic evasion, enabling-weaponization, and reconstitution.

**Pass C — Documented Claude-behavior cases (10 cases)**: test candidate's own dual-use-boundary queries against Claude via claude.ai (within Anthropic's usage policy — representative researcher queries, not adversarial jailbreak attempts); optionally solicit boundary refusals from colleagues. Cases here focus on *boundary* (would reasonable experts disagree on allow/refuse?) not on over-refusal-as-defect (which goes to Artifact 1). If a candidate case is really an over-refusal case, reassign to Artifact 1 to avoid duplication.

**Pass D — Ecosystem / AI-era cases (6 cases)**: foundation-model orchestration, automated-lab integration, agent tools for biology, retrieval-augmented biology, multi-turn escalation, cross-query intent.

### Phase 3 — Index + cross-references (Day 2 afternoon, first 2 hours)
- Build `cases.jsonl` with all 11 (or 12) fields per case
- Build `cross_references.md`: by category, by regulatory anchor, by precedent type, by disagreement framework
- Write `references/regulatory_mapping.md` (from regulatory research brief)
- Write `references/literature_cited.md` (from literature research brief)
- Write `references/nsabb_sources.md`

### Phase 4 — README, self-review, publish (Day 2 afternoon, final 2 hours)
- Finalize `README.md`: methodology, navigation, defensive framing (Section 7 of handoff verbatim), explicit v1.0-vs-v2.0 scope, expert-panel roadmap
- Self-review checklist (handoff Section 9): all 11 fields present, every case traceable to precedent, defensive-framing pass, JSONL manual schema check (field names + types, no Pydantic needed at this scale)
- Publish to GitHub (`jang1563/ambiguity-casebook`)
- Upload `cases.jsonl` + scenario metadata as HuggingFace dataset (`jang1563/ambiguity-casebook`). Include a proper HF dataset card: YAML frontmatter with `license: cc-by-4.0`, `task_categories`, `tags: [biosecurity, dual-use, ai-safety, casebook]`; a description, citation block, and "intended use / out-of-scope use" section matching the defensive framing.
- Draft concise responsible-disclosure email with casebook link. Channels: (a) Greenhouse application cover letter includes the link; (b) LinkedIn outreach to publicly identifiable current Safeguards / Frontier Red Team members (per Feb 2026 intel, Mrinank Sharma resigned with no named replacement — use other current employees or the general safeguards contact). If no response in 5 business days, publish openly with explicit review-invitation line in the README.
- **Optional stretch (post-Day-2)**: draft bioRxiv preprint using `bioarxiv-harness` template; submit only after Anthropic Safeguards response (or 5-business-day timeout)

## Critical files to create/reference

**New files (to create during execution — out of plan mode):**
- All files under `AmbiguityCasebook/` per the directory layout above

**Source files (read-only inputs):**
- `/Users/jak4013/Dropbox/Lab/Post-doc_cmlab/Application/Anthropic/Application_documents/Application_strategy/2026_04_15/Anthropic_BioSafety_RS_Package/Artifacts/Artifact_2_AmbiguityCasebook_Handoff.md` (handoff; copied to `_meta/handoff.md`)
- `…/Research/Anthropic_BioSafety_Deep_Research_2026_04_15.md`
- `…/Research/Portfolio_Key_Points_2026_04_15.md`
- `…/Research/Anthropic_BioSafety_Handoff_2026_04_16.md`
- `…/Artifacts/Artifact_1_OverRefusal_Handoff.md` (sibling — cross-reference)
- `…/Artifacts/Artifact_3_ConstitutionRules_Handoff.md` (sibling — cross-reference)

**Tooling to reuse (already in candidate's environment):**
- `bioarxiv-harness` (at `/Users/jak4013/Dropbox/…` — candidate's bioRxiv LaTeX template) for optional preprint
- HuggingFace account `jang1563` (already hosts 14+ datasets) for dataset publishing

## Verification

- **Completeness**: 30 case files across 6 categories, each with all 11 template fields non-trivially filled; `cases.jsonl` has one valid JSON object per line with the 11 field names present
- **Traceability**: every case cites ≥1 precedent (NSABB case, publication, policy doc, or historical analog) in field 9
- **Regulatory coverage**: every case has a non-trivial regulatory anchor in field 11; `cross_references.md` shows all of NSABB/DURC, FSAP, Australia Group, BWC, IGSC represented across the casebook
- **Defensive framing pass**: self-review against handoff Section 7 — zero novel threat scenarios, zero operational pathways, zero novel agent enumeration beyond NSABB public literature. Stretch goal: one colleague from SOMA network scans 5-10 random cases for operational uplift risk (~30 min of their time)
- **Template consistency**: automated check that every case file has all 11 H2 headers present
- **JSONL validity**: `cases.jsonl` loads cleanly in Python `json` line-by-line; manual field-name/type check (no formal schema library needed at 30-case scale)
- **Publication verification**: GitHub repo renders correctly; HuggingFace dataset downloads and parses; README navigation links all resolve
- **External-facing integrity**: README explicitly states v1.0 is solo-authored and names expert-panel review as v2.0 roadmap; responsible-disclosure line invites Anthropic Safeguards feedback before broader distribution

## Out of scope for v1.0 (deferred to v2.0)

- Full 6-8 expert panel review (requires $3k-$8k honoraria + 4-6 weeks)
- Expansion from 30 → 50 cases
- Disagreement meta-analysis across reviewers
- Formal biosecurity-journal submission (Health Security, Frontiers in Bioengineering)
- Interactive searchable web UI
