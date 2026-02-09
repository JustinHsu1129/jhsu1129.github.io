---
title: "Configurable Logic Block Verification Tool"
excerpt: "Created a Python based framework using the PODEM algorithm for test vector generation for fault detection in configurable logic blocks."
collection: portfolio
---

This project involved developing a sophisticated automated test pattern generation (ATPG) tool specifically designed for FPGA architectures. By implementing the PODEM (Path-Oriented Decision Making) algorithm in Python, I created a framework capable of identifying structural defects in the fundamental building blocks of programmable logic.

1. CLB Component Modeling

To perform fault simulation, I modeled the standard primitives of a CLB in Python:

* Look-Up Tables (LUTs): Modeled as truth-table-based logic where faults could occur at the input address lines or the memory bitmask.

* Multiplexers (MUXs): Modeled to verify select-line integrity and path transparency.

* Flip-Flops (FFs): Modeled with clocking behavior to verify sequential fault propagation.

2. PODEM Algorithm Implementation

I implemented the PODEM algorithm to overcome the limitations of the classic D-Algorithm, specifically to handle the reconvergent fan-out often found in FPGA interconnects.

* Objective Setting: The framework selects a target fault (e.g., Stuck-At-0) and establishes an objective to "excite" that fault.

* Backtracing: The algorithm recursively traces from the fault site back to the primary inputs to determine the necessary input assignments.

* D-Drive (Implication): Once the fault is excited, the framework propagates the "D-frontier" (the fault shadow) through the CLB's LUTs and MUXs until it reaches an observable output.

3. Verification & Fault Coverage

* Fault Simulation: I integrated a fault simulator to verify that the generated test vectors actually detected the targeted faults.

* Coverage Analysis: The framework provides a comprehensive report on fault coverage percentage, identifying any "undetectable" faults caused by logical redundancies within the CLB architecture.

![Presentation](https://justinhsu1129.github.io/jhsu1129.github.io/files/Creating%20a%20tool%20for%20FPGA%20Design%20Verification-1.pdf)

![Report](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20283%20Report-2.pdf)