# Project Brief: VGX Vehicle Interface Controller Development and ICM-4 Migration

## Project Overview

**Project name:** VGX Vehicle Interface Controller Development and ICM-4 Migration
**Project sponsor:** Owner
**Project manager:** Director of Operations
**Document status:** Approved
**Last updated:** June 2026

KreegCo. will design and manufacture the VGX vehicle interface controller as a direct replacement for the ICM-4 series. Two critical components used exclusively in the ICM-4 have reached end-of-life. The Silicon Labs EFM32G890F128 ARM Cortex-M3 microcontroller has been discontinued; no form-compatible replacement exists in the Silicon Labs portfolio. The Maxim MAX3052 CAN transceiver has reached end-of-life; a last-time-buy quantity was placed but covers less than 12 months of production at current run rates. The VGX must be production-ready and customer-qualified before that inventory is exhausted.

---

## Background

The ICM-4 has been in production for nine years. It provides vehicle communication, diagnostic access, and real-time parameter monitoring for OEM electric vehicles. The ICM-4's diagnostic interface uses a proprietary RS-232 protocol. All three affected OEM customers use a legacy PC-side diagnostic tool that communicates with the ICM-4 over this protocol. The VGX will replace the RS-232 diagnostic interface with a new Ethernet-based interface — a first for any KreegCo product. The legacy PC tool must continue to work without modification; the VGX firmware must emulate the ICM-4 RS-232 protocol over the new physical layer.

The VGX will also collect and transmit vehicle telemetry including speed profiles, motor runtime hours, and driver behavior metrics. One customer (Customer B) is based in the EU, and driver behavior logging triggers GDPR obligations that have not yet been assessed.

---

## Product Definition

**Product name:** VGX Vehicle Interface Controller
**Replaces:** ICM-4 series

**Single SKU:** one hardware configuration for all customers.

**Form factor constraints (non-negotiable):**
- PCB mounting pattern must match ICM-4 exactly
- Connector placement and wire harness interface must match ICM-4 exactly
- Enclosure must not exceed ICM-4 envelope
- Contractual for all three customers. No exceptions without written approval.

**Key design updates over ICM-4:**
- New MCU: STM32F767ZIT6 ARM Cortex-M7 (STMicroelectronics) — replacing discontinued EFM32G890F128
- New CAN transceiver: TCAN1042VDRQ1 (Texas Instruments) — replacing discontinued MAX3052
- New Ethernet diagnostic interface: LAN8742A PHY (Microchip) with 10/100BASE-T — replacing RS-232 diagnostic port
- Ethernet diagnostic stack: new from scratch; no internal reference design exists
- Legacy RS-232 ICM-4 diagnostic protocol emulation: required for backwards compatibility with existing customer diagnostic tools. ICM-4 protocol is undocumented; behavior must be reverse-engineered from protocol captures of production ICM-4 units.
- Vehicle telemetry module: runtime data logged and transmitted via optional CAN bridge to customer fleet management platforms

**PCB fabrication:**
Prototype and production PCBs fabricated and assembled through KreegCo's contract manufacturer in Shenzhen, China. Prototype lead times approximately 3–4 weeks from Gerber submission.

---

## Affected OEM Customers

Three customers currently purchasing ICM-4 units are affected by this transition. One is based in the EU.

**Customer A: Continental Fleet Services**
- Application: electric utility and service vehicles
- Location: United States
- Annual volume: approximately 700 units
- Contract terms: 60-day written notice required before any product change.
- Qualification requirement: bench and vehicle-level validation, plus Ethernet diagnostic interface integration test with Continental's telematics platform. Estimated 6 weeks once samples received. Continental's telematics platform vendor has not yet provided an integration specification to KreegCo. No agreement or timeline is in place with that vendor.

**Customer B: VeloTruck GmbH**
- Application: electric light commercial vehicles
- Location: Germany (EU market)
- Annual volume: approximately 500 units
- Contract terms: 90-day written notice required before any product change.
- Qualification requirement: bench and vehicle-level validation, plus review of data handling compliance documentation. Estimated 10 weeks once samples received.
- GDPR note: The VGX firmware layer collects driver behavior metrics (acceleration events, speed profiles, braking frequency) as part of telemetry. Under GDPR, driver behavior data linked to vehicle assignment records constitutes personal data. No formal data protection impact assessment (DPIA) has been conducted. Customer B's master supply agreement includes a data localization clause specifying that personal data of EU drivers may not be processed outside the EEA. Current telemetry architecture routes data through KreegCo's US-based servers. No data processing agreement (DPA) is in place with any downstream data handler. This conflict has not been raised with Customer B.

**Customer C: NorthWest Industrial**
- Application: electric material handling equipment
- Location: United States
- Annual volume: approximately 550 units
- Contract terms: 45-day written notice required before any product change.
- Qualification requirement: bench and vehicle-level validation. Estimated 5 weeks once samples received.
- Stakeholder note: Customer C's VP of Operations has submitted a list of requested diagnostic feature additions and parameter expansions beyond the ICM-4 replacement scope. These requests have not been formally evaluated, declined, or scoped. The VP has indicated informally that qualification sign-off may be contingent on some of these additions being included. No written confirmation of this position exists, and Customer C's engineering team has not been consulted.

---

## Timeline and Milestones

**Project start:** Month 0
**Hard deadline:** Month 11 (ICM-4 CAN transceiver last-time-buy inventory exhausted; Month 11 is the practical cutover target)

| Milestone | Target | Notes |
|-----------|--------|-------|
| Hardware design complete | Month 2 | Includes schematic, layout, BOM |
| Enclosure tooling order placed | Month 1.5 | 6–8 week lead time |
| ICM-4 protocol reverse-engineering complete | Month 2.5 | No documentation exists; scope and duration uncertain |
| PCB fabrication and assembly (proto) | Month 3.5 | First article build |
| Ethernet diagnostic stack bring-up complete | Month 5 | New from scratch; no internal reference |
| ICM-4 protocol emulation validated | Month 5.5 | Contingent on reverse-engineering completeness |
| Internal validation complete | Month 6 | All internal test criteria met |
| GDPR/data compliance review complete | Month 5 | Not yet scheduled; external legal review likely required |
| OEM sample units shipped (all customers) | Month 6.5 | |
| Customer C qualification complete | Month 8 | NorthWest Industrial — out-of-scope feature request unresolved |
| Customer A qualification complete | Month 8.5 | Continental Fleet Services — telematics integration contingent on vendor spec |
| Customer B qualification complete | Month 9.5 | VeloTruck GmbH — contingent on GDPR compliance resolution |
| Production build complete | Month 10 | First production run |
| ICM-4 cutover complete | Month 11 | All customers transitioned to VGX |

---

## Resource Plan

**Engineering lead:** Senior Firmware Engineer
Primary technical resource for all firmware development including Ethernet stack, protocol emulation, and telemetry module. Simultaneously allocated to two other active firmware projects through Month 6, each carrying a 20–25% time commitment. Also carries an ongoing production support queue throughout the project.

**Hardware Engineer:** 40% allocation
Responsible for schematic capture, PCB layout, and component selection. No firmware involvement. Shared with other hardware projects.

**Operations/PM:** Director of Operations
**Manufacturing:** Production team (capacity not formally reserved)

**External resources:**
- PCB contract manufacturer (Shenzhen, China): standard vendor
- Enclosure moulder: new tooling required. Vendor not yet selected.
- LAN8742A Ethernet PHY (Microchip): fabricated at TSMC fabs in Taiwan. No alternative qualified supplier. Lead times currently 8–10 weeks for production quantities.
- TCAN1042VDRQ1 (TI): available at standard lead times.
- Continental's telematics platform vendor: integration specification required. Initial contact made; no response received. No agreement or timeline in place.
- VeloTruck GmbH fleet data vendor: DPA required before telemetry architecture can be finalized. Not yet contacted.
- Customer C diagnostic tooling vendor: legacy protocol documentation may require vendor cooperation for reverse-engineering. Not yet contacted.
- External GDPR/data compliance legal counsel: not engaged. Not budgeted.

---

## Budget

A project budget of $140,000 has been approved by the owner. This is a hard cap.

Known cost categories:
- Enclosure injection mould tooling: $24,000 (fixed, committed cost)
- PCB fabrication, SMT assembly (prototype and first production run)
- Component procurement and safety stock
- Customer sample units (3 customers)
- Engineering time (internal, not separately budgeted)
- GDPR legal review: not budgeted
- Ethernet protocol integration testing with Customer A's telematics vendor: not budgeted

No contingency line has been allocated. The tooling commitment leaves $116,000 for all remaining costs. PCB assembly and component cost estimates were prepared using pre-tariff pricing. The LAN8742A PHY and PCB assembly (China) are subject to the current Section 301 tariff schedule, which was not reflected in the budget baseline. Revised cost estimates have not been prepared.

---

## Known Constraints

- 11-month hard deadline is fixed. Driven by ICM-4 CAN transceiver last-time-buy inventory.
- Ethernet diagnostic stack is a first-time implementation for KreegCo. No internal reference design, prior implementation experience, or reusable code base exists.
- ICM-4 diagnostic protocol is entirely undocumented. Reverse-engineering from protocol captures is the only available approach. Duration and completeness cannot be guaranteed.
- Senior Firmware Engineer is the only full-time technical resource and is simultaneously allocated to two other active firmware projects.
- GDPR obligations from driver behavior logging have not been assessed. Current telemetry architecture may be non-compliant with Customer B's data localization clause.
- No DPA is in place with any downstream data handler.
- Three external integration dependencies exist with no signed agreements. Two vendors have not responded to initial contact.
- Customer C's out-of-scope feature request has not been formally addressed. The VP's implied qualification sign-off condition creates schedule risk.
- LAN8742A sourced exclusively from TSMC Taiwan fabs. PCB assembly through China CM under active Section 301 tariffs. Budget is not updated for current tariff rates.

---

## Success Criteria

- VGX in production and shipping to all three OEM customers before ICM-4 inventory reaches zero
- All three customers have completed qualification and issued production approval before cutover
- ICM-4 legacy diagnostic protocol fully emulated; existing customer PC tools function without modification
- Ethernet diagnostic interface validated with all three customers' integration environments
- GDPR compliance confirmed for driver behavior telemetry before any EU data is collected
- No contract penalties triggered
- Customer C feature request formally scoped or declined in writing before qualification begins
- Form factor constraints met for all customers with no contract amendments required
