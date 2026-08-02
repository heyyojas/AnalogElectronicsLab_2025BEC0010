# Experiment 02: CMOS Inverter — Schematic, Layout & Verification

**Name:** Ojas Sharma
**Roll Number:** 2025BEC0010
**Course:** Analog Electronics Lab
**Institution:** IIIT Kottayam

---

## 1. Aim
To design, implement, and verify a CMOS inverter in Cadence Virtuoso — at schematic
level, layout level, and through DRC/LVS/post-layout simulation.

## 2. Design Specifications
| Parameter | Value |
|---|---|
| Technology | GPDK090 |
| PMOS device | gpdk090_pmos1v |
| PMOS width (W) | 240n |
| PMOS length (L) | 100n |
| NMOS device | gpdk090_nmos1v |
| NMOS width (W) | 120n |
| NMOS length (L) | 100n |
| Supply voltage (VDD) | 1.2 V |

## 3. Circuit Description
A CMOS inverter consisting of one PMOS transistor (source at VDD, drain at VOUT)
acting as the pull-up network, and one NMOS transistor (source at GND, drain at VOUT)
acting as the pull-down network. Both gates are tied to the input node Vin, and both
drains are tied together at the output node VOUT.

When Vin is high (1.2V), the NMOS conducts and pulls VOUT low (0V) while the PMOS
is off. When Vin is low (0V), the PMOS conducts and pulls VOUT high (1.2V) while the
NMOS is off — giving the expected inverting behavior.

## 4. Schematic
*[Insert schematic screenshot]*

Testbench: a `vdc` source (V0, 1.2V) supplies VDD, a `vpulse` source (V1) drives Vin
with V1=0, V2=1.2, rise/fall time = 1n, pulse width = 5n, period = 10n, and the
`gnd` symbol from analogLib provides the ground reference.

## 5. Layout
*[Insert layout screenshot]*

Metal1 routing connects VDD, GND, Vin, and VOUT nets to the PMOS/NMOS transistor
terminals, with well/substrate taps at the VDD and GND rails.

## 6. DRC (Design Rule Check)
**Status:** Pending — PVS tool configuration issue in the lab environment (rules
file/runset not resolving). Following up with TA to identify the correct DRC
invocation for this lab setup.

## 7. LVS (Layout vs Schematic)
**Status:** Pending — blocked on the same PVS toolchain issue as DRC above.

## 8. Simulation Procedure
Transient analysis run in ADE L (Spectre simulator), stop time = 30n, with Vin and
VOUT selected as outputs. DC operating point obtained via "Save DC Operating Point"
option under the DC analysis setup, annotated onto the schematic via
Results → Annotate → DC Operating Points.

## 9. Results

### 9.1 Pre-layout Transient Simulation
*[Insert waveform screenshot — Vin vs VOUT]*

VOUT cleanly swings 0V–1.2V, inverse of Vin, with sharp transition edges — confirming
correct inverter switching behavior.

### 9.2 DC Operating Point
*[Insert DC operating point screenshot]*

At Vin = 0V (input low):

| Transistor | Vgs | Vds | Id | gm |
|---|---|---|---|---|
| PMOS (PM0) | -1.2 V | -174.585 µV (~0) | -46.6738 nA | 28.077 nA |
| NMOS (NM0) | 0 V | 1.19983 V | 46.6814 nA | 1.11899 µA |

This confirms correct operation: with Vin low, the PMOS is ON (Vgs = -1.2V) pulling
VOUT to VDD, while the NMOS is OFF (Vgs = 0V), consistent with VOUT settling near
1.2V. The small nA-level currents reflect off-state leakage, as expected.

### 9.3 Post-layout Simulation
**Status:** Pending — requires LVS-clean extracted view (see Section 7).

## 10. Observations
- The inverter's transient response confirms correct logical inversion with clean
  rise/fall transitions.
- DC operating point values match expected MOSFET region-of-operation behavior for
  the given bias condition (Vin = 0V): PMOS in triode/on-state, NMOS cut-off.
- DRC/LVS could not be completed due to a tool configuration issue (missing/
  unresolved rules file) in the lab's PVS setup — this is an environment issue,
  not a design issue, and is being followed up on separately.

## 11. Conclusion
The CMOS inverter was successfully designed and verified at the schematic level —
transient simulation confirms correct inverting behavior (0V–1.2V swing, inverse of
input) and DC operating point analysis confirms both transistors bias correctly for
their expected on/off states. Layout was completed and DRC/LVS/post-layout
verification remain pending due to a tool environment issue.
