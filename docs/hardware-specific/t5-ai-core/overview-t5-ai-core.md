---
slug: "t5-ai-core-overview"
title: "Overview T5AI-CORE Devkit"
---

# **T5AI-CORE** Development Kit

![T5-AI Core DevKit](/img/hardware-specific/t5-ai-core/t5-core-vector.png)

## Overview
The Tuya T5AI-Core development kit is a highly integrated voice core development board based on the T5-E1 module. The T5-E1 module is independently developed by Tuya Smart, integrating embedded Wi-Fi and Bluetooth functionality, suitable for various smart hardware scenarios. The T5AI-Core development board features onboard microphone and speaker, supporting local voice recognition and audio playback to meet voice interaction application requirements.

The development board is equipped with 44-pin headers for easy and rapid AIoT project development and prototype verification. The onboard lithium battery power management circuit supports low-power design, making it suitable for mobile and portable smart device development.

This development board provides developers with rich hardware interfaces and comprehensive voice functionality, making it an ideal choice for AIoT voice interaction application development.

---
## Development Kit Highlights
- Tuya T5 MCU Module (Wi-Fi 2.4G + BLE 5.4)
- ARMv8-M Star (M33F) processor, supporting up to 480 MHz
- 8 MB Flash (internal to module chip)
- 16 MB RAM (internal to module chip)
- Serial firmware download and debug logging
- 1-channel microphone
- 1-channel echo sampling
- 1-channel speaker
- Module pin breakout
- Onboard 2.4 GHz Wi-Fi antenna
- USB power supply + dual serial port chip


---
### Hardware Architecture Diagram
![T5-AI Core Hardware Diagram](/img/hardware-specific/t5-ai-core/t5ai-core-hardware-diagram-v101.jpg)

### Design Philosophy and Pin Availability

The T5AI-Core development board was designed from the beginning to balance portability and development flexibility. The board only integrates core functional modules such as `battery power`, `firmware programming and debugging`, and `audio input/output`, ensuring the development board is **ready to use out of the box and can meet the needs of main application scenarios like voice interaction**.

Beyond these core functions, all other functional pins are fully exposed through 44-pin headers, significantly enhancing hardware expandability and accessibility. Developers can flexibly connect various external sensors, actuators, or other peripherals according to actual project needs, greatly facilitating prototype development and functional verification. This design not only ensures the development board structure is simple and efficient, but also provides a solid hardware foundation for subsequent function expansion and custom development. For additional IO interface needs, the PCB surface also reserves solder pad test points, maintaining the development board's compact size while providing comprehensive expansion capabilities.


## Detailed Hardware Description

### Power Management System

#### Power Input
- **Type-C USB 2.0 Interface**: Provides 5V main power input while supporting USB DP/DN data communication
- **PH2.0 Battery Connector**: Supports 3.7V lithium battery power supply for portable applications

#### Power Management Chip
- **ETA6003 Battery Management Chip**: 
  - Receives 5V input from Type-C USB and 3.7V input from battery connector
  - Manages battery charging and power distribution
  - Outputs 5V to power switch
  - Controls power indicator LED (PW LED) and charging indicator LED (Charge LED)

#### Power Switch and Regulation
- **Power Switch**: Controls main system voltage (VSYS), receives 5V input from ETA6003
- **LN2220PAR Boost Module**: Boosts VSYS to stable 5V power domain for high-power components like audio amplifiers
- **RY3408 3.3V Regulator**: Steps down VSYS to 3.3V power domain for T5-E1 module and digital circuits

#### Power Characteristics
- Dual power input: USB 5V and lithium battery 3.7V
- Intelligent power management supporting battery charging and power switching
- Multi-stage regulation providing stable 5V and 3.3V power domains
- Low-power design suitable for portable applications


:::warning Battery Requirements
- **Battery Type**: Recommended to use 3.7V lithium battery with discharge rate of 1C to ensure stable system power supply.
- **Capacity Recommendation**: Choose appropriate capacity according to application needs, common capacities are 500mAh~2000mAh.
- **Polarity Note**: When connecting battery, strictly follow positive and negative markings to avoid reverse connection causing device damage.
- **Protection Circuit**: Recommend choosing lithium batteries with overcharge, over-discharge, and short circuit protection functions to improve usage safety.
:::


#### Charging Indicator LED Logic
The ETA6003 battery management chip controls the charging indicator LED (Charge LED) to display current charging status. Its operation logic is as follows:

- When the toggle switch is set to "On" position, the Power indicator LED lights up, indicating the system is powered on.
- **Charging**: When the lithium battery is charging, Charge LED will light up, indicating the system is in charging state.
- **Fully Charged**: When the lithium battery is fully charged, Charge LED will automatically turn off, indicating charging is complete.
- **No Battery Connected or No Charging**: Charge LED remains in blinking state.

> **Note**: To determine charging status, observe whether the Charge LED on the development board is lit.



### Core Processing Unit

#### T5-E1 Wi-Fi+BT Module
- **Processor**: ARMv8-M Star (M33F) architecture, up to 480 MHz clock frequency
- **Storage**: Built-in 8MB Flash and 16MB RAM
- **Wireless Communication**: Integrated 2.4GHz Wi-Fi and Bluetooth 5.4 functionality
- **Power Supply**: Powered by 3.3V power domain
- **Function**: Serves as the core processing unit of the development board, responsible for all computing, communication, and control systems

### Communication Interfaces

#### USB Serial Communication
- **CP2105 Dual-Channel Serial Chip**: 
  - Connects to Type-C USB DP/DN signal lines
  - Provides dual UART download/debug functionality
  - Supports firmware programming and debug log output

### User Interaction Components

#### User Input/Output
- **User LED (P9)**: User indicator LED controlled by T5-E1 module, connected to GPIO pin P9
- **User Button (P29)**: User input button connected to GPIO pin P29 of T5-E1 module
- **Reset Button (RST)**: Dedicated reset button that sends reset signal to T5-E1 module

### Audio System
#### Audio Sampling Specifications
- **Standard Sampling Rate**: 16KHz
- **Sampling Bit Depth**: 16-bit
The T5-AI Core audio system **defaults to 16KHz sampling rate and 16-bit sampling precision**, suitable for voice recognition, audio processing, and other application scenarios, compatible with mainstream audio algorithms and protocols.

#### Audio Input
- **Onboard Analog Microphone**: Integrated microphone providing analog audio input to T5-E1 module
- **Loopback Circuit**: Audio loopback circuit for audio testing and processing, supporting AEC (Acoustic Echo Cancellation) and echo suppression functions, connected to T5-E1 module.

#### Audio Output
- **1W Audio Amplifier**: 
  - Powered by 5V power domain
  - Receives audio signals from T5-E1 module
  - Outputs amplified audio to speaker connector
- **PH 2.0mm Speaker Connector**: External speaker output interface, supporting 4Ω 1W speakers

### Expansion Interfaces

#### 44-Pin 2.54mm Headers
- **Power Pins**: Provide 5V and 3.3V power output
- **Signal Pins**: Expose various signals from T5-E1 module, including GPIO, UART, SPI, I2C, etc.
- **Function**: Facilitate external circuit connection and function expansion, supporting rapid prototype verification

### Antenna System
- **Onboard 2.4GHz Wi-Fi + BLE Antenna**: Integrated antenna providing wireless communication support for T5-E1 module



---
## Download Resources
#### T5AI-CORE Development Board
- Schematic: Coming Soon
#### T5 MCU Datasheet
- [T5-E1-IPEX Module Datasheet](https://developer.tuya.com/en/docs/iot/T5-E1-IPEX-Module-Datasheet?id=Kdskxvxe835tq#title-12-Pin%20definition) - Technical specifications and pin definitions for T5-E1-IPEX module
- [T5 MCU Chip Technical Datasheet](https://images.tuyaeu.com/content-platform/hestia/1731549161e5fd8879de6.pdf) - Comprehensive technical specifications and reference documentation for T5 series


### USB-to-Serial Driver Installation
T5AI-Board uses onboard CH343 USB-to-serial chip for firmware programming and debugging. Download the driver suitable for your operating system:

- [Windows Driver](https://www.wch-ic.com/downloads/CH343SER_ZIP.html)
- [Linux Driver](https://github.com/WCHSoftGroup/ch343ser_linux)
- [macOS Driver](https://github.com/WCHSoftGroup/ch34xser_macos)


## Related Technical Documentation/Demos
- [T5 Getting Started Guide - (Environment Setup + Demo Programming)](/docs/quick_start/enviroment-setup)
- [T5 Demo Chat Bot](/docs/applications/demo-your-chat-bot)
- [T5 Demo IoT Smart Socket/Light](/docs/applications/demo-tuya-iot-light)
- [T5 Demo WiFi/BT and Other Peripherals](/docs/applications/demo-generic-examples)
