# Project Brief: NVX Battery Management System Development and CBM-3 Migration

## Project Overview

**Project name:** NVX Battery Management System Development and CBM-3 Migration
**Project sponsor:** Owner
**Project manager:** Director of Operations
**Document status:** Approved
**Last updated:** June 2026

KreegCo. will design, certify, and manufacture the NVX battery management system as a direct replacement for the CBM-3 series. Two critical components used exclusively in the CBM-3 have reached end-of-life. The LTC6804-2 multicell battery monitor (Analog Devices) has been officially discontinued; the STM8S207 microcontroller (STMicroelectronics) has an EOL notice in effect with last-time-buy window closing in four months. Current CBM-3 component inventory supports approximately 9 months of production at current run rates. The NVX must be production-ready and customer-qualified before that inventory is exhausted.

---

## Background

The CBM-3 has been in production for seven years and supports only NMC (nickel manganese cobalt) lithium cell chemistry. Since the CBM-3 was designed, LFP (lithium iron phosphate) cell chemistry has become the dominant choice for commercial fleet applications due to its cycle life, thermal stability, and lower cost. Two of the three affected OEM customers have either transitioned or are planning to transition their battery packs to LFP. The NVX must support both NMC and LFP chemistries. KreegCo has no prior production experience with LFP cell chemistry in a BMS context. Thermal management profiles, balancing algorithms, and state-of-charge estimation differ significantly between chemistries.

The NVX must also meet IEC 62133-2 certification requirements for Customer A's EU and Australian markets. The CBM-3 did not carry this certification.

---

## Product Definition

**Product name:** NVX Battery Management System
**Replaces:** CBM-3 series

**Single hardware platform, chemistry-selectable via firmware configuration:**
- NVX-NMC: NMC cell chemistry profile active
- NVX-LFP: LFP cell chemistry profile active

**Form factor constraints (non-negotiable):**
- PCB mounting dimensions must match CBM-3 exactly
- Connector pinout and placement must match CBM-3 exactly
- Enclosure dimensions must not exceed CBM-3 envelope
- Contractual for all three customers.

**Key design updates over CBM-3:**
- New cell monitoring IC: BQ76952 (Texas Instruments) — replacing discontinued LTC6804-2
- New main MCU: STM32G071CBT6 (STMicroelectronics) — replacing EOL STM8S207
- LFP chemistry support: new firmware balancing algorithms, SoC estimation, and thermal models (no internal reference exists)
- IEC 62133-2 compliance design targets: cell-level protection, thermal runaway detection, overcurrent and overvoltage response

**PCB fabrication:**
Prototype and production PCBs fabricated and assembled through KreegCo's contract manufacturer in Shenzhen, China. Prototype lead times approximately 3–4 weeks from Gerber submission.

---

## Affected OEM Customers

Three customers currently purchasing CBM-3 units are affected by this transition.

**Customer A: Summit Power Systems**
- Application: electric utility storage and material handling vehicles
- Annual volume: approximately 450 units
- Contract terms: 90-day written notice required before any product change.
- Qualification requirement: bench validation, vehicle-level validation, and IEC 62133-2 compliance documentation review. Estimated 14–16 weeks once samples received. Customer A's EU and Australian distributors will not accept units without a valid IEC 62133-2 certificate. Thermal runaway protection testing is required as part of the IEC scope; acceptance criteria have not been defined internally, and the external certification body will set the test parameters.

**Customer B: Meridian Fleet Technologies**
- Application: electric fleet delivery vehicles
- Annual volume: approximately 800 units
- Contract terms: liquidated damages clause if supply is interrupted for more than 21 consecutive days. 45-day written notice required before any product change.
- Qualification requirement: bench and vehicle-level validation. Estimated 6–8 weeks once samples received.
- Stakeholder note: Customer B's procurement VP has communicated a required transition timeline of 4 months, citing inventory planning constraints. Customer B's engineering team has assessed the NVX scope and stated that 9 months is the minimum viable timeline given LFP validation and certification requirements. The two positions have not been reconciled. No formal agreement on transition timeline has been reached. KreegCo has continued planning against the 9-month schedule while the customer-side position remains unresolved.

**Customer C: Alpine Industrial Equipment**
- Application: electric pallet movers and material handling
- Annual volume: approximately 300 units
- Contract terms: 30-day written notice required before any product change.
- Qualification requirement: bench validation only. Estimated 4 weeks once samples received.

---

## Timeline and Milestones

**Project start:** Month 0
**Hard deadline:** Month 9 (CBM-3 component inventory exhausted)

| Milestone | Target | Notes |
|-----------|--------|-------|
| Hardware design complete | Month 1.5 | Includes schematic, layout, BOM |
| Enclosure tooling order placed | Month 1 | 6–8 week lead time |
| LFP cell samples sourced for characterization | Month 1.5 | Cell supplier not yet confirmed |
| PCB fabrication and assembly (proto) | Month 3 | First article build |
| NMC firmware validation complete | Month 4 | Internal test criteria |
| LFP thermal characterization testing begin | Month 4 | No internal precedent; scope and duration uncertain |
| LFP firmware validation complete | Month 4.5 | Contingent on thermal model accuracy; acceptance criteria undefined |
| IEC 62133-2 pre-test with external lab | Month 5.5 | External lab not yet selected or engaged |
| IEC 62133-2 formal submission | Month 6 | Contingent on pre-test results |
| OEM sample units shipped (Customer C) | Month 5 | Bench-only customer, earliest qual path |
| OEM sample units shipped (Customers A and B) | Month 6.5 | After IEC pre-test milestone |
| IEC 62133-2 certificate received | Month 7.5 | Target. Timeline outside KreegCo control. |
| Customer C qualification complete | Month 7 | Alpine Industrial Equipment |
| Customer B qualification complete | Month 8 | Meridian Fleet Technologies — timeline alignment unresolved |
| Customer A qualification complete | Month 8.5 | Summit Power Systems — contingent on IEC cert |
| Production build complete | Month 8.5 | First production run |
| CBM-3 cutover complete | Month 9 | All customers transitioned to NVX |

---

## Resource Plan

**Engineering lead:** Hardware Engineer
Primary designer for NVX hardware. No prior BMS certification experience. No prior LFP implementation experience. Sole dedicated technical resource on this project.

**Firmware Engineer:** 60% allocation through Month 5, then reassigned.
Responsible for BQ76952 driver development, cell chemistry firmware, and SoC estimation algorithms. Shared with an active pre-production project that requires full engineering attention from Month 5 onward. Remaining firmware work after Month 5 falls to the hardware engineer, who has limited firmware development experience.

**Operations/PM:** Director of Operations
**Manufacturing:** Production team (capacity not formally reserved)

**External resources:**
- PCB contract manufacturer (Shenzhen, China): standard vendor
- Enclosure moulder: new tooling required. Vendor not yet selected.
- IEC 62133-2 certification body: not yet selected or engaged. Typical engagement lead time 3–4 weeks; test and review cycle 6–8 weeks after sample submission.
- LFP cell supplier for validation samples: CATL and EVE Energy are under consideration. No PO placed. Both are China-based manufacturers. No alternative non-China supplier has been evaluated.
- Component suppliers: BQ76952 (TI) available at standard lead times. STM32G071CBT6 available at standard lead times.

---

## Budget

A project budget of $185,000 has been approved by the owner. This is a hard cap.

Known cost categories:
- Enclosure injection mould tooling: $28,000 (fixed, committed cost)
- IEC 62133-2 testing and certification: estimated $12,000–$20,000
- LFP thermal characterization testing: estimated $8,000–$14,000 (not formally scoped; external test facility may be required)
- PCB fabrication, SMT assembly (prototype and first production run)
- Component procurement and safety stock
- Customer sample units (3 customers)
- Engineering time (internal, not separately budgeted)

No contingency line has been allocated within the $185,000. The mould tooling commitment leaves $157,000 for all remaining costs. IEC testing and LFP characterization alone could consume $34,000 at high-end estimates, representing 22% of remaining budget against zero formal contingency.

---

## Known Constraints

- 9-month hard deadline is fixed. Driven by CBM-3 component inventory.
- LFP cell chemistry support is a first-time implementation for KreegCo. Thermal models, balancing algorithms, and SoC estimation have no internal reference.
- LFP thermal runaway protection acceptance criteria have not been defined. The IEC 62133-2 certification body will define test parameters during the engagement — scope is not known in advance.
- Firmware engineer departs project at Month 5. Remaining firmware work transfers to hardware engineer with limited firmware experience.
- IEC 62133-2 certification timeline is outside KreegCo control and is on the critical path for Customer A.
- Customer B timeline alignment is unresolved. Procurement VP's 4-month position is incompatible with the project schedule.
- EU Battery Regulation (EU) 2023/1542 enters its enforcement phase during the project window. Full impact on NVX compliance scope has not been assessed. Regulation may require additional documentation or design changes not currently scoped.
- LFP cell supply is concentrated among Chinese manufacturers. No non-China cell source has been evaluated.

---

## Success Criteria

- NVX in production and shipping to all three OEM customers before CBM-3 component inventory reaches zero
- IEC 62133-2 certificate received before any unit ships to Customer A's EU or Australian distributors
- All three customers have completed qualification and issued production approval before cutover
- No contract penalties triggered
- LFP and NMC chemistry profiles validated to internal and customer acceptance criteria
- Form factor constraints met for all customers
- Customer B transition timeline formally agreed before production approval
