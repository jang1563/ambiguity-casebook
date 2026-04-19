# LinkedIn Outreach — Anthropic Safeguards / Frontier Red Team

*Send to publicly identifiable current Anthropic Safeguards or Frontier Red Team members found via LinkedIn. As of April 2026, Mrinank Sharma has resigned (no named replacement identified). Use other current Safeguards/Policy team members or the general safeguards contact at safety@anthropic.com.*

---

## Message Template

**Subject / Connection Note:**

> Biosafety Research Scientist applicant — sharing dual-use casebook for review before publication

**Message body:**

> Hi [Name],
>
> I'm applying for the Biological Safety Research Scientist role at Anthropic and wanted to share a portfolio artifact with your team before I publish it publicly — including an empirical finding you may want to see before it's in a preprint.
>
> I've built a **Dual-Use Ambiguity Casebook** — 36 structured biology cases at the AI-era dual-use decision boundary, each with a fixed 12-field template (scenario, query form, arguments both ways, resolving context, expert recommendation, precedent citation, documented disagreement, per-case regulatory anchor, and uplift context variable). The casebook spans 6 categories — including an Ecosystem/Emerging category covering AI-biology governance gaps like multi-turn intent escalation and AI training data biosafety — and covers NSABB/FSAP/IGSC/P3CO/Australia Group anchors per case. It is grounded entirely in NSABB literature, published biosecurity research, and public policy; no novel threat scenarios or operational uplift content are included.
>
> I've also completed **systematic model validation** of all 36 cases against 4 frontier models (April 2026). The headline finding: Anthropic's constitutional classifier refuses **53–65% of cases that expert review and GPT-4o/Gemini agree should be allowed** — and every refusal is API-level (stop_reason="refusal", empty content), meaning the classifier fires on domain keywords before model reasoning engages. GPT-4o agreed with expert recommendations on 17/17 (100%) high-ambiguity cases; Gemini on 16/17 (94%); Sonnet 4.6 on 8/17 (47%); Opus 4.7 on 6/17 (35%). The asymmetry is notable: both Anthropic models correctly refused the two multi-turn escalation cases where GPT-4o and Gemini engaged — suggesting the classifier is optimized for escalation detection at the cost of high false-positive rates on single-turn legitimate queries.
>
> The dataset is currently **private** and I would welcome any feedback — factual corrections, framing concerns, or cases you'd flag for revision — before I release it publicly.
>
> - GitHub (private): https://github.com/jang1563/ambiguity-casebook
> - HuggingFace (private): https://huggingface.co/datasets/jang1563/ambiguity-casebook
>
> If you'd like to grant access, my GitHub is `jang1563` and my HuggingFace is `jang1563`. If there is a better channel for responsible-disclosure submissions, please let me know.
>
> Thank you for your time. I look forward to the possibility of contributing to this work.
>
> Best,  
> JangKeun Kim, Ph.D.

---

## Email Alternative (safety@anthropic.com)

**Subject:** Dual-Use Ambiguity Casebook — responsible-disclosure review request (Biosafety RS applicant)

**Body:** Use the LinkedIn message body above verbatim; add your full contact information at the bottom (email, LinkedIn URL, phone if comfortable).

---

## Timeline Note (from plan)

> If no reply in 5 business days from submission date, publish openly with explicit review-invitation line in README.

The README already includes this line under "Responsible Disclosure":
> "This casebook was shared with Anthropic's Safeguards team under responsible-disclosure review before distribution. If you identify factual errors, framing concerns, or cases warranting revision, please open a GitHub issue or contact the author directly."
