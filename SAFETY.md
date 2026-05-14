# Responsible Use and Safety Scope

The Dual-Use Ambiguity Casebook documents **decision-boundary cases** in
biology dual-use governance for the AI-query era. It is structured to
support adjudication training, safeguard calibration, and policy research.
It is **not** a jailbreak resource and must not be used for adversarial
elicitation.

## In Scope

- Training and calibration of safeguard adjudication systems
- Research on dual-use biology governance for AI-mediated queries
- Comparison and benchmarking of model decisions against expert recommendations
  on documented edge cases
- Education on the NSABB DURC framework extended to query-level decisions
- Disagreement documentation: each case captures where reasonable experts
  would diverge and why

## Out of Scope

- Adversarial elicitation, jailbreak development, or evasion strategy design
- Operational uplift: every case has been reviewed for synthesis, dosing,
  weaponization, or deployment detail; none should provide direct misuse
  advantage. If you find a case that crosses that line, file a redaction
  request (see Reporting Concerns below).
- Use of `query_form` fields as direct prompts in production systems without
  the surrounding context, expert recommendation, and resolving-context fields
- Reframing model-evaluation results as global model-quality rankings
- Use of `documented_disagreement` fields as a "right answer" by either side;
  the field exists to document the disagreement structure, not to declare a
  winner

## Withheld Content

The following are intentionally **not** in this public corpus:

- Synthesis pathways, dosing, or weaponization parameters
- Specific FSAP (Federal Select Agent Program) operational handling detail
  beyond what is already in published policy
- Concrete enhancement protocols beyond what NSABB / journal precedent has
  already documented publicly
- Any case where the Uplift Context Variable (UCV) was scored "high" without
  a corresponding sanitization pass

## Reporting Concerns

For row-level concerns (a case that exposes operational detail; a tier label
that is wrong; a regulatory anchor that is misapplied):

- Open a GitHub issue labelled `safety` with the case ID
- For sensitive disclosures, email jak4013@med.cornell.edu with subject
  "AMBIG SAFETY [case-id]"
- Do not paste operational biological detail into public issues

The author commits to: 14-day acknowledgement, redaction within 30 days
where the concern is sustained, and version-bump (v1.0.x) with a public
changelog entry.

## Limitations Recap

- Single primary annotator; expert-panel review planned for v2
- 36 cases is a seed corpus; not exhaustive of the dual-use space
- Tier 1 (low-ambiguity) and Tier 5 (true expert-disagreement) framings
  may not generalize across all biosafety jurisdictions (US-anchored)
- Evaluations against frontier models reflect those models at a specific
  date; refusal behavior changes with provider updates
