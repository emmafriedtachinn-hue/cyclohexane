# Stages 4–8 — DWSIM Model Construction Log

This file records the model **chronologically**. It is intended to preserve failed approaches and engineering corrections, not only successful settings.

---

## 1. Component and property-package setup

Components added:

- H2
- benzene
- cyclohexane
- methane
- nitrogen
- methylcyclopentane

Base property package:

- Peng–Robinson

The aim was to keep one consistent EOS through the high-pressure reaction, flash separation and recycle sections.

---

## 2. Fresh-feed definition

### Benzene stream

A benzene basis near **250 kmol/h** was used during development.

### Hydrogen-rich fresh gas

A trial fresh-gas composition of:

- 95 mol% H2
- 4.9 mol% CH4
- 0.1 mol% N2

was introduced.

This allowed recycle-loop inert accumulation to be represented rather than modeling an unrealistically pure hydrogen feed.

---

## 3. Feed compression and conditioning

The benzene stream is pumped to reaction-section pressure.

The fresh gas is compressed to approximately reaction pressure.

### Observation

Gas compression caused a substantial discharge-temperature rise.

### DWSIM action

An aftercooler was introduced before the gas entered the mixing/reaction-conditioning section.

### Lesson

Pressure specification alone is not sufficient: compressor temperature rise affects downstream mixing and reaction inlet conditions.

---

## 4. E-100 feed-preheating study

The original report contains a detailed exchanger calculation that treats benzene vaporization with a plateau near its atmospheric boiling point.

### Initial DWSIM difficulty

At high process pressure, the source temperature path cannot simply be reproduced as an atmospheric boiling process.

### Temporary modeling approach

A pressure reduction toward atmospheric pressure was tested before E-100, followed by heating to about 150 °C and later recompression.

A Heater was used in place of a detailed heat exchanger when the report's stated heat-transfer fluid could not be represented directly with the available DWSIM component set.

### Status

**Under review.**

The sequence:

~~~text
high pressure -> throttling -> low-pressure vaporization -> recompression
~~~

may reproduce the report's thermal calculation but is energetically unattractive as an industrial design.

It must not be retained in the final flowsheet unless justified by a real process configuration.

---

## 5. Reactor-model selection

The source report specifies a catalytic fixed-bed/multi-stage concept but does not provide a complete rate law with all kinetic parameters needed for a rigorous reactor model.

### DWSIM decision

Use **Conversion Reactor** blocks as an initial surrogate.

This allows:

- stoichiometry to be checked
- overall conversion to be matched
- heat release to be quantified
- staged heat-removal requirements to be explored

It does **not** predict:

- catalyst mass
- residence time
- axial temperature profile
- pressure drop
- deactivation
- hot-spot location

---

## 6. Adiabatic reactor experiments

A single reactor at near-total benzene conversion was tested adiabatically.

### Result

The calculated temperature rose to an extremely high value (roughly of order 900 °C in the trial model).

### Interpretation

This was a useful physical warning, not merely a convergence problem.

Benzene hydrogenation is strongly exothermic; very high conversion cannot be treated as one uncontrolled adiabatic step.

Additional tests with much lower single-stage conversion showed correspondingly smaller but still important temperature rises.

---

## 7. Staged conversion-reactor arrangement

The model was changed to multiple successive conversion reactors with temperature control/heat removal between stages.

A three-stage equal-conversion mathematical split was explored.

To obtain approximately 99% overall conversion:

~~~text
Xstage = 1 - (1 - Xoverall)^(1/3)
~~~

For Xoverall = 0.99:

~~~text
Xstage ≈ 0.7846
~~~

This does not prove that three equal industrial catalyst beds are optimal. It is a simulation scaffold for the staged process concept.

---

## 8. MCP side-product model

MCP was introduced to make the purification section more representative.

A provisional product split of approximately:

- 99% cyclohexane
- 1% MCP

among reacted benzene was implemented using separate conversion reactions.

### Important distinction

**99% benzene conversion is not the same as 99% cyclohexane selectivity.**

Conversion and selectivity are tracked separately.

### Status

The 99/1 selectivity value is still an assumption and requires literature validation.

---

## 9. Reactor outlet and E-200

The source report expects the reactor effluent to be cooled to ~200 °C at ~23 bar before gas/liquid separation.

### DWSIM observation

At approximately those conditions, the PR model predicted the reactor effluent remained essentially **all vapor**.

The source report's reasoning used the boiling point of pure cyclohexane, but the actual stream contains a large amount of H2 and other light gases. The relevant hydrocarbon partial pressures are therefore much lower than the total pressure.

### Modification

E-200 was allowed to cool the stream much further.

A trial outlet near **50 °C** produced the required two-phase split.

### Status

The need for deeper cooling is supported by the simulated phase behavior.

The final temperature is still to be optimized.

---

## 10. S-100 high-pressure separator

At the cooler condition:

- H2/CH4/N2 preferentially enter the vapor phase
- cyclohexane/MCP/benzene preferentially enter the liquid phase

The gas outlet is intended for a purge/recycle split.

The liquid outlet proceeds toward final light-gas removal and purification.

---

## 11. Gas recycle / purge

The source report describes roughly 50% recycle and 50% purge.

This was retained only as an initial simulation basis.

### Final design requirement

The purge fraction must eventually be determined from recycle-loop material balances and inert accumulation, not simply copied from the report.

A DWSIM **Recycle** operation is planned for the fully closed loop.

---

## 12. Low-pressure flash before distillation

A second flash was added after pressure reduction to remove remaining dissolved H2, CH4 and N2 before the distillation column.

The second-flash liquid proceeds through HT-3 before the column. The resulting integrated column-feed stream 33 was observed at approximately:

- total flow: 249.032 kmol/h
- mass flow: 20,896.9 kg/h
- temperature: 70 °C
- pressure: 1.2 bar
- vapor fraction: ~0.00386
- cyclohexane: ~0.9775 mole fraction
- benzene: ~0.0100
- MCP: ~0.00985
- CH4: ~0.00244
- H2: ~0.000245
- N2: trace

### Loss identified

The low-pressure flash vapor contained some cyclohexane.

A development result suggested roughly **2 t/day cyclohexane loss**, around 0.4% of the nominal product scale.

This must be optimized or recovered later.

---

## 13. Shortcut distillation

A Shortcut Column was used before attempting a rigorous column.

Keys:

- Light key = MCP
- Heavy key = cyclohexane

Representative results:

- Rmin ≈ 18.4545
- Nmin ≈ 39.7775
- at R = 22.2:
  - estimated stages ≈ 77.9
  - optimum feed stage ≈ 14.6
  - estimated height ≈ 40 m using the shortcut model
  - condenser duty ≈ 182 kW
  - reboiler duty ≈ 872 kW

### Comparison with source report

The minimum-stage count in this early case was broadly similar to the source hand calculation.

The minimum reflux ratio was **much lower** than the source report's value.

This discrepancy remains part of the development history and is unresolved.

### Latest standalone rebuild

The distillation section was later isolated into a standalone DWSIM case using the actual integrated process output as the basis.

To diagnose whether the residual permanent gases were distorting the Shortcut Column, a hydrocarbon-only diagnostic feed was constructed by removing H2/CH4/N2 while retaining the actual hydrocarbon flow from stream 33.

Approximate diagnostic feed:

- total hydrocarbon flow: ~248.36 kmol/h
- benzene: ~0.00998 mole fraction after renormalization
- cyclohexane: ~0.98014
- MCP: ~0.00987

With:

- LK = MCP
- HK = cyclohexane
- LK in bottoms = 0.001
- HK in distillate = 0.001
- total condenser
- pressure near 1.01325 bar

the Shortcut Column calculated approximately:

- Rmin = 70.846
- Nmin = 48.070
- at R ~85:
  - actual equilibrium stages = 93.418
  - optimum feed stage = 15.807
  - condenser duty = 446.0 kW
  - reboiler duty = 1655.2 kW

### New issue identified

Despite removal of the permanent gases, the Shortcut Column still returned **negative condenser and reboiler temperatures**.

These temperatures are not physically credible for the benzene/cyclohexane/MCP system near atmospheric pressure.

The current diagnostic is therefore:

1. inspect predicted distillate and bottoms compositions
2. reproduce those compositions in independent material streams
3. perform independent phase-equilibrium temperature checks
4. isolate whether the problem lies in the shortcut product calculation, thermodynamic setup or specification choice

The latest shortcut numbers are therefore **diagnostic results, not accepted design data**.

---

## 14. ChemSep attempt

A CAPE-OPEN ChemSep column was tested with approximately:

- 78 stages
- feed stage ~15
- initial reflux around 22.2

Convergence was difficult.

Because the purpose of the project is also to practice native DWSIM, the project returned to the DWSIM Distillation Column for continued work.

---

## 15. Native DWSIM rigorous column

An initial native-column configuration used approximately:

- 78 stages
- feed stage ~15
- atmospheric pressure basis
- reflux ratio ~22.2
- bottoms flow initialized from shortcut results

### Error encountered

DWSIM raised:

~~~text
PR EOS: Unable to calculate compressibility factor at given conditions
~~~

The stack trace showed the failure occurring during rigorous-column calculations using a bubble-point/Wang–Henke-type solution sequence.

### Current troubleshooting

Available DWSIM solvers identified:

- Wang–Henke (Bubble Point)
- Naphtali–Sandholm (Simultaneous Correction)
- Modified Wang–Henke (Bubble Point)

The next serious tests should focus on:

1. Naphtali–Sandholm
2. modified Wang–Henke
3. improved initialization
4. partial condenser if residual noncondensables remain
5. more complete removal of H2/CH4/N2 before the column
6. realistic feed preheating
7. simplified initial pressure profile
8. reduced stage count for first convergence, followed by gradual increase

---

## 16. Current model-development point

The project has reached the transition from:

**open-loop process construction**

to:

**rigorous purification + recycle closure + validation**

No final flowsheet should be published yet.

The next accepted model version should converge the rigorous separation without introducing a physically unjustified numerical workaround.

---

## 17. Process instrumentation and safeguard planning

A dedicated Stage 9 workstream has been added for preliminary process instrumentation, control philosophy and safety safeguards.

Planned outputs include:

- instrument index
- P&ID-style instrumentation markup
- control-loop narrative
- alarm/interlock register
- preliminary cause-and-effect matrix
- candidate SIF identification
- separation of BPCS, SIS, relief protection and fire/gas detection

This work will be developed around a stable process model and linked to abnormal-scenario studies. Final trip set points and SIL claims are outside the current model until supported by HAZOP/LOPA, equipment limits and dynamic/safety studies.
