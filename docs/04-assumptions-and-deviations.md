# Assumptions and Deviations Register

This register prevents temporary DWSIM choices from quietly becoming “design facts”.

Status labels:

- **Source** — directly from original report
- **Supported modification** — changed because simulation/engineering evidence indicates the source assumption is inadequate
- **Provisional assumption** — useful for model development but not yet validated
- **Under review** — current implementation may not be suitable for final design
- **Planned** — not yet implemented

---

## Register

| Topic | Original report | Current DWSIM treatment | Status | Reason / next action |
|---|---|---|---|---|
| Production target | 500 t/day | 500 t/day basis | Source | Retain |
| Reaction route | Vapor-phase benzene hydrogenation | Same | Source | Retain unless stronger process-selection work changes it |
| Reactor T | 180–200 °C | Inlet/outlet controlled around this range | Source / working | Validate against selected catalyst/process |
| Reactor P | ~23 bar | ~23 bar | Source / working | Validate against industrial process literature |
| Catalyst | Raney Ni on alumina | Not explicitly modeled as catalyst inventory | Source | Kinetic model still missing |
| Thermodynamics | Not a DWSIM package selection | Peng–Robinson | Provisional assumption | Validate VLE, especially purification section |
| Fresh gas | H2 with inerts | 95% H2 / 4.9% CH4 / 0.1% N2 | Provisional assumption | Replace with documented feed specification |
| E-100 boiling treatment | Atmospheric-style benzene vaporization calculation | Temporary depressurization + heater + recompression tested | Under review | Likely not industrially efficient; redesign required |
| E-100 utility | Dowtherm-type fluid in report | Heater used temporarily | Under review | Replace with defensible exchanger/utility model |
| Reactor type | Multi-stage catalytic fixed-bed concept | 3 Conversion Reactors | Provisional assumption | Upgrade when kinetics/bed data become available |
| Stage conversions | Not equal mathematical split | Equal conversion used to reach overall ~99% | Provisional assumption | Do not interpret as real bed design |
| MCP selectivity | MCP identified but quantified selectivity not fully established | 99% CH / 1% MCP among reacted benzene | Provisional assumption | Literature validation required |
| E-200 outlet | ~200 °C | ~50 °C development case | Supported modification, value provisional | 200 °C remained vapor in PR mixture; optimize actual separator T |
| S-100 phase behavior | Report expects gas/liquid split | Explicit PR flash | Supported modification | Use actual multicomponent equilibrium |
| H2 recycle split | ~50% recycle | 50/50 used initially | Provisional assumption | Determine from inert balance and economics |
| Second flash | Not central in report flowsheet | Added before distillation | Provisional process modification | Helps remove noncondensables; quantify product loss |
| Low-pressure flash loss | Not reported | Cyclohexane loss observed | Open issue | Recover or optimize |
| Column method | Hand design | Shortcut then rigorous DWSIM column | Supported modeling progression | Rigorous convergence pending |
| Column Rmin | ~151.8 in report | ~18.45 in shortcut model | Unresolved discrepancy | Revisit definitions/calculation basis |
| Column Nmin | ~39 | ~39.8 | Agreement | Useful cross-check |
| Column stages | ~68 theoretical / ~88 physical after efficiency | ~78 equilibrium stages from shortcut | Under review | Reconcile stage-count conventions and efficiency |
| Condenser | Conventional source representation | Total initially; partial considered for noncondensables | Under review | Depends on residual H2/CH4/N2 |
| Column solver | N/A | Several DWSIM solvers tested/planned | Numerical choice | Must not change physical model |
| Benzene recycle | Not yet fully implemented in DWSIM | Concept considered | Planned | Close carbon balance only if separation scheme supports it |
| Heat integration | Limited source exchanger work | Not yet optimized | Planned | Add after stable base case |

---

## Rules for future changes

Before changing a major unit operation or specification:

1. Record the current value.
2. State whether it comes from the report, DWSIM, literature, or assumption.
3. Explain the physical problem being solved.
4. Make the modification.
5. Re-run mass/energy balance.
6. Record the result.
7. Decide whether the change is retained, rejected, or left provisional.

This file should be updated whenever the flowsheet architecture changes.
