# Project Brief: CRX Motor Controller Development and PRX Migration

## Project Overview

**Project name:** CRX Motor Controller Development and PRX Migration
**Project sponsor:** Owner
**Project manager:** Director of Operations
**Document status:** Approved
**Last updated:** June 2026

KreegCo. will design and manufacture the CRX motor controller as a direct replacement for the PRX series. Two critical components used exclusively in the PRX have reached manufacturer end-of-life and can no longer be sourced. Current PRX component inventory supports approximately 7 months of production at current run rates. The CRX must be production-ready and customer-qualified before that inventory is exhausted.

---

## Background

The PRX has been in production for eight years. It is a reliable but aging platform with a processor architecture that no longer has active ecosystem support and a power stage that has become difficult to source. Component EOL presents a forced transition. The CRX will replace the PRX on a one-to-one basis for all three affected OEM customers while adding a SAE J1939 CAN interface required by one customer for fleet telemetry integration.

---

## Product Definition

**Product name:** CRX Motor Controller
**Replaces:** PRX series

**Two SKUs, one PCB:**
- CRX-BT: Bluetooth module populated. Required by two customers for wireless configuration.
- CRX: No Bluetooth. Identical PCB. BT functionality disabled at stuffing stage.

**Form factor constraints (non-negotiable):**
- Mounting hole pattern must match PRX exactly
- Wire harness connector positions must match PRX exactly
- Overall enclosure dimensions must not exceed PRX envelope
- These constraints are contractual. No exceptions without written customer approval.

**Key design updates over PRX:**
- New processor: RP2040 dual-core ARM Cortex-M0+ (Raspberry Pi Ltd) — replacing EOL PIC32MX795F512L (Microchip)
- New power stage: IXFB120N20P3 MOSFET (IXYS) — replacing EOL IRFS4010-7P MOSFET array (Infineon)
- New injection-moulded enclosure (new tooling required; PRX mould not compatible with updated layout)
- SAE J1939 CAN interface (required by Customer A for fleet management integration — not present on PRX)
- RP2040 has not been used by Alltrax in a production motor controller context. Prior use limited to internal tooling.

**PCB fabrication:**
Prototype and production PCBs fabricated and assembled through Alltrax's contract manufacturer in Shenzhen, China. Prototype lead times approximately 3–4 weeks from Gerber submission.

---

## Affected OEM Customers

Three customers currently purchasing PRX units are affected by this transition.

**Customer A: Titan Industrial Equipment**
- Application: electric tugger and burden carrier
- SKU required: CRX (no Bluetooth, with J1939 interface)
- Annual volume: approximately 820 units
- Contract terms: 45-day written notice required before any product change. Failure triggers per-unit penalty on affected orders.
- Qualification requirement: bench validation, vehicle-level validation, and J1939 integration test with Titan's fleet management software. Estimated 6–8 weeks once samples received. Titan's fleet management software vendor has not yet provided the J1939 PGN specification to Alltrax. Acceptance criteria for the integration test have not been defined.

**Customer B: Coastal Marine Electric**
- Application: electric dock handling equipment
- SKU required: CRX (no Bluetooth)
- Annual volume: approximately 400 units
- Contract terms: liquidated damages clause if supply is interrupted for more than 15 consecutive days.
- Qualification requirement: bench validation only. Estimated 3–4 weeks once samples received.

**Customer C: BlueLine Mobility**
- Application: compact electric passenger transport
- SKU required: CRX-BT
- Annual volume: approximately 1,200 units
- Contract terms: 60-day written notice required before any product change.
- Qualification requirement: bench and vehicle-level validation. Estimated 8–10 weeks once samples received.
- Stakeholder note: Customer C's procurement VP has expressed a preference for continuing to purchase the PRX, citing supplier change risk. Customer C's engineering manager understands the EOL situation and supports the CRX transition. The two contacts have not reached an internal position. Qualification sign-off requires written approval from the procurement VP.

---

## Timeline and Milestones

**Project start:** Month 0
**Hard deadline:** Month 7 (PRX component inventory exhausted)

| Milestone | Target | Notes |
|-----------|--------|-------|
| Hardware design complete | Month 1 | Includes schematic, layout, BOM |
| Enclosure tooling order placed | Month 1 | 6–8 week lead time; must not slip |
| PCB fabrication and assembly (proto) | Month 2.5 | First article build |
| Firmware bring-up complete | Month 3 | Basic functionality on proto hardware |
| Internal validation complete | Month 3.5 | All internal test criteria met |
| OEM sample units shipped (Customers B and C) | Month 4 | Non-J1939 samples |
| OEM sample units shipped (Customer A) | Month 4.5 | Contingent on J1939 spec receipt from Titan's vendor |
| Customer B qualification complete | Month 5.5 | Coastal Marine Electric |
| Customer C qualification complete | Month 6 | BlueLine Mobility |
| Customer A qualification complete | Month 6.5 | Titan Industrial Equipment — J1939 integration adds uncertainty |
| Production build complete | Month 6.5 | First production run |
| PRX cutover complete | Month 7 | All customers transitioned to CRX |

---

## Resource Plan

**Engineering lead:** VP Engineering
Primary designer for hardware and firmware. Only engineer available for this project. Also managing active production support and one other new development project concurrently through Month 3.

**Operations/PM:** Director of Operations
Owns customer communication, contract management, qualification coordination, and overall project timeline.

**Manufacturing:** Production team
Responsible for prototype assembly and production ramp. Manufacturing capacity has not been formally reserved for CRX builds.

**External resources:**
- PCB contract manufacturer (Shenzhen, China): standard vendor. Prototype lead times 3–4 weeks.
- Enclosure moulder: new injection mould tooling required. Vendor not yet selected.
- Component suppliers: IXFB120N20P3 (IXYS) has a 14-week lead time for quantities exceeding 500 units. Quantities below 500 units available at standard lead times and sufficient for prototype and validation. Production quantities require a separate PO placed no later than Month 2.
- J1939 integration testing: no external lab identified. Testing will depend on Titan Industrial Equipment's internal test environment and their software vendor's cooperation.

---

## Budget

A project budget of $95,000 has been approved by the owner. This is a hard cap. Overruns require a formal scope change request with owner sign-off and a five-business-day review cycle.

Known cost categories within the approved budget:
- Enclosure injection mould tooling: $22,000 (fixed, committed cost)
- PCB fabrication and SMT assembly (prototype and first production run)
- Component procurement including safety stock
- Customer sample units (3 customers, approximately 2–3 units each)
- Engineering time (internal, not separately budgeted)

No contingency line has been allocated. The mould tooling commitment leaves $73,000 for all remaining project costs. J1939 integration testing costs are not separately budgeted; the scope was added after the budget was approved.

---

## Known Constraints

- 7-month hard deadline is fixed. Driven by physical PRX component inventory.
- Engineering lead has no dedicated project capacity and carries active competing commitments through Month 3.
- J1939 interface is a new capability not present on the PRX. Titan's fleet management software vendor has not provided the PGN specification. Acceptance criteria for the integration test are undefined.
- RP2040 has not been used by Alltrax in production. No internal reference design exists.
- IXFB120N20P3 production lead time exceeds the window available for late PO placement.

---

## Success Criteria

- CRX and CRX-BT in production and shipping to all three OEM customers before PRX component inventory reaches zero
- All three customers have completed qualification and issued production approval before cutover date
- J1939 integration validated by Customer A before cutover
- No contract penalties triggered
- Form factor constraints met for all customers with no contract amendments required
- Manufacturing defect rate equal to or lower than PRX baseline
