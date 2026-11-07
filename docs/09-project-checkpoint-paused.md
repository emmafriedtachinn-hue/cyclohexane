# Project Checkpoint — Paused for Process-Control Study

> **Status:** Cyclohexane simulation temporarily paused.  
> **Resume point:** Distillation-model diagnosis before rigorous-column rebuild.

---

## Why the project is paused

The cyclohexane project is being paused intentionally while a separate process-control learning exercise is completed.

The purpose of the separate exercise is to strengthen practical understanding of:

- process instrumentation
- control loops
- manipulated and controlled variables
- P&ID interpretation
- alarms and interlocks
- preliminary safety safeguards

The knowledge gained will later be applied back to the cyclohexane project during **Stage 9 — Process Control, Instrumentation and Safety Safeguards**.

---

## Current cyclohexane flowsheet status

The steady-state DWSIM model currently includes:

- benzene feed preparation
- hydrogen-rich gas compression/conditioning
- feed mixing and preheating
- staged benzene hydrogenation using multiple Conversion Reactors
- intermediate cooling between reaction stages
- reactor-effluent cooling
- high-pressure gas/liquid separation
- purge/recycle concept
- pressure reduction and low-pressure flash
- final feed conditioning before distillation
- shortcut/rigorous distillation development

The model still contains provisional design choices that must not be treated as final industrial design.

---

## Current reactor model

The real process concept is a multi-stage catalytic hydrogenation system, but the DWSIM model currently uses Conversion Reactors because validated kinetics and catalyst-bed data are not yet available.

A three-stage mathematical conversion split was used as a simulation scaffold to approach ~99% overall benzene conversion.

The reaction section demonstrated that uncontrolled adiabatic conversion causes an extreme temperature rise, confirming the need for staged reaction and strong heat removal.

---

## Current separation model

The original source design expected reactor-effluent condensation near ~200 °C and ~23 bar.

The Peng–Robinson simulation showed that the H2-rich multicomponent stream remained essentially vapor under those conditions.

A much lower cooling temperature was therefore introduced as a supported modification to obtain a realistic gas/liquid split.

A second low-pressure flash was also added to reduce residual H2/CH4/N2 before distillation, although measurable cyclohexane loss to the flash vapor remains an open optimization issue.

---

## Current integrated distillation-feed basis

The integrated model currently sends stream 33 to the purification section at approximately:

- molar flow: **249.032 kmol/h**
- mass flow: **20,896.9 kg/h**
- temperature: **70 °C**
- pressure: **1.2 bar**
- vapor fraction: **~0.00386**

Overall mole fractions:

- CH4: ~0.002442
- N2: trace
- H2: ~0.000245
- benzene: ~0.009956
- cyclohexane: ~0.977502
- methylcyclopentane: ~0.009848

---

## Current distillation diagnostic

The distillation section was isolated into a standalone DWSIM case.

A hydrocarbon-only diagnostic feed was created by removing H2/CH4/N2 while retaining the actual hydrocarbon flow from stream 33.

Approximate diagnostic basis:

- total hydrocarbon flow: **~248.36 kmol/h**
- benzene: **~0.00998 mole fraction**
- cyclohexane: **~0.98014**
- MCP: **~0.00987**

Shortcut-column settings:

- Light Key: MCP
- Heavy Key: cyclohexane
- LK mole fraction in bottoms: 0.001
- HK mole fraction in distillate: 0.001
- total condenser
- condenser/reboiler pressure near atmospheric

Latest diagnostic results:

- Rmin: **70.846**
- Nmin: **48.070**
- trial reflux ratio: **~85**
- estimated equilibrium stages: **93.418**
- optimum feed stage: **15.807**
- condenser duty: **~446 kW**
- reboiler duty: **~1.655 MW**

### Unresolved problem

Despite removal of the permanent gases, the Shortcut Column still returns **negative condenser and reboiler temperatures**, which are not physically credible for the benzene/cyclohexane/MCP system near atmospheric pressure.

These shortcut results are therefore **diagnostic only and are not accepted as final design values**.

---

## Exact resume point

When the cyclohexane project resumes, the first task is:

1. inspect Shortcut Column distillate composition
2. inspect Shortcut Column bottoms composition
3. reproduce both product compositions in independent DWSIM material streams
4. perform independent bubble/dew-point temperature checks with Peng–Robinson
5. determine whether the negative-temperature issue originates from:
   - shortcut product calculations
   - thermodynamic setup
   - specifications
   - pressure basis
6. only after resolving this issue, rebuild the rigorous column
7. then close the gas recycle/purge loop
8. then proceed to process-control/instrumentation design

---

## Current roadmap position

Completed:

- Stages 1–6: report review, scope, thermodynamics, feed preparation, reactor development, effluent cooling/separation

Open:

- Stage 7: recycle/purge closure
- Stage 8: rigorous distillation and purification
- Stage 9: process control, instrumentation and safety safeguards
- Stage 10: sensitivity analysis, validation and process-safety review
- Stage 11: final engineering assessment and release

---

## Resume rule

Do not restart the project from the original report or from the early shortcut-column values.

Resume from the **latest integrated process state and latest standalone distillation diagnostic documented here**.

Earlier values remain useful only as development history.
