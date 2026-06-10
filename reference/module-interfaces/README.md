# Module Interfaces

This folder defines the inter-module interface specifications for the multi-module PM agent system. Each specialist module maintains its own interface file here when it is built.

---

## Purpose

Future PM agent modules — Schedule Analyst, Budget Tracker, Scope Change Evaluator, Stakeholder Communication Drafter — will read and write shared context through defined interfaces. Interface files specify what data each module produces, what it consumes, and where it expects to find project state. Keeping these definitions in one place ensures modules can be built independently without creating incompatibilities.

---

## Module Registry

| Module | Status | Interface file |
|--------|--------|----------------|
| RIPPER — Risk Specialist | Active | [risk-interface.md](risk-interface.md) |
| Schedule Analyst | Planned | — |
| Budget Tracker | Planned | — |
| Scope Change Evaluator | Planned | — |
| Stakeholder Communication Drafter | Planned | — |

---

## Interface File Convention

Each interface file defines:

- **Produces** — what structured data this module outputs (format and location)
- **Consumes** — what data from other modules this module reads
- **Trigger** — what events or queries activate this module
- **Scope boundary** — what this module does not handle, and which module does

When a new module is built, add its interface file here and update the registry above before writing any module logic. The interface is the contract; the implementation comes after.
