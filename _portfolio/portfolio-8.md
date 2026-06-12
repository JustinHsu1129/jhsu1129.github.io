---
title: "32-Bit Low-Power Square Root Carry Select Adder"
excerpt: "Designed and simulated a 32-bit square root carry select adder in Cadence Virtuoso and Spectre, optimizing for low-power operation at sub-threshold Vdd."
collection: portfolio
order: 3
---

Designed, simulated, and verified a low-power, high-performance 32-bit Square Root Carry Select Adder using a CMOS mirror adder topology and transmission gate multiplexers in Cadence Virtuoso. The project focused on sub-threshold voltage operation and low-power design verification using Cadence Spectre.

### 1. Adder Architecture & Circuit Design

To balance area, power, and propagation delay, a heterogeneous square root carry select adder structure was implemented:
* **Block Topology:** Arranged in a **2-2-3-4-5-6-10** block structure to match the quadratic delay profile of carry-out propagation.
* **Even & Odd Mirror Cells:** Developed custom mirror adder cells using symmetric layouts to equalize charge times and minimize critical path delay.
* **Transmission Gate Multiplexers:** Designed high-speed transmission gate multiplexers to perform rapid path selection of carry inputs, reducing propagation delay and static power consumption.

### 2. Critical Path & Interconnect Parasitics

* **Worst-Case Delay:** Identified as the propagate state \text{0xFFFFFFFF}, \text{0x00000000}, and C_in = 1, where the carry-out value ripples through all 32 bits of the adder.
* **Parasitic Impact:** The carry-propagate wire spanning across all 32 bit slices introduces significant resistance and capacitance. The design optimized layout geometries to minimize signal degradation, voltage drops, and capacitive coupling between adjacent signals.

### 3. Simulation & Low-Power Metrics (Spectre)

Spectre simulations verified correct operation across a wide voltage range down to the sub-threshold region:
* **Sub-Threshold Operation:** Determined the optimal sub-threshold supply voltage to be **0.32V**.
  - **Critical Path Delay:** 7.43ns
  - **Average Total Power:** 2.902443*10^-6W
  - **Power-Delay Product (PDP):** 29.02fJ
  - **Energy-Delay Product (EDP):** 2.90*10^-22J
* **Leakage Power Analysis:**
  - **Minimum Leakage:** 308.37nW in the A=0, B=0, C_in=0 state, maximizing the stacked transistor effect.
  - **Maximum Leakage:** 806.45nW in the A=0xFFFFFFFF, B=0, C_in=1 state, where only a single NMOS device remains off at the bottom of the stack.
* **Minimum Energy Point (MEP):** Found the most energy-efficient operating point to be 7.87fJ per operation at 0.6V (operating at 1.47GHz).
* **Frequency vs. Voltage Sweep:**
  - **1.0V:** F_max = 3088.33MHz, Delay = 0.3238ns, Energy 16.09fJ
  - **0.6V (MEP):** F_max = 1467.35MHz, Delay = 0.6815ns, Energy = 7.87fJ
  - **0.3V:** F_max = 101.61MHz, Delay = 9.842ns, Energy = 24.63fJ
  - **0.2V:** F_max = 14.59MHz, Delay = 68.54ns, Energy = 48.51fJ
  - **0.1V:** Fails (below Vmin)

[Report](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20216%20Design%20Project%202.pdf)
