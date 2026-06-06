---
title: "Real-Time Hardware Video Edge Detection & Template Matching Architectures"
excerpt: "Designed and compared three distinct fully hardware-accelerated architectures on an Intel Cyclone V FPGA for real-time edge detection and template matching: Score Tree, Systolic Array, and FFT-based convolution."
collection: portfolio
order: 2
---

Designed, implemented, and compared three distinct fully hardware-accelerated (100% RTL) architectures on an Intel Cyclone V FPGA to execute real-time Sobel/Canny edge detection and template matching. The project evaluated each architecture across throughput (latency), logical resource utilization (LEs/ALMs), and memory bandwidth to identify the optimal design for varying template sizes.

### Architecture 1: Pipelined Score Tree Design
* **Design Philosophy:** Optimizes for low-latency score computation using spatial-domain reduction.
* **Implementation:**
  - The incoming video stream is filtered using a pipelined Sobel/Canny edge detector (leveraging dual-port Block RAMs as line buffers to create local sliding windows).
  - The resulting edge maps feed a **pipelined adder/score tree reduction network** to evaluate template matches.
  - The score tree features a balanced binary tree pipeline, minimizing critical path logic depth and maximizing operating frequency. This allows the system to compute peak correlation coordinates within standard video timing constraints.

### Architecture 2: 2D Systolic Array Design
* **Design Philosophy:** Optimizes for high data reuse and minimal memory bandwidth.
* **Implementation:**
  - Configured a **2D grid of hardware Processing Elements (PEs)** running a **weight-stationary dataflow pattern**.
  - Template weights are locked in local PE registers, while edge-detected pixel streams flow horizontally and vertically through the array.
  - By utilizing local, neighbor-to-neighbor PE buffers, this architecture minimizes external memory access, keeping power consumption low and preventing memory-bus bottlenecks.

### Architecture 3: FFT-Based Frequency Domain Convolution Design
* **Design Philosophy:** Optimizes for large template sizes where spatial-domain correlation becomes computationally prohibitive.
* **Implementation:**
  - Implemented a pipelined **Radix-2/Radix-4 Fast Fourier Transform (FFT) hardware accelerator** and corresponding Inverse FFT (IFFT) processor.
  - The design transforms both the video frame and the template into the frequency domain, performs fast point-wise multiplication, and applies the IFFT to reconstruct the spatial correlation map.
  - Because frequency-domain convolution complexity is independent of template size, this design provides stable, high-throughput execution for large search templates.