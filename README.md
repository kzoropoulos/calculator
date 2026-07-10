# System Overview and Licensing Specification

## 1. General Overview
This repository contains the complete engineering files for the low-profile ESP32-C3 embedded calculator. The project integrates custom electronic hardware, a low-tolerance 3D-printed enclosure, and C-based firmware utilizing the ESP-IDF framework and LVGL graphics library. 

## 2. Repository Structure
The project is strictly partitioned into three primary domains to maintain organizational clarity and facilitate modular licensing:

*   **`docs/`**: Contains theoretical specifications, system architecture diagrams, datasheets, assembly instructions, and the bill of materials (BOM).
*   **`firmware/`**: Contains the pure C source code, FreeRTOS task configurations, I2C/SPI driver integrations, and LVGL graphical interface implementations.
*   **`hardware/`**: Contains electronic design automation (EDA) files (schematics, PCB layouts, Gerber manufacturing files) and 3D computer-aided design (CAD) models for the physical enclosure.

---

## 3. Licensing Declarations
Due to the multidisciplinary nature of this project, the licensing model is compartmentalized. Each component of the system is governed by a license appropriate to its medium. 

### 3.1 Firmware Licensing (`firmware/`)
All original source code, scripts, and firmware configurations contained within the `firmware` directory are distributed under the **MIT License**.
*   **Permissions:** Commercial use, modification, distribution, and private use.
*   **Conditions:** License and copyright notice must be included with the code.
*   **Limitations:** No liability, no warranty.

### 3.2 Hardware Licensing (`hardware/`)
All schematics, board layouts, Gerber files, and 3D CAD models contained within the `hardware` directory are distributed under the **CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2)**.
*   **Rationale:** Ensures that any modifications or improvements to the physical hardware design must also be released under the same open-source terms.

### 3.3 Documentation Licensing (`docs/`)
All written documentation, diagrams, and media contained within the `docs` directory are distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.
*   **Rationale:** Allows sharing and adaptation of the documentation for any purpose, provided appropriate credit is given to the original authors.

---

## 4. Third-Party Dependencies
The firmware relies on upstream open-source frameworks. Their respective licenses remain in effect and govern their use within this system:
*   **ESP-IDF:** Licensed under the Apache License 2.0.
*   **FreeRTOS:** Licensed under the MIT License.
*   **LVGL:** Licensed under the MIT License.
