# Risk Identification Pattern Library

Standalone reference version of the identification patterns used by the risk specialist module. Future PM agent modules may import this file to apply consistent risk identification logic without duplicating definitions.

Each pattern includes: trigger condition, primary category, default probability and impact scores, and calibration notes.

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
