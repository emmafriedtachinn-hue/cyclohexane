# Cyclohexane Production by Benzene Hydrogenation in DWSIM

> **Process engineering / simulation practice project**  
> **Simulation engine:** DWSIM  
> **Thermodynamic model:** Peng–Robinson (current base case)  
> **Nominal production target:** 500 t/day cyclohexane  
> **Current status:** Rigorous distillation troubleshooting, recycle closure and instrumentation/safeguard planning in progress

---

## Project Overview

This repository documents the progressive development of a DWSIM model for the production of cyclohexane by catalytic hydrogenation of benzene.

The project starts from the original engineering report **“Production de cyclohexane par hydrogénation du benzène”**, then progressively tests, reproduces, questions, and improves the process in DWSIM.

The objective is twofold:

1. **Practice DWSIM as extensively as possible** across realistic process-engineering tasks.
2. **Keep the simulation as close to industrial reality as the available data allow.**

The original report is the design basis, but it is not treated as untouchable. When a report assumption does not reproduce physically in DWSIM, or when a more realistic implementation is supported by thermodynamics, equipment practice, process safety, or literature, the change is documented rather than silently introduced.

## Core Engineering Principle

Every important design decision is tracked through four layers:

| Layer | Question |
|---|---|
| **Original report** | What did the source design specify? |
| **DWSIM result** | What happens when that design is simulated? |
| **Engineering / literature check** | Is the result physically and industrially credible? |
| **Final project decision** | What is implemented, and why? |

## Project Roadmap

- [x] **Stage 1 — Original report review and process background**
- [x] **Stage 2 — Project scope and simulation philosophy**
- [x] **Stage 3 — Initial process design basis and thermodynamic setup**
- [x] **Stage 4 — Components, feeds, compression and conditioning**
- [x] **Stage 5 — Reactor-model development and thermal behavior**
- [x] **Stage 6 — Reactor-effluent cooling and phase separation**
- [ ] **Stage 7 — Gas recycle, purge and full closed-loop convergence**
- [ ] **Stage 8 — Rigorous distillation and product purification**
- [ ] **Stage 9 — Process instrumentation, control philosophy and safety safeguards**
- [ ] **Stage 10 — Sensitivity analysis, validation and process-safety review**
- [ ] **Stage 11 — Final engineering assessment and release**

The checkboxes represent the current simulation-development state, not completion of detailed engineering.

## Current Process Concept

~~~text
Benzene feed ----> Pump -----------------------------\
                                                       > Mixer
Hydrogen-rich feed -> Compressor -> Aftercooler -----/

Mixer
  |
  v
Feed preheating / vaporization
  |
  v
Reaction section
  |   staged benzene hydrogenation
  |   strong heat removal requirement
  v
Effluent cooler
  |
  v
High-pressure gas/liquid separator
  |------------------> H2-rich gas -> purge + recycle
  |
  v
Hydrocarbon-rich liquid
  |
  v
Pressure reduction / light-gas removal
  |
  v
Distillation
  |------------------> light impurities / MCP-rich stream
  |
  v
Cyclohexane product
~~~

The exact arrangement is still being audited. Temporary modeling accommodations are explicitly listed in [Assumptions and deviations](docs/04-assumptions-and-deviations.md).

## Reaction

Main reaction:

~~~text
C6H6 + 3 H2 -> C6H12
~~~

The reaction is strongly exothermic. The original report uses vapor-phase benzene hydrogenation over Raney nickel supported on alumina at approximately 180–200 °C and ~23 bar, with conversion above 99%.

The current DWSIM model uses staged **Conversion Reactors** as a provisional representation because the source report does not provide a complete validated kinetic expression suitable for a rigorous packed-bed reactor model.

## Current DWSIM Components

- Hydrogen
- Benzene
- Cyclohexane
- Methane
- Nitrogen
- Methylcyclopentane (MCP)

Current fresh-gas basis used during model development:

- H2: 95 mol%
- CH4: 4.9 mol%
- N2: 0.1 mol%

The final feed specification remains subject to validation against the selected industrial process basis.

## Current Key Findings

### Reactor thermal behavior

A single high-conversion adiabatic conversion reactor produced an unrealistically severe temperature rise in DWSIM. This confirmed the need for staged reaction and/or strong heat removal, consistent with the original report's multi-stage concept.

### Reactor-effluent condensation

The original report cools the reactor effluent to about 200 °C at ~23 bar before gas/liquid separation. In the Peng–Robinson simulation, the multicomponent reactor effluent remained essentially vapor at those conditions because the light-gas content lowers the hydrocarbon partial pressures.

The current model therefore cools the effluent further before separation. The exact optimized separator temperature is still to be established.

### Distillation

The integrated model currently sends stream 33 to the purification column at approximately **249.032 kmol/h, 70 °C and 1.2 bar**, with a small vapor fraction and residual H2/CH4/N2.

A standalone column case is now being used to diagnose the separation independently. In a hydrocarbon-only diagnostic feed derived from the actual simulation stream, the Shortcut Column returned approximately:

- Minimum stages: **48.07**
- Minimum reflux ratio: **70.85**
- Trial design reflux ratio: **~85**
- Estimated equilibrium stages: **93.4**
- Optimum feed stage: **~15.8**
- Condenser duty: **~446 kW**
- Reboiler duty: **~1.66 MW**

These values are **not yet accepted as final design data** because the shortcut model is still returning unphysical negative condenser/reboiler temperatures. The current task is to isolate whether the issue is caused by shortcut-product calculations, thermodynamic setup or specification choice before transferring any design to the rigorous column.

Earlier shortcut and rigorous-column trials are retained in the construction log as development history.

## DWSIM Skills Practiced

This project is intentionally being used as a broad DWSIM learning exercise. Features already used or planned include:

- Property-package selection
- Material streams
- Pumps
- Compressors
- Valves
- Mixers
- Heaters and coolers
- Heat exchangers
- Reaction definitions and reaction sets
- Conversion reactors
- Flash separators
- Splitters
- Recycle blocks
- Shortcut distillation
- Rigorous distillation
- Column convergence methods
- Sensitivity studies
- Equipment sizing and energy integration
- Preliminary process instrumentation and control philosophy
- Alarm/interlock and cause-and-effect development
- Safety-instrumented-function screening

## Repository Structure

~~~text
.
├── README.md
├── docs/
│   ├── 00-original-report-basis.md
│   ├── 01-project-scope.md
│   ├── 02-process-design-basis.md
│   ├── 03-model-construction-log.md
│   ├── 04-assumptions-and-deviations.md
│   ├── 05-process-safety.md
│   ├── 06-sensitivity-analysis.md
│   └── 07-engineering-evaluation.md
├── simulation/
│   └── README.md
├── figures/
│   └── README.md
└── references/
    └── README.md
~~~

## Documentation

- [Original report basis](docs/00-original-report-basis.md)
- [Project scope](docs/01-project-scope.md)
- [Process design basis](docs/02-process-design-basis.md)
- [Model construction log](docs/03-model-construction-log.md)
- [Assumptions and deviations](docs/04-assumptions-and-deviations.md)
- [Process safety](docs/05-process-safety.md)
- [Sensitivity-analysis plan](docs/06-sensitivity-analysis.md)
- [Engineering evaluation](docs/07-engineering-evaluation.md)
- [Process instrumentation, control and safety safeguards](docs/08-process-instrumentation-and-control.md)

## Project Status

The repository is a **working engineering log**, not a claim of construction-ready design.

A DWSIM flowsheet can establish material/energy balances and test process behavior, but industrial implementation would additionally require validated kinetics, detailed equipment design, hydraulic checks, metallurgy, relief and flare design, control/SIS design, HAZOP/LOPA, mechanical design, vendor data, operability studies, environmental permitting and professional engineering review.

The goal is to make each successive simulation version more technically defensible while preserving the development history.
