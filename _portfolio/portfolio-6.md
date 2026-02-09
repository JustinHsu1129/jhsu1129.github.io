---
title: "32 Bit MIPS CPU"
excerpt: "Designed a 32 bit MIPS CPU in Verilog and carried through physical design flow with OpenLane<br/><img src='https://justinhsu1129.github.io/jhsu1129.github.io/images/Pasted%20image%2020250915004236.png'>"
collection: portfolio
---

Design a 32 bit MIPS CPU with a 5 stage pipeline with modules for fowarding, flush control, stall control, and hazard resolution in Verilog. Design of cache done using gem5.

My current work for RTL improvements include designing a branch predictor, multicore and memory coherency, and possibly redesigning for superscalar execution.

The physical design flow of this processor was done using OpenLane2. I have implemented low power technqiues such as using a subthreshold adder, clock gating, and using low leakage stacked transistor cells.

This design was simulated using Verilator for individual functional units and Xcelium for the overall design. The physical implementation has achieved timing closure, and passed DRC and LVS checks.

![Layout](https://justinhsu1129.github.io/jhsu1129.github.io/images/Pasted%20image%2020250915004236.png)

![Routing Congestion](https://justinhsu1129.github.io/jhsu1129.github.io/images/Pasted%20image%2020250915004236.png/images/Pasted%20image%2020250915223638.png)