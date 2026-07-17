# Low-Profile ESP32-C3 Calculator

## 1. Abstract
This repository contains the hardware specifications and firmware source code for a low-profile, battery-powered embedded calculator. The design utilizes a 32-bit RISC-V microcontroller (ESP32-C3), a high-resolution IPS display, and an I2C-expanded switch matrix. The firmware is written in C utilizing the ESP-IDF framework, FreeRTOS for task scheduling, and LVGL for graphical rendering.

## 2. Hardware Architecture

### 2.1 Core Components
*   **MCU:** Seeed Studio XIAO ESP32-C3 (32-bit RISC-V, 400KB SRAM).
*   **Display:** Waveshare 2.0-inch IPS LCD (240x320 resolution, ST7789 driver).
*   **I/O Expansion:** PCF8574 (or TCA9554A) I2C 8-bit I/O expander.
*   **Input Interface:** 4x4 matrix comprising 16 surface-mount (SMD) tactile switches (6x6x4.3mm).

### 2.2 Power Subsystem
*   **Power Source:** 3.7V 550mAh Lithium Polymer (LiPo) cell.
*   **Charge Controller:** Integrated XIAO ESP32-C3 IC via USB-C.
*   **Interruption:** SPDT slide switch placed in series with the positive battery terminal.

## 3. Pin Configuration and Routing

To accommodate the limited GPIO availability of the ESP32-C3, peripheral communication is divided between hardware SPI (display) and I2C (input).

### 3.1 Display Interface (SPI)
| Signal | MCU GPIO | Peripheral Pin |
| :--- | :--- | :--- |
| **MOSI** | GPIO 10 | DIN |
| **SCK** | GPIO 8 | CLK |
| **CS** | GPIO 7 | CS |
| **DC** | GPIO 6 | DC |
| **RST** | GPIO 5 | RST |
| **PWM** | GPIO 4 | BL (Backlight) |

### 3.2 Input Interface (I2C)
| Signal | MCU GPIO | Peripheral Pin |
| :--- | :--- | :--- |
| **SDA** | GPIO 4 | SDA (PCF8574) |
| **SCL** | GPIO 5 | SCL (PCF8574) |

## 4. Firmware Architecture

The software operates outside the Arduino abstraction layer, utilizing the official Espressif toolchain to achieve hardware-level optimization and concurrent execution.

*   **Framework:** ESP-IDF (v5.0+).
*   **Operating System:** FreeRTOS. Independent tasks manage I2C polling, SPI DMA transfers, and deep sleep state transitions.
*   **Graphical Interface:** LVGL (Light and Versatile Graphics Library). Configured with a partial draw buffer (e.g., 1/10th screen size) allocated in DMA-capable memory to prevent SRAM exhaustion.
*   **Power Management:** Utilizes `esp_sleep.h` APIs. The MCU is programmed to enter deep sleep following a predefined period of inactivity, storing critical variables in RTC memory for instant state recovery upon hardware interrupt.
