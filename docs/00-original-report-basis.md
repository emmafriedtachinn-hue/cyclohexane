# Stage 1 — Original Report Basis

## Source

The starting point for this project is the engineering report:

**Production de cyclohexane par hydrogénation du benzène**

The report develops a conceptual industrial unit for producing **500 tonnes/day of cyclohexane** from benzene and hydrogen.

This document records the source design before DWSIM-specific modifications are introduced.

---

## Process selected in the report

The report selects **vapor-phase hydrogenation of benzene** because of its high conversion, high selectivity and established industrial use.

Main reaction:

~~~text
C6H6 + 3 H2 -> C6H12
~~~

Key source conditions:

| Parameter | Report basis |
|---|---:|
| Cyclohexane production target | 500 t/day |
| Reaction phase | Vapor |
| Reaction temperature | ~180–200 °C |
| Reaction pressure | ~23 bar |
| Catalyst | Raney Ni supported on alumina |
| Benzene conversion | >99% |
| Final cyclohexane purity target | 99.9% |

The reaction is strongly exothermic, so the report proposes a **multi-stage reactor arrangement with intermediate cooling**.

---

## Report process sequence

The source design contains the following major operations:

1. Benzene storage and pumping
2. Hydrogen supply
3. Mixing of benzene and hydrogen
4. Feed preheating
5. Multi-stage catalytic hydrogenation
6. Reactor-effluent cooling
7. Gas/liquid separation
8. Partial hydrogen recycle with purge
9. Reheating of the liquid stream
10. Final distillation
11. Cyclohexane and impurity storage

The report identifies methylcyclopentane (MCP) as a principal light impurity in the purification section.

---

## Major equipment identifiers in the report

| Tag | Function |
|---|---|
| TK-100 | Benzene storage |
| P-100 | Benzene feed pump |
| M-100 | Benzene / hydrogen mixer |
| E-100 | Feed preheater |
| R-100 | Reaction section |
| E-200 | Reactor-effluent cooler |
| S-100 | Gas/liquid separator |
| E-300 | Liquid-stream reheater |
| T-100 | Distillation column |
| TK-200 | Cyclohexane storage |
| TK-300 | Impurity storage |

---

## Benzene-feed and exchanger work in the report

The report includes detailed design work for the benzene-feed system, including:

- hydraulic sizing
- pump selection
- pressure losses
- power and efficiency
- cavitation checks
- E-100 heat-exchanger sizing
- distillation-column sizing

The E-100 calculation treats benzene heating/vaporization using a boiling plateau near atmospheric benzene boiling temperature. This later creates a consistency question when the same process is represented at high reactor pressure in DWSIM.

That issue is tracked separately in the assumptions/deviations log.

---

## Reactor-effluent separation in the report

The source report cools the reactor effluent in E-200 to approximately **200 °C** before S-100.

The report argues that because pure cyclohexane has a boiling temperature around 233 °C at ~23 bar, cooling below this temperature favors condensation.

The gas phase from S-100 is primarily hydrogen and volatile impurities. Approximately 50% of the hydrogen-containing gas is described as recycled toward M-100, with the remaining fraction purged to limit inert accumulation.

The liquid phase is sent toward E-300 and T-100 for final purification.

This source reasoning is retained here as the original design basis. DWSIM later showed that the real multicomponent mixture does not necessarily condense at the same condition as pure cyclohexane.

---

## Distillation basis in the report

The report's hand design for the MCP/cyclohexane separation includes approximately:

- minimum theoretical stages: ~39
- reflux design based on a calculated minimum reflux
- ~68 theoretical stages after Gilliland-type estimation
- tray efficiency: ~78%
- ~88 physical stages
- tray spacing: 0.5 m
- active height: ~44 m
- total height estimate: ~50.5 m
- valve trays selected

The report targets **99.9% cyclohexane purity**.

DWSIM shortcut-column results differ substantially in minimum reflux ratio while giving a similar minimum-stage count. This discrepancy is preserved for later analysis rather than being hidden.

---

## Safety coverage in the source report

The report includes sections covering:

- SEVESO classification
- ICPE applicability
- ATEX zoning and explosion prevention
- pressure equipment
- storage of flammable liquids
- hydrogen-specific hazards
- chemical-risk assessment
- functional safety
- fire protection
- benzene hazards
- cyclohexane hazards
- MCP hazards
- installation-wide risk review

The DWSIM project will build on this foundation but will distinguish source-report statements from later process-safety literature and incident analysis.

---

## How this report is used in the DWSIM project

The report is treated as the **starting design**, not as a numerical target that DWSIM must reproduce at all costs.

When a source assumption:

- produces a physically inconsistent phase state,
- requires an unrealistic pressure/temperature path,
- conflicts with equipment behavior,
- is missing data needed for simulation,
- or is contradicted by stronger industrial/literature evidence,

the DWSIM implementation may be modified.

Every such modification must be documented in:

- [Model construction log](03-model-construction-log.md)
- [Assumptions and deviations](04-assumptions-and-deviations.md)
