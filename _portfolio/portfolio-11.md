---
title: "FPGA-Accelerated Quantized CNN for Handwritten Digit Recognition"
excerpt: "Proposed and co-designed a quantized CNN accelerator on an Intel DE1-SoC FPGA for MNIST digit recognition using PyTorch, 4-bit power-of-two quantization, and hardware systolic arrays."
collection: portfolio
order: 1
---

Proposed an end-to-end hardware acceleration framework to run a Convolutional Neural Network (CNN) for handwritten digit recognition on resource-constrained FPGA platforms. The project covers CNN design and training, post-training quantization optimization, and high-throughput systolic array hardware architectures.

### 1. CNN Model Design & Training (PyTorch)

* **Architecture:** Designed a custom CNN to recognize handwritten digits ($0$-$9$) using the MNIST dataset:
  - **Layers:** 2 Convolutional layers, 2 Pooling layers, 2 Fully Connected layers, and 1 final Output layer.
  - **Pooling Optimization:** Selected **Average Pooling** over Max Pooling. Average pooling retains general spatial features across pixel regions, improving generalization and reducing overfitting for handwriting variations (e.g., messy digit outlines).
* **Training Flow:** Trained the model in 32-bit floating point (FP32) using PyTorch on an Nvidia 5050 Laptop GPU (2560 CUDA cores) to capture fine-grained gradients and achieve high baseline accuracy.

### 2. 4-Bit Power-of-Two Quantization Scheme

To minimize the computational complexity of FPGA inference, an efficient quantization technique was proposed:
* **Quantization Target:** Quantized weights from FP32 down to a **4-bit integer representation** post-training.
* **Power-of-Two Scaling:** Implemented a linear, symmetric power-of-two quantization scheme with a zero point of $0$.
* **Hardware Efficiency:** Because weights scale strictly by powers of 2, FPGA hardware can execute quantization and de-quantization scaling using simple **bit-shifting operations (left/right)** rather than expensive hardware multipliers, reducing resource area and power consumption.

### 3. Hardware Systolic Array Architectures

To maximize processing throughput and minimize DRAM bottleneck constraints, four parallel systolic array configurations were designed for the Intel DE1-SoC FPGA:
1. **Weight Stationary:** Keeps weights fixed in local Processing Element (PE) registers while inputs stream through, minimizing weight reload cycles.
2. **Input Stationary:** Holds input feature maps in local PE buffers while weights stream through, ideal for small input sizes.
3. **Output Stationary:** Accumulates partial sums locally in PEs and streams inputs and weights, reducing output write bandwidth.
4. **Row Stationary:** Optimizes 2D convolution data reuse (weights, inputs, and outputs) across adjacent rows of PEs, maximizing local buffer efficiency.

### 4. Performance & Resource Comparison

The implementation plan compares the four systolic array styles on the Intel DE1-SoC FPGA using the following metrics:
* **Computation Latency:** Total execution time for a full feedforward inference cycle.
* **FPGA Area:** Logical resource utilization (LEs, ALMs, Registers).
* **Memory Bandwidth:** Total DRAM read/write cycles compared against local buffer hit rates.

[Proposal](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20289Q%20Project%20Proposal-2.pdf)
