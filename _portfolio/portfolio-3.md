---
title: "Heterogeneous Multicore RISC-V Processor"
excerpt: "Designed a multicore RISC-V processor with a big.LITTLE heterogeneous architecture and cache coherence."
collection: portfolio
order: 5
---

Designed and verified a heterogeneous multi-core processor framework modeling modern mobile SoC architectures. The system features a "Big" core optimized for high-performance execution and a "LITTLE" core optimized for energy-efficient background operations, integrated with a cohesive cache coherence protocol and peripheral interconnects.

### 1. Heterogeneous Core Architectures (SystemVerilog)

Designed two distinct processor architectures complying with the RISC-V ISA specifications:
* **The "Big" Core (RV64GC compliant):** A deeply pipelined, in-order execution engine featuring dynamic branch prediction (using a **Gshare predictor** coupled with a Branch Target Buffer) and optimized multi-cycle ALU stages to maximize raw instruction throughput.
* **The "LITTLE" Core (RV32IM compliant):** A lean, area-efficient 3-stage execution pipeline designed to minimize leakage and switching power, serving as an energy-efficient controller for background operations.
* **Coherent Cache Hierarchy:** Developed private, set-associative write-back L1 caches for each core. Coherency across the heterogeneous cores is maintained via a custom-designed **MESI (Snooping) Coherence Protocol** managing data transactions over a shared crossbar bus.

### 2. Logic Verification (Cadence Xcelium)

* **Instruction Verification:** Executed a comprehensive verification suite in Cadence Xcelium to ensure full compatibility with RISC-V instruction definitions.
* **Coherence Testing:** Simulated cache hit/miss scenarios, memory eviction loops, and write-back hazards to verify the logical consistency of the MESI coherence protocol.
* **Bottleneck Analysis:** Monitored pipeline stall rates and cache collision frequency to optimize structural interfaces within the multi-core fabric.

### 3. VLSI Physical Implementation (OpenLane)

Completed physical implementation steps to prepare the multi-core SoC for fabrication:
* **Caravel SoC Harness:** Integrated the multi-core cluster into the **Efabless Caravel harness**, mapping control registers and internal buses to the Caravel system via a Wishbone interconnect.
* **Custom Floorplanning & Power Routing:** Authored specialized scripts to manage cell placement and power distribution networks, establishing distinct voltage and power domains for active power management.
* **Sign-off Validation:** Verified physical layout integrity by passing standard **Design Rule Checking (DRC)** and **Layout vs. Schematic (LVS)** comparison sign-offs.