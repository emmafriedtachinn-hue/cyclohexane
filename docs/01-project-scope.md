# Stage 2 — Project Scope and Simulation Philosophy

## Purpose

The purpose of this project is to develop a progressively more realistic DWSIM representation of a **500 t/day cyclohexane unit based on benzene hydrogenation**.

The project is intentionally both:

- a **process-engineering exercise**, and
- a **DWSIM learning project**.

The simulation should therefore expose as many relevant DWSIM operations and workflows as practical without sacrificing physical credibility simply to increase software complexity.

---

## Main objective

> Reproduce the original process in DWSIM as faithfully as possible, identify where the source design does not behave realistically, and implement justified engineering modifications while documenting the reason for every major change.

---

## What “realistic” means in this project

A modification is considered justified when supported by one or more of:

1. material and energy balances
2. thermodynamic phase behavior
3. equipment operating principles
4. process-control or operability requirements
5. process-safety considerations
6. credible industrial literature
7. published industrial process descriptions
8. realistic convergence behavior that reveals a genuine modeling inconsistency

A modification should **not** be introduced solely because it makes DWSIM converge if the resulting flowsheet has no reasonable physical interpretation.

---

## Four-layer decision record

Every major parameter should eventually be traceable as:

~~~text
Original report value
        ↓
DWSIM reproduction
        ↓
Engineering/literature review
        ↓
Final project value
~~~

This is especially important for:

- reactor temperature and pressure
- conversion and selectivity
- hydrogen excess
- reactor staging
- heat-removal strategy
- separator conditions
- recycle/purge fraction
- distillation design
- heat integration
- equipment pressure drops

---

## Scope included

The project includes:

- thermodynamic model selection
- process-feed definition
- compression and pumping
- feed conditioning
- heat exchange
- reaction modeling
- staged heat removal
- flash separation
- purge/recycle loops
- shortcut distillation
- rigorous distillation
- convergence analysis
- sensitivity analysis
- material and energy balance validation
- preliminary equipment-performance checks
- process-safety review
- comparison against industrial/literature benchmarks

---

## Scope not yet claimed

The current project does **not** claim:

- construction-ready reactor design
- validated commercial catalyst kinetics
- final catalyst loading
- detailed mechanical design
- complete piping design
- final relief-valve sizing
- flare-network design
- full HAZOP/LOPA
- SIL verification
- detailed metallurgy specification
- civil/structural design
- vendor-certified equipment selection
- permitting package
- final CAPEX/OPEX estimate

These can only be added when supported by the necessary engineering data.

---

## DWSIM-learning objective

The project should deliberately practice relevant DWSIM features when they are technically appropriate.

Current or planned operations include:

- streams and property packages
- pump
- compressor
- valve
- mixer
- heater/cooler
- heat exchanger
- reaction manager
- conversion reactor
- flash separator
- splitter
- recycle block
- shortcut column
- rigorous distillation column
- convergence-solvers
- design specifications
- sensitivity analysis
- energy integration

Where possible, simple temporary blocks should later be replaced by more realistic equipment models once the required data are available.

---

## Model-development strategy

The project will be developed in increasing levels of rigor:

### Level 1 — Reproduce
Implement the source process and verify basic material/energy behavior.

### Level 2 — Diagnose
Identify inconsistencies, unrealistic states, convergence problems and missing data.

### Level 3 — Improve
Introduce documented engineering modifications.

### Level 4 — Validate
Compare key results with literature, industrial references and independent calculations.

### Level 5 — Stress-test
Perform sensitivities and examine operating envelopes.

### Level 6 — Release
Publish a clean final flowsheet together with assumptions, limitations and validation evidence.

---

## Repository philosophy

GitHub is used as an **engineering development log**, not only as final file storage.

Meaningful model milestones should be recoverable in version history, while the Markdown documentation explains why the model changed.

A final simulation file without the engineering reasoning is considered incomplete.
