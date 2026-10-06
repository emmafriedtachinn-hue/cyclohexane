# Stage 9 — Process Instrumentation, Control and Safety Safeguards

> **Status:** Planned workstream. Develop after the steady-state base case is sufficiently stable. This is a preliminary engineering layer, not a final P&ID, SIS design, or SIL verification.

---

## Purpose

The next maturity step after obtaining a credible steady-state process is to define how the plant would be **measured, controlled, alarmed and brought to a safe state** when conditions deviate from normal operation.

This workstream will convert the process concept from a flowsheet-only model toward a preliminary **P&ID-level control and safeguarding philosophy**.

The design must clearly distinguish between:

- **BPCS / normal process control**
- **operator alarms and interlocks**
- **Safety Instrumented Functions (SIFs) / SIS candidates**
- **mechanical protection such as PSVs and depressurization**
- **fire and gas detection**

No safeguard should be credited as an independent protection layer until its independence and reliability have been demonstrated through the appropriate safety study.

---

## Planned instrumentation philosophy

### 1. Feed preparation

Candidate measurements and controls:

- benzene flow measurement and flow control
- hydrogen-rich gas flow measurement and flow control
- hydrogen/benzene ratio monitoring or ratio control
- pump suction/discharge pressure
- compressor suction/discharge pressure
- compressor discharge temperature
- aftercooler outlet temperature

Candidate safeguards to evaluate:

- low hydrogen/benzene ratio alarm/interlock
- high compressor discharge temperature alarm/trip
- low suction pressure protection
- high discharge pressure protection
- loss-of-feed / loss-of-compressor response

---

### 2. Reaction and interstage cooling

Candidate measurements and controls:

- reactor inlet temperature
- reactor outlet temperature
- additional bed/interstage temperature measurements where the final reactor architecture requires them
- reactor inlet/outlet pressure
- pressure-drop monitoring across catalytic sections
- interstage cooler outlet-temperature control
- cooling-medium flow and temperature monitoring
- hydrogen/benzene ratio monitoring

Candidate safeguards to evaluate:

- high and high-high reactor temperature alarms
- high-high pressure trip
- low cooling-flow alarm/interlock
- low hydrogen/benzene ratio trip
- loss-of-recycle response
- emergency isolation and depressurization logic

The exact shutdown actions and trip set points must be established through HAZOP/LOPA, relief/depressurization studies, equipment limits and validated kinetics. They are not to be guessed from the steady-state model.

---

### 3. High-pressure separator and recycle loop

Candidate measurements and controls:

- separator pressure control
- separator liquid-level control
- vapor and liquid outlet flow measurement
- recycle flow measurement
- purge flow measurement
- recycle-gas composition monitoring where justified
- compressor suction/discharge pressure and temperature

Candidate safeguards:

- high-high separator level
- high-high separator pressure
- recycle-compressor trip response
- high inert concentration / low hydrogen concentration warning where an analyzer is justified
- hydrocarbon and hydrogen gas detection around relevant equipment

---

### 4. Low-pressure flash and distillation feed

Candidate measurements and controls:

- flash pressure control
- flash liquid-level control
- feed-heater outlet-temperature control
- distillation-feed flow, temperature and pressure indication

Candidate safeguards:

- high pressure
- high-high liquid level
- loss of heat / excessive feed temperature
- abnormal vapor carryover

---

### 5. Distillation column

Candidate measurements and controls:

- column pressure control
- reflux flow control
- condenser duty / cooling-medium control
- distillate accumulator level control
- bottoms level control
- reboiler duty or temperature control
- top and bottom temperature indication
- selected tray-temperature monitoring
- feed flow and temperature monitoring

Candidate safeguards:

- high-high column pressure
- condenser cooling failure response
- high reboiler temperature / duty limit
- high-high accumulator or bottoms level
- low reflux / loss-of-reflux alarm
- emergency isolation and relief routing

The final control structure will only be accepted after the rigorous column has converged and the normal operating window is understood.

---

### 6. Fire, gas and occupational-safety instrumentation

The preliminary layout should consider:

- hydrogen detectors
- hydrocarbon / LEL detectors
- fire detection
- detector placement around low points, pits and enclosed areas
- benzene exposure monitoring strategy
- alarms associated with ventilation or containment systems where applicable

Detector type, quantity and location require a separate layout study and must reflect vapor behavior, ventilation and credible leak scenarios.

---

## Planned deliverables

This workstream should ultimately produce:

1. a preliminary instrument index
2. a P&ID-style marked-up process diagram
3. a control narrative for each major process section
4. a normal-control loop list
5. an alarm and trip register
6. a preliminary cause-and-effect matrix
7. candidate Safety Instrumented Functions for later HAZOP/LOPA review
8. a clear separation between BPCS, SIS, relief protection and fire/gas systems
9. a set-point basis tied to equipment limits and process studies
10. DWSIM sensitivity cases that support the safeguard design

---

## Relationship to process-safety work

Instrumentation is not being added as decoration to the flowsheet. It should be derived from credible deviations such as:

- cooling failure
- hydrogen-feed loss
- excess benzene feed
- recycle loss
- blocked outlet
- separator high level
- condenser failure
- reboiler over-duty
- utility loss
- compressor trip

The process-safety review should identify the hazard; the instrumentation work should define how the condition is detected and controlled or tripped; HAZOP/LOPA should then determine whether additional independent protection is required.

---

## Current limitations

The present project does not yet claim:

- final instrument set points
- detailed control-loop tuning
- validated dynamic response
- final P&IDs
- certified SIS architecture
- SIL targets or SIL verification
- proof-test intervals
- final relief-system integration
- vendor-selected instruments

These require a stable process design plus dynamic, mechanical and formal safety studies.
