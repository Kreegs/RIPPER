# Project Brief: ARC Variable Speed Drive Development and ZBR-II Migration

## Project Overview

**Project name:** ARC Variable Speed Drive Development and ZBR-II Migration
**Project sponsor:** Owner
**Project manager:** Director of Operations
**Document status:** Approved
**Last updated:** June 2026

KreegCo. will design, certify, and manufacture the ARC variable speed drive module as a direct replacement for the ZBR-II series. Two critical components used in the ZBR-II have reached end-of-life. The custom power management ASIC was manufactured exclusively by MagnaChip Semiconductor; MagnaChip announced closure of the relevant fabrication line, and no compatible replacement ASIC exists. The IXTH20N60 power MOSFET (IXYS) has been discontinued; a last-time-buy quantity was placed but covers less than 11 months of production at current run rates. The ARC must be production-ready and customer-qualified before that stock is exhausted.

---

## Background

The ZBR-II has been in production for twelve years. Its custom ASIC handled motor phase monitoring, fault detection, and thermal management functions previously unachievable in firmware. The ARC must replicate these functions in software on a new processor platform — a significant scope increase over a straightforward component swap. Two of the four affected OEM customers operate in markets requiring CE marking and international regulatory approvals not required by the ZBR-II. This project adds regulatory compliance scope that did not exist in the original product.

The ARC will include a data logging module that records cycle counts, fault events, and runtime hours. This data is transmitted to a cloud-hosted dashboard accessed by two customers for fleet analytics. The cloud dashboard is operated by a third-party SaaS vendor.

---

## Product Definition

**Product name:** ARC Variable Speed Drive Module
**Replaces:** ZBR-II series

**Single SKU:**
- ARC: one hardware configuration for all customers. Regional variants are software-configured.

**Form factor constraints (non-negotiable):**
- Mounting pattern must match ZBR-II exactly
- Connector placement and wire harness interface must match ZBR-II exactly
- Enclosure envelope must not exceed ZBR-II dimensions
- Contractual for all four customers. No exceptions without written approval and contract amendment.

**Key design updates over ZBR-II:**
- New processor: STM32H743ZIT6 ARM Cortex-M7 (STMicroelectronics) — replacing MagnaChip ASIC and existing control MCU
- New power stage: IPW60R070C7 CoolMOS MOSFET (Infineon) — replacing discontinued IXTH20N60
- ASIC functions (phase monitoring, fault detection, thermal management) reimplemented in firmware — no prior implementation reference exists internally
- New injection-moulded enclosure (new tooling required)
- Data logging module: onboard flash storage + cellular modem for cloud transmission (Quectel EC21 module)
- EMC-compliant design required for CE marking

**PCB fabrication:**
Prototype and production PCBs fabricated and assembled through Alltrax's contract manufacturer in Shenzhen, China.

---

## Affected OEM Customers

Four customers currently purchasing ZBR-II units are affected by this transition. Two operate in markets requiring CE marking.

**Customer A: Inland Logistics Systems**
- Application: electric tow vehicles and AGVs
- Annual volume: approximately 600 units
- Contract terms: 60-day written notice required before any product change.
- Qualification requirement: bench and vehicle-level validation. Estimated 6 weeks once samples received.
- Data logging: Customer A uses the cloud dashboard. Data includes vehicle cycle counts and fault events.

**Customer B: Harborview Equipment**
- Application: electric forklifts and reach trucks
- Annual volume: approximately 900 units
- Contract terms: liquidated damages clause if supply is interrupted for more than 30 consecutive days.
- Qualification requirement: bench validation, vehicle validation, and fleet analytics integration review. Estimated 8 weeks once samples received.
- Data logging: Customer B uses the cloud dashboard. Customer B's master supply agreement contains a data processing clause specifying that vehicle operational data may not be stored outside the EU. Current cloud dashboard architecture stores data on US-based servers. This clause has not been reviewed against the proposed architecture. No data processing agreement (DPA) is in place with the SaaS dashboard vendor.

**Customer C: Europort Handling GmbH**
- Application: electric port equipment
- Location: Germany (EU market)
- Annual volume: approximately 250 units
- Contract terms: 90-day notice clause. CE marking is a prerequisite for any product sold into EU market. Non-compliant product cannot legally ship.
- Qualification requirement: bench and vehicle-level validation, plus review of CE technical file and Declaration of Conformity. Estimated 10–12 weeks once samples received. Europort's procurement process requires a certified CE mark before any purchase order will be issued.

**Customer D: Pacific Industrial Solutions**
- Application: electric maintenance and utility vehicles
- Location: Australia and New Zealand
- Annual volume: approximately 300 units
- Contract terms: 60-day notice clause.
- Qualification requirement: bench validation and RCM mark (Australia/New Zealand regulatory requirement). Estimated 6–8 weeks once samples received. RCM testing and registration must be completed before units can be legally sold in the AU/NZ market.

---

## Timeline and Milestones

**Project start:** Month 0
**Hard deadline:** Month 11 (ZBR-II MOSFET last-time-buy stock exhausted; practical cutover target is Month 11 to provide one month buffer)

| Milestone | Target | Notes |
|-----------|--------|-------|
| Hardware design complete | Month 2 | Includes schematic, layout, BOM |
| Enclosure tooling order placed | Month 1.5 | 6–10 week lead time |
| PCB fabrication and assembly (proto) | Month 3.5 | First article build |
| ASIC firmware function reimplementation complete | Month 4.5 | No internal reference; timeline estimate carries high uncertainty |
| Internal validation complete | Month 5 | All internal test criteria met |
| CE pre-compliance testing | Month 5.5 | External lab. Lab not yet selected or scheduled. |
| CE formal submission | Month 6.5 | Contingent on pre-compliance results |
| RCM test submission | Month 6 | External AU test facility. Not yet engaged. |
| CE mark received | Month 8.5 | Target. Timeline outside Alltrax control. |
| RCM mark received | Month 7.5 | Target. Timeline outside Alltrax control. |
| OEM sample units shipped (Customers A and B) | Month 5.5 | Non-certified units for domestic customers |
| OEM sample units shipped (Customers C and D) | Month 8.5 | Contingent on CE/RCM receipt |
| Customer A qualification complete | Month 7.5 | Inland Logistics Systems |
| Customer B qualification complete | Month 9 | Harborview Equipment |
| Customer C qualification complete | Month 10 | Europort Handling — contingent on CE mark |
| Customer D qualification complete | Month 9.5 | Pacific Industrial — contingent on RCM mark |
| Production build complete | Month 10.5 | First production run |
| ZBR-II cutover complete | Month 11 | All customers transitioned to ARC |

---

## Resource Plan

**Engineering lead:** Senior Electrical and Firmware Engineer
Primary designer for all hardware and firmware including ASIC function reimplementation. Sole technical resource on this project. Also allocated to a separate R&D initiative beginning Month 4, carrying an estimated 30% time commitment through project end.

**QA Manager:** shared resource
Responsible for CE and RCM compliance documentation, test coordination, and technical file preparation. Also carries ongoing production QA responsibilities throughout the project. No prior CE certification experience on the Alltrax product line.

**Operations/PM:** Director of Operations
**Manufacturing:** Production team (capacity not formally reserved)

**External resources:**
- PCB contract manufacturer (Shenzhen, China): standard vendor
- Enclosure moulder: new tooling required. Vendor not yet selected.
- CE test laboratory (EU or accredited US lab): not yet selected. Typical slot lead time 4–6 weeks.
- RCM test facility (Australia): not yet engaged. International shipping of test samples adds 2–3 weeks.
- Cloud dashboard SaaS vendor: third-party provider. No formal agreement beyond subscription terms. No DPA in place.
- Component suppliers: IPW60R070C7 (Infineon) available at standard lead times. Quectel EC21 cellular module: 8–10 week lead time for production quantities.

---

## Budget

A project budget of $280,000 has been approved by the owner. This is a hard cap.

Known cost categories:
- Enclosure injection mould tooling: $35,000 (fixed, committed cost)
- CE testing and certification: estimated $18,000–$30,000 (range reflects lab selection and test scope uncertainty)
- RCM testing and registration: estimated $6,000–$10,000
- PCB fabrication, SMT assembly (prototype and first production run)
- Component procurement including safety stock
- Customer sample units (4 customers)
- Engineering time (internal, not separately budgeted)
- GDPR/data compliance legal review: not budgeted

Contingency: $12,000 allocated (4.3% of total budget). CE and RCM testing cost range alone spans $24,000. Contingency does not cover a high-side testing outcome.

---

## Known Constraints

- 11-month hard deadline is fixed. Driven by ZBR-II MOSFET last-time-buy inventory.
- ASIC function reimplementation in firmware has no internal precedent. Effort and timeline carry meaningful uncertainty.
- CE marking and RCM approval timelines are outside Alltrax control. Both are on the critical path for two customers.
- ZBR-II firmware (~40,000 lines of undocumented C) must be partially ported to the STM32H743 platform. No test suite exists. No isolated test environment exists for validation.
- Cloud dashboard data storage may conflict with Customer B's EU data localization clause. No DPA exists with the SaaS vendor.
- QA Manager has no prior CE certification experience on Alltrax products.
- Manufacturing in China and component sourcing from Taiwan-based fabs introduces tariff exposure. Budget cost estimates were prepared before the most recent tariff schedule revision.

---

## Success Criteria

- ARC in production and shipping to all four OEM customers before ZBR-II MOSFET inventory reaches zero
- CE mark received before any unit ships to Customer C or EU-market customers
- RCM mark received before any unit ships to Customer D or AU/NZ-market customers
- All four customers have completed qualification and issued production approval before cutover
- No contract penalties triggered
- Customer B data processing reviewed and compliant architecture confirmed before cloud dashboard goes live
- ASIC firmware functions validated to ZBR-II behavioral specification
- Manufacturing defect rate equal to or lower than ZBR-II baseline
