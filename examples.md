# Examples

Four worked examples demonstrating correct RIPPER behavior.

1. Full risk register — HTML output from the demo project
2. Top 5 risks — filtered query response
3. Interactive refinement — rescore exchange
4. Out-of-scope request — correct handling

---

## Example 1: Full Risk Register (Demo Project)

**Prompt:** "What are the risks for this project?"

**RIPPER output:** *(self-contained HTML document — full output in `reference/register-style.md`)*

RIPPER reads `reference/Project-files/demo-project.md`, applies the identification patterns from `rules.md`, scores each risk, and returns the complete HTML risk register. No clarifying questions are asked. No additional input is required.

15 risks identified: 4 Critical · 9 High · 2 Medium · 0 Low. Output is sorted critical first. Every risk includes a full detail card with probability rationale, impact rationale, mitigation recommendation, contingency plan, and owner — all grounded in specific facts from the project brief, not generic statements.

---

## Example 2: Top 5 Risks Query

**Prompt:** "What are the top 5 risks for this project?"

**RIPPER output:**

The five highest-scored risks for the MKR Motor Controller Development and SBR Migration project are:

**R01 — 8-month hard deadline with no float** | Schedule | Score: 20 (Critical)
The deadline is driven by physical SBR component inventory exhaustion, not a business preference. It cannot be moved. Multiple sequential external dependencies (FCC certification, four customer qualifications) make a slip likely without active management. Mitigation: build a schedule with an internal Month 7 completion gate and identify the critical path now.

**R02 — Engineering lead is sole designer with no dedicated capacity** | Resource | Score: 20 (Critical)
The Director of Engineering is the single point of failure for all hardware and firmware work while simultaneously responsible for production support, warranty escalations, and two other active development projects. Any competing priority disrupts MKR milestones directly. Mitigation: formally allocate and document this person's MKR capacity and identify a contract engineering backup before one is needed.

**R03 — Key components not yet ordered; long lead times likely** | External | Score: 20 (Critical)
The new processor and power stage have been identified but not ordered. Electronic component lead times of 12–26+ weeks are common. PCB assembly is targeted at Month 3, meaning components must arrive well before that. Until orders are placed, there is no confirmed delivery date and no timeline. Mitigation: place orders immediately.

**R04 — FCC certification timeline outside Alltrax control** | External | Score: 16 (Critical)
FCC grants typically take 8–16 weeks from submission. The project targets submission at Month 4.5 and grant receipt at Month 6 — a 6-week window that is already shorter than the minimum typical timeline. Customer A and B (both requiring MKR-BT) cannot begin qualification until FCC-certified samples are in hand. Mitigation: engage a test lab now and design for FCC compliance from the start of layout.

**R05 — Customer qualification timelines driven by customers, not Alltrax** | External | Score: 12 (High)
All four customers must complete qualification before Month 8 cutover. Timelines range from 2–3 weeks (Customer C) to 6–8 weeks (Customer A). These are customer-controlled processes. Mitigation: notify all customers immediately, ship samples at the earliest possible date, and establish a qualification status checkpoint at Month 6.

---

## Example 3: Interactive Refinement — Rescore Exchange

**Prompt:** "I think R05 is higher risk than a 12. The customers have been slow to respond already. I want to rescore it with probability 4."

**RIPPER output:**

Understood. Updating R05.

**R05 — Customer qualification timelines driven by customers, not Alltrax**
- Previous score: Probability 3 × Impact 4 = **12 (High)**
- Updated score: Probability 4 × Impact 4 = **16 (Critical)**
- Priority tier: High → **Critical**
- Adjustment note: manually rescored; probability raised from 3 to 4 based on observed customer response delays.

At score 16, R05 is now the fifth Critical risk and sits above R06, R07, R08, and R09 in the register. The priority order for Critical risks is now: R01 (20), R02 (20), R03 (20), R04 (16), R05 (16).

The updated mitigation remains: notify all customers formally now, align sample delivery to their earliest qualification windows, and establish a status checkpoint at Month 6. Given the observed slow response pattern, consider escalating customer communications to executive level for Customer A and B specifically, given their longer qualification windows and higher contract penalty exposure.

No other scores have been changed.

---

## Example 4: Out-of-Scope Request

**Prompt:** "Can you build out the full project schedule with the critical path identified?"

**RIPPER output:**

Critical path identification and schedule development belong to the Schedule Analyst module, which is not part of this build.

What I can do from a risk perspective: I've already scored the schedule-related risks in this register — R01 (hard deadline, score 20), R04 (FCC timeline, score 16), and R05 (customer qualification timelines, score 12 or 16 if manually adjusted). If you want me to analyze which of those risks is most likely to cascade into others, or assess what a slip at a specific milestone would do to the rest of the timeline from a risk exposure standpoint, I can do that.
