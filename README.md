# SaaS Profit Finder

An anti-hallucination Claude Code plugin that discovers, validates, and ranks profitable SaaS opportunities through a structured 9-stage pipeline.

It refuses to brainstorm generic AI-wrapper ideas. Instead, it forces the model to interview the founder, map specific markets, mine evidence of real workflow pain, stress-test willingness-to-pay, run an adversarial critique, and produce a ranked SaaS opportunity brief with a 14-day validation plan and explicit kill criteria.

## Installation

In Claude Code, run:

```
/plugin marketplace add Darksmoke911301/saas-profit-finder
/plugin install saas-profit-finder
```

Then restart Claude Code.

## Usage

In any conversation, type:

```
/saas-hunt
```

Or speak naturally — the skill auto-triggers on phrases like *"find me a saas idea to build"*, *"what saas should I build"*, *"validate this saas idea"*.

The first thing it does is ask you a 30-question intake interview. It will not produce ideas before you answer.

## What's Inside

**1 orchestrator skill:** `saas-profit-finder` — the thin pipeline coordinator
**8 specialist agents** (each with its own system prompt):

| Agent | Role |
|---|---|
| `intake_interviewer` | 30-question founder + market + revenue + distribution interview |
| `market_mapper` | Selects 5–12 candidate niches with reachability and "why now" |
| `pain_miner` | Converts vague pain into concrete `Every [frequency], [role] must [task]` workflows |
| `evidence_verifier` | Grades evidence on an 8-level hierarchy; founder intuition = UNVALIDATED |
| `opportunity_designer` | Produces ICP, MVP wedge, pricing hypothesis, distribution plan |
| `scoring_agent` | Weighted SaaS Profit Scorecard (pain, frequency, budget, reach, etc.) |
| `devils_advocate` | "Why won't they pay?" / "Why is this just a feature?" — pushback isn't evidence |
| `validation_planner` | 14-day validation plan with scripts and kill criteria |

**1 slash command:** `/saas-hunt`

## The 9-Stage Pipeline

```
0. INTAKE          → 30-question questionnaire (BLOCKING)
1. MARKET SELECT   → 5–12 candidate niches
2. PAIN MINING     → concrete workflow pain
3. EVIDENCE VERIFY → source quality + hallucination check (BLOCKING)
4. OPPORTUNITY     → ICP, wedge, MVP, pricing
5. SCORING         → weighted scorecard
6. DEVIL'S ADV     → adversarial attack (BLOCKING)
7. VALIDATION      → 14-day plan + scripts
8. FINAL BRIEF     → ranked opportunity memo
```

## The 10 Iron Rules

1. Intake first. Never produce SaaS ideas before the intake questionnaire.
2. No generic AI-wrapper ideas. Every idea must name a specific customer, workflow, pain, workaround, WTP signal, MVP wedge, and distribution path.
3. Every claim must be backed by a cited source, observed customer signal, or labeled assumption.
4. **Gray zone = unvalidated.** Weak evidence stays labeled weak.
5. Contradictory evidence must be disclosed, not hidden.
6. Adversarial review is mandatory before final ranking.
7. Prefer boring, urgent, repeated B2B pain over flashy consumer ideas.
8. Optimize for profitable, reachable, bootstrappable SaaS (unless user asks for VC-scale).
9. Never claim an idea is "profitable." Use: promising / validated / unvalidated / weakly validated / high risk.
10. Final output must include kill criteria.

## Design Principles

This plugin is built on the same architectural patterns as the academic-research-skills suite:

- **Thin orchestrator, fat agents.** The orchestrator only routes and gates. The thinking lives in specialist prompts.
- **Mandatory blocking checkpoints.** Intake, Evidence Verification, and Devil's Advocate cannot be skipped.
- **Output schemas, not free-form text.** Every agent emits a structured markdown template.
- **Anti-sycophancy.** The Devil's Advocate doesn't concede because the user pushed back. Pushback is not evidence.
- **Tiered evidence hierarchy.** Direct customer interviews > public complaint clusters > job postings > competitor reviews > regulatory deadlines > marketplace reviews > search volume > founder intuition.

## Manual Installation (alternative)

If you don't want to use the marketplace:

```bash
git clone https://github.com/Darksmoke911301/saas-profit-finder.git
cp -r saas-profit-finder/skills/saas-profit-finder ~/.claude/skills/
cp saas-profit-finder/commands/saas-hunt.md ~/.claude/commands/
```

Then restart Claude Code and run `/saas-hunt`.

## License

MIT
