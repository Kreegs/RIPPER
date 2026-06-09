# Project Brief: MKR Motor Controller Development and SBR Migration

## Project Overview

**Project name:** MKR Motor Controller Development and SBR Migration
**Project sponsor:** Owner
**Project manager:** Director of Sales and Operations
**Document status:** Approved
**Last updated:** June 2026

Alltrax Inc. will design, certify, and manufacture the MKR motor controller as a direct replacement for the SBR series. Two critical electronic components used exclusively in the SBR have reached manufacturer end-of-life and can no longer be sourced. Current SBR component inventory supports approximately 8 months of production at current run rates. The MKR must be production-ready and customer-qualified before that inventory is exhausted.

---

## Background

The SBR has been in production for over a decade. It is an aging design with a complex manufacturing process that carries a high defect rate relative to current product lines. Component EOL presents a forced transition, but also an opportunity to update the hardware, reduce manufacturing complexity, and meet new customer feature requests.

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
- New processor replacing EOL component 1
- New power stage replacing EOL component 2
- Simplified PCB layout targeting reduced assembly time and defect rate
- Bluetooth 5.0 module (MKR-BT SKU)
- Updated thermal management

---

## Affected OEM Customers

Four customers currently purchasing SBR units are affected by this transition. All four have active supply agreements with Alltrax containing continuity of supply clauses and penalty provisions for unplanned disruption.

**Customer A: GreenTech Mobility**
- Application: light industrial electric vehicle
- SKU required: MKR-BT
- Annual volume: approximately 800 units
- Contract penalty: 90-day written notice required before any product change. Failure to notify triggers a per-unit penalty on all affected orders.
- Qualification requirement: full vehicle-level validation required before production approval. Estimated 6-8 weeks once sample units are received.

**Customer B: Pacific Electric Vehicles**
- Application: NEV/LSV platform
- SKU required: MKR-BT
- Annual volume: approximately 1,200 units
- Contract penalty: liquidated damages clause if supply is interrupted for more than 30 consecutive days.
- Qualification requirement: bench and vehicle validation. Estimated 4-6 weeks once sample units are received. NEV/LSV application may trigger additional regulatory review on their end.

**Customer C: Summit Industrial Equipment**
- Application: electric tugger and ground support vehicle
- SKU required: MKR (no Bluetooth)
- Annual volume: approximately 400 units
- Contract penalty: 60-day notice clause. Penalty is credit toward future orders.
- Qualification requirement: bench validation only. Estimated 2-3 weeks once sample units are received.

**Customer D: Coastal Cart Company**
- Application: electric golf and utility cart
- SKU required: MKR (no Bluetooth)
- Annual volume: approximately 600 units
- Contract penalty: no explicit penalty clause but master supply agreement requires 90-day notice of product changes.
- Qualification requirement: bench and vehicle validation. Estimated 4-5 weeks once sample units are received.

---

## Timeline and Milestones

**Project start:** Month 0
**Hard deadline:** Month 8 (SBR component inventory exhausted)

| Milestone | Target | Notes |
|-----------|--------|-------|
| Hardware design complete | Month 2 | Includes schematic, layout, BOM |
| PCB fabrication and assembly (proto units) | Month 3 | First article build |
| Firmware bring-up complete | Month 3.5 | Basic functionality on proto hardware |
| Internal validation complete | Month 4 | All internal test criteria met |
| FCC pre-certification testing | Month 4 | MKR-BT only. External test lab. |
| FCC submission | Month 4.5 | Contingent on pre-cert results |
| FCC grant received | Month 6 | Target. Timeline outside Alltrax control. |
| OEM sample units shipped | Month 5 | MKR (no BT) samples. MKR-BT samples contingent on FCC. |
| Customer A qualification complete | Month 6.5 | GreenTech Mobility |
| Customer B qualification complete | Month 7 | Pacific Electric Vehicles |
| Customer C qualification complete | Month 6 | Summit Industrial |
| Customer D qualification complete | Month 6.5 | Coastal Cart Company |
| Production build complete | Month 7.5 | First production run |
| SBR cutover complete | Month 8 | All customers transitioned to MKR |

---

## Resource Plan

**Engineering lead:** Director of Engineering
Primary designer for hardware and firmware. No dedicated project engineering resource. Engineering lead is shared with ongoing production support, warranty escalations, and two other active development projects.

**Operations/PM:** Director of Sales and Operations
Owns customer communication, contract management, qualification coordination, and overall project timeline.

**Manufacturing:** Production team
Responsible for prototype assembly, first article build, and production ramp. Capacity has not been formally reserved for MKR builds. Scheduling is managed alongside existing production orders.

**External resources:**
- PCB fabrication vendor: standard vendor, lead times approximately 3-4 weeks for prototype quantities
- FCC test lab: external lab required for Bluetooth certification. Lab selection and scheduling is pending.
- Component suppliers: new processor and power stage components identified. Long lead times possible. Orders not yet placed.

---

## Budget

Formal budget has not been finalized. Known cost categories:

- PCB design and fabrication (prototype and first production run)
- Component procurement including safety stock for new EOL-risk components
- FCC pre-certification testing (estimated $8,000-15,000 depending on lab and test scope)
- FCC certification filing fees
- Engineering time (internal, not separately budgeted)
- Customer sample units (4 customers, estimated 2-5 units each)

No contingency budget has been allocated. Cost overruns will require owner approval.

---

## Known Constraints and Risks (Initial List)

The following are known at project start. This list is not exhaustive and is intended to seed the risk analysis, not replace it.

- 8-month hard deadline is fixed. It is driven by physical inventory, not a business preference.
- FCC certification timeline is not within Alltrax control. Typical grant timelines run 8-16 weeks from submission. Pre-certification failures require retest and resubmission.
- Engineering lead has no dedicated capacity for this project. Competing priorities exist.
- Customer qualification timelines are driven by customer availability and internal processes, not Alltrax.
- Long lead time components have not been ordered. Supply chain risk is unquantified.
- No contingency budget exists.
- Contract penalty clauses are active for all four customers. Notification requirements vary.
- Pacific Electric Vehicles' NEV/LSV application may introduce regulatory dependencies outside this project's scope.

---

## Success Criteria

- MKR-BT and MKR in production and shipping to all four OEM customers before SBR component inventory reaches zero
- All four customers have completed qualification and issued production approval before cutover date
- FCC grant received for MKR-BT before MKR-BT ships to production customers
- No contract penalties triggered
- Form factor constraints met for all customers with no contract amendments required
- Manufacturing defect rate lower than SBR baseline
