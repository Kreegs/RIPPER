# Risk Identification Pattern Library

Standalone reference version of the identification patterns used by the risk specialist module. Future PM agent modules may import this file to apply consistent risk identification logic without duplicating definitions.

Each pattern includes: trigger condition, primary category, default probability and impact scores, and calibration notes.

Patterns P1–P12 are document-bound: they fire on signals found in the project brief. Patterns P13–P15 are ambient intelligence patterns: they fire on project signals but require web search to calibrate. Default scores for P13–P15 represent an unconfirmed signal; search results drive calibration up or suppress the pattern entirely.

---

## Pattern Index

1. Hard deadline with no float — Schedule — P3, I4
2. Single point of failure resource — Resource — P3, I5
3. Technically undefined scope element — Technical / Scope — P4, I3
4. External dependency without a signed agreement — External — P3, I4
5. Budget contingency under 10% — Budget — P3, I3
6. New technology or first-time implementation — Technical — P4, I3
7. Regulatory or compliance requirement — External — P3, I5
8. Shared resource across multiple projects — Resource — P4, I3
9. Aggressive timeline relative to scope — Schedule — P4, I4
10. Stakeholder alignment not confirmed — Scope / External — P3, I4
11. Security and data compliance requirement — Technical / External — P3, I4
12. Legacy system or codebase integration — Technical — P4, I3
13. Supply chain concentration risk — External — P2, I4 *(ambient — requires search)*
14. Regulatory landscape in active flux — External — P2, I4 *(ambient — requires search)*
15. Trade and tariff exposure — External / Budget — P2, I3 *(ambient — requires search)*

---

## Patterns

**P1 — Hard deadline with no float**
Category: Schedule | Default: P3, I4
A fixed deadline exists that is driven by a constraint outside the project team's control. No alternative timeline exists.
Calibrate probability up if multiple unresolved upstream dependencies must complete sequentially before the deadline.

---

**P2 — Single point of failure resource**
Category: Resource | Default: P3, I5
One named person or one vendor is the only path for a critical deliverable. No backup or alternate path exists.
Calibrate probability up if that resource has confirmed competing commitments.

---

**P3 — Technically undefined scope element**
Category: Technical / Scope | Default: P4, I3
A deliverable is described in outcome terms with no defined technical approach, method, or acceptance criteria.

---

**P4 — External dependency without a signed agreement**
Category: External | Default: P3, I4
Project success depends on a vendor, partner, regulatory body, or customer action, and no binding agreement, confirmed timeline, or formal commitment is in place.
Search calibration: When a specific named vendor is the dependency, search for that vendor's current business status, recent delivery or capacity issues, financial health, and ownership changes. Calibrate probability up if search reveals distress signals, a pattern of delivery failures, or a recent acquisition that could affect continuity. Not applicable when the dependency is a customer action or an unnamed partner.

---

**P5 — Budget contingency under 10%**
Category: Budget | Default: P3, I3
Stated contingency is under 10% of total budget, or no contingency has been allocated.
Calibrate up when scope includes new technology, undefined elements, or regulatory requirements.

---

**P6 — New technology or first-time implementation**
Category: Technical | Default: P4, I3
A component, platform, protocol, or approach has not been used by this team in a production context before.

---

**P7 — Regulatory or compliance requirement**
Category: External | Default: P3, I5
Project delivery requires approval from a regulatory body and the approval timeline is undefined or outside the team's control.
Calibrate probability down only if approval is routine, precedented, and already in process with a known timeline.
Search calibration: When a specific regulatory body or device class is named, search for current processing times and active backlogs for that body, and any pending rule changes for the relevant device category. Calibrate probability up if current processing times exceed the project's approval window; calibrate impact up if a rule change in progress would require redesign of work already underway.

---

**P8 — Shared resource across multiple projects**
Category: Resource | Default: P4, I3
A person or team is allocated to this project while carrying confirmed commitments to other active work simultaneously.

---

**P9 — Aggressive timeline relative to scope**
Category: Schedule | Default: P4, I4
The stated timeline appears compressed given sequential dependencies, external handoffs, new technology, or unknowns in scope.

---

**P10 — Stakeholder alignment not confirmed**
Category: Scope / External | Default: P3, I4
A key decision, requirement, or constraint has not been formally agreed to by the affected party, or agreement has been assumed but not documented.

---

**P11 — Security and data compliance requirement**
Category: Technical / External | Default: P3, I4
The project handles sensitive data or must meet a compliance framework (GDPR, SOC2, HIPAA, PCI-DSS) with no formal security review or compliance assessment completed or scheduled.
Calibrate probability up if the team has no prior compliance experience, the timeline has no room for audit cycles, or third-party vendors handle sensitive data without a signed DPA or BAA.
Calibrate impact up to 5 if a compliance failure would block delivery or expose the organization to regulatory action.

---

**P12 — Legacy system or codebase integration**
Category: Technical | Default: P4, I3
The project must integrate with, extend, or migrate data from an existing system where documentation is incomplete, ownership is unclear, or the system was not designed for the integration being planned.
Calibrate probability up if no isolated test environment exists for the legacy system, integration requires modifying code with no clear owner, or a data migration is required with no validated rollback plan.
Calibrate impact up if the legacy system is load-bearing for production and cannot be taken offline during integration work.

---

*Ambient Intelligence Patterns — P13–P15 require web search to evaluate. Default scores represent an unconfirmed signal. Search results either calibrate the score upward or suppress the pattern entirely.*

---

**P13 — Supply chain concentration risk**
Category: External | Default: P2, I4
The project requires specific physical components, materials, or subassemblies where manufacturing is concentrated in a small number of facilities or geographic regions. Concentration alone does not trigger this pattern — it fires when the project brief identifies specific components AND a search reveals an active disruption signal or historically fragile supply path.
Search queries: "[component type] supply chain [current year]", "[component] shortage", "[key manufacturer] production disruption".
Calibrate probability up if search confirms an active shortage, factory disruption, or exit of a single dominant supplier. Calibrate impact up if the component is on the critical path with no qualified alternative supplier. Suppress if search finds no current signal and the component has a broad manufacturing base.

---

**P14 — Regulatory landscape in active flux**
Category: External | Default: P2, I4
The project must comply with a named regulatory standard or framework that has pending amendments, contested enforcement, or an upcoming implementation deadline not yet reflected in current design requirements.
Search queries: "[standard name] update [current year]", "[standard] amendment", "[standard] enforcement changes".
Calibrate probability up if search finds a pending amendment with a deadline inside the project window, or active enforcement disputes in the project's market sector. Calibrate impact up if the amendment would require redesign of a completed or in-progress deliverable. Suppress if search confirms the standard is stable with no pending changes in the relevant timeframe.

---

**P15 — Trade and tariff exposure**
Category: External / Budget | Default: P2, I3
The project sources components, materials, or manufacturing from countries with active or pending trade tensions, tariff schedules, or export control regimes that could affect cost or availability.
Search queries: "tariffs [component category] [current year]", "[country] export restrictions [material]", "import duties [component type]".
Calibrate probability up if active tariff changes are announced or in progress. Calibrate impact up if project budget has no contingency for cost increases, or if export controls could restrict access to the component entirely. Use External/Budget dual category if tariff impact is cost only; use External/Schedule if controls could cut off availability.
