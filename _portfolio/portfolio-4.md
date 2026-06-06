---
title: "32-Bit Sub-threshold Kogge-Stone Adder"
excerpt: "Designed a low-power pipelined 32-bit sub-threshold Kogge-Stone adder operating at 100 MHz, utilizing optimized static CMOS topologies."
collection: portfolio
order: 4
---

Designed a high-speed, low-power pipelined 32-bit adder operating in the sub-threshold region for ultra-low power digital VLSI applications. The design utilizes static CMOS logic and a Kogge-Stone prefix-tree architecture, optimized to run at a target operating frequency of $100\text{ MHz}$.

### 1. Sub-threshold Logic Design & Physics Challenges

Operating a circuit in the sub-threshold region ($V_{dd} < V_{th}$) introduces severe physical design constraints:
* **Exponential Sensitivity:** The drive current ($I_{sub}$) depends exponentially on the threshold voltage ($V_{th}$) and temperature, rendering the design highly sensitive to process, voltage, and temperature (PVT) variations and severely degrading noise margins.
* **Logic Family Choice:** Implemented the design using static CMOS logic rather than dynamic styles. Static CMOS provides robust noise margins and high noise immunity at sub-threshold voltages, eliminating the need for complementary clock inputs and reducing routing complexity.
* **Transistor Sizing & Stacking:** Reduced all logic gate stacks to a maximum of 2 transistors to minimize body effect impact and decrease sub-threshold leakage currents. Critical paths were sized to optimize gate delay, and level-restoring buffers were inserted between pipeline stages to combat signal degradation.

### 2. Kogge-Stone Architecture & Pipelining

* **Tree Optimization:** Selected a Kogge-Stone parallel prefix-tree structure for its minimum logic depth (5 stages for 32-bit addition), which minimizes the propagation path.
* **Pipeline Partitioning:** Pipelined the prefix network using custom **low-voltage transmission-gate registers** to satisfy the $100\text{ MHz}$ clock frequency constraint. The low logic depth per pipeline stage allowed aggressive voltage scaling while maintaining structural timing margins.