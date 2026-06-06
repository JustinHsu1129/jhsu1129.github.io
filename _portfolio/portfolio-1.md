---
title: "8-Bit Custom Barrel Shifter Design"
excerpt: "Designed and laid out a custom high-performance 8-bit barrel shifter and decoder in Cadence Virtuoso, achieving physical verification sign-off (DRC/LVS)."
collection: portfolio
order: 8
---

Designed and laid out a high-performance custom 8-bit barrel shifter and a supporting 3-to-8 binary decoder. The design flow encompassed schematic capture, transistor-level simulation, manual physical layout, and full physical verification closure using Cadence Virtuoso and Spectre.

### 1. Circuit Topology & Design Decisions

* **Logic Style:** Implemented shift logic using a multiplexer-based architecture structured with custom **transmission-gate pass-transistor logic (TG-PTL)**. Transmission gates were selected to ensure full-swing logic outputs and high noise margins while significantly reducing the transistor count compared to standard complementary CMOS multiplexers.
* **Decoder Interface:** Designed a supporting 3-to-8 static CMOS decoder to decode shift-select signals, optimizing gate-sizing ratios to drive the transmission-gate select inputs without introducing excessive gate propagation delay.

### 2. Manual Physical Layout & Optimization

* **Parasitic Minimization:** Conducted manual cell-level layout with a strong focus on symmetry and metal routing optimization. Wires were routed carefully to minimize parasitics and balance delay times across all shift paths.
* **Design Rule Guidelines:** Managed transistor sizing ratios (P/N ratio tuning) to optimize rise/fall symmetries. Grouped PMOS and NMOS devices in common wells and aligned standard cell heights, ensuring clean routing channels and avoiding latch-up issues.

### 3. Verification & Sign-Off Results

* **Functional Verification (Spectre):** Simulated the design under typical and worst-case corners in Cadence Spectre. Waveform analysis verified exact shift timing, clean signal transitions, and robust operation across voltage variations.
* **Physical Verification:** Achieved full sign-off closure by passing all **Design Rule Checking (DRC)**, **Layout vs. Schematic (LVS)** comparison checks, and antenna checks, confirming error-free fabrication readiness.

![8 Bit Barrel Shifter Result](https://justinhsu1129.github.io/jhsu1129.github.io/images/8%20bit%20barrel%20shifter.jpg)

![8 Bit Barrel Shifter Waveform](https://justinhsu1129.github.io/jhsu1129.github.io/images/8%20bit%20barrel%20shifter%20waveform.jpg)

![8 Bit Barrel Shifter Schematic](https://justinhsu1129.github.io/jhsu1129.github.io/images/8%20bit%20barrel%20shifter%20circuit.jpg)

![3-To-8 Decoder Layout](https://justinhsu1129.github.io/jhsu1129.github.io/images/3-8%20decoder%20layout.jpg)

![3-To-8 DecoderWaveform](https://justinhsu1129.github.io/jhsu1129.github.io/images/decoder%20waveform.jpg)
