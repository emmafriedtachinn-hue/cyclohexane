# Stage 10 — Engineering Evaluation

> **Status:** Planned framework.

The final project should evaluate whether the completed DWSIM model is technically credible, not simply whether the solver reports “converged”.

---

## Final checks

### Material balance

Verify:

- benzene in
- hydrogen in
- cyclohexane out
- MCP/by-products
- purge losses
- vent/flash losses
- recycle consistency

Overall mass imbalance should be quantified.

### Reaction performance

Report:

- overall benzene conversion
- cyclohexane selectivity
- cyclohexane yield
- hydrogen consumption
- reaction heat release
- temperature profile / stage temperatures

### Energy balance

Quantify:

- compressor duties
- pump duty
- preheating duty
- reactor heat-removal duty
- E-200 duty
- column condenser duty
- column reboiler duty
- potential recoverable process heat

### Separation performance

Report:

- H2 recovery
- purge composition
- hydrocarbon loss to purge
- second-flash loss
- cyclohexane purity
- cyclohexane recovery
- benzene in final product
- MCP in final product

### Equipment realism

For each major item, compare DWSIM operation against realistic equipment constraints:

- pump head and NPSH
- compressor temperature and pressure ratio
- exchanger temperature approach
- flash residence/phase separation assumptions
- reactor pressure drop
- column hydraulics
- condenser feasibility
- reboiler temperature

---

## Literature / industrial benchmark

The final project should compare its architecture and performance with publicly documented cyclohexane-production examples and process descriptions.

Real-world reference set retained for later study:

- Chevron Phillips Chemical — Port Arthur, Texas
- Saudi Chevron Phillips — Al Jubail, Saudi Arabia
- Phillips 66 / CPChem — Sweeny, Texas
- ExxonMobil — Rotterdam Aromatics Plant
- historical Exxon Baytown / UOP benzene-hydrogenation reference
- Fives ProSim cyclohexane process example

Not all of these facilities necessarily use the exact same catalyst, reactor arrangement or operating conditions. They are benchmarks for industrial context, not proof that the DWSIM flowsheet is identical.

---

## Final maturity statement

The final report should explicitly separate:

### Demonstrated by the model
Material/energy behavior and steady-state process performance represented in DWSIM.

### Supported by literature
Industrial-practice assumptions that are externally documented.

### Assumed
Parameters not yet validated.

### Outside current scope
Detailed design tasks still required before implementation.

This prevents the repository from overstating the maturity of the design.
