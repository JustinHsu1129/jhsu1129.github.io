---
title: "Systolic Matrix Multiplier Design"
excerpt: "Designed an 8x8 systolic matrix multiplier in Verilog, exploring structural vs. behavioral RTL optimization, and completed the OpenLane2 VLSI flow."
collection: portfolio
order: 6
---

Designed and implemented an 8x8 Systolic Matrix Multiplier to accelerate matrix computations. The project explored structural and behavioral RTL implementations in Verilog, simulated and verified logic using Verilator and Cadence Xcelium, and executed a physical RTL-to-GDSII VLSI design flow using OpenLane2.

### 1. Architectural Architecture & Design Trade-offs

The multiplier features a 2D grid of processing elements (PEs) optimized for parallel data flow:
* **Array Design:** Configured as a **2D systolic array** running a **weight-stationary dataflow pattern**. This pattern keeps weights locked in local PE registers, minimizing interconnect switching activity and external memory bandwidth during vector multiplications.
* **Structural Implementation:** Custom-coded each PE to maximize pipeline throughput:
  - **Multiplier Unit:** Implemented **Radix-4 Booth encoding** combined with a **Wallace Tree reduction network** to compile partial products with minimal delay.
  - **Accumulator Unit:** Utilized a high-speed **Carry Lookahead Adder (CLA)** to finalize carry propagation.
* **Behavioral Implementation:** Designed a second version of the array using behavioral RTL. This allowed the logic synthesizer to map arithmetic operators freely, resulting in a more area-efficient layout compared to the highly optimized structural design.

### 2. VLSI Physical Design (OpenLane2)

Executed a complete RTL-to-GDSII flow in OpenLane2 for both implementations:
* **Floorplanning:** Defined core utilization, pad placement, and Power Distribution Network (PDN) rings to ensure minimal IR drop across the array grid.
* **Clock Tree Synthesis (CTS):** Configured CTS parameters to control clock skew across all 64 PEs, maintaining synchronous timing alignments.
* **Routing & DRC/LVS:** Synthesized and routed the designs, resolving routing congestion issues and achieving physical verification sign-off (passing DRC and LVS checks).
* **PE Hardening:** Designed custom scripts to harden individual processing elements as standard macro blocks, laying the foundation for a fully custom hierarchical layout.

![Layout](https://justinhsu1129.github.io/jhsu1129.github.io/images/Layout.png)

![Routing Congestion](https://justinhsu1129.github.io/jhsu1129.github.io/images/Routing%20congestion.png)