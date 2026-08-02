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
| Supply voltage (VDD) | [fill in] |
 
## 3. Circuit Description
A CMOS inverter consisting of one PMOS transistor (source at VDD, drain at VOUT)
acting as the pull-up network, and one NMOS transistor (source at GND, drain at VOUT)
acting as the pull-down network. Both gates are tied to the input node Vin, and both
drains are tied together at the output node VOUT.
 
*[Add 2-3 lines on how the inverter functions — when Vin is high, NMOS conducts and
pulls VOUT low; when Vin is low, PMOS conducts and pulls VOUT high.]*
 
## 4. Schematic
*[Insert schematic screenshot]*
 
Brief note on the schematic setup — instance names, connectivity, any testbench
elements added for simulation (pulse source at Vin, load cap at VOUT, etc.)
 
## 5. Layout
*[Insert layout screenshot]*
 
Brief note on the layout — placement of PMOS/NMOS, well taps, metal routing for
VDD/GND/Vin/VOUT.
 
## 6. DRC (Design Rule Check)
**Status:** [DRC Clean / Errors found — list them]
 
*[Insert DRC report screenshot or summary]*
 
## 7. LVS (Layout vs Schematic)
**Status:** [LVS Clean / Mismatch found — list them]
 
*[Insert LVS report screenshot or summary]*
 
## 8. Simulation Procedure
Describe the testbench used for simulation:
- Input signal type (e.g., pulse/DC sweep) applied at Vin
- Simulation type run (transient / DC)
- Tool used (ADE L / ADE XL / Spectre)
## 9. Results
 
### 9.1 Pre-layout Simulation
*[Insert waveform — Vin vs VOUT]*
 
### 9.2 DC Operating Point
*[Insert DC operating point table/screenshot — Vgs, Vds, Ids for both transistors]*
 
### 9.3 Post-layout Simulation
*[Insert extracted-view waveform — compare against pre-layout]*
 
| Parameter | Pre-layout | Post-layout |
|---|---|---|
| Rise time | | |
| Fall time | | |
| Propagation delay (tpLH) | | |
| Propagation delay (tpHL) | | |
 
## 10. Observations
*[Note any differences between pre-layout and post-layout results — typically
post-layout shows added delay/degraded performance due to parasitic capacitance
from routing.]*
 
## 11. Conclusion
*[Summarize: was the inverter successfully designed and verified? Did it meet
expected switching behavior? Any DRC/LVS issues resolved?]*
