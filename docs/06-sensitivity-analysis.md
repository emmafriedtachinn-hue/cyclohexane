# Stage 9 — Sensitivity Analysis Plan

> **Status:** Planned. Populate with results only after a stable base case is converged.

The purpose of sensitivity analysis is to distinguish robust process behavior from a flowsheet that only works at one arbitrary set of specifications.

---

## Priority studies

### Reactor section

Variables to test:

- reactor inlet temperature
- reactor pressure
- hydrogen/benzene ratio
- per-stage conversion assumption
- overall conversion
- product selectivity
- interstage outlet-temperature target

Responses:

- peak temperature
- heat duty
- unreacted benzene
- H2 consumption
- product flow
- downstream vapor fraction

### E-200 / S-100

Variables:

- cooler outlet temperature
- separator pressure

Responses:

- hydrogen recovery to vapor
- cyclohexane loss to vapor
- benzene distribution
- MCP distribution
- cooling duty

Goal: find an operating window that produces an effective gas/liquid split without unnecessary refrigeration or hydrocarbon loss.

### Purge / recycle

Variables:

- purge fraction
- recycle fraction
- compressor discharge pressure
- fresh-H2 makeup

Responses:

- CH4 accumulation
- N2 accumulation
- reactor H2 mole fraction
- recycle flow
- compressor duty
- hydrocarbon purge loss

### Low-pressure flash

Variables:

- pressure
- temperature

Responses:

- residual noncondensables in liquid
- cyclohexane loss
- benzene/MCP loss
- distillation-feed quality

### Distillation

Variables:

- reflux ratio
- stage count
- feed stage
- column pressure
- feed temperature

Responses:

- cyclohexane purity
- cyclohexane recovery
- condenser duty
- reboiler duty
- column convergence
- top/bottom temperatures

---

## Validation approach

Every sensitivity should include:

1. base-case value
2. tested range
3. physical reason for the range
4. output metric
5. convergence status
6. interpretation
7. final design consequence

Plots should be stored under the figures directory and linked from this document.

---

## Do not optimize before convergence

~~~text
Stable base case
    ↓
Mass/energy validation
    ↓
Sensitivity analysis
    ↓
Engineering constraints
    ↓
Optimization
~~~

A numerically unstable flowsheet should not be optimized.
