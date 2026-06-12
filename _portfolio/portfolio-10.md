---
title: "High-Level Fault Simulation and Test Pattern Generation for RISC-V ALUs"
excerpt: "Implemented a structural Python simulator and a PODEM-based ATPG framework to achieve 100% fault coverage for stuck-at faults in a Verilog-designed 32-bit RISC-V ALU."
collection: portfolio
order: 10
---

Developed a multi-layered verification framework to validate a 32-bit RISC-V ALU design. The project integrated RTL design, dynamic self-checking hardware testbenches, software-based structural gate-level simulation, and automated test pattern generation (ATPG) using the PODEM algorithm to achieve complete fault coverage.

### 1. 32-Bit RISC-V ALU RTL Design & Hardware Testbench

* **RTL Development:** Designed a robust 32-bit RISC-V compliant ALU in Verilog, adding M-extension operations (multiplication, division, modulo). The ALU decodes the RISC-V opcode to select execution units and generates appropriate status flags (zero, overflow, division-by-zero).
* **Self-Checking Testbench:** Built an automated Verilog testbench that dynamically compared RTL execution outputs against a software-based golden reference model.
  - **Test Coverage:** Verified 12 core ALU functions across 56 targeted tests, applying random values and boundary edge cases (e.g. division-by-zero, maximum overflow).
  - **Results:** Achieved a 100% pass rate in just 0.053 seconds of simulation.

### 2. Software-Based Structural Simulator (Python)

To enable internal fault injection and gate-level observability, a structural simulator was implemented in Python:
* **Object-Oriented Netlist Modeling:** Modeled the ALU's internal structures using custom object abstractions representing gates (`Gate`, `FullAdder32`, `Multiplier32`, etc.) and wires (`Wire`).
* **Bit-Level Observability:** Unlike high-level behavioral RTL, the Python simulator explicitly modeled individual wire bits and 32-bit buses. This representation allowed precise monitoring of internal signal values.

### 3. Fault Injection and Coverage Analysis

Using the structural Python model, single stuck-at-fault (SSF) models were injected:
* **Fault Models:** Supported **stuck-at-0 (SA0)** and **stuck-at-1 (SA1)** models.
* **Injection Mechanics:** Implemented two modes of injection:
  1. **Whole-Wire Faults:** Forces all bits of a bus to a constant value, modeling physical short circuits to VDD or Ground.
  2. **Bit-Level Faults:** Targets a single bit within a multi-bit wire or bus to model localized defects.
* **Evaluation:** Injected a total of **906 possible stuck-at faults** across every internal node and wire bit of the ALU. The simulator executed test vectors for each fault individually, comparing outputs against the golden reference model to log successful fault detections.

### 4. PODEM ATPG Implementation

To automate the detection of hard-to-reach faults and handle reconvergent fan-outs, the **Path-Oriented Decision Making (PODEM)** algorithm was implemented in Python:
* **Backtracing:** Recursively traced path constraints from the internal fault site back to the primary inputs to determine required test vector assignments.
* **D-Drive Propagation:** Excites the fault and propagates the fault shadow (D-frontier) forward through internal gate structures to observable outputs.
* **Backtracking:** Implemented decision-driven backtracking to resolve gate conflicts by systematically reversing and attempting alternate input assignments.
* **Results:** Executed across 94 critical faults in the fault list (covering primary inputs, control signals, primary output, and internal buses). The PODEM generator achieved **100% fault coverage**, producing a verified test vector for every target fault.

[Report](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20286%20Project%20Report.pdf)
