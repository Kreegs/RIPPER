# Project Brief: MKR Motor Controller Development and SBR Migration

## Project Overview

**Project name:** MKR Motor Controller Development and SBR Migration
**Project sponsor:** Owner
**Project manager:** Director of Sales and Operations
**Document status:** Approved
**Last updated:** June 2026

KreegCo. will design, certify, and manufacture the MKR motor controller as a direct replacement for the SBR series. Two critical electronic components used exclusively in the SBR have reached manufacturer end-of-life and can no longer be sourced. Current SBR component inventory supports approximately 10 months of production at current run rates. The MKR must be production-ready and customer-qualified before that inventory is exhausted.

---

## Background

The SBR has been in production for over a decade. It is an aging design with a complex manufacturing process that carries a high defect rate relative to current product lines. Component EOL presents a forced transition, but also an opportunity to modernize the hardware platform, reduce manufacturing complexity, and address new customer interface requirements that have emerged since the SBR was designed.

The MKR will replace the SBR on a one-to-one basis for all four affected OEM customers. It must maintain full backward compatibility in mounting dimensions, connector placement, and wire harness interface. Customers will not modify their vehicle designs or tooling to accommodate this transition.

---

## Product Definition

**Product name:** MKR Motor Controller
**Replaces:** SBR series

**Two SKUs, one PCB:**
- MKR-BT: Bluetooth module populated. Intended for customers requiring wireless configuration and telemetry.
- MKR: Bluetooth module unpopulated. Identical PCB and enclosure. BT functionality disabled.

The single-PCB approach reduces design complexity and allows shared firmware with feature gating. Manufacturing differentiates the two SKUs at the stuffing stage.

**Form factor constraints (non-negotiable):**
- Mounting hole pattern must match SBR exactly
- Wire harness connector positions must match SBR exactly
- Overall enclosure dimensions must not exceed SBR envelope
- These constraints are contractual. No exceptions without written customer approval and contract amendment.

**Key design updates over SBR:**
- New processor: STM32G474RET6 (STMicroelectronics) — replacing EOL component 1
- New power stage: DRV8353RS gate driver (Texas Instruments) with WSP4953 MOSFETs (Onsemi) — replacing EOL component 2
- New injection-moulded enclosure (new tooling required; existing SBR mould is not compatible with updated internal layout)
- Simplified PCB layout targeting reduced assembly time and defect rate
- Bluetooth 5.0 module (MKR-BT SKU)
- CAN 2.0B interface (required by Customer D for fleet management integration — not present on SBR)
- Updated thermal management

**PCB fabrication:**
Prototype and production PCBs are fabricated and assembled through Alltrax's contract manufacturer in Shenzhen, China. Prototype lead times are approximately 3–4 weeks from Gerber submission.

---

## Affected OEM Customers

Four customers currently purchasing SBR units are affected by this transition. All four have active supply agreements with Alltrax.

**Customer A: Meridian Industrial Vehicles**
- Application: electric burden carrier and tugger
- SKU required: MKR-BT
- Annual volume: approximately 950 units
- Contract terms: 60-day written notice required before any product change. Failure to provide notice triggers a per-unit penalty on affected orders.
- Qualification requirement: bench and vehicle-level validation required before production approval. Estimated 5–7 weeks once sample units are received.

**Customer B: Apex Electric Platforms**
- Application: NEV/LSV platform
- SKU required: MKR-BT
- Annual volume: approximately 1,100 units
- Contract terms: liquidated damages clause if supply is interrupted for more than 21 consecutive days.
- Qualification requirement: bench validation, vehicle validation, and internal homologation review. Estimated 8–10 weeks once sample units are received. NEV/LSV application may require additional regulatory review on their end.

**Customer C: Harbor Ground Support**
- Application: electric ground support vehicle
- SKU required: MKR (no Bluetooth)
- Annual volume: approximately 350 units
- Contract terms: 45-day notice clause. No formal monetary penalty; breach triggers Customer C's right of early termination.
- Qualification requirement: bench validation only. Estimated 2–3 weeks once sample units are received.
- Stakeholder note: Customer C's primary stakeholder has repeatedly objected to the SBR transition, stating a preference for Alltrax to continue SBR production. Customer C's engineering lead understands the EOL situation and supports the MKR transition. The two contacts are not aligned, and this friction has already slowed internal communications. Qualification sign-off requires approval from the primary stakeholder.

**Customer D: Pinnacle Utility Vehicles**
- Application: electric utility and maintenance vehicle
- SKU required: MKR (no Bluetooth, with CAN bus interface)
- Annual volume: approximately 700 units
- Contract terms: master supply agreement requires 90-day notice of product changes. No explicit penalty clause.
- Qualification requirement: bench and vehicle validation, plus CAN bus integration test with Customer D's fleet management software. Estimated 5–6 weeks once sample units are received. Customer D's fleet management software vendor has not yet provided the CAN protocol specification to Alltrax.

---

## Timeline and Milestones

**Project start:** Month 0
**Hard deadline:** Month 10 (SBR component inventory exhausted)

| Milestone | Target | Notes |
|-----------|--------|-------|
| Hardware design complete | Month 2 | Includes schematic, layout, BOM |
| Enclosure tooling order placed | Month 1 | 6–10 week lead time; must not slip |
| PCB fabrication and assembly (proto units) | Month 3 | First article build |
| Firmware bring-up complete | Month 3.5 | Basic functionality on proto hardware |
| Internal validation complete | Month 4 | All internal test criteria met |
| FCC pre-certification testing | Month 4 | MKR-BT only. External test lab. |
| FCC submission | Month 5 | Contingent on pre-cert results |
| FCC grant received | Month 7 | Target. Timeline outside Alltrax control. |
| OEM sample units shipped | Month 5.5 | MKR and CAN samples. MKR-BT samples contingent on FCC. |
| Customer A qualification complete | Month 7.5 | Meridian Industrial Vehicles |
| Customer B qualification complete | Month 9.5 | Apex Electric Platforms — 8–10 week window after FCC-gated sample delivery |
| Customer C qualification complete | Month 6 | Harbor Ground Support |
| Customer D qualification complete | Month 7.5 | Pinnacle Utility Vehicles |
| Production build complete | Month 9 | First production run |
| SBR cutover complete | Month 10 | All customers transitioned to MKR |

---

## Resource Plan

**Engineering lead:** Director of Engineering
Primary designer for hardware and firmware. No dedicated project engineering resource. Engineering lead is shared with ongoing production support, warranty escalations, and two other active development projects — one of which is currently in pre-production validation and requires active engineering involvement through Month 2.

**Operations/PM:** Director of Sales and Operations
Owns customer communication, contract management, qualification coordination, and overall project timeline.

**Manufacturing:** Production team
Responsible for prototype assembly, first article build, and production ramp. Capacity has not been formally reserved for MKR builds. Scheduling is managed alongside existing production orders.

**External resources:**
- PCB contract manufacturer (Shenzhen, China): Alltrax's standard vendor for PCB fabrication and SMT assembly. Prototype lead times approximately 3–4 weeks from Gerber submission.
- Enclosure moulder: new injection mould tooling required. Vendor not yet selected. Tooling lead times typically 6–10 weeks.
- FCC test lab: external lab required for Bluetooth pre-certification testing and formal submission. Lab has not been selected or scheduled.
- Component suppliers: STM32G474RET6, DRV8353RS, and WSP4953 have been identified and specified. Purchase orders have not been placed. WSP4953 (Onsemi) carries a 26-week lead time for orders exceeding 200 units. Quantities of 200 units or fewer are available at standard lead times and are sufficient for prototype and validation builds. Production run quantities will require a separate order placed well in advance.

---

## Budget

A project budget of $170,000 has been approved by the owner. This figure is a hard cap. The owner has stated that overruns will not be approved without a formal scope change request, which requires owner sign-off and a minimum five-business-day review cycle.

Known cost categories within the approved budget:
- Enclosure injection mould tooling: $30,000 (fixed, committed cost)
- PCB fabrication and SMT assembly (prototype and first production run)
- Component procurement including safety stock
- FCC pre-certification testing and certification filing fees (estimated $8,000–$15,000 depending on lab and test scope)
- Customer sample units (4 customers, approximately 2–4 units each)
- Engineering time (internal, not separately budgeted)

No contingency line has been allocated within the $170,000. The mould tooling commitment leaves $140,000 for all remaining project costs.

---

## Known Constraints

The following are known at project start. This list is not exhaustive.

- 10-month hard deadline is fixed. It is driven by physical SBR inventory, not a business preference.
- Engineering lead has no dedicated capacity for this project and carries a competing pre-production commitment through at least Month 2.
- CAN bus interface is a new capability not present on the SBR. Customer D's fleet management software vendor has not provided the CAN protocol specification; acceptance criteria for the CAN integration test have not been defined.
- FCC certification is required for the MKR-BT SKU. Timeline is outside Alltrax control.

---

## Success Criteria

- MKR-BT and MKR in production and shipping to all four OEM customers before SBR component inventory reaches zero
- All four customers have completed qualification and issued production approval before cutover date
- FCC grant received for MKR-BT before MKR-BT ships to production customers
- No contract penalties triggered
- Form factor constraints met for all customers with no contract amendments required
- CAN bus interface validated by Customer D before cutover
- Manufacturing defect rate lower than SBR baseline
