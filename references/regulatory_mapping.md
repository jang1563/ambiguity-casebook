# Regulatory Mapping

Per-framework summary of which regulations apply to which case categories, with status notes as of April 2026.

---

## NSABB / DURC Framework

**Scope:** Research that generates, transfers, or uses agents or toxins in ways that could be misused to pose a significant threat to public health, agriculture, plants, animals, the environment, or materially threatens U.S. national security or economic security. Seven DURC categories defined.

**Status (April 2026):** HHS DURC Policy reportedly paused under executive action (May 2025). ⚠️ EO number unverified. NIH Guidelines remain in effect.

**Relevant cases:** ENH-01, ENH-05, SCR-01, SCR-02, ECO-03

**DURC Categories represented in casebook:**
- Category 1 (enhanced transmissibility): ENH-01, ENH-03 (negative case), ECO-03
- Category 2 (enhanced virulence): ENH-01 (adjacent), ENH-05
- Category 3 (host range alteration): ENH-02 (educational), CON-01 (adjacent)
- Category 5 (increased evasion of immune response): ENH-05 (adjacent)
- Category 7 (reconstruct eradicated/extinct pathogen): SYN-05

---

## FSAP / Federal Select Agent Program

**Scope:** Possession, use, and transfer of Select Agents and Toxins. Tier 1 agents are highest risk. Registration required; FSAP-excluded strains and procedures do not require registration.

**Status:** Active. Administered jointly by CDC (human pathogens) and USDA (agricultural pathogens).

**Relevant cases:** CON-02, CON-05, DIA-01, DIA-03, DIA-04, SCR-04, SCR-05, SYN-01

**Tier 1 agents in casebook:** *Bacillus anthracis* (virulent, DIA-01), *Burkholderia pseudomallei* (DIA-04), *Coxiella burnetii* (DIA-03), *Ebola virus* (SCR-04 — Tier 1 agent, GP-only construct may be excluded), *Francisella tularensis* type A (DIA-04), *Yersinia pestis* (SYN-01, SCR-05)

---

## IGSC / International Gene Synthesis Consortium

**Scope:** Sequence screening and customer vetting for gene synthesis orders. Applies to IGSC member providers and, under HHS/OSTP framework, to federally funded providers.

**Status (April 2026):** IGSC Harmonized Screening Protocol v3.0 (September 2024) in effect for IGSC members. HHS/OSTP Nucleic Acid Synthesis Screening Framework (April 2024) reportedly under regulatory review ⚠️. 50 bp oligonucleotide screening implementation deadline (October 2026) status uncertain.

**Relevant cases:** SYN-01, SYN-02, SYN-06, SCR-03

---

## HHS P3CO / Potential Pandemic Pathogen Care and Oversight

**Scope:** Research reasonably anticipated to create, transfer, or use enhanced potential pandemic pathogens (ePPP). Triggers enhanced review for research on PEPPs (Pathogens with Enhanced Pandemic Potential).

**Status (April 2026):** HHS P3CO Framework reportedly paused under executive action (May 2025). ⚠️

**Relevant cases:** ENH-01, ECO-03, SCR-01

**PEPPs referenced in casebook:** 1918 H1N1 (SYN-05), H5N1 (ENH-01, ECO-03), Nipah virus (CON-01, DIA-02)

---

## Australia Group

**Scope:** Multilateral export control arrangement. Common Control Lists include human and animal pathogens, plant pathogens, biological toxins, and dual-use biological equipment. 2025 Plenary added AI-driven gene synthesis platforms to dual-use equipment list.

**Status:** Active. 2025 Plenary additions include AI-biology convergence equipment.

**Relevant cases:** CON-04 (VSV-Ebola international transfer), SYN-05 (1918 HA export implications), SCR-05 (Y. pestis to Germany), ECO-02 (AI protein design platforms), ECO-04 (automated lab platforms), ECO-05 (RAG system data)

---

## BWC / Biological Weapons Convention

**Scope:** Prohibits development, production, and stockpiling of biological weapons. Prohibitions apply to states party; no verification mechanism.

**Relevant cases:** ENH-01, ENH-05, CON-05 (Sterne strain dual-use boundary)

---

## CWC / Chemical Weapons Convention

**Scope:** Prohibits development, production, stockpiling, and use of chemical weapons. Schedule 1 chemicals (including saxitoxin, ricin) are most controlled. Peptide toxins generally not covered unless specifically listed.

**Relevant cases:** SYN-03 (omega-conotoxin — not listed, negative case)

---

## EAR / Export Administration Regulations

**Scope:** Dual-use goods and technologies, including biological materials under ECCN E1. Administered by BIS (Commerce Department).

**Relevant cases:** CON-04, SCR-05

---

## NIH Guidelines

**Scope:** Research involving recombinant or synthetic nucleic acids conducted at or receiving NIH funding. IBC review required for covered research. Not paused by any executive action.

**Relevant cases:** CON-04, SCR-01, SCR-02, SCR-04, ECO-04, ECO-05

---

## BMBL / Biosafety in Microbiological and Biomedical Laboratories

**Scope:** CDC/NIH guidance document establishing biosafety levels (BSL-1 through BSL-4) and containment recommendations. Sixth edition (2020).

**Relevant cases:** CON-01 (BSL assignment), CON-03 (MTb BSL-3), DIA-03 (C. burnetii BSL-3)

---

## LRN / Laboratory Response Network

**Scope:** CDC-coordinated network of public health, clinical, and environmental labs for emergency response. Published validated detection protocols for Select Agents and other threat agents.

**Relevant cases:** DIA-01 (B. anthracis PCR protocols), DIA-04 (Burkholderia clinical ID workflow)

---

## Regulatory Gaps Documented in This Casebook

1. **AI-generated laboratory protocols** — no framework governs LLM-assisted protocol generation for high-risk pathogen work; existing frameworks assume human-generated protocols reviewed by qualified personnel (ECO-01, ECO-04)
2. **RAG systems accessing biosecurity-sensitive corpora** — FSAP information security requirements apply to documents, but no framework specifically addresses LLM-based retrieval synthesis of sensitive protocol content (ECO-05)
3. **AI protein design for pathogen-relevant targets** — Australia Group 2025 addresses AI-driven gene synthesis platforms but not AI protein design tools; no framework governs LLM assistance with protein design targeting pathogen-relevant receptors (ECO-02)
4. **Multi-turn LLM conversation accumulation** — no framework addresses how per-turn dual-use evaluation should account for accumulated context across a conversation (ECO-03)
5. **FSAP/EAR interaction for avirulent Select Agent derivatives** — regulatory guidance on when FSAP-excluded avirulent strains remain EAR-controlled is inconsistent across BIS guidance documents and institutional practice (SCR-05)
