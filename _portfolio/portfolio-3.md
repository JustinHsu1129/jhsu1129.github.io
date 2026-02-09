---
title: "Multicore RISC-V Processor"
excerpt: "Designed a multicore RISC-V processor with big.LITTLE architecture"
collection: portfolio
---

The goal was to develop a scalable RISC-V framework that mimics modern mobile SoC architectures. The system features "Big" cores optimized for raw throughput and "LITTLE" cores tuned for energy efficiency.

1. Heterogeneous Core Design (SystemVerilog)

Each core was custom-architected to meet specific Power, Performance, and Area (PPA) targets:

* The "Big" Core: A deeply pipelined, high-performance RISC-V implementation featuring advanced branch prediction and optimized ALU stages.

* The "LITTLE" Core: A lean, area-efficient design focused on minimizing leakage and switching power, ideal for background tasks.

* Custom Cache Hierarchy: I designed specialized L1 caches for each core type, integrated with a Snooping or Directory-based Coherence Protocol to ensure data consistency across the multi-core cluster.

2. Verification & Analysis

To ensure the architectural integrity of the multi-core framework:

* Logic Verification: Used Cadence Xcelium to run extensive testbenches, verifying instruction set compatibility and cache hit/miss scenarios.

* Performance Metrics: Analyzed pipeline stalls and cache contention to fine-tune the interconnect fabric between the heterogeneous cores.

3. Physical Implementation (VLSI Flow)

Moving from RTL to GDSII, I utilized the OpenLane open-source flow to prep the design for fabrication:

* Caravel SoC Harness: Integrated the multi-core cluster into the Efabless Caravel harness, managing the interface between the project logic and the chip's housekeeping functions.

* Custom Layout Scripting: Authored specialized scripts for floorplanning, power grid synthesis, and clock tree synthesis (CTS) to handle the unique power domains required by a big.LITTLE configuration.

* Sign-off: Performed Design Rule Checking (DRC) and Layout vs. Schematic (LVS) to ensure the physical layout matched the verified SystemVerilog intent.