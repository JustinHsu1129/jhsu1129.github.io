---
permalink: /
title: "Justin Hsu"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am a fourth year Electrical Engineering student at UC Davis with plans to pursue a Master degree in electrical engineering. I am broadly interested in physical design and VLSI. I am particularly interested in accelerator design for machine learning algorithms and low power IC design. My work focuses on the intersection between computer architecture and physical implementation. I am driven by the challenge of designing domain specific architectures, and specifically aiming to achieve maximum performance in a low power package.

Work Experience
======
1. RTL Design Engineer-Lotus Communication Systems
* Using the Xilinx Zynq 7000 SoC, I designed and implemented a digital FIR high pass and bandpass filter for cleaning recieved signals. Through Matlab simulation I found the necessary weights required to perform the digital filtering, and implemented the filters using verilog. I took advantage of the parallelism available on an FPGA-using a 4 stage pipelined transpose form filter.
* My final project was designing and implementing a cascaded integrator-comb decimation filter in Verilog designed for resource constrained FPGA environments. The architecture features automated bit-growth calculation and pipelining. Additionally, I used scalable parameterization when designing this module so this design could be reused across different projects. Lastly, numerous architectural decisions were made in order to implement the CIC filter to be completely multiplier free.

2. PCB Design Engineer-Lotus Communication Systems
* I designed a 4 layer PCB for a high frequency (~10GHz range) mixed signal two channel block up/down converter from schematics to physically soldering the components onto the board. Designing the schematics from OrCad, I was a key contributor to parts selection, and managed the bill of materials for sourcing availability. After, I designed the PCB using PADS. I carefully implemented a split grounding scheme and carefully managed return paths to prevent noise leakage from the digital blocks from coupling into the RF front end.
* I designed multiple sub-modules of the PCB, including a custom loop filter, digital microcontroller control block, and RF block. This modular design strategy allowed more effective isolation of critical RF signal paths, and greatly helped when designing the power and ground planes.

Featured Projects
======
* [FPGA-Accelerated Quantized CNN](/portfolio/portfolio-11/): Co-designed a 4-bit power-of-two quantized CNN accelerator on an Intel DE1-SoC FPGA for MNIST digit recognition using PyTorch and parallel systolic arrays.
* [Real-Time Video Edge Detection & Template Matching](/portfolio/portfolio-5/): Designed and compared three distinct RTL hardware architectures (Score Tree, Systolic Array, and FFT-based convolution) on an Intel Cyclone V FPGA.
* [32-Bit Low-Power Square Root Carry Select Adder](/portfolio/portfolio-8/): Designed and simulated a low-power, mirror-cell-based 32-bit square root carry select adder in Cadence Virtuoso and Spectre, optimizing for sub-threshold ($0.32\text{V}$) operation.
* [RISC-V Cache Performance Analysis](/portfolio/portfolio-9/): Evaluated L1 cache parameters (associativity and block size) for a CVA6 RISC-V core using Chipyard, Synopsys Design Compiler, and CACTI.