# Interface: RIPPER — Risk Specialist

## Produces

- **Risk register** — self-contained HTML document following the template in `reference/register-style.md`
- **Risk categories** — Schedule, Budget, Scope, Resource, Technical, External
- **Scoring** — Probability × Impact (integers 1–5 each); Risk score range 1–25
- **Priority tiers** — Critical (15–25), High (8–14), Medium (4–7), Low (1–3)
- **Status values** — Open, Accepted, Mitigated, Resolved
- **Per-risk fields** — description, category, probability rationale, impact rationale, mitigation, contingency, owner

## Consumes

- Project brief, charter, SOW, timeline, resource plan, budget summary — any combination
- Competition mode: `reference/Project-files/demo-project.md` (auto-loaded as project context)
- Web search results for ambient intelligence patterns P13–P15 (supply chain, regulatory flux, trade exposure)

## Trigger

Any risk-related question or instruction. Examples:

- "Identify the top risks" → produces full risk register
- "What are the schedule risks?" → filters register by category
- "Rescore R04 with probability 3" → updates register entry, acknowledges change
- "Add a risk for the new firmware vendor" → creates new scored entry
- "Which risks are most likely to cascade?" → cascade analysis from current register

## Scope boundary

Risk identification and scoring only. Requests outside this scope are named and routed:

| Request type | Correct module |
|---|---|
| Schedule and critical path analysis | Schedule Analyst |
| Budget variance tracking | Budget Tracker |
| Scope change evaluation | Scope Change Evaluator |
| Stakeholder communication drafting | Stakeholder Communication Drafter |

## Category routing notes for future modules

- **Schedule risks** feed directly into Schedule Analyst. RIPPER flags schedule risks and scores them; Schedule Analyst builds the response plan and timeline adjustments.
- **Budget risks** feed into Budget Tracker. RIPPER identifies budget exposure; Budget Tracker tracks actuals against plan.
- **Resource risks** are relevant to both Schedule Analyst (capacity affects critical path) and Budget Tracker (resource costs affect spend).
- **External risks** involving customers or regulatory bodies may require Stakeholder Communication Drafter to draft notifications or escalation messages.
- **Scope risks** are input to Scope Change Evaluator when a change request is being evaluated.

## Shared data conventions

Future modules reading RIPPER output should expect:
- Risk IDs in the format `R##` (e.g., R01, R12)
- Scores as integers, never as decimals or ranges
- Categories as exact strings from the category list above (case-sensitive)
- Priority tier derived from score only, never set independently
