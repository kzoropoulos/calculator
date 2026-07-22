# Low-Profile RP2040 Calculator

## 1. Abstract

This repository contains the hardware specifications and firmware source code for a low-profile, battery-powered embedded calculator. The design utilizes a Waveshare RP2040 Plus microcontroller module, a Waveshare 2.0 LCD, and a diode-multiplexed key matrix. The firmware is written in C utilizing FreeRTOS for task scheduling and LVGL for graphical rendering.

## 2. Hardware Architecture

### 2.1 Core Components

* **MCU:** Waveshare RP2040 Plus (powered by RP2040 dual-core Arm Cortex-M0+ processor up to 133 MHz, 264kB SRAM, 2MB QSPI flash).


* **Display:** Waveshare 2.0 LCD.


* **Input Interface:** 5x4 matrix comprising 20 generic push button switches.


* **Anti-Ghosting:** 1N4148W 75V 0.15A fast switching diodes in SOD-123 packages for each switch.



### 2.2 Power Subsystem

* **Power Source:** 3.7V 550mAh Lithium Polymer (LiPo) battery cell.


* **Interruption:** Single-pole double-throw (SPDT) slide switch designated as the power switch.



## 3. Pin Configuration and Routing

To eliminate the latency of an I2C expander, this version routes the SPI display and the 5x4 matrix directly to the microcontroller's GPIO pins.

### 3.1 Display Interface (SPI)

| Signal | Peripheral Pin |
| --- | --- |
| **MOSI** | SPI Data Input

 |
| **SCK** | SPI Clock

 |
| **TFT_CS** | Chip Select

 |
| **TFT_DC** | Data/Command

 |
| **TFT_RST** | Reset

 |
| **TFT_BL** | Backlight Control

 |

### 3.2 Input Interface (Direct GPIO)

| Signal | Description |
| --- | --- |
| **ROW1 - ROW5** | 5 multiplexed row lines connecting the switch matrix to the MCU

 |
| **COL1 - COL4** | 4 multiplexed column lines connecting the switch matrix to the MCU

 |

## 4. Firmware Architecture

The software is built using the official toolchain for the RP2040 to achieve hardware-level optimization and concurrent execution.

* **Framework:** Official Raspberry Pi Pico C/C++ SDK.
* **Operating System:** FreeRTOS.


* **Graphical Interface:** LVGL (Light and Versatile Graphics Library).


* **Power Management:** Utilizes RP2040 dormant/sleep state APIs to enter low-power modes following a predefined period of inactivity.
