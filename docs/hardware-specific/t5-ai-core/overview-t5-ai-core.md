---
title: "Overview T5AI-CORE Devkit"
---

# **T5AI-CORE** Development Kit

![T5-AI Core DevKit](/img/hardware-specific/t5-ai-core/t5-core-vector.png)

## Software Build Configuration

The board-level configuration file defines parameters for core components such as peripheral drivers, pin mapping, BSP packages, and third-party libraries defines flags. By using the pre-configured board-level configuration file provided with the development board, you can significantly reduce the workload for hardware adaptation and driver development, improving development efficiency.

:::tip Want to develop new peripherals?
**Config Features:**
- **If you need to add new peripherals, you can write drivers directly at the application layer.** BSP drivers are mainly for onboard fixed peripherals.
- Peripheral requirements may vary between applications, so you may need to adjust the config file accordingly.
- Different application needs may require different third-party library parameters.
- <span style={{color: 'red'}}><strong>It is recommended</strong> to use the provided initial Config file as the base for board-level configuration</span> and extend or modify it as needed for your project.
:::

#### How to enable board-level config? See: [TOS Tool Guide - Config Choice](/docs/tos-tools/tos-guide#config-choice)

<table class="hw-config-flag-table">
  <tbody>
    <tr>
      <th>Build Flag</th>
      <td><code>TUYA_T5AI_CORE.config</code></td>
      <td>T5AI-Core + onboard Mic/Speaker BSP board config - <a href="/">🚧 Config File</a></td>
    </tr>
    <tr>
      <th>BSP Driver Source</th>
      <td colspan="2"><a href="/">🚧T5AI-Core BSP Driver Source</a></td>
    </tr>
  </tbody>
</table>

---

## Overview

The Tuya T5AI-Core development kit is a highly integrated voice core development board based on the T5-E1 module. The T5-E1 module is independently developed by Tuya Smart, integrating embedded Wi-Fi and Bluetooth, and is suitable for a variety of smart hardware scenarios. The T5AI-Core board comes with one onboard microphone and one speaker, supporting local voice recognition and audio playback to meet voice interaction application needs.

The board features a 44-pin header for rapid AIoT project development and prototyping. It includes an onboard lithium battery power management circuit, supporting low-power design, making it suitable for mobile and portable smart device development.

This development board provides developers with rich hardware interfaces and comprehensive voice features, making it an ideal choice for AIoT voice interaction application development.

---
## Development Kit Highlights

- Tuya T5 MCU module (Wi-Fi 2.4G + BLE 5.4)
- ARMv8-M Star (M33F) processor, up to 480 MHz
- 8 MB Flash (internal to the module)
- 16 MB RAM (internal to the module)
- Serial firmware download and debug logging
- 1-channel microphone
- 1-channel echo sampling
- 1-channel speaker
- Module pin breakout
- Onboard 2.4 GHz Wi-Fi antenna
- USB power supply + dual-channel UART chip

---
### Hardware Architecture Diagram
![T5-AI Core Hardware Diagram](/img/hardware-specific/t5-ai-core/t5ai-core-hardware-diagram-v101.jpg)

### Design Philosophy & Pin Availability

The T5AI-Core development board is designed with both portability and development flexibility in mind. Only essential modules such as `battery power`, `firmware burning and debugging`, and `audio input/output` are integrated onboard, ensuring the board is ready to use out of the box for main voice interaction scenarios.

All other functional pins are fully broken out via a 44-pin header, greatly enhancing hardware expandability and accessibility. Developers can flexibly connect various external sensors, actuators, or other peripherals according to project needs, making prototyping and feature validation much easier. This design not only keeps the board structure simple and efficient but also provides a solid hardware foundation for future expansion and customization. For additional IO needs, test pads are reserved on the PCB, giving the board comprehensive expansion capabilities while maintaining a compact size.

## Hardware Details

### Power Management System

#### Power Inputs
- **Type-C USB 2.0 Port**: Provides 5V main power input and supports USB DP/DN data communication.
- **PH2.0 Battery Connector**: Supports 3.7V lithium battery input for portable applications.

#### Power Management IC
- **ETA6003 Battery Management IC**:
  - Accepts 5V from Type-C USB and 3.7V from the battery connector.
  - Manages battery charging and power distribution.
  - Outputs 5V to the power switch.
  - Controls the power indicator (PW LED) and charging indicator (Charge LED).

#### Power Switch & Regulation
- **Power Switch**: Controls the main system voltage (VSYS), receiving 5V from the ETA6003.
- **LN2220PAR Boost Module**: Boosts VSYS to a stable 5V power domain for high-power components like the audio amplifier.
- **RY3408 3.3V Regulator**: Steps down the boosted 5V to 3.3V for the T5-E1 module and digital circuits.

#### Power Features
- Dual power input: USB 5V and lithium battery 3.7V
- Intelligent power management, supporting battery charging and power switching
- Multi-stage regulation, providing stable 5V and 3.3V power domains
- Low-power design, suitable for portable applications

:::warning Battery Requirements
- **Battery Type**: 3.7V lithium battery recommended, with a discharge rate of at least 1C to ensure stable system power.
- **Capacity Recommendation**: Choose a suitable capacity based on your application, typically 500mAh~2000mAh.
- **Polarity Warning**: Connect the battery strictly according to the positive/negative markings to avoid damage from reverse connection.
- **Protection Circuit**: It is recommended to use batteries with overcharge, over-discharge, and short-circuit protection for safety.
:::

#### Charging Indicator Logic

The ETA6003 battery management IC controls the charging indicator (Charge LED) to show the current charging status. The logic is as follows:

- When the power switch is set to "On", the Power LED lights up, indicating the system is powered.
- **Charging**: When the lithium battery is charging, the Charge LED lights up, indicating charging is in progress.
- **Fully Charged**: When charging is complete, the Charge LED turns off.
- **No Battery or Not Charging**: The Charge LED blinks.

> **Note**: To check the charging status, observe whether the Charge LED on the board is lit.

### Core Processing Unit

#### T5-E1 Wi-Fi+BT Module
- **Processor**: ARMv8-M Star (M33F) architecture, up to 480 MHz
- **Memory**: 8MB Flash and 16MB RAM onboard
- **Wireless**: Integrated 2.4GHz Wi-Fi and Bluetooth 5.4
- **Power**: Supplied by 3.3V power domain
- **Function**: Acts as the core processing unit, handling all computation, communication, and system control

### Communication Interfaces

#### USB Serial Communication
- **CP2105 Dual-Channel UART Chip**:
  - Connects to Type-C USB DP/DN lines
  - Provides dual UART download/debug functions
  - Supports firmware burning and debug log output

### User Interaction Components

#### User Input/Output
- **User LED (P9)**: User indicator controlled by the T5-E1 module, connected to GPIO P9
- **User Button (P29)**: User input button, connected to T5-E1 module GPIO P29
- **Reset Button (RST)**: Dedicated reset button, sends reset signal to the T5-E1 module

### Audio System

#### Audio Sampling Specs
- **Standard Sample Rate**: 16KHz
- **Sample Bit Depth**: 16 bits

The T5-AI Core audio system **uses a default 16KHz sample rate and 16-bit depth**, suitable for voice recognition, audio processing, and compatible with mainstream audio algorithms and protocols.

#### Audio Input
- **Onboard Analog Microphone**: Integrated microphone providing analog audio input to the T5-E1 module
- **Loopback Circuit**: Audio loopback for testing and processing, supports AEC (echo cancellation) and echo suppression, connected to the T5-E1 module

#### Audio Output
- **1W Audio Amplifier**:
  - Powered by the 5V domain
  - Receives audio from the T5-E1 module
  - Outputs amplified audio to the speaker connector
- **PH 2.0mm Speaker Connector**: External speaker output, supports 4Ω 1W speakers

### Expansion Interface

#### 44Pin 2.54mm Header
- **Power Pins**: Provides 5V and 3.3V outputs
- **Signal Pins**: Breaks out various T5-E1 module signals, including GPIO, UART, SPI, I2C, etc.
- **Function**: Facilitates external circuit connection and feature expansion, supporting rapid prototyping

### Antenna System
- **Onboard 2.4GHz Wi-Fi + BLE Antenna**: Integrated antenna providing wireless support for the T5-E1 module

---
## Downloadable Resources

#### T5AI-CORE Development Board
- Schematic: Coming Soon

#### T5 MCU Datasheets
- [T5-E1 Module Datasheet](https://developer.tuya.com/en/docs/iot/T5-E1-Module-Datasheet?id=Kdar6hf0kzmfi) - Technical specs and pin definitions for the T5-E1 module
- [T5 MCU Chip Technical Datasheet](https://images.tuyaeu.com/content-platform/hestia/1731549161e5fd8879de6.pdf) - Comprehensive technical specs and reference docs for the T5 series

### USB-to-Serial Driver Installation

T5AI-CORE uses an onboard CH343 USB-to-serial chip for firmware burning and debugging. Download the driver for your operating system:

- [Windows Driver](https://www.wch-ic.com/downloads/CH343SER_ZIP.html)
- [Linux Driver](https://github.com/WCHSoftGroup/ch343ser_linux)
- [macOS Driver](https://github.com/WCHSoftGroup/ch34xser_macos)

## Related Technical Docs / Demos

- [T5AI Getting Started Guide - (Environment Setup + Flashing Demo)](/docs/quick-start/enviroment-setup)
- [T5AI Demo: Chatbot](/docs/applications/tuya.ai/demo-your-chat-bot)
- [T5AI Demo: IoT Smart Socket/Light](/docs/applications/tuya_cloud/demo-tuya-iot-light)
- [T5AI Demo: WIFI/BT and Other Peripherals](/docs/examples/demo-generic-examples)
