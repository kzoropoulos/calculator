# System Overview and Licensing Specification

## 1. General Overview

This repository contains the complete engineering files of the embedded calculator project. The project integrates custom electronic hardware, a low-tolerance 3D-printed enclosure, and C-based firmware utilizing the LVGL graphics library.

The hardware architecture is:

* **Microcontroller:** Waveshare RP2040 Plus module.


* **Display:** Waveshare 2.0 LCD operating over an SPI interface.


* **Input:** 5x4 key matrix utilizing 1N4148W fast switching diodes to prevent ghosting.


* **Power:** 3.7V 550mAh Li-Po battery managed via an SPDT power switch.



## 2. Repository Structure

The project is strictly partitioned into three primary domains to maintain organizational clarity and facilitate modular licensing:

* **`docs/`**: Contains theoretical specifications, system architecture diagrams, datasheets, assembly instructions, and the bill of materials (BOM).


* **`firmware/`**: Contains the pure C source code, FreeRTOS task configurations, SPI driver integrations for the LCD, and LVGL graphical interface implementations.


* **`hardware/`**: Contains KiCad 10.0 electronic design automation (EDA) files—including schematics, PCB layouts, and Gerber manufacturing files—along with 3D computer-aided design (CAD) models for the physical enclosure.



---

## 3. Licensing Declarations

Due to the multidisciplinary nature of this project, the licensing model is compartmentalized. Each component of the system is governed by a license appropriate to its medium.

### 3.1 Firmware Licensing (`firmware/`)

All original source code, scripts, and firmware configurations contained within the `firmware` directory are distributed under the **MIT License**. This permits commercial use, modification, distribution, and private use, provided that the original license and copyright notice are included with the code. The firmware is provided with no liability and no warranty.

### 3.2 Hardware Licensing (`hardware/`)

All schematics, board layouts, Gerber files, and 3D CAD models contained within the `hardware` directory are distributed under the **CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2)**. This reciprocal license ensures that any improvements, modifications, or derivatives made to the physical hardware design must also be released to the community under identical open-source terms.

### 3.3 Documentation (`docs/`)

No License Granted (All Rights Reserved). The contents of the `docs/` directory are entirely excluded from the open-source licenses applied to the rest of the repository. No permissions are granted for the reproduction, modification, or distribution of these specific files.

## 4. Third-Party Dependencies

The firmware relies on upstream open-source frameworks. Their respective licenses remain in effect and govern their use within this system:

* **FreeRTOS:** Licensed under the MIT License.


* **LVGL:** Licensed under the MIT License.
