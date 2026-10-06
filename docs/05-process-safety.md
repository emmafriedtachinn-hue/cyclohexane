# Stage 10 Workstream — Process Safety

> **Status:** Working safety framework. Not a substitute for formal HAZOP, LOPA, relief design or professional review.

The dedicated preliminary instrumentation/control workstream is documented in [Process instrumentation, control and safety safeguards](08-process-instrumentation-and-control.md).

---

## Why this process requires serious safety treatment

The flowsheet combines:

- high-pressure hydrogen
- highly flammable hydrocarbons
- carcinogenic benzene
- a strongly exothermic catalytic reaction
- hot pressurized equipment
- compressors and recycle gas
- potential catalyst-related hazards
- distillation and hydrocarbon storage

A converged DWSIM model is therefore only one part of the engineering problem.

---

## Main process hazards

### 1. Reaction runaway and catalyst-bed hot spots

Benzene hydrogenation is strongly exothermic.

The DWSIM adiabatic tests already demonstrated that near-total conversion in one uncontrolled step can produce an extreme temperature rise.

The final design must therefore address:

- heat-removal capacity
- hydrogen/benzene ratio
- interstage temperature control
- maximum catalyst temperature
- cooling failure
- feed maldistribution
- loss of recycle gas
- loss of temperature control

### 2. Hydrogen fire and explosion

Relevant areas include:

- fresh-H2 compression
- recycle compressor
- reactor feed system
- reactor section
- high-pressure separator
- purge system
- depressurization / flare connections

The real design will require appropriate gas detection, ventilation, ignition-source control, electrical area classification, emergency isolation, depressurization, relief systems and inerting procedures where applicable.

### 3. Benzene exposure

Benzene is a major occupational-health hazard in addition to its flammability.

Design implications include closed transfer, leak minimization, vapor control, sampling strategy, maintenance isolation, appropriate PPE/exposure monitoring, drainage and containment.

### 4. Cyclohexane release

Cyclohexane is highly flammable and its vapors can form dangerous vapor clouds.

Special attention is needed around separators, distillation, storage, pumps, drains, loading/unloading and maintenance pits/low points.

### 5. Hot hydrogen service and materials

High-temperature hydrogen can create materials-degradation risks depending on temperature, pressure and metallurgy.

The DWSIM model does not evaluate high-temperature hydrogen attack, hydrogen embrittlement, weld quality, corrosion allowance or material compatibility.

These require separate mechanical/materials engineering.

---

## Incident lessons to retain for later formal study

### Flixborough, UK (1974)

A catastrophic cyclohexane release and vapor-cloud explosion followed failure of a temporary bypass.

**Relevance:** management of change, mechanical integrity, temporary modifications, pressure testing and large flammable inventories.

Flixborough involved cyclohexane oxidation rather than benzene hydrogenation, but the containment and vapor-cloud lessons remain directly relevant.

### Hydrogenation-reactor maintenance incidents

Published accident databases contain cases where hydrogen, catalyst and oxygen were present during maintenance/opening operations.

**Relevance:** catalyst handling, pyrophoric behavior, isolation, purge/inerting sequence, gas testing and startup/shutdown procedures.

### Hot-hydrogen piping failures

Recent investigation reports have highlighted catastrophic hot-H2 piping failure where materials were unsuitable for the actual service.

**Relevance:** materials selection, damage mechanisms, inspection and assumptions that full-bore rupture is impossible.

### Cyclohexane maintenance / confined-area releases

Recent incidents have shown that cyclohexane vapor can accumulate in low areas and may not be detected by poorly located sensors.

**Relevance:** detector placement, vapor density, pits/drains, maintenance configuration and line reinstatement.

---

## Safety features to add to the engineering documentation

The future process-safety package should at minimum consider:

- PSVs on relevant pressure vessels
- emergency depressurization philosophy
- flare/vent routing
- high-high temperature reactor trip
- high-high pressure trip
- low hydrogen/benzene ratio interlock if required
- compressor trip behavior
- emergency isolation valves
- H2 detection
- hydrocarbon detection
- fire detection
- nitrogen purge/inerting philosophy
- drainage and bunding
- benzene exposure-control strategy
- safe catalyst loading/unloading
- startup and shutdown sequences
- BPCS control-loop philosophy
- alarm rationalization
- trip/interlock register
- preliminary cause-and-effect matrix
- candidate SIF identification before HAZOP/LOPA
- clear independence between credited protection layers

---

## DWSIM safety-related studies that can be practiced

While DWSIM is not a complete safety-analysis platform, the model can support:

- cooling-failure temperature sensitivity
- hydrogen-feed-loss sensitivity
- recycle-loss sensitivity
- separator-temperature sensitivity
- pressure sensitivity
- utility-loss scenarios
- compressor-outage material balance
- relief-load inputs for later independent calculations

---

## Safety gate for final release

The final repository should not describe the flowsheet as industrially deployable unless the documentation clearly states that detailed safety engineering remains required.

A realistic process simulation is a prerequisite for safety work, not a replacement for it.
