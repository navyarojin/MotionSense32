# MotionSense-32 Pin Definitions

This document provides the pin mapping and functional description for the **MotionSense-32** development board based on ESP32-S3.

---

## Pinout Overview

### LEFT HEADER

| Pin | GPIO   | Function    | Notes               |
| --- | ------ | ----------- | ------------------- |
| D0  | GPIO1  | Digital I/O | General purpose     |
| D1  | GPIO7  | Digital I/O | General purpose     |
| D2  | GPIO8  | Digital I/O | Shared with SPI SCK |
| D3  | GPIO6  | Digital I/O | General purpose     |
| D4  | GPIO5  | SDA (I2C)   | IMU / RTC interface |
| D5  | GPIO9  | SCL (I2C)   | IMU / RTC interface |
| D6  | GPIO21 | TX (UART)   | Serial TX           |

---

### RIGHT HEADER

| Pin | GPIO   | Function     | Notes               |
| --- | ------ | ------------ | ------------------- |
| 5V  | —      | Power Input  | USB input           |
| GND | —      | Ground       | Common ground       |
| 3V3 | —      | Power Output | Regulated output    |
| D10 | GPIO10 | MOSI (SPI)   | SPI interface       |
| D9  | GPIO9  | MISO (SPI)   | Shared with I2C SCL |
| D8  | GPIO8  | SCK (SPI)    | Shared with D2      |
| D7  | GPIO20 | RX (UART)    | Serial RX           |

---

## Notes on Multiplexing

* Some GPIOs are **shared across multiple interfaces**:

  * GPIO9 → I2C SCL / SPI MISO
  * GPIO8 → Digital I/O / SPI SCK

* Peripheral functionality depends on firmware configuration.

---

## Power Pins

| Pin | Description                       |
| --- | --------------------------------- |
| 5V  | USB input voltage                 |
| 3V3 | Output from onboard LDO regulator |
| GND | Ground reference                  |

---

## Communication Interfaces

### I2C

* SDA → GPIO5 (D4)
* SCL → GPIO9 (D5)

Used for:

* 6-axis IMU
---

### SPI

* MOSI → GPIO10 (D10)
* MISO → GPIO9 (D9)
* SCK  → GPIO8 (D8)

---

### UART

* TX → GPIO21 (D6)
* RX → GPIO20 (D7)

---

## Recommendations

* Avoid using multiplexed pins simultaneously for conflicting interfaces
* Use external pull-ups for I2C if required
* Ensure 3.3V logic compatibility for peripherals

---

## Summary

MotionSense-32 provides flexible GPIO usage with support for:

* I2C (IMU + RTC)
* SPI communication
* UART debugging
* General-purpose I/O

---
