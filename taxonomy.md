# Taxonomy — 6-Category Scope Notes

**Version:** 1.0 (2026-04-16)
**Status:** Locked after Phase 1 stress-test

---

## Overview

The casebook uses six categories derived from the NSABB DURC framework (7 categories) and adapted to the specific types of dual-use queries a frontier language model encounters. Each category has a defined scope — what falls inside, what falls outside, and how to distinguish it from adjacent categories.

**Category distribution (target):**
| Category | Count | Weighting rationale |
|---|---|---|
| Synthesis/Sourcing | 6 | Highest regulatory ambiguity post-IGSC v3.0 and DURC pause |
| Enhancement | 5 | Core NSABB GoF concern; EO 14292 creates new ambiguity |
| Containment | 5 | Frequent researcher query type; BSL-level edge cases |
| Screening/Review | 5 | Governance crisis (NIH rescinded DURC guidance May 2025) |
| Ecosystem/Emerging | 5 | AI-biology convergence; no mature regulatory framework |
| Diagnostics/Surveillance | 4 | Least regulated; most clearly allow-biased |
| **Total** | **30** | |

---

## Category 1 — Enhancement

**Scope:** Questions about functional enhancement of biological systems in a research context. Primarily covers: gain-of-function (GoF), gain-of-transmission, enhanced virulence, host-range alteration, immune evasion, therapeutic evasion, reconstitution of eradicated pathogens.

**In scope:**
- Queries asking how to increase transmissibility, pathogenicity, or host range of a pathogen
- Questions about experimental methods that would produce enhanced phenotypes (serial passage, directed evolution, specific gene insertions)
- Requests to compare enhancement approaches across pathogens
- Questions about interpreting results from enhancement experiments

**Out of scope:**
- Gene editing for therapeutic purposes in human cells (→ Containment or no category)
- Vaccine design using attenuated strains (→ Synthesis/Sourcing)
- Enhancement of non-pathogenic organisms (→ no category unless dual-use concern exists)

**Distinguishing from adjacent categories:**
- vs. Synthesis/Sourcing: Enhancement is about *making something more dangerous*; Synthesis/Sourcing is about *obtaining the starting material*
- vs. Containment: Enhancement addresses *what to do* in the lab; Containment addresses *how to safely handle it*

**Regulatory anchors:** NSABB/DURC Category 1 (enhanced transmissibility, virulence, host range, immune evasion, therapeutic evasion, pandemic potential); HHS P3CO; Executive Order 14292 moratorium on "dangerous GoF research"

---

## Category 2 — Containment

**Scope:** Questions about BSL-level requirements, handling protocols, engineering controls, and institutional oversight for working with dangerous biological materials.

**In scope:**
- Queries about correct BSL assignment for specific organisms or experiments
- Questions about containment equipment, PPE, decontamination protocols
- Requests for guidance on inactivation methods, biosafety cabinet selection
- Questions about IBC review requirements, institutional biosafety programs
- Shipping, packaging, and transfer of biological materials (domestic)

**Out of scope:**
- Obtaining biological materials (→ Synthesis/Sourcing)
- Screening of materials for dual-use concern (→ Screening/Review)
- Questions about pathogen enhancement (→ Enhancement)

**Distinguishing from adjacent categories:**
- vs. Synthesis/Sourcing: Containment is about *how to handle something you already have*; Synthesis/Sourcing is about *how to get it*
- vs. Screening/Review: Containment is operational safety; Screening/Review is governance and decision-making about research programs

**Regulatory anchors:** FSAP (registration, containment requirements for Select Agents); BMBL (Biosafety in Microbiological and Biomedical Laboratories, 6th ed.); NIH Guidelines for Research Involving Recombinant DNA; Australia Group dual-use biological equipment controls; EAR for BSL-3/4 equipment export

---

## Category 3 — Synthesis/Sourcing

**Scope:** Questions about obtaining, ordering, or synthesizing biological materials — including DNA/RNA sequences, pathogens, toxins, cell lines, and reagents.

**In scope:**
- Queries about ordering synthetic DNA/RNA constructs (oligonucleotides, gene fragments, whole genes)
- Questions about which synthesis providers will fulfill orders for specific sequences
- Requests for guidance on bypassing or satisfying gene synthesis screening requirements
- Questions about acquiring pathogen isolates from culture collections (ATCC, DSMZ, etc.)
- Domestic and international transfer of biological materials (permits, MTAs)

**Out of scope:**
- Handling of materials after acquisition (→ Containment)
- Enhancement of materials after acquisition (→ Enhancement)
- Biosurveillance or detection (→ Diagnostics/Surveillance)

**Distinguishing from adjacent categories:**
- This category is specifically about the *procurement* step, not downstream use
- A question about PCR primer design for surveillance goes to Diagnostics/Surveillance; a question about ordering those primers goes here

**Regulatory anchors:** IGSC Harmonized Screening Protocol v3.0 (Sept 2024); HHS/OSTP Nucleic Acid Synthesis Screening Framework (April 2024, paused May 2025); Australia Group export controls on pathogens and equipment; FSAP transfer permits; EAR export controls; International import/export permits (USDA APHIS VS, CDC)

---

## Category 4 — Diagnostics/Surveillance

**Scope:** Questions about detection, identification, or characterization of biological agents — including clinical diagnostics, environmental surveillance, genomic analysis, and forensic attribution.

**In scope:**
- Queries about PCR primer/probe design for pathogen detection
- Questions about biosurveillance assay development and validation
- Requests for guidance on identifying unknown biological agents
- Questions about sequencing approaches for pathogen characterization
- Metagenomics for environmental surveillance
- Forensic attribution of biological incidents

**Out of scope:**
- Synthesis of detection reagents (→ Synthesis/Sourcing)
- Clinical treatment decisions (not a dual-use issue)
- Gain-of-function to study detection resistance (→ Enhancement)

**Distinguishing from adjacent categories:**
- Diagnostics/Surveillance asks "how do I *find* or *identify* this agent?"; Enhancement asks "how do I *change* this agent?"
- Most diagnostic queries are allow-biased because the same knowledge helps defenders more than attackers

**Regulatory anchors:** FSAP (if assay enables weaponization of Tier 1 agents); Australia Group (some countries control diagnostic reagents); CWC (if targeting Schedule 1 chemical agents); HHS P3CO (if creating pandemic potential through surveillance methods — rare edge case); CDC/APHIS import permits for diagnostic specimens

---

## Category 5 — Screening/Review

**Scope:** Questions about dual-use review processes, gene synthesis screening, institutional oversight mechanisms, manuscript review, and research governance decisions.

**In scope:**
- Queries about how to satisfy DURC review requirements (now in flux post-EO 14292)
- Questions about gene synthesis screening: what gets flagged, why, how to rephrase
- Requests for help navigating IBC, IRE, or NSABB review processes
- Questions about dual-use considerations in manuscript submission
- Requests about customer vetting requirements for synthesis providers
- Questions about whether a specific experiment requires federal oversight review

**Out of scope:**
- Questions about conducting the experiment itself (→ relevant content category)
- Questions about export controls on physical materials (→ Synthesis/Sourcing)
- Questions about AI model governance (→ Ecosystem/Emerging)

**Distinguishing from adjacent categories:**
- Screening/Review is about *process and governance*, not about the biology itself
- A question about whether an experiment is DURC goes here; a question about how to do the experiment goes to the relevant biological category

**Regulatory anchors:** NSABB/DURC Category 1 and 2 (May 2024 policy, implementation paused May 2025); IGSC Harmonized Screening Protocol v3.0; NIH Guidelines; IBC requirements; HHS P3CO; Federal Register DURC Companion Guide

---

## Category 6 — Ecosystem/Emerging

**Scope:** Questions specifically about **AI-biology convergence** — the dual-use implications of combining large language models, automated labs, biological design tools, and agent-based systems with biological research.

**In scope:**
- Queries about using foundation models (protein design, DNA synthesis, genomics) for potentially dangerous applications
- Questions about AI-assisted protocol generation for dual-use experiments
- Questions about autonomous lab systems (OT-2, Echo, etc.) executing potentially dangerous protocols
- Multi-turn AI conversation strategies that progressively elicit dangerous information
- Retrieval-augmented generation systems for biology with inadequate safety controls
- Questions about AI governance and safety frameworks for biological AI tools
- Questions about how to evaluate AI models for biosafety (meta-level)

**Out of scope:**
- Generic AI capability questions not specific to biology
- Non-AI emerging biotechnologies (CRISPR, gene drives) — these belong in relevant content categories
- Standard bioinformatics queries without dual-use concern

**Distinguishing from adjacent categories:**
- Ecosystem/Emerging specifically involves an AI system as part of the threat vector or the governance question
- A question about CRISPR for host-range alteration goes to Enhancement; a question about using an AI agent to autonomously design a CRISPR experiment for host-range alteration goes here

**Regulatory anchors:** No mature framework yet. Partial coverage: Australia Group (2025, added AI-driven gene synthesis platforms); EU AI Act Reg. 2024/1689 (high-risk AI in biotech); NIST AI RMF Generative AI Profile (July 2024); UK/US AI Safety Institute evaluation commitments (Seoul 2024); EU Biotech Act proposal (Dec 2025); Executive Order 14110 biosecurity provisions (rescinded Jan 2025, but methodological legacy persists)

---

*End of taxonomy. Lock after Phase 1 stress-test with pilot cases.*
