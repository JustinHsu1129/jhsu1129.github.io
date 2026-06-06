---
title: "FPGA Configurable Logic Block (CLB) Verification Tool"
excerpt: "Developed a Python-based ATPG framework utilizing the PODEM algorithm for fault simulation and test vector generation in FPGA Configurable Logic Blocks."
collection: portfolio
order: 11
---

Developed an Automated Test Pattern Generation (ATPG) and fault simulation tool written in Python, specifically designed for testing FPGA Configurable Logic Block (CLB) architectures. By implementing the PODEM (Path-Oriented Decision Making) algorithm, the framework computes optimized test vectors to detect manufacturing defects in programmable logic elements.

### 1. CLB Component Netlist Modeling

To support accurate fault simulation, the tool models the standard primitives of an FPGA Basic Logic Element (BLE) structurally in Python:
* **Look-Up Tables (LUTs):** Modeled as programmable truth-table arrays. The tool simulates faults on both input address lines and internal configuration SRAM bitmasks using Boolean difference logic.
* **Multiplexers (MUXs):** Modeled with select-path evaluation logic to verify select-line transparency and interconnect routing integrity.
* **Flip-Flops (FFs):** Modeled as sequential state elements with clocking behaviors, enabling sequential fault propagation analysis.

### 2. 5-Valued Logic & PODEM ATPG Heuristics

Implemented the PODEM algorithm to overcome structural reconvergent fan-out issues common in FPGA routing architectures:
* **Logic System:** Utilized a **5-valued logic system** ($0, 1, X, D, \bar{D}$) to represent fault excitation and fault propagation states.
* **Backtracing:** Implemented recursive backtracing from the fault site to primary inputs, utilizing cost-based heuristics to determine optimal input assignments.
* **D-Drive Propagation:** Excites the targeted fault (e.g. Stuck-At-0) and propagates the resulting $D$ or $\bar{D}$ state through the BLE's internal LUTs and multiplexers until it reaches an observable primary output.

### 3. Fault Simulation & Collapsing

* **Fault Collapsing:** Built a pre-processing module to group equivalent and dominant faults, reducing the target fault list size and accelerating ATPG execution.
* **Coverage Analysis:** The framework runs the generated test vectors through an integrated fault simulator to measure overall fault coverage. It outputs detailed reports of coverage percentages and identifies logically redundant, undetectable faults in the CLB layout.

[Presentation](https://justinhsu1129.github.io/jhsu1129.github.io/files/Creating%20a%20tool%20for%20FPGA%20Design%20Verification-1.pdf)

[Report](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20283%20Report-2.pdf)