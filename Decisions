# Decision Log

This log records assumptions and design choices as they are made, so the reasoning behind the project stays traceable. Each decision has a status:

- **Accepted**: decided and in use.
- **Proposed**: initial assumption, to be confirmed when the design brief is finalised.
- **Superseded**: replaced by a later decision (link to the new one).

Decisions are never deleted. If something changes, add a new entry and mark the old one as superseded.

## Overview

| ID | Decision | Status |
|----|----------|--------|
| D-001 | Building type and staged versions | Accepted |
| D-002 | Structural concept: concrete core + steel frame | Accepted |
| D-003 | Design codes and basis of design | Proposed |
| D-004 | Materials | Proposed |
| D-005 | Geometry: storeys and column grid | Proposed |
| D-006 | Slab system and diaphragm action | Proposed |
| D-007 | Connections and support conditions | Proposed |
| D-008 | Loads | Proposed |
| D-009 | Analysis method | Proposed |
| D-010 | BIM and analytical modelling conventions | Accepted |
| D-011 | Scope limitations | Accepted |

---

## D-001: Building type and staged versions

**Date:** 2026-10-04 · **Status:** Accepted

**Decision:** A 5–6 storey mixed-use building in Copenhagen with retail on the ground floor and offices above. The project is developed in three versions:

- **A:** regular baseline building.
- **B:** column-free ground floor hall with transfer beams.
- **C:** cantilevered or set-back top floor.

**Rationale:** A realistic and typical Danish building type. Staging means the full pipeline is proven on a simple model before complexity is added, and there is always a finished version to fall back on.

---

## D-002: Structural concept

**Date:** 2026-10-04 · **Status:** Accepted

**Decision:** Horizontal stability is provided by a cast-in-situ concrete core (stairs and lifts) only. Vertical loads are carried by a steel frame of columns and beams. The steel frame is not part of the stabilising system.

**Rationale:** A common system in Danish office buildings. It gives a clear load path and separates the problem into a stabilising system (concrete) and a gravity system (steel), so both materials are covered.

**Consequences:** The position of the core relative to the building's center of mass governs torsion. This becomes important in Version C.

---

## D-003: Design codes and basis of design

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:**
- Eurocodes with Danish National Annexes (DS/EN 1990–1993).
- Consequence class **CC2**, giving $K_{FI} = 1.0$.
- Design working life: **50 years**.

**Rationale:** CC2 is the normal class for an office building of this size.

---

## D-004: Materials

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:**
- Structural steel: **S355** for all members.
- Concrete core and foundations: **C30/37**.
- Reinforcement: **B500**, ductility class B.
- Exposure class: **XC1** for interior elements; foundations to be assessed separately.

**Rationale:** Standard, widely available grades.

---

## D-005: Geometry

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:**
- Ground floor (retail): storey height approx. **4.5 m**.
- Office floors: storey height approx. **3.6 m**.
- Regular column grid of approx. **7.2 m × 7.2 m** in Version A. To be confirmed against the slab spans in D-006.

**Rationale:** Typical values that give room for installations and suit both hollow-core and composite slab spans.

---

## D-006: Slab system and diaphragm action

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:** Precast hollow-core slabs spanning one way between steel beams. The floors are assumed to act as **rigid diaphragms** that transfer horizontal loads to the core, provided by grouted joints and tie reinforcement.

**Alternatives considered:** Composite steel-concrete slabs. These may be revisited if the analysis or the Version B layout favours them.

**Rationale:** Hollow-core slabs are standard in Denmark and fit well with a steel frame.

---

## D-007: Connections and support conditions

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:**
- Beam-to-column connections are **pinned** (simple connections).
- Steel columns are **pinned at the base** and modelled as continuous over at least two storeys, with splices assumed pinned in the global model.
- The core is **fixed at the base**.
- Soil-structure interaction is not modelled initially.

**Rationale:** Consistent with D-002: the steel frame carries only vertical loads and relies on the core for stability.

---

## D-008: Loads

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:**
- **Imposed loads:** category B (offices) and category D (retail), with values taken from DS/EN 1991-1-1 and the DK NA.
- **Partitions:** included as an equivalent distributed load according to DS/EN 1991-1-1.
- **Snow:** characteristic ground snow load according to DS/EN 1991-1-3 with DK NA.
- **Wind:** DS/EN 1991-1-4 with DK NA, terrain category to reflect an urban location.
- **Imperfections:** equivalent horizontal forces included in all ULS combinations.
- **Not included:** accidental loads and seismic loads. Seismic loading is generally not governing in Denmark.

**Rationale:** These cover the governing actions for this building type. Exact values are documented with references in the load calculations.

---

## D-009: Analysis method

**Date:** 2026-10-04 · **Status:** Proposed

**Decision:**
- **Linear elastic, first-order** global analysis as the default.
- Check $\alpha_{cr}$ for each ULS combination. If $\alpha_{cr} < 10$, second-order effects must be included.
- Concrete core stiffness: use **uncracked** properties initially, and run a sensitivity check with reduced stiffness.

**Rationale:** Standard practice for a braced building. The sensitivity check shows how much the results depend on the stiffness assumption.

---

## D-010: BIM and analytical modelling conventions

**Date:** 2026-10-04 · **Status:** Accepted

**Decision:**
- **Schema:** IFC4, authored in Blender with Bonsai.
- **BIM content:** only load-bearing elements are modelled in detail. Facades and interior walls are represented as loads, not geometry.
- **Analytical model:** a centerline model, with nodes snapped at member intersections using a fixed tolerance.
- **Units:** SI throughout (m, kN, kPa, MPa) in the analysis code.
- **Analysis data:** stored in custom property sets in the IFC model.

**Rationale:** Keeps the BIM model focused on structure and makes the IFC-to-analysis conversion predictable.

---

## D-011: Scope limitations

**Date:** 2026-10-04 · **Status:** Accepted

**Decision:** The following are **out of scope**, at least initially:
- fire design, beyond noting requirements;
- detailed foundation design and geotechnics;
- dynamic analysis beyond modal analysis;
- construction stages and temporary works.

**Rationale:** Keeps the project focused on FEM, steel and concrete design. These can be added later as extensions.

---

## Open questions

- Should the steel beams be designed as composite with the slab, or as plain steel beams?
- Where should the core be placed, central or eccentric? An eccentric core would make the torsion analysis more interesting.
- Hollow-core vs. composite slabs for the transfer region in Version B.
- How should cracked stiffness of the core be handled in the final analysis?
