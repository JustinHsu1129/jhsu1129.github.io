---
title: "32-Bit MIPS CPU Design"
excerpt: "Designed a pipelined 32-bit MIPS CPU in Verilog, analyzed memory subsystem hierarchies in gem5, and executed the OpenLane2 VLSI flow with low-power optimizations."
collection: portfolio
order: 7
---

Designed, simulated, and physically implemented a pipelined 32-bit RISC processor. The project included custom Verilog RTL development, architectural memory modeling using gem5, and physical VLSI synthesis using OpenLane2 featuring advanced low-power optimization techniques.

### 1. Processor Microarchitecture & RTL Design

Designed a 32-bit MIPS32 compliant processor core in Verilog:
* **Pipelined Execution:** Implemented a standard **5-stage pipeline** (Fetch, Decode, Execute, Memory, Writeback).
* **Hazard Resolution:** Developed control units to handle data and structural hazards:
  - **Forwarding Paths:** Integrated EX-to-EX and MEM-to-EX bypass channels to eliminate stalls on register dependencies.
  - **Stall & Flush Logic:** Built a hazard detection unit to manage pipeline stalls during load-use hazards and branch flush cycles.

### 2. Cache Hierarchy Simulation (gem5)

Used **gem5** to model the processor's memory subsystem:
* **Configuration:** Simulated L1 Instruction and Data caches (2-way set-associative, 64-byte lines) and a unified L2 cache (8-way set-associative).
* **Performance Profiling:** Analyzed the execution of benchmark programs to study the impact of cache line size and associativity on instruction-per-cycle (IPC) and memory bottlenecks.

### 3. VLSI Implementation & Low-Power Optimization (OpenLane2)

Carried the verified RTL through a physical design flow in OpenLane2:
* **Low-Power Topologies:**
  - **Clock Gating:** Integrated integrated clock-gating cells (ICGs) to disable clock trees on inactive registers.
  - **Multi-Threshold CMOS (MTCMOS):** Partitioned the layout into distinct power domains, utilizing high-threshold leakage-control cells for non-critical paths.
  - **Transistor Stacking:** Selected low-leakage stacked-transistor standard cells to suppress sub-threshold leakage power.
* **Verification Sign-Off:** Synthesized, placed, and routed the design to timing closure, passing physical validation sign-off (DRC and LVS checks).

![Layout](https://justinhsu1129.github.io/jhsu1129.github.io/images/Pasted%20image%2020250915004236.png)

![Routing Congestion](https://justinhsu1129.github.io/jhsu1129.github.io/images/Pasted%20image%2020250915004236.png)