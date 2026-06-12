---
title: "FPGA-Accelerated Quantized CNN for Handwritten Digit Recognition"
excerpt: "Designed and implemented a quantized LeNet-5 CNN accelerator on an Intel DE1-SoC FPGA, comparing PPA metrics across four systolic array dataflows."
collection: portfolio
order: 1
---

Designed, implemented, and verified a custom hardware accelerator on the Terasic DE1-SoC (Cyclone V) FPGA to execute LeNet-5 Convolutional Neural Network (CNN) inference. The project involved PyTorch training, post-training quantization, and a comprehensive comparative analysis of four distinct systolic array hardware architectures coded in SystemVerilog.

### 1. CNN Model & 4-Bit Quantization (QAT)

* **Architecture:** Based on the LeNet-5 topology, consisting of convolutional layers, average pooling layers, and fully connected layers trained on the MNIST dataset.
* **Quantization Aware Training (QAT):** Trained the model in PyTorch on an RTX 5050 GPU. To fit the constraints of the FPGA's block RAM (BRAM), weights were aggressively quantized to **4-bit integers (int4)**.
* **Accuracy:** The QAT model achieved an offline test set inference accuracy of **98.83%**. Weights were exported in `.csv` formats for hardware translation.

### 2. Hardware Accelerator Architecture (SystemVerilog)

The entire design was mapped to Cyclone V FPGA fabric using 100% hardware RTL:
* **Convolutional Layers:** Accelerated using a 2D systolic array of processing elements (PEs) consisting of a multiplier, accumulator, and register. Skewing FIFOs and output de-skewing delay pipelines were implemented to align data streams.
* **Average Pooling:** Coded in SystemVerilog using a 2x2 window with a stride of 2. Summed inputs are quantized and scaled using shift registers, with outlier clipping to mitigate overfitting.
* **Fully Connected Layers:** Implemented with serialized pipelined MAC units to reduce pin counts and physical area. Outputs are one-hot encoded to drive a seven-segment display on the board.

### 3. Comparative Analysis of Systolic Dataflows

We designed and evaluated four distinct dataflow mappings for the 2D systolic array:
1. **Input Stationary:** Activations remain in PEs, weights/outputs stream. Best for multi-channel processing, but suffers from high memory read cycles (98,000 reads) and high fan-out bottlenecks.
2. **Weight Stationary:** Weights remain in PEs, activations/outputs stream. Yields lowest memory read cycles (125 reads) and high throughput but doubles BRAM utilization due to weight partitioning.
3. **Output Stationary:** Partial sums accumulate in PEs, activations/weights stream. Minimizes high-precision data movement, making it highly efficient.
4. **Row Stationary:** Localized 1D rows maximize reuse of weights, activations, and outputs. However, this introduces substantial control logic overhead.

### 4. Experimental Results

Physical board simulations and hardware measurements yielded the following performance, power, and area (PPA) comparisons:

| Architecture | Compute Time (ms) | Memory Accesses | Power (mW) | Logic Util. (%) | Registers Used | Block Memory Bits |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Input Stationary** | 20.955 | 2k writes / 98k reads | 548.21 | 23% | 12,240 | 962,880 |
| **Weight Stationary** | 8.906 | 2k writes / 125 reads | 613.38 | 29% | 20,786 | 1,679,680 |
| **Output Stationary** | **8.845** | 2k writes / 3.9k reads | **546.59** | **20%** | **10,580** | **862,528** |
| **Row Stationary** | 13.947 | 2k writes / 75k reads | 622.08 | 39% | 21,796 | 868,672 |

* **Hardware Accuracy:** Validated on-board using a test suite of 20 MNIST digits, achieving a **95% accuracy rate** (19/20 correct classifications).
* **Key Findings:** **Output Stationary** and **Weight Stationary** architectures provided the best throughput. Output Stationary achieved the highest energy and area efficiency (lowest compute time of 8.85 ms, lowest power of 546.59 mW, and lowest logic utilization of 20%).

[Paper / Report](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20289Q%20Project%20Paper.docx.pdf)

[Project Proposal](https://justinhsu1129.github.io/jhsu1129.github.io/files/EEC%20289Q%20Project%20Proposal-2.pdf)
