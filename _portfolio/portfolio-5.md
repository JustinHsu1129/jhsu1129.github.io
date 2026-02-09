---
title: "Live Video Feed Edge Detection Accelerator"
excerpt: "Senior design project-building a edge detection accelerator for Altera DE1-SoC FPGA"
collection: portfolio
---

This project showcases a high-performance Canny Edge Detection system implemented on the Intel DE1-SoC. By leveraging a Hardware/Software co-design approach, I utilized the Cyclone V FPGA for high-speed image preprocessing and the ARM Cortex-A9 for complex algorithmic decision-making.

The goal was to build a real-time image processing pipeline capable of transforming raw video data into clean, tracked edges. The Canny algorithm is computationally demanding, requiring several stages of filtering and analysis. To achieve real-time performance, I partitioned the workload: deterministic pixel math was mapped to Verilog modules, while recursive logic was handled in C.

1. Hardware Acceleration (Verilog)

The FPGA fabric handles the "heavy lifting" of the stream-based pixel operations.

* Gaussian Blur & 11x11 Convolution: To suppress noise, I designed a versatile 2-D convolution engine. It utilizes a series of Line Buffers to create a sliding window, allowing for an 11x11 Gaussian kernel.

* Sobel Gradient Module: This module calculates the intensity gradients in both x and y directions. By calculating the magnitude and direction in hardware, the system identifies potential edge candidates at wire speed.

* Video Effects: I integrated a custom Vignetting module that applies a radial intensity mask to the video feed, demonstrating the ability to stack multiple real-time DSP effects.

2. Software Logic (C/HPS)

The final stage of the Canny algorithm—Hysteresis Edge Tracking—is difficult to implement in pure hardware because it requires searching through neighboring pixels to connect edge segments.

* HPS Integration: I mapped the FPGA’s processed frame buffer into the ARM processor’s memory space.

* Hysteresis Algorithm: The C code scans the gradient data, using dual-thresholding to distinguish between "strong" and "weak" edges. It then performs a connectivity analysis to preserve weak pixels only if they are connected to strong ones, effectively eliminating noise while maintaining edge continuity.