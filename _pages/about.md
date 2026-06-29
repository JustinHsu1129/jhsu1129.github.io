---
permalink: /
title: "Justin Hsu"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am an Electrical Engineering Master's student at the Georgia Institute of Technology, having recently graduated with a B.S. in Electrical Engineering from UC Davis. I am broadly interested in physical design and VLSI, particularly accelerator design for machine learning algorithms and low-power IC design. My work focuses on the intersection between computer architecture and physical implementation, and I am driven by the challenge of designing domain-specific architectures that achieve maximum performance in a low-power package.

Work Experience
======
1. **RTL Design Engineer Intern** — Lotus Communication Systems (Acton, MA)
   * *June 2025 - September 2025*
   * Designed and implemented a high-performance digital Finite Impulse Response (FIR) filter and Block Up/Down Converter (BUDC) to optimize signal processing efficiency for Xilinx FPGA deployment using SystemVerilog.
   * Achieved a 19% reduction in hardware area and improved operational clock frequency to 200 MHz by leveraging Vivado and MATLAB to execute Power, Performance, and Area (PPA) analysis, rewriting critical RTL blocks to minimize multiply-and-accumulate (MAC) calculations.
   * Validated system functionality through rigorous RTL simulation and timing closure verification, successfully integrating the BUDC block into the larger communication system pipeline to ensure error-free up/down-conversion.

2. **PCB Layout Intern** — Lotus Communication Systems (Acton, MA)
   * *June 2024 - September 2024*
   * Designed and implemented a complex mixed-signal PCB layout for a gigahertz-frequency Block Up/Down Converter (BUDC) with the goal of isolating high-frequency RF paths from digital control circuitry.
   * Achieved 40 dB of noise isolation and met strict 50 ohm controlled impedance requirements across all critical paths using Siemens PADS and Cadence Allegro to optimize differential pair routing, component placement, and board area.
   * Validated signal integrity and layout performance through post-route parasitic extraction and simulation, ensuring successful hardware integration and error-free operation of the converter within the larger RF front-end system.

Featured Projects
======
* [Handwritten Number CNN Accelerator](/portfolio/portfolio-11/): Architected a LeNet-5 CNN accelerator on an Altera DE1-SoC FPGA and executed an RTL-to-GDSII flow under Skywater 130nm PDK using Synopsys Design Compiler and Cadence Innovus, achieving 100 MHz.
* [Subthreshold Minimum Energy 32-Bit Adder](/portfolio/portfolio-8/): Engineered a low-power 32-bit Square Root Carry Select Adder (SRCSA) optimized for subthreshold operation, achieving 100 MHz at Vdd = 0.32V using Cadence Virtuoso, Spectre, and Xcelium.
* [Heterogeneous Multicore RISC-V Processor](/portfolio/portfolio-3/): Designed a heterogeneous RISC-V big.LITTLE multi-core architecture in SystemVerilog, achieving 400 MHz and a 30% increase in energy efficiency using Synopsys Design Compiler and Cadence Innovus.