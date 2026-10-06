# Stage 3 — Current Process Design Basis

> **Status:** Working basis. Values marked as provisional must be validated before final release.

---

## Production target

Nominal cyclohexane production target:

**500 t/day**

Target product purity from the source report:

**99.9% cyclohexane**

---

## Components currently included in DWSIM

| Component | Role |
|---|---|
| Hydrogen | Reactant / recycle gas |
| Benzene | Main reactant |
| Cyclohexane | Main product |
| Methane | Fresh-gas inert / recycle-loop inert |
| Nitrogen | Fresh-gas inert / recycle-loop inert |
| Methylcyclopentane | Light hydrocarbon impurity / side product |

---

## Thermodynamic model

Current base-case property package:

**Peng–Robinson**

Reason for current use:

- hydrocarbon-rich system
- hydrogen-containing high-pressure section
- convenient consistency across compressors, flashes, reactors and separation units

The final model should still test whether PR adequately represents the close-boiling benzene/cyclohexane/MCP purification section.

---

## Main chemistry

Primary reaction:

~~~text
Benzene + 3 Hydrogen -> Cyclohexane
~~~

Source report basis:

- vapor-phase reaction
- Raney Ni supported on alumina
- ~180–200 °C
- ~23 bar
- conversion >99%
- strongly exothermic

The current DWSIM reaction model is a **conversion-based surrogate**, not a validated kinetic model.

---

## Current feed basis used during development

### Benzene

Development basis:

- approximately 250 kmol/h
- pure benzene in the initial model

This flow is close to the stoichiometric scale required for ~500 t/day cyclohexane, subject to conversion/selectivity/recycle losses.

### Fresh hydrogen-rich gas

Current trial composition:

| Species | Mole fraction |
|---|---:|
| H2 | 0.950 |
| CH4 | 0.049 |
| N2 | 0.001 |

A representative development flow used in the current model is approximately 904 kmol/h total fresh gas.

This specification is provisional and should ultimately be linked to a documented industrial hydrogen-feed basis rather than retained only because it was used in the original calculations.

---

## Upstream pressure basis

Current reaction-section target pressure:

**~23 bar**

The benzene feed is pumped; the hydrogen-rich gas is compressed.

Compression produces a significant gas-temperature rise, so an aftercooler is included before mixing/conditioning where required.

---

## Reactor representation

Current DWSIM implementation:

- multiple Conversion Reactors in series
- temperature controlled between reaction stages
- total benzene conversion targeted near 99%

For three equal-conversion stages, a stage conversion near 78.46% produces approximately 99% overall conversion:

~~~text
Xoverall = 1 - (1 - Xstage)^3
~~~

This is a mathematical distribution of conversion, **not evidence that a real three-bed reactor would naturally divide conversion equally**.

---

## Side-product treatment

MCP has been introduced as a side product.

Current provisional assumption:

- 99% of reacted benzene -> cyclohexane
- 1% of reacted benzene -> MCP

This assumption is explicitly temporary until selectivity data are found for the chosen catalyst and operating window.

---

## Reactor-effluent cooling and separation

The source report specifies cooling to ~200 °C before S-100.

DWSIM/PR showed that the actual H2-rich multicomponent stream remained vapor at roughly 200 °C and 23 bar.

Current working model therefore cools much further, with **~50 °C** used as a development case to obtain a meaningful gas/liquid split.

This is a justified modeling correction to the source phase-equilibrium assumption, but **50 °C is not yet the final optimized separator temperature**.

---

## High-pressure separator

Current intended function:

### Vapor
Primarily:

- H2
- CH4
- N2

with some hydrocarbon carryover depending on operating condition.

### Liquid
Primarily:

- cyclohexane
- MCP
- residual benzene

The vapor is intended to feed a purge/recycle system.

---

## Gas recycle and purge

Source report basis:

- partial H2-rich gas recycle
- purge to prevent inert accumulation
- approximately 50% recycle described in the report

Current project position:

The 50/50 split is treated as an **initial condition**, not automatically the final optimum.

The final purge fraction must satisfy:

- stable inert inventory
- adequate reactor hydrogen partial pressure
- acceptable compression duty
- acceptable hydrocarbon losses
- stable recycle convergence

---

## Downstream light-gas removal

A second low-pressure flash has been added in the current DWSIM development model to reduce dissolved H2/CH4/N2 before distillation.

The second flash is followed by the current feed heater HT-3. The integrated model currently sends **stream 33** to the distillation section at approximately:

- 249.032 kmol/h
- 20,896.9 kg/h
- 70 °C
- 1.2 bar
- vapor fraction ~0.00386
- cyclohexane ~0.97750 mole fraction
- benzene ~0.00996
- MCP ~0.00985
- CH4 ~0.00244
- H2 ~0.000245
- N2 trace

The second flash also causes measurable cyclohexane loss in its vapor stream. That loss must be quantified and minimized or recovered in the final design.

---

## Distillation basis

Shortcut-column development currently uses:

- Light key: MCP
- Heavy key: cyclohexane

Earlier shortcut work produced approximately Nmin ~39.8 and Rmin ~18.45. Those values are retained as historical development results, but the actual integrated feed condition has since been rebuilt in a standalone column case.

For diagnostic purposes, residual H2/CH4/N2 were removed from stream 33 and the actual hydrocarbon flow was retained, giving a standalone feed near **248.36 kmol/h** containing benzene, cyclohexane and MCP.

The latest Shortcut Column diagnostic produced:

| Quantity | Latest diagnostic result |
|---|---:|
| Minimum stages | ~48.07 |
| Minimum reflux ratio | ~70.85 |
| Trial design reflux ratio | ~85 |
| Estimated actual equilibrium stages | ~93.42 |
| Optimum feed stage | ~15.81 |
| Condenser duty | ~446 kW |
| Reboiler duty | ~1.655 MW |

These results are **not yet accepted as design data** because the Shortcut Column is still returning unphysical negative condenser/reboiler temperatures. The current priority is to diagnose the temperature/product-flash behavior before using these values to initialize the rigorous column.

---

## Current distillation-model issues

### Shortcut-column temperature anomaly

The latest hydrocarbon-only Shortcut Column case gives plausible-looking stage/reflux magnitudes but unphysical negative condenser and reboiler temperatures at approximately atmospheric pressure.

The current diagnostic plan is to:

- inspect shortcut distillate and bottoms compositions
- reproduce each product composition in independent material streams
- perform bubble/dew-point checks with Peng–Robinson
- determine whether the anomaly originates in the shortcut calculation, product specification or thermodynamic setup

No shortcut result will be accepted solely because the calculation converges.

### Earlier rigorous-column issue

A native DWSIM rigorous column has produced a Peng–Robinson error of the form:

~~~text
PR EOS: Unable to calculate compressibility factor at given conditions
~~~

The error occurred during rigorous-column solution using a bubble-point method.

Current troubleshooting directions include:

- alternative column solver (Naphtali–Sandholm)
- modified Wang–Henke
- partial condenser if residual noncondensables remain
- improved feed conditioning
- simpler pressure profile
- more conservative initialization
- reviewing whether the light gases should be removed more completely before T-100

No final rigorous-column configuration has yet been accepted.

---

## Design-basis status

The following are currently considered reasonably well established:

- overall chemistry
- target capacity
- high-pressure catalytic hydrogenation concept
- need for strong heat removal
- need for H2-rich recycle/purge
- need for purification

The following remain provisional:

- exact fresh-gas composition
- catalyst kinetic representation
- MCP selectivity
- reactor-stage count
- separator temperature
- purge fraction
- second-flash operating point
- final distillation configuration
- final pressure profile
- heat-integration scheme
- control philosophy and instrument set points
- alarm/interlock and SIS architecture
