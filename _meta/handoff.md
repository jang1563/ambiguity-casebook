# Artifact 2 — Dual-Use Ambiguity Casebook

Handoff document for independent execution in a separate Claude session.

## Section 1 — Quick Context

- **Goal:** Produce 30-50 structured cases that sit exactly at the dual-use decision boundary. Each case uses a fixed template: scenario, query, arguments both ways, resolving context, expert recommendation, documented disagreement.
- **Why Anthropic cares:** The Safeguards team and Frontier Red Team debate similar cases weekly. Their internal methodology is not public. A well-structured casebook from a domain expert becomes a shared reference for the decisions the team makes daily.
- **Effort:** Highest per-unit quality bar of the three artifacts. Each case requires genuine biological reasoning that survives expert review.
- **Risk:** Low-to-moderate. Cases use historical/public scenarios from NSABB literature and researcher interviews; no novel threat scenarios are generated.
- **Candidate fit:** Only a domain expert with biosecurity governance experience (SOMA: EAR/ITAR, DURC review, 100+ institutions) can author these cases credibly.

## Section 2 — Full Context

### The problem Anthropic faces

NSABB's Dual-Use Research of Concern (DURC) framework provides a formal structure for case analysis but predates large language models. Every published NSABB case addresses a pre-LLM scenario (manuscript submission review, gain-of-function research oversight). There is no AI-era equivalent — no structured casebook of the specific query-level decisions a frontier model like Claude must make.

Anthropic's Frontier Red Team has spent 150+ hours with biosecurity experts red-teaming Claude, but the methodology is not public. The Safeguards team must make similar judgment calls daily. Training Constitutional Classifiers requires consistent decisions about where the line falls in specific dual-use-adjacent biology scenarios, and those decisions must be auditable and defensible.

What would help: a structured casebook showing 30-50 specific scenarios with arguments both ways, the context that resolves the ambiguity, and documented disagreement between reasonable experts. This is exactly what a biologist with biosecurity governance experience can produce.

### Why this candidate uniquely fits

- PhD Biomedical Science and Engineering, BSL-2 wet lab, 60+ publications — can write biologically credible scenarios
- SOMA co-founder coordinating biosecurity governance across 100+ institutions in 25+ countries — has navigated EAR/ITAR, DURC review, material transfer agreements at scale
- Constitutional BioGuard author (7 NSABB categories) — already implemented the decision framework in a working classifier
- 23+ mentees across institutional contexts — has seen the spectrum of legitimate research questions first-hand

### What existing work covers

- NSABB DURC Companion Guide (osp.od.nih.gov): canonical case framework, pre-LLM
- Dual-Use AI Challenge Benchmark (arXiv:2502.06867): controlled substance queries with prompt variation
- LLM Novice Uplift study (arXiv:2602.23329): documents where AI creates ambiguity zones
- PLOS Comp Bio "Dual-use capabilities of concern" (2024): conceptual framework
- Anthropic Frontier Red Team announcements (anthropic.com/news/strategic-warning): methodology not public
- iGEM Biosecurity Case Studies (tandfonline 2020): synthetic biology cases

### The gap

None of the above provides: AI-era query-level decisions + structured template + expert-panel-validated disagreement documentation + scale of 30-50 cases.

## Section 3 — Scope

### Target size: 30-50 cases

### Category distribution (initial taxonomy)

Approximately balanced across six categories:
- **Enhancement research** (~8 cases): questions about functional enhancement of biological systems in research context
- **Containment and biosafety** (~8 cases): questions about BSL-level requirements, handling protocols, institutional oversight
- **Synthesis and sourcing** (~8 cases): questions about obtaining, ordering, or synthesizing biological materials
- **Diagnostics and surveillance** (~6 cases): questions about detection, identification, or characterization of biological agents
- **Screening and review** (~6 cases): questions about dual-use review, gene synthesis screening, manuscript review
- **Ecosystem and emerging technology** (~6 cases): questions about automated labs, foundation models, AI orchestration in biological research

### Fixed case template (required fields per case)

1. **Case ID and category**
2. **Scenario** (200-300 words describing realistic research context)
3. **Query form** (exact phrasing a researcher might ask Claude)
4. **Current Claude response** (if publicly documented or tested directly; may be "unknown")
5. **Arguments for refusal** (2-3 bullet points, biosecurity or safety framing)
6. **Arguments for allowance** (2-3 bullet points, research utility and legitimacy framing)
7. **Resolving context** (what additional information from the user or query would clearly tilt the decision toward allow or toward refuse)
8. **Expert recommendation** (candidate's judgment with reasoning)
9. **Precedent citation** (NSABB case, publication, policy decision, or analogous historical precedent)
10. **Documented disagreement** (where reasonable experts would disagree, and why)
11. **Regulatory anchor** (which NSABB/FSAP/BWC/CWC/Australia Group category applies, if any)

### Quality bar

- Each scenario must read as plausible to a domain expert in the relevant subfield
- Each argument both ways must reflect genuine considerations, not strawmen
- Each resolving context must be concrete and testable (e.g., "user identifies as a BSL-3 PI at an NIH-funded institution with IBC approval" is concrete; "user has legitimate research purpose" is not)
- Each expert recommendation must have stated reasoning the reviewer can agree or disagree with
- Each disagreement documented must be a real disagreement, not a rhetorical straw position

## Section 4 — Methodology

### Phase 1: Taxonomy and template validation

- Finalize 6-category taxonomy with category-level scope notes
- Finalize fixed case template with field definitions
- Draft first 5 cases to stress-test the template
- Iterate template based on Phase 1 drafting experience

### Phase 2: Source mining

- Mine NSABB published decisions for scenarios adaptable to AI-query form
- Review Gryphon Scientific published methodology for scenario inspiration
- Solicit from research colleagues: "real Claude refusals you thought were wrong"
- Pull from iGEM biosecurity case studies
- Reference public Anthropic Frontier Red Team communications for topic areas

### Phase 3: Drafting

- Write first 10 cases using fixed template
- Self-review for template consistency and biological credibility
- Circulate first 10 cases to 2-3 expert reviewers for template validation

### Phase 4: Expert panel review

- Recruit 6-8 expert reviewers (biosecurity experts, working biologists, safety/ethics specialists, policy background)
- Distribute cases individually for independent review
- Collect feedback on: arguments both ways (completeness), resolving context (concreteness), expert recommendation (reasoning quality), disagreement (authenticity)

### Phase 5: Expansion

- Incorporate reviewer feedback
- Expand to 30-50 cases balanced across categories
- Ensure Tier 5-style genuine ambiguity cases are included (some cases should have no clear answer)

### Phase 6: Disagreement analysis

- Identify disagreement patterns across reviewers
- Document in separate analysis file: where do biosecurity experts and working biologists most often disagree? Where do safety/ethics specialists disagree with operational biologists?
- Include this meta-analysis in the final casebook

### Phase 7: Publishing

- Structure markdown for each case (`case_01.md` through `case_50.md`)
- Build JSONL index (`cases.jsonl`) with all field values for machine processing
- Build searchable index and cross-references (by category, by regulatory anchor, by precedent)
- Publish as GitHub repo; optional preprint

## Section 5 — Prior Art and Novelty

### Closest existing work with URLs

- NSABB DURC Companion Guide: https://osp.od.nih.gov (policies, case studies)
- Dual-Use AI Challenge Benchmark: https://arxiv.org/abs/2502.06867
- LLM Novice Uplift study: https://arxiv.org/abs/2602.23329
- PLOS Comp Bio "Dual-use capabilities of concern": https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1012975
- Anthropic Frontier Red Team progress: https://www.anthropic.com/news/strategic-warning-for-ai-risk-progress-and-insights-from-our-frontier-red-team
- iGEM Biosecurity Cases: https://www.tandfonline.com/doi/full/10.1080/10736700.2020.1866884
- Gryphon Scientific methodology discussion: https://thebulletin.org/2024/06/

### Genuinely novel

- AI-era cases (query-level decisions rather than manuscript or research-program-level)
- Fixed structured template (NSABB cases vary in structure)
- Expert panel disagreement documentation (transparent disagreement, not hidden)
- Scale (30-50 cases in one resource vs. scattered historical cases)
- Regulatory mapping (explicit NSABB/FSAP/BWC/CWC anchoring per case)

### Novelty risks

- NSABB cases are authoritative; our cases must cite and extend, not contradict
- Historical cases can feel outdated when adapted to AI-query form — the adaptation itself is novel contribution

## Section 6 — Task Breakdown

Executable task list (convert to TodoWrite in new session):

1. Read handoff, read plan file, read three reference files for full context
2. Finalize 6-category taxonomy with explicit scope per category
3. Finalize fixed case template with field definitions
4. Draft first 5 cases to stress-test template
5. Iterate template based on stress-test
6. Mine NSABB published decisions for adaptable scenarios
7. Solicit real Claude refusals from research colleagues
8. Draft first 10 cases using finalized template
9. Self-review for consistency and credibility
10. Send first 10 cases to 2-3 expert reviewers for template validation
11. Recruit 6-8 expert panel for full review (see Section 11)
12. Distribute cases for independent review
13. Collect and aggregate reviewer feedback
14. Incorporate feedback and expand to 30-50 cases
15. Run disagreement analysis across reviewer feedback
16. Format all cases as structured markdown
17. Build JSONL index for machine processing
18. Build searchable index and cross-references
19. Publish GitHub repo
20. Optional: submit to biosecurity journal (Health Security, Frontiers in Bioengineering)

## Section 7 — Defensive Framing

### What the casebook does NOT contain

- No novel threat scenarios
- No operational uplift content
- No synthesis pathways
- No detailed threat-actor personas
- No enumeration of specific dangerous organisms or agents beyond what is in NSABB case literature

### What the casebook DOES contain

- Scenarios already public in NSABB cases, iGEM reports, or published biosecurity literature, adapted to AI-query form
- Decision framework arguments at the policy/judgment level, not the operational detail level
- Regulatory anchors to public frameworks

### Expert panel validation of defensive posture

Each case reviewed by at least 2 reviewers with an explicit question: "Does this case provide operational uplift beyond public literature?" If any reviewer answers yes, the case is revised or removed.

### Responsible disclosure

Before public release, share draft with Anthropic Safeguards team (if appropriate contact identified). Offer to hold cases private if they prefer.

## Section 8 — Deliverable Structure

```
Artifacts/02_ambiguity_casebook/
├── README.md                           # project overview, methodology, navigation
├── template.md                         # fixed case template with field definitions
├── taxonomy.md                         # 6-category definitions with scope notes
├── cases/
│   ├── enhancement/
│   │   ├── case_01.md
│   │   └── ... (~8 cases)
│   ├── containment/
│   │   └── ... (~8 cases)
│   ├── synthesis_sourcing/
│   ├── diagnostics_surveillance/
│   ├── screening_review/
│   └── ecosystem_emerging/
├── cases.jsonl                         # machine-readable index of all cases
├── cross_references.md                 # by category, by regulatory anchor, by precedent
├── expert_panel/
│   ├── reviewer_roster.md              # (anonymized if preferred)
│   ├── feedback_log.md
│   └── disagreement_analysis.md
├── references/
│   ├── nsabb_sources.md
│   ├── regulatory_mapping.md
│   └── literature_cited.md
└── LICENSE                             # Apache 2.0
```

### Case file format

Each `case_XX.md` follows the fixed 11-field template from Section 3. JSONL index mirrors the same fields.

## Section 9 — Verification

- Each case reviewed by at least 2 independent experts (see Section 11 for panel)
- Disagreement documented for every case where reviewers disagree
- Every case traceable to a precedent (NSABB case, published paper, policy document, or documented analogous situation)
- Template consistently applied (all 11 fields present, non-trivial in every case)
- Searchable index complete (by category, by regulatory anchor)
- Defensive framing checklist signed off: no case provides operational uplift
- JSONL index loads and validates against schema

## Section 10 — Integration with Application

### CV integration

Add to CV under "Bio Safety Artifacts (Apr 2026)":
> **Dual-Use Ambiguity Casebook** — 30-50 structured cases covering the dual-use decision boundary with expert panel validation. Each case includes biological reasoning, arguments both ways, resolving context, and documented disagreement. Modeled on NSABB DURC framework adapted for AI-query decisions. [GitHub link]

### Cover letter integration

Cover letter paragraph 3: "I have written 30-50 structured dual-use ambiguity cases with expert panel validation, covering the exact decisions your team debates weekly. Each case documents the biological reasoning, arguments both ways, and where reasonable experts disagree. I would bring this case methodology to the Safeguards team."

### Interview prep

- Be ready to walk through 2-3 cases on demand
- Prepare to discuss disagreement patterns (where biosecurity experts and working biologists most often split)
- Offer to write a case live during interview

## Section 11 — Open Decisions (for user to resolve at execution)

1. **Publication openness.** Publish casebook openly or share with Anthropic first? Recommendation: share draft with Anthropic Safeguards team before public release; publish openly after internal review unless Anthropic requests private hold.
2. **Expert panel composition and compensation.** Target 6-8 reviewers across biosecurity experts (2), working biologists (2), safety/ethics (1-2), policy (1-2). Budget: $500-$1000/reviewer honorarium. Recruit via personal network, SOMA contacts, or formal outreach to NTI/CSHP/RAND.
3. **Case sourcing.** Include cases where current Claude behavior is publicly documented (test them ourselves), or only hypothetical cases? Recommendation: mix — some documented cases for empirical grounding, some hypothetical for boundary exploration.
4. **Category weighting.** Distribution across 6 categories — even split or weighted toward highest-ambiguity categories (enhancement, synthesis)?
5. **Target size.** 30 (focused, deep) or 50 (comprehensive)? Recommendation: start with 30 high-quality cases; expand to 50 if time and reviewer capacity allow.
6. **Preprint target.** Biosecurity journal (Health Security, Frontiers in Bioengineering), arXiv-only, or GitHub + blog post only?

## Reference Files in Package

- `../Research/Anthropic_BioSafety_Deep_Research_2026_04_15.md` — company, team, JD intel
- `../Research/Portfolio_Key_Points_2026_04_15.md` — candidate portfolio inventory
- `../Research/Anthropic_BioSafety_Handoff_2026_04_16.md` — summary with all 30 artifact scores
- `/Users/jak4013/.claude/plans/playful-exploring-bird.md` — plan file with full three-artifact outlines
- `../Artifacts/Artifact_1_OverRefusal_Handoff.md` — sibling handoff for cross-reference

## Session Start Checklist

- [ ] Read this handoff end-to-end
- [ ] Read three reference files for context
- [ ] Confirm with user: Section 11 open decisions resolved
- [ ] Confirm expert panel reviewers identified
- [ ] Initialize `Artifacts/02_ambiguity_casebook/` directory structure
- [ ] Convert Section 6 task breakdown into TodoWrite
- [ ] Begin Phase 1 (taxonomy + template finalization)

---

*End of Artifact 2 handoff. This document is self-contained for independent execution.*