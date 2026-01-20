# ClearLogicAnalyzer -- Pico-Based High-Speed Logic Analyzer Front-End

This repository contains the **hardware design for a low-noise, high-bandwidth logic analyzer front-end**, intended for use with Raspberry Pi Pico–class devices.

The design focuses on **clean edge capture, minimal loading, and robust level translation** for real-world digital systems operating at **100 MHz and beyond**.

---

## Design Goals

- **100–200 MHz+ signal capture**
- **16–32 simultaneous channels**
- **Wide input voltage range:** **1.2 V to 5.5 V**
- **Minimal signal loading**
- **Clean edges and low jitter**
- **Cost-effective 2-layer PCB**
- Compatibility with existing open-source logic analyzer firmware

---

## Key Features

### ✔ High-Speed Signal Integrity
- Series input resistors for ringing and edge control
- Tight local decoupling per translator IC
- Solid top and bottom ground planes
- Dense stitching vias to maintain return current paths
- 0.8 mm PCB thickness for reduced inductance and low-cost PCB manufacturing

### ✔ Proper Level Translation
- Uses **SN74LXC8T245** level translators
- Supports input logic from **1.2 V to 5.5 V**
- Translates cleanly into **3.3 V domain**
- Fully supports partial power-down and safe power sequencing
- Supports multiple voltage domains (one per stacked board) or shared single domain

### ✔ Analyzer-Friendly Front-End
- Designed for **passive observation**, not bus driving
- Handles capacitive loading from probes and test leads
- Stable thresholds for low-voltage logic (1.2 V / 1.8 V / 2.5 V)

### ✔ Modular & Expandable
- Pin-header interconnects for stacking or extension
- External trigger input with fast clamp protection
- Compatible with standard Pico-style firmware flows

---

## Electrical Overview

| Feature | Specification |
|------|---------------|
| Input voltage range | 1.2 V – 5.5 V |
| Logic translation | SN74LXC8T245 |
| Target logic domain | 3.3 V |
| Input protection | Series resistors + clamp diode |
| PCB | 2-layer, 0.8 mm |
| Grounding | Solid planes + stitching vias |
| Intended bandwidth | 100–200 MHz+ |

---

## Why This Design Exists

Many low-cost logic analyzer front-ends focus on:
- Trace-length matching while ignoring return paths
- Thin power routing
- Inadequate decoupling
- Over-reliance on software compensation for hardware issues

This project instead prioritizes **fundamental signal integrity principles**, ensuring that captured data is clean *before* it ever reaches firmware.

---

## Status

- ✔ PCB layout complete
- ✔ Design rule checked for high-speed operation
- ✔ Prototypes in fabrication
- ⏳ Validation with real-world buses (DRAM, CPUs, FPGAs)

---

## Firmware & Software

This hardware is designed to be compatible with the open-source logic analyzer firmware:

🔗 **https://github.com/gusmanb/logicanalyzer**

---

## Disclaimer

This is an **experimental high-speed hardware design** intended for developers, FPGA engineers, and hardware hackers.  
Performance depends on probe quality, cable length, grounding, and the system under test.

---

## License

Hardware design files are released under an open license.  
See the repository LICENSE file for details.

---

## Contributions

Suggestions, improvements, and measured results are welcome.  
Please include scope captures or timing data when reporting issues.

