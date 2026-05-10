---
description: SaaS Profit Finder — intake → research → validation → adversarial review → ranked SaaS opportunities
model: opus
---

Load and execute the SaaS Profit Finder skill.

Skill entry: `.claude/skills/saas-profit-finder/SKILL.md`.

Mandatory behavior:
1. Start with the Intake Interview unless the user explicitly provides a completed intake.
2. Do not brainstorm generic ideas before intake.
3. Run the full research and validation pipeline before recommending ideas.
4. Block final recommendations until the Evidence Integrity Gate and Devil's Advocate Gate pass.
5. Output ranked opportunities with evidence, risk, validation plan, MVP wedge, pricing hypothesis, and kill criteria.
