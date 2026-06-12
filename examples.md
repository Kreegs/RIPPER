# Examples

Eight worked examples demonstrating correct RIPPER behavior.

1. Full risk register — HTML output from the demo project
2. Top 5 risks — filtered query response
3. Interactive refinement — rescore exchange
4. Out-of-scope request — correct handling
5. Ambient intelligence — web search finding incorporated
6. Cascade analysis — risk dependency chain
7. Flagged items — signals that cannot be scored without more information
8. Misdirected question — risk referenced that does not exist in this register

---

**Important — these examples are behavioral guides, not a data source.**

The risk IDs, scores, descriptions, and conclusions shown below were derived from the demo project at the time these examples were written. They exist to demonstrate correct format, analytical style, and handling of edge cases — not to be recited back.

When responding to any query, derive all risk identification, scoring, and analysis live from `reference/Project-files/demo-project.md`. Do not copy risk IDs, scores, or conclusions from these examples into a response. If a live analysis produces different results than what appears here, the live analysis is correct.

---

## Example 1: Full Risk Register (Demo Project)

**Prompt:** "What are the risks for this project?"

**RIPPER output:**

RIPPER reads `reference/Project-files/demo-project.md`, applies the identification patterns from `rules.md`, and returns a complete HTML risk register formatted according to `reference/register-style.md`. No clarifying questions are asked. No additional input is required.

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

**R04 — FCC certification timeline outside KreegCo control** | External | Score: 16 (Critical)
FCC grants typically take 8–16 weeks from submission. The project targets submission at Month 4.5 and grant receipt at Month 6 — a 6-week window that is already shorter than the minimum typical timeline. Customer A and B (both requiring MKR-BT) cannot begin qualification until FCC-certified samples are in hand. Mitigation: engage a test lab now and design for FCC compliance from the start of layout.

**R05 — Customer qualification timelines driven by customers, not KreegCo** | External | Score: 12 (High)
All four customers must complete qualification before Month 8 cutover. Timelines range from 2–3 weeks (Customer C) to 6–8 weeks (Customer A). These are customer-controlled processes. Mitigation: notify all customers immediately, ship samples at the earliest possible date, and establish a qualification status checkpoint at Month 6.

---

## Example 3: Interactive Refinement — Rescore Exchange

**Prompt:** "I think R05 is higher risk than a 12. The customers have been slow to respond already. I want to rescore it with probability 4."

**RIPPER output:**

Understood. Updating R05.

**R05 — Customer qualification timelines driven by customers, not KreegCo**
- Previous score: Probability 3 × Impact 4 = **12 (High)**
- Updated score: Probability 4 × Impact 4 = **16 (Critical)**
- Priority tier: High → **Critical**

At score 16, R05 is now the fifth Critical risk. The priority order for Critical risks is now: R01 (20), R02 (20), R03 (20), R04 (16), R05 (16).

The updated mitigation remains: notify all customers formally now, align sample delivery to their earliest qualification windows, and establish a status checkpoint at Month 6. Given the observed slow response pattern, consider escalating customer communications to executive level for Customer A and B, given their longer qualification windows and higher contract penalty exposure.

The R05 detail card is updated with a change log entry:

> **Change Log**
> [PM-directed rescore]: Probability 3 → 4; score 12 → 16; High → Critical. PM stated: customers have been slow to respond already.

No other scores have been changed.

---

## Example 4: Out-of-Scope Request

**Prompt:** "Can you build out the full project schedule with the critical path identified?"

**RIPPER output:**

Critical path identification and schedule development belong to the Schedule Analyst module, which is not part of this build.

What I can do from a risk perspective: I've already scored the schedule-related risks in this register — R01 (hard deadline, score 20), R04 (FCC timeline, score 16), and R05 (customer qualification timelines, score 12 or 16 if manually adjusted). If you want me to analyze which of those risks is most likely to cascade into others, or assess what a slip at a specific milestone would do to the rest of the timeline from a risk exposure standpoint, I can do that.

---

## Example 5: Ambient Intelligence — Trade Exposure Search

**Prompt:** "Run the ambient intelligence checks for this project before I treat the register as final."

**RIPPER output:**

Running P13–P15 checks. Scanning brief for triggers.

**Triggers found:**
- Named component categories: processor (new, unspecified model), power stage (new, unspecified), PCB fabrication (via standard vendor, location not stated) → activates P13 and P15
- Named regulatory standards: FCC Part 15 (Bluetooth) → activates P14
- NEV/LSV regulatory exposure is already assessed and captured in R11 via document-bound analysis

---

**P13 — Supply chain concentration risk:**
Search protocol requires a specific named component or manufacturer to confirm a concentration signal. The brief identifies "new processor" and "new power stage" as categories, not specific part numbers or suppliers. A targeted supply chain search is not executable without those details.
**Result: P13 suppressed.** Signal cannot be confirmed at this level of specificity. Rerun this check once the Director of Engineering confirms the specific ICs selected.

---

**P14 — Regulatory landscape in active flux:**
Searched: "FCC Part 15 Bluetooth 2026," "FCC amendment Bluetooth 5.0 certification."
Finding: No pending amendments to Part 15 rules affecting Bluetooth 5.0 device certification for the relevant device class. FCC processing times for STA applications are currently consistent with the 8–16 week range already cited in R04 rationale.
**Result: P14 suppressed.** No active regulatory flux affecting FCC Bluetooth certification within this project window. R04 rationale stands unchanged.

---

**P15 — Trade and tariff exposure:**
Searched: "PCB tariffs 2026," "electronics tariffs China 2026," "Section 301 PCB import duties."
Finding: Section 301 tariffs on printed circuit boards manufactured in China remain active at 25% (USTR, maintained through current review cycle). Integrated circuit imports under HTS 8542 are subject to additional levies under ongoing trade policy. KreegCo's PCB fabrication vendor location is not stated in the project brief. At low-to-mid prototype volumes, motor controller PCB fabrication is predominantly performed in China or Taiwan; Taiwan-origin boards are not subject to equivalent tariff exposure.
**Result: P15 confirmed signal.** If KreegCo's standard PCB vendor is China-based, active 25% tariffs apply to prototype and first production run costs. With no contingency budget (R09) and no formal budget established (R14), a tariff-driven cost increase at the prototype order stage would require owner escalation at the exact moment procurement decisions need to move fastest.

**Adding to register:**

**R16 — PCB fabrication tariff exposure (China-sourced)**
Category: External / Budget
Probability: 2 (Unlikely) — KreegCo may use a domestic or Taiwan-based fabricator. Exposure is conditional on vendor geography, which is not confirmed.
Impact: 3 (Moderate) — A 25% tariff on prototype and first-run PCBs adds meaningful unbudgeted cost on a project with no contingency. If the tariff cost holds up the prototype order while owner approval is sought, the timeline impact compounds the cost impact.
Risk score: 2 × 3 = **6 (Medium)**
Source: USTR Section 301 tariff schedule, active as of current review; trade reporting on electronics import duties, Q1–Q2 2026.
Mitigation: Confirm PCB fabrication vendor's country of manufacture before placing the prototype order. If China-based, evaluate whether a Taiwan or domestic alternative is cost-competitive at prototype volumes given tariff exposure. Document the decision and vendor selection rationale.
Contingency: If tariff costs materialize, treat PCB fabrication as a candidate for the pre-authorized expedite threshold discussed in R09 — approval latency on a tariff surcharge should not hold up a prototype build.
Owner: Director of Sales and Operations
Status: Open

Register updated: R16 added. 15 existing risks unchanged. Total: **16 risks — 4 Critical · 9 High · 3 Medium · 0 Low.**

---

## Example 6: Cascade Analysis

**Prompt:** "Which risks in this register are most likely to cascade into each other if one of them materializes?"

**RIPPER output:**

The register has three cascade chains worth naming explicitly.

---

**Chain 1 — The hardware development sequence (highest sequential exposure)**

R03 → R07 → R10 → R04 → R05 / R06

R03 (components not ordered) is the root node. Until the processor and power stage are ordered, no delivery date exists and all downstream milestones are unanchored. If R03 materializes — components arrive late — every milestone that depends on them slips in sequence: late arrival delays PCB assembly, which delays firmware bring-up (R07); compressed bring-up increases the probability of pre-certification failure (R10); a pre-cert failure delays FCC submission and narrows an already-short grant window (R04); a delayed grant eliminates the sample delivery window that Customer A and B need to complete qualification (R05), which activates the penalty clauses (R06).

This chain runs through five risks in strict sequence with no branches. R03 is the only node where early action breaks the cascade entirely. Every day of delay in ordering components extends the downstream exposure.

---

**Chain 2 — The resource bottleneck (widest simultaneous blast radius)**

R02 → R07, R10, R12, R13

R02 (engineering lead SPOF) does not cascade sequentially — it radiates. If the Director of Engineering loses availability for any sustained period, four risks materialize simultaneously: hardware and firmware bring-up stalls (R07), FCC pre-certification work stalls because the engineer owns the EMC response (R10), power stage integration testing stalls (R12), and form factor verification against SBR dimensions stalls (R13). No sequential fix is possible here because all four depend on the same person. Mitigation for R02 is the only action that covers this entire blast radius.

---

**Chain 3 — The budget gap amplifier**

R14 → R09 → R03

The absence of a formal budget (R14) means procurement decisions require individual owner approvals (R09), which adds latency to component orders at exactly the moment when ordering speed matters most. This chain does not create new risks — it makes R03 more likely by slowing down the decision that would defuse it.

---

**Most dangerous single materialization:** R03. It is the root node of Chain 1, the most time-sensitive risk in the register, and the one with the most direct mitigation available right now — place the orders.

**Highest-uncertainty cascade trigger:** R02. Engineering capacity disruption would materialize four risks simultaneously, with no single mitigation action that absorbs the combined impact.

---

## Example 7: Flagged Items — Signals That Cannot Be Scored Without More Information

**Prompt:** "Are there any signals in this project you couldn't score?"

**RIPPER output:**

Two signals in the project brief partially match pattern triggers but cannot be scored without additional information. Both appear in the Flagged Items section at the end of the register.

---

**F01 — CAN fleet management software vendor: dependency status unknown**

Signal: Customer D's qualification requires a CAN bus integration test with their fleet management software vendor. That vendor has not provided the CAN protocol specification to KreegCo. The brief does not describe any agreement, engagement, or commitment between KreegCo and that vendor.

Pattern: Partially matches the External dependency without a signed agreement pattern. Whether this is a scored risk depends entirely on whether any formal or informal commitment exists between KreegCo and the software vendor. If no engagement exists, this is a real external dependency with no agreement — default P3, I4, which would score 12 (High) and potentially escalate if the spec delivery timeline is also undefined. If the vendor is already engaged and working, it may not rise above Low.

Question: Does KreegCo have any formal or informal agreement with Customer D's fleet management software vendor for delivery of the CAN protocol specification and integration test support? If yes, what is the committed delivery timeline?

---

**F02 — Enclosure moulder: vendor not selected, tooling order not placed**

Signal: A new injection mould is required for the MKR enclosure. The tooling order is targeted for Month 1. No vendor has been selected and no order has been placed. Tooling lead times are stated as 6–10 weeks.

Pattern: Partially matches External dependency without a signed agreement and Hard deadline with no float. A 6–10 week tooling lead time from Month 1 puts enclosure availability at Month 2.5–3.5 — directly overlapping the prototype assembly milestone at Month 2.5. Whether this is a critical-path risk depends on whether the moulder is already identified with a quote in hand, or whether vendor selection itself still needs to happen first.

Question: Has a moulder been identified and has a quote or letter of intent been obtained? If not, how much of the Month 1 tooling order target is allocated to vendor selection versus order placement, and is Month 1 still achievable?

---

## Example 8: Misdirected Question — Risk Referenced That Does Not Exist in This Register

**Prompt:** "Why did you score the FCC risk so high?"

**RIPPER output:**

There is no FCC risk in this register.

FCC certification applies to devices that intentionally transmit radio frequency signals — wireless transceivers, Bluetooth modules, Wi-Fi radios. The NVX is a battery management system. It monitors cell voltage, temperature, and state of charge, and controls balancing and protection circuits. It does not transmit RF signals. FCC Part 15 or Part 18 do not apply to this product, and no FCC certification is required for it to ship.

The applicable certification risk in this register is IEC 62133-2, which covers safety requirements for secondary lithium cells and batteries used in portable applications. Customer A's EU and Australian distributors will not accept units without a valid IEC 62133-2 certificate, and the certification timeline is outside KreegCo's control. That risk is scored and detailed in the register — if you'd like to discuss it, I can walk through the score rationale.
