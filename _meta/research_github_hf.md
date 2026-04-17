# Research Brief — GitHub / HuggingFace Landscape Scan

**Date:** 2026-04-16
**Agent:** Explore (GitHub/HF focus)
**Purpose:** Identify existing casebook-style resources for dual-use biology AI safety and map the gap our Ambiguity Casebook fills.

---

## Dual-Use AI Biology Casebook: Gap Analysis Report

Based on systematic searches across GitHub, HuggingFace, bioRxiv, and web resources, here is the existing landscape of dual-use biology + AI safety resources.

### 1. Closest Existing Resources

1. **WMDP Benchmark (Weapons of Mass Destruction Proxy)** — Center for AI Safety, 2024
   - **Link:** [GitHub: centerforaisafety/wmdp](https://github.com/centerforaisafety/wmdp), [HF Dataset: cais/wmdp](https://huggingface.co/datasets/cais/wmdp)
   - **Format:** 3,668 multiple-choice questions across bio (1,273), cyber (1,987), chem (408)
   - **Coverage:** Proxy knowledge in bioweapons/bioterrorism, viral genetics, vector engineering, pandemic pathogens
   - **Gap vs. Casebook:** MCQ format only; no scenario context or regulatory anchoring; refusal-focused rather than ambiguity-navigating; no expert disagreement documentation; designed to filter before public release (sanitized proxy knowledge)

2. **Dual-Use AI Challenge Benchmark** — arXiv:2502.06867
   - **Format:** "Scientific Refusal Test" across biology, chemistry, computer security
   - **Coverage:** Red-team methods for sensitive domains; guardrail consistency testing
   - **Gap:** Primary focus on refusal/rejection consistency; no case-by-case decision reasoning; unclear if dataset is publicly released with examples

3. **LLM Novice Uplift Study** — arXiv:2602.23329
   - **Format:** Multi-model benchmark evaluation (8 biosecurity task sets)
   - **Coverage:** Novices with LLM access vs. internet access; expert uplift comparison (novices with LLM outperformed experts on 3/4 benchmarks)
   - **Gap:** Benchmark-driven (MCQ style); no casebook structure; focused on capability measurement, not decision boundaries

4. **LAB-Bench (Language Agent Biology Benchmark)** — Future-House et al., arXiv:2407.10362
   - **Format:** 2,400+ multiple-choice questions
   - **Coverage:** Biology research capabilities (literature recall, practical reasoning, lab protocols)
   - **Gap:** General research capability (not safety-focused); no dual-use flagging or ambiguity mapping; no scenario context

5. **BioLP-bench** — Benchmark for biological lab protocol understanding
   - **Format:** Multi-choice tasks with protocol errors/corrections
   - **Coverage:** Lab protocol comprehension and error detection
   - **Gap:** Practical/technical skills only; not safety-oriented; no dual-use decision framework

6. **SOSBench (Safety on Science Bench)** — Regulation-grounded, UK government
   - **Link:** [UK Gov Inspect Evals](https://ukgovernmentbeis.github.io/inspect_evals/evals/knowledge/sosbench/)
   - **Format:** 3,000 prompts from real-world regulations
   - **Coverage:** 6 high-risk domains (chemistry, biology, medicine, pharmacology, physics, psychology); LLM-assisted evolutionary pipeline for diverse misuse scenarios
   - **Gap:** Prompt collection with scenarios (better than MCQ alone), but lacks case study structure; no expert judgment documentation; regulatory anchoring is by-domain, not query-level decision guidance

7. **HarmBench** — Center for AI Safety, arXiv:2402.04249
   - **Format:** Behavior Registry (510 behaviors × 7 semantic categories × 4 functional types); standardized evaluation framework
   - **Coverage:** 18 red-teaming attack methods; 33 LLM+defense combinations; includes chemical/bioweapons (209 behaviors)
   - **Gap:** General harm categories (not bio-specific); no regulatory/DURC framework; focuses on jailbreak attack-defense pairs, not ambiguity resolution; no expert disagreement documentation

8. **FrontierScience Benchmark** — OpenAI, 2025
   - **Format:** 700+ expert-written questions (Olympiad + Research tracks)
   - **Coverage:** PhD-level scientific reasoning in physics, chemistry, biology (42 Olympiad medalists, 45 PhD scientists)
   - **Gap:** Capability/performance benchmark, not safety-focused; no dual-use flagging; not publicly released with examples

9. **SecureBio Virology Capabilities Test (VCT)** — SecureBio/CAIS, 2025
   - **Format:** 322 expert-written questions (text + images, tacit knowledge)
   - **Coverage:** Complex virology lab protocol troubleshooting
   - **Gap:** Narrow scope (virology only); no scenario/context; expert benchmark but not decision-support oriented

10. **Gryphon Scientific + RAND Biorisk Evaluations**
    - **Work:** Red-teaming, evaluation development, controlled experiments, biosecurity policies
    - **Gap:** No publicly released casebook-style dataset (internal/proprietary assessments)

11. **Dual-Use Capabilities of Concern (PLOS Comp Bio, e1012975)** — Pannu et al., May 2025
    - **Link:** [PLOS Comp Bio](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1012975)
    - **Format:** Literature review + policy framework (not a benchmark dataset)
    - **Coverage:** Adapts traditional DURC framework to AI capabilities; CBRN threat categories
    - **Gap:** Conceptual framework, no concrete case dataset; theoretical guidance without decision-support

12. **NSABB DURC Framework** — US Government Policy
    - **Format:** Federal oversight policy document
    - **Coverage:** Risk identification, mitigation, researcher responsibility, institutional review
    - **Link:** [ASPR DURC Policy](https://aspr.hhs.gov/S3/Documents/durc-policy.pdf)
    - **Gap:** Institutional/grant-level governance (not query/model-level); designed for lab safety, not LLM safeguards

13. **iGEM Biosecurity Case Studies**
    - **Format:** Project-level case-by-case risk assessments (gene drives, synthetic biology)
    - **Coverage:** Adaptive risk management, lifecycle review, edge-case identification
    - **Gap:** Institutional/project-scope; no LLM/AI safety adaptation; limited public casebook

---

### 2. Critical Gap Analysis

| Dimension | Existing Resources | Casebook Vision | Gap |
|-----------|-------------------|-----------------|-----|
| **Granularity** | Benchmark-level (MCQ, broad categories) | Query-level (individual prompt→decision) | No existing resource operates at query-level decision boundary |
| **Ambiguity Centering** | Refusal-focused or capability-focused | Ambiguity-navigating (borderline cases) | None center on "should this be allowed?" edge cases |
| **Regulatory Anchoring** | NSABB framework exists but not adapted to queries | DURC principles + NSABB re-interpreted for safeguards | No resource bridges institutional policy to model decision |
| **Expert Disagreement** | Rare documentation of rater disagreement (DICES, mental health AI mention uncertainty) | Explicitly document expert disagreement + decision rationale | No bio-safety casebook tracks expert uncertainty |
| **Scenario Context** | SOSBench provides scenarios; LAB-Bench/WMDP do not | Deep scenario context (background, justification, constraints, misuse vectors) | Scenarios exist but lack depth for decision-support |
| **Structured Format** | Varied (MCQ, prompt collections, red-team registries) | Standardized: scenario + query + expert judgment + disagreement + regulatory basis | No unified casebook format |
| **Scale** | 300–3,000 items typical | 30–50 cases (depth over breadth) | Different paradigm: curated expert cases vs. large-scale benchmarks |
| **Decision Type** | Pass/fail safety, capability, refusal success | Gradient decisions: clearly allow / allow-with-monitoring / clearly refuse / expert-disagreement / context-dependent | No existing resource handles non-binary safety judgments |

---

### 3. Overlap with Prior Art

- **Mentioned arXiv:2502.06867 (Dual-Use AI Challenge):** Located; focus on refusal consistency, not ambiguity cases
- **Mentioned arXiv:2602.23329 (LLM Novice Uplift):** Located; capability uplift study, not safety casebook
- **PLOS Comp Bio 10.1371/journal.pcbi.1012975:** Located; excellent conceptual framework but not a dataset
- **NSABB framework:** Fully documented; no LLM-specific adaptation exists
- **iGEM Biosecurity cases:** Exist but scattered across web; no unified casebook format

---

### 4. Unexpected Finds

1. **Expert disagreement is under-documented:** Multiple papers note that when experts disagree on safety, benchmarks treat disagreement as noise rather than signal. A casebook that explicitly captures disagreement (framework differences, value disagreements, empirical uncertainties) would be novel.

2. **Query-level decision-making gap is acute:** Most resources operate at benchmark/capability level. The specific need for "what should Claude do on *this* query?" is not systematically addressed in any public resource.

3. **Regulatory policy → model decision is uncharted:** NSABB/DURC frameworks exist for institutional review, but no public work adapts institutional decision logic to query-level LLM safeguards.

4. **Scenario depth varies wildly:** SOSBench provides scenarios; HarmBench is behavior-focused; LAB-Bench is MCQ. None combine scenario richness with expert disagreement tracking + regulatory logic.

5. **RAND and Gryphon work is largely private:** Despite their prominence in biosecurity + AI, evaluations are proprietary or not yet published as open casebooks.

---

### 5. Suggested Concrete Casebook Additions

1. **Expert Disagreement Module**
   - For each case, track: expert votes (allow/monitor/refuse), reasoning diversity (regulatory vs. empirical vs. ethical concerns), confidence levels, and resolution logic if consensus exists
   - Model: Adapt from DICES dataset structure + mental health AI safety work showing disagreement on high-stakes content
   - Rationale: No existing bio-safety casebook documents this; critical for safeguards teams understanding judgment boundaries

2. **Regulatory Anchoring Card**
   - Each case includes explicit mapping to NSABB categories + specific federal policy citations
   - Include "regulatory ambiguity flag" for cases where institutional DURC review itself would be uncertain
   - Model: Adapt from PLOS e1012975 framework + iGEM case-by-case approach
   - Rationale: Bridges institutional policy to model-level decisions; satisfies Safeguards teams' need for defensible compliance

3. **Misuse Vector Documentation**
   - For each case, explicitly document: legitimate research use, likely misuse pathway, skill/resource prerequisites for misuse, and whether query-level refusal meaningfully degrades misuse likelihood
   - Model: Inspired by SOSBench misuse scenarios + BioLP-bench protocol error patterns
   - Rationale: Forces clarity on whether refusal is theater (query too specific to matter) vs. substantive risk reduction

4. **Decision Boundary Case Clustering**
   - Organize cases by "ambiguity intensity": (a) clear refusal (high consequence), (b) defensible allow (legitimate research), (c) decision boundary (expert disagreement expected), (d) context-dependent (depends on user/deployment)
   - Rationale: Acknowledges that not all cases are binary; helps Safeguards teams understand where their confidence should be lower

5. **Comparative LLM Response Track** (optional, longitudinal)
   - Each case includes: ground-truth judgment + actual responses from 2–3 frontier models
   - Identify failure modes by model (e.g., Claude refuses conservatively, GPT-4 allows broadly)
   - Rationale: Connects casebook to real deployment; helps Red Teams/Safeguards understand which models need which guardrails

---

### 6. Final Assessment

The landscape is rich in **capability benchmarks** (LAB-Bench, FrontierScience, BioLP-bench) and **refusal robustness** (HarmBench, WMDP, SOSBench), but **absent** in domain-expert-authored casebooks for query-level ambiguity navigation. The NSABB/DURC framework is mature at the institutional level, but no resource has translated it to safeguards-team decision support. Our casebook fills a genuine gap: expert-curated, regulatory-grounded, ambiguity-centered cases for LLM safeguards teams to calibrate their judgment on borderline biology queries.

---

### Sources
- [Dual-Use AI Challenge (arXiv:2502.06867)](https://arxiv.org/pdf/2502.06867)
- [LLM Novice Uplift (arXiv:2602.23329)](https://arxiv.org/pdf/2602.23329)
- [WMDP Benchmark](https://github.com/centerforaisafety/wmdp)
- [LAB-Bench (arXiv:2407.10362)](https://arxiv.org/abs/2407.10362)
- [SOSBench](https://ukgovernmentbeis.github.io/inspect_evals/evals/knowledge/sosbench/)
- [HarmBench (arXiv:2402.04249)](https://arxiv.org/abs/2402.04249)
- [PLOS CompBio: Dual-Use Capabilities (e1012975)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1012975)
- [NSABB DURC Policy](https://aspr.hhs.gov/S3/Documents/durc-policy.pdf)
- [OpenAI FrontierScience](https://openai.com/index/frontierscience/)
- [Epoch AI on Biorisk Evaluations](https://epoch.ai/gradient-updates/do-the-biorisk-evaluations-of-ai-labs-actually-measure-the-risk-of-developing-bioweapons/)
