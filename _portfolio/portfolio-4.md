---
title: "32 Bit Subthreshold Adder"
excerpt: "Designed a low power 32 bit subthreshold adder operating at 100 MHz"
collection: portfolio
---

Designed for a project in EEC 216-Low Power Digital ICs. This subthreshold adder operates at 100 MHz and features a multistage pipeline. Static CMOS logic style was chosen along with Kogge Stone adder architecture.

Static CMOS logic style was chosen for its surperior robustness to noise, less layout complexity due to not needing complementary inputs, and stronger drive strength. Transistors were aggressively sized-large widths on critical paths, and device stacks were reduced to around 2 transistors per stack. Buffers were liberally inserted between pipeline stages to restore signal levels.

Kogge Stone adder architecture was chosen beacuse of its minimum depth of 5 for 32 bit addition. It allows for maximum parallelism along with ease of pipelining to achieve the 100 MHz target operating frequency. Thanks to the minimal logic depth per pipeline stage, circuits could be adjusted aggressively for speed.