---
title: "RISC-V Cache Configuration and Performance Analysis"
excerpt: "Analyzed hardware performance, area, power, and leakage trade-offs under different L1 cache configurations for a CVA6 RISC-V core using Chipyard, Synopsys Design Compiler, and CACTI."
collection: portfolio
order: 9
---

Performed a comprehensive evaluation of cache design parameters (associativity and block size) for a CVA6 (formerly Ariane) in-order RISC-V core. Using agile hardware tools, logic synthesizers, and memory modeling toolchains, this project quantified the architectural trade-offs between processing performance, silicon area, dynamic power, and leakage.

### 1. Hardware Generation & Customization (Chipyard)

* **Platform:** Utilized the **Chipyard** SoC integration framework developed at UC Berkeley.
* **Cores:** Generated **nine distinct configurations** of the tapeout-ready 64-bit/32-bit CVA6 core.
* **HDL Flow:** Used Chisel HDL and Scala-based configuration files to adjust cache capacities, associativity, and line widths dynamically.
* **Baseline Control:** Configured a private L1 Instruction Cache (16 KB, 4-way associative) and a private L1 Data Cache (32 KB, 8-way associative), both using a 128-bit block size.

### 2. Logic Synthesis & Memory Modeling

* **Core Synthesis (Design Compiler):** Synthesized the core logic utilizing **Synopsys Design Compiler** with the **45nm Nangate PDK** at $250\text{ MHz}$ and $1.1\text{V}$. The synthesized logic yielded:
  - **Logic Area:** $0.0458\text{ cm}^2$
  - **Standard Cell Count:** ~2 million cells (1.432 million combinational, 621,000 sequential)
  - **Dynamic Power:** $90.74\text{ mW}$
  - **Leakage Power:** $98.42\text{ mW}$
* **SRAM Macro Modeling (CACTI 7):** Because standard compilers do not synthesize SRAM arrays efficiently, **CACTI 7** was used to model the area, read/write energy, and leakage power of the caches:
  - **Baseline D-Cache Area & Leakage:** $0.363\times0.457\text{ mm}$ bounding box, $54.41\text{ mW}$ leakage power at $2.14\text{ GHz}$ operational frequency (read energy $0.026\text{ nJ}$, write energy $0.036\text{ nJ}$).
  - **Baseline I-Cache Area & Leakage:** $0.362\times0.237\text{ mm}$ bounding box, $28.64\text{ mW}$ leakage power at $3.03\text{ GHz}$ operational frequency (read energy $0.013\text{ nJ}$, write energy $0.023\text{ nJ}$).
  - **Elongated Layout Trade-offs:** Analyzed non-uniform, highly associative cache layouts (e.g. 16-way D-Cache with $0.198\times0.733\text{ mm}$ bounding box). This elongated structure introduced unbalanced critical paths, degrading maximum frequency from $2.14\text{ GHz}$ to $1.18\text{ GHz}$.

### 3. Performance Simulation & Benchmarking

Simulated core configurations on a RISC-V Proxy Kernel (PK) environment, analyzing cache hit/miss behavior using **GTKWave** waveforms across four distinct workloads:
1. **Matrix Multiplication:** Evaluates CPU parallelism and memory reuse patterns.
2. **Stream:** Tests cache throughput and eviction handling using oversized arrays (4x cache size) to expose write-through vs. write-back policies.
3. **Stride:** Assesses spatial locality by fetching data at configurable offsets.
4. **Pointer Chasing:** Probes serial dependencies to isolate cache latency and associativity limits.

### 4. Cache Parameter Observations

* **Associativity Sweeps:** Increasing instruction cache associativity to 8-way and data cache associativity to 16-way showed negligible execution time improvements ($0.02\%$ overall, max $1\%$ in Matrix Multiplication). However, higher associativity required wider multiplexers and massive parallel tag comparators, tax-penalizing area and clock speed.
* **Block Size Sweeps:**
  - **Wider Blocks (256-bit):** Drastically reduced cache miss rates ($33\%$ reduction in I-Cache, $30\%$ reduction in D-Cache) due to spatial locality benefits in sequential matrix multiplication and stream workloads.
  - **Narrower Blocks (64-bit):** Caused a significant spike in misses ($86\%$ increase in I-Cache, $60\%$ increase in D-Cache) and degraded overall execution speed due to high capacity and compulsory misses.

[Report](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20270%20Project%20Report.pdf)
