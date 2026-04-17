# Research Brief — Academic Literature Scan (arXiv / bioRxiv / PubMed)

**Date:** 2026-04-16
**Agent:** Explore (literature focus)
**Purpose:** Identify academic prior art, methodological analogues, and citations for the Ambiguity Casebook.

---

## Section A — Direct Prior Art (closest benchmarks and case frameworks)

**1. arXiv:2502.06867 — "Forbidden Science: Dual-Use AI Challenge Benchmark and Scientific Refusal Tests"**
- Authors: Noever & McKee (Feb 2025)
- Provides an open-source dataset and testing framework evaluating LLM safety across controlled substance queries
- Finds significant refusal-vs.-allowance variation: Claude-3.5-sonnet (73% refusal), Mistral (0% refusal), GPT-3.5-turbo (10% refusal)
- **Relevance:** Demonstrates systematic prompt variation methodology and comparative model behavior at the refusal boundary — directly applicable to our query-level decision framework.

**2. arXiv:2602.23329 — "LLM Novice Uplift on Dual-Use, In Silico Biology Tasks"**
- Authors: Zhang et al. (Feb–Mar 2026, latest revision)
- Experimental study: novices with LLM access achieved 4.16× higher accuracy than internet-only controls on biosecurity-relevant tasks
- 89.6% of participants reported minimal difficulty obtaining dual-use information despite LLM safeguards; standalone models often outperformed model-assisted users
- **Relevance:** Gold-standard empirical foundation for understanding uplift dynamics and user-model interaction patterns central to casebook scenarios.

**3. PLOS Computational Biology 10.1371/journal.pcbi.1012975 — "Dual-Use Capabilities of Concern of Biological AI Models"**
- Authors: Pannu et al. (Johns Hopkins Center for Health Security, Stanford, Carnegie Mellon, Fordham; published May 2025)
- Bridges classical DURC frameworks to AI capability assessment; proposes criteria adapted from NSF/NIH DURC definitions
- **Relevance:** Directly translates NSABB precedent to AI-era query classification; essential theoretical grounding for casebook resolving context.

**4. RAND Corporation — "Global Risk Index for AI-enabled Biological Tools" (Sept 2025)**
- First systematic risk-indexing framework for 1,107 AI-enabled biotools across 76 countries
- Five-point misuse capability scale; maturity-vs.-accessibility matrix; Red/Amber/Green classification
- Convened expert panels (June 2024: Johns Hopkins, RAND, biosecurity experts, policymakers) to define hazardous capabilities
- **Relevance:** Provides scalable methodology for structuring "resolving context" and expert recommendation tiers.

**5. SecureBio VCT (Virology Capabilities Test) — 2025 flagship**
- Expert-designed multimodal virology Q&A benchmark; expert virologists averaged 22.1% accuracy in their own sub-specialties
- Large-scale model-vs.-expert comparison now canonical in AI-bio risk discourse
- **Relevance:** Model for expert-baseline calibration and establishing "concerning capability threshold" operationally.

---

## Section B — Context & Framework Literature (NSABB, AI policy, governance anchors)

**1. US Government DURC Policy (May 6, 2024)**
- "United States Government Policy for Oversight of Dual Use Research of Concern and Pathogens with Enhanced Pandemic Potential"
- Supersedes 2012/2014 versions; integrated framework for DURC + pandemic pathogen oversight
- Definition (carried forward): "life sciences research that, based on current understanding, can be reasonably anticipated to provide knowledge, information, products, or technologies that could be directly misapplied to pose a significant threat with broad potential consequences to public health and safety, agricultural crops and other plants, animals, the environment, materiel, or national security"
- **Relevance:** Casebook's normative anchor for "dual-use concern" definition; provides regulatory continuity bridge.

**2. NIH Office of Science Policy — NSABB & Biosafety Modernization (2024–2025)**
- NSABB issued March 2023 recommendations informing May 2024 policy revision
- NIH Biosafety Modernization Initiative (2025): broadens oversight to emerging technologies; strengthens Institutional Biosafety Committees
- IBC transparency mandate (June 1, 2025+): minutes publicly posted
- **Relevance:** Signals institutional environment and recent policy evolution that casebook should reflect.

**3. Frontier Model Forum — Seoul AI Safety Commitments (May 2024)**
- 16 signatories (now 20+); 12 published Frontier AI Safety Frameworks as of Feb 2025
- Requires companies to evaluate CBRN risks from advanced AI
- **Relevance:** Establishes precedent for industry-scale dual-use capability evaluation; framework for understanding how frontier labs operationalize casebook-like decisions.

**4. UK & US AI Safety Institutes Joint Evaluations (2024–2025)**
- US AISI evaluated Claude 3.5 Sonnet on biology, cyber, software capabilities
- UK AISI pre-deployment eval of OpenAI's o1
- Finding: models approach/exceed undergrad-level skills in cybersecurity; some exceed expert baselines in biology *with tools*
- **Relevance:** Live evaluation methodology and benchmark saturation signals that underscore need for fine-grained scenario-based approach.

---

## Section C — Methodological Analogues (case-based evaluation frameworks)

**1. Constitutional AI & Constitutional Classifiers (Anthropic, 2022–2025)**
- CAI: rules-based safeguard training; uses self-critique + preference learning
- Constitutional Classifiers: defended against 3,000+ red-teaming hours; tested against universal jailbreaks across "most target queries"
- C3AI framework: item selection → standardization → curation of machine-readable principles
- **Relevance:** Demonstrates how natural-language rules can be operationalized into decision boundaries; template for casebook "expert recommendation" formulation.

**2. SciSafeEval: Comprehensive Benchmark (arXiv:2410.03769, Oct 2024)**
- 31,840 science safety examples spanning chemistry, biology, medicine, physics
- Multi-prompt conditions: zero-shot, few-shot, chain-of-thought (CoT) + jailbreak
- **Relevance:** Cross-domain safety evaluation design; jailbreak simulation methodology applicable to casebook scenario variation.

**3. LAB-Bench & LABBench2 (July 2024–2026)**
- 2,400+ questions on practical biology research (LitQA, FigQA, TableQA, DbQA, ProtocolQA, SeqQA)
- Later evolved to 1,900+ tasks in realistic contexts (LABBench2)
- **Important caveat:** NOT designed for dual-use risk measurement — focuses on general research capability
- **Relevance:** Demonstrates how to structure granular biology task taxonomy; inverse lesson on why general competence benchmarks miss dual-use boundaries.

**4. RAND Red-Team Study: "Operational Risks of AI in Large-Scale Biological Attacks" (2024)**
- Expert red-team methodology; multi-stage threat model (ideation, acquisition, magnification, formulation, deployment)
- Gryphon Scientific partnership: troubleshooting dataset spanning biothreat creation stages
- **Relevance:** Structured threat-stage taxonomy for organizing case scenarios; expert red-teaming protocol as model.

**5. Scenario-Based Risk Frameworks in Cybersecurity & Ethics**
- Risk-based ethical assessment frameworks demonstrate qualitative scenario analysis
- Ethical OS checklist (8 zones × 14 scenario cards) as catalytic harm-conversation tool
- **Relevance:** Established playbook for scenario-based reasoning in high-stakes domains; transferable structure.

---

## Section D — Key Findings That Shape the Plan

**Finding 1: Benchmark Saturation & Opacity Crisis**
- Epoch AI's analysis (2025): publicly described benchmarks (WMDP-Bio, VCT, etc.) are already saturating; frontier models exceed thresholds
- Opaque "private" evaluations by labs dominate but lack methodological transparency
- **Implication:** Our casebook's strength lies in *structured reasoning transparency* and case-by-case deliberation, not multiple-choice saturation. Invest in multi-argument formats with explicit weighing of pro/con, not closed-form answers.

**Finding 2: Uplift as Primary Decision Signal**
- Zhang et al. (2602.23329) finding that uplift is dramatic (4.16×) and nearly irreversible even with safeguards (89.6% evasion)
- But also: models often underperform their true capability when guided by users
- **Implication:** Our query-level framework should capture *both* uplift potential AND user-model interaction quality, not assume one query = one capability unlock.

**Finding 3: Expert Baseline Variability Is High & Critical**
- SecureBio VCT: expert virology baseline is ~22%, not 90%
- UK/US AISI: with bioinformatic tools, models exceed expert baselines; without, they don't
- **Implication:** Casebook should include contextual resource variables (tool access, literature access, etc.) as part of the scenario, not abstract capability levels.

**Finding 4: NSABB Definition Remains Operationally Vague at Query Level**
- May 2024 DURC policy updated definition but institutional implementation (IBC review) remains traditional — pre-publication, pre-funding, not real-time query
- **Implication:** Our casebook fills a genuine governance gap: real-time LLM-era decision-making at query boundaries. Frame this explicitly as *extending* NSABB logic to frontier model deployment, not replacing it.

**Finding 5: Constitutional/Rule-Based Approaches Are Tractable but Not Sufficient Alone**
- Constitutional AI + Classifiers show that rule-based filtering can block crude jailbreaks but miss subtle cases
- Case-based reasoning (scenario interpretation) complements rules but requires domain expertise
- **Implication:** Our casebook is positioned as *expert decision support tool*, not an automatic classifier. Each case should require interpretive judgment supported by structured arguments, modeling how human + AI teams can deliberate dual-use boundaries.

---

## Section E — Specific Citations for Casebook References

1. Noever, D. A., & McKee, F. (2025). Forbidden Science: Dual-Use AI Challenge Benchmark and Scientific Refusal Tests. arXiv:2502.06867.

2. Zhang, C. B., et al. (2026). LLM Novice Uplift on Dual-Use, In Silico Biology Tasks. arXiv:2602.23329.

3. Pannu, J., et al. (2025). Dual-use capabilities of concern of biological AI models. *PLOS Computational Biology*, 21(5), e1012975. https://doi.org/10.1371/journal.pcbi.1012975

4. RAND Corporation. (2025). Global Risk Index for AI-enabled Biological Tools: Summary Assessment & Methods Report. (External Publication EP71093). https://www.rand.org/pubs/external_publications/EP71093.html

5. Bai, Y., Kadavath, S., et al. (2022). Constitutional AI: Harmlessness from AI Feedback. arXiv:2212.08073.

6. Li, T., et al. (2024). SciSafeEval: A Comprehensive Benchmark for Safety Alignment of Large Language Models in Scientific Tasks. arXiv:2410.03769.

7. U.S. Government. (2024, May 6). Policy for Oversight of Dual Use Research of Concern and Pathogens with Enhanced Pandemic Potential. https://aspr.hhs.gov/S3/Documents/durc-policy.pdf

8. Frontier Model Forum. (2024, May). Frontier AI Safety Commitments, AI Seoul Summit 2024. https://www.frontiermodelforum.org/

9. UK AI Security Institute & US AI Safety Institute. (2024–2025). Pre-deployment evaluations of frontier LLMs. https://www.aisi.gov.uk/

10. METR & Apollo Research. (2024–2025). Frontier AI Capabilities & Autonomous Evaluation Methodology. https://metr.org/, https://www.apolloresearch.ai/

11. SecureBio. (2025). Virology Capabilities Test (VCT): A Multimodal Virology Q&A Benchmark. https://securebio.org/

12. National Institutes of Health, Office of Science Policy. (2024). Biosafety and Biosecurity Policy; Biosafety Modernization Initiative. https://osp.od.nih.gov/policies/biosafety-and-biosecurity-policy/

13. Council on Strategic Risks. (2025). Assessing Dual-Use Issues at the AIxBio Convergence. https://councilonstrategicrisks.org/

14. Epoch AI. (2025). Do the Biorisk Evaluations of AI Labs Actually Measure the Risk of Developing Bioweapons? https://epoch.ai/gradient-updates/do-the-biorisk-evaluations-of-ai-labs-actually-measure-the-risk-of-developing-bioweapons/

---

## Handoff Summary

Our casebook adapts NSABB frameworks to real-time LLM query evaluation and fills a critical gap: while benchmarks saturate rapidly and institutional review remains pre-publication, frontier models require decision-making at the moment of query. The literature confirms:

- **Uplift is the primary concern** but highly variable by context (user expertise, available tools, prompt structure)
- **Expert baselines anchor risk** but are domain-specific and tool-dependent
- **Transparency in reasoning** matters more than classification accuracy as benchmarks saturate
- **Constitutional/rule-based + case-based reasoning** is a tractable hybrid for governance
- **Recent policy evolution** (May 2024 DURC, Seoul commitments, UK/US AISI evaluations) positions this work as timely operationalization of emerging standards

The 11-field structure (scenario, query, arguments both ways, resolving context, expert recommendation, regulatory anchor, etc.) aligns with best practices from Constitutional AI, RAND's risk indexing, and Epoch AI's methodological critiques. Prioritize capturing **expert deliberation and conditional reasoning** over certainty.
