---
title: "Systolic Matrix Multiplier"
excerpt: "Designed an 8x8 systolic matrix multiplier in Verilog and carried through physical design flow with OpenLane"
collection: portfolio
---

Continued an in class systolic multiplier project. I am still working on improving the layout for low power applications. Designed RTL using Verilog and verified functionality using both Verilator and Xcelium.

Right now there are two versions of the design-a structural version and a behaioral version. The structural version uses a radix-2 kogge stone adder and a wallace tree multiplier implementing Booth's alogrithm in each processing unit. The idea of this structural design was to optimize for power efficiency while retaining high throughput via wide parallelism. 

In the second version of the design, the multply accumulate modules are designed behaviorally, leaving it up to the synthesizer to infer what design should be used. As a result this behavioral design is much more area efficient as opposed to the structural design. 

Both of the designs shown below are full RTL-to-GDSII flows done exclusively in OpenLane2. My future work includes using Synopsys ICC2 to layout my synthesized design from Design Compiler, as well as making hardened macros for each processing element and multiply accumulate module to create a fully custom layout.

![Layout](https://justinhsu1129.github.io/jhsu1129.github.io/images/Layout.png)

![Routing Congestion](https://justinhsu1129.github.io/jhsu1129.github.io/images/Layout.png/images/Routing%20congestion.png)