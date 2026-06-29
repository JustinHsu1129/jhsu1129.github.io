---
title: "Heterogeneous Multicore RISC-V Processor"
excerpt: "Designed a heterogeneous multicore RISC-V processor in SystemVerilog, optimizing physical design using Synopsys Design Compiler and Cadence Innovus to achieve 400 MHz."
collection: portfolio
order: 5
---

Designed and verified a heterogeneous multi-core processor framework modeling modern mobile SoC architectures. The system features a "Big" core optimized for high-performance execution and a "LITTLE" core optimized for energy-efficient background operations, integrated with a cohesive cache coherence protocol and peripheral interconnects.

### 1. Heterogeneous Core Architectures (SystemVerilog)

Designed two distinct processor architectures complying with the RISC-V ISA specifications:
* **The "Big" Core (RV64GC compliant):** A deeply pipelined, in-order execution engine featuring dynamic branch prediction (using a **Gshare predictor** coupled with a Branch Target Buffer) and optimized multi-cycle ALU stages to maximize instruction throughput under strict thermal design power constraints.
* **The "LITTLE" Core (RV32IM compliant):** A lean, area-efficient 3-stage execution pipeline designed to minimize leakage and switching power, serving as an energy-efficient controller for background operations.
* **Coherent Cache Hierarchy:** Developed private, set-associative write-back L1 caches for each core. Coherency across the heterogeneous cores is maintained via a custom-designed **MESI (Snooping) Coherence Protocol** managing data transactions over a shared crossbar bus.

### 2. Logic Verification & Protocol Compliance (Cadence Xcelium)

* **Verification Suite:** Authored self-checking, constrained-random testbenches in **Cadence Xcelium** to rigorously stress the hardware-enforced cache coherence protocol and ensure flawless multi-core synchronization.
* **Coherence Testing:** Simulated cache hit/miss scenarios, memory eviction loops, and write-back hazards to verify the logical consistency of the MESI coherence protocol.
* **Instruction Verification:** Executed a comprehensive verification suite in Cadence Xcelium to ensure full compatibility with RISC-V instruction definitions.

### 3. VLSI Physical Design & Optimization (Design Compiler & Innovus)

Completed physical implementation steps and PPA optimizations using industry-standard EDA tools:
* **Synthesis & Optimization:** Synthesized the design using **Synopsys Design Compiler**, optimizing pipeline register placement to resolve timing bottlenecks.
* **Physical Layout & P&R:** Leveraged **Cadence Innovus** to perform floorplanning, Clock Tree Synthesis (CTS), routing, and multi-voltage domain planning under strict power constraints.
* **PPA Metrics:** Achieved a peak operational frequency of **400 MHz** and a **30% increase in energy efficiency** through clock tree optimization, multi-voltage floorplanning, and routing congestion management.