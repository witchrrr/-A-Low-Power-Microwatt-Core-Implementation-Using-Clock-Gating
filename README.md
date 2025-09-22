# 💡 A Low-Power Microwatt Core Using Clock Gating

This repository contains the RTL and design files for a power-optimized version of the open-source Microwatt CPU core, enhanced with fine-grained clock gating to significantly reduce dynamic power consumption.

---

## 📝 Overview

This project creates a power-efficient version of the open-source **Microwatt CPU core**, making it suitable for energy-sensitive applications like IoT and edge devices. The standard Microwatt core is designed for functionality, not for low-power operation. This work re-engineers the core at the hardware level by implementing **fine-grained clock gating**, a highly effective technique for reducing dynamic power. The result will be a functionally identical processor that consumes significantly less power, unlocking its use in a new class of battery-powered and thermally constrained environments while remaining fully compliant with the OpenPOWER ISA.

---

## 🏛️ Architecture

The SoC architecture remains centered on the Microwatt CPU, but its implementation is enhanced with a distributed, power-aware design. This is not a single block but a systemic modification where the core's own activity is used to manage its power consumption intelligently. High-activity modules are redesigned to shut down their internal clocks when idle, preventing the wasteful power consumption that occurs from unnecessary transistor switching.

### The Controller: Microwatt CPU Core
The system is based on the `Microwatt` core, an open-source, 64-bit processor that implements the **OpenPOWER Instruction Set Architecture (ISA)**. In this project, it serves two roles: it is both the subject of the optimization and the controller that benefits from it. Its baseline functionality will remain unchanged, ensuring that all existing software and toolchains are fully compatible with the final, low-power design.

### The Engine: Fine-Grained Clock Gating
The "engine" of the power savings is the implementation of fine-grained clock gating logic. This involves analyzing the processor's design to identify components that do not operate on every clock cycle and then wrapping their registers in **Integrated Clock Gating (ICG)** cells. This logic acts as a smart switch
