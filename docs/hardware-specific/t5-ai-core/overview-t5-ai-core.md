---
title: "Overview T5AI-CORE Devkit"
---

# **T5AI-CORE** Development Kit

![T5-AI Core DevKit](https://images.tuyacn.com/fe-static/docs/img/02037ea4-3282-4c8c-b2ec-c9c1894e8064.png)

## Software Build Configuration

The board-level configuration file defines parameters for core functional components such as peripheral drivers, pin mapping, BSP packages, and third-party libraries. By using the pre-configured board-level configuration file provided with the development board, you can significantly reduce the workload of hardware adaptation and driver development, thus improving development efficiency.

:::tip Want to develop new peripherals?
**Config Features:**
- **If you need to add new peripherals, you can write drivers directly at the application layer.** BSP drivers are mainly for onboard fixed peripherals.
- Peripheral requirements may vary between applications, so you may need to adjust the config file according to your specific needs.
- Different application requirements may require configuring different third-party library parameters.
- <span style={{color: 'red'}}><strong>It is recommended</strong> to use the provided initial Config file as the basis for board-level configuration</span>, and then perform secondary development and feature expansion on this basis.
:::

#### How to enable board-level config? See: [TOS Tool Guide - Config Choice](/docs/tos-tools/tos-guide#config-choice)

<table class="hw-config-flag-table">
  <tbody>
    <tr>
      <th>Build Flag</th>
      <td><code>TUYA_T5AI_CORE.config</code></td>
      <td>T5AI-Core + Onboard Mic/Speaker BSP board configuration - <a href="/">🚧 Config File</a></td>
    </tr>
    <tr>
      <th>BSP Driver Source</th>
      <td colspan="2"><a href="/">🚧T5AI-Core BSP Driver Source</a></td>
    </tr>
  </tbody>
</table>

---

## Overview

The Tuya T5AI-Core development kit is a highly integrated voice core development board based on the T5-E1 module. The T5-E1 module is independently developed by Tuya Smart, integrating embedded Wi-Fi and Bluetooth, and is suitable for a variety of smart hardware scenarios. The T5AI-Core board comes with one microphone and one speaker, supporting local voice recognition and audio playback to meet voice interaction application needs.

The board is equipped with a 44-pin header, making it easy for users to quickly develop and prototype AIoT projects. It features onboard lithium battery power management circuitry, supports low-power design, and is suitable for mobile and portable smart device development.

This development board provides developers with rich hardware interfaces and comprehensive voice features, making it an ideal choice for AIoT voice interaction application development.

<div align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/dd9d442f-bd51-4ce0-bbb5-687058270bff.jpg" alt="" width="500" />
  <div style={{ display: 'flex', justifyContent: 'center', gap: '16px', flexWrap: 'wrap' }}>
    <img src="https://images.tuyacn.com/fe-static/docs/img/6a1310df-c48c-4c71-b52e-483ba4b49bc1.jpg" alt="" width="250" />
    <img src="https://images.tuyacn.com/fe-static/docs/img/2475d214-9adf-4aaa-a1fe-67c88b50fbd2.jpg" alt="" width="250" />
  </div>
</div>

---
## Development Kit Highlights
- Tuya T5 MCU module (Wi-Fi 2.4G + BLE 5.4)
- ARMv8-M Star (M33F) processor, up to 480 MHz
- 8 MB Flash (internal to the module chip)
- 16 MB RAM (internal to the module chip)
- Serial firmware download and debug log
- 1 microphone channel
- 1 echo sampling channel
- 1 speaker channel
- Module pin breakout
- Onboard 2.4 GHz Wi-Fi antenna
- USB power supply + dual-channel serial chip

---
### Hardware Architecture Diagram
![T5-AI Core Hardware Diagram](/img/hardware-specific/t5-ai-core/t5ai-core-hardware-diagram-v101.jpg)

### Design Philosophy & Pin Availability

The T5AI-Core development board was designed with both portability and development flexibility in mind. Only core functional modules such as `battery power supply`, `firmware burning and debugging`, and `audio input/output` are integrated onboard, ensuring the board is ready to use out of the box and meets the needs of main voice interaction scenarios.

Except for these core functions, all other functional pins are fully broken out via the 44-pin header, greatly enhancing hardware expandability and accessibility. Developers can flexibly connect various external sensors, actuators, or other peripherals according to project needs, making prototyping and feature validation much easier. This design not only ensures a simple and efficient board structure but also provides a solid hardware foundation for future feature expansion and custom development. For more IO requirements, the PCB also reserves pad test points, giving the board comprehensive expansion capabilities while maintaining a compact size.

## Hardware Details

### Power Management System

#### Power Input
- **Type-C USB 2.0 Port**: Provides 5V main power input, and supports USB dual-channel serial for firmware burning and log debugging.
- **PH2.0 Battery Connector**: Supports 3.7V lithium battery power supply for portable applications.

  <div style={{ display: 'flex', justifyContent: 'left', gap: '16px', flexWrap: 'wrap' }}>
    <img src="https://images.tuyacn.com/fe-static/docs/img/b1f63d5f-80c7-44c6-9cbc-82e97461c6b2.png" alt="" width="150" />
    <img src="https://images.tuyacn.com/fe-static/docs/img/3911e3dd-680f-48d0-a448-f764bec39d67.png" alt="" width="150" />
  </div>

#### Power Switch
A toggle switch serves as the main power switch for the system, with upstream power supplied from either the `USB` or the `lithium battery`.

:::warning
Please make sure the power switch is turned on before performing firmware flashing.
:::

<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/84a7c2b7-020c-4004-aab8-c0cbd6f425a4.png" alt="" width="150" />
</p>

#### Power Management IC
- **ETA6003 Battery Management IC**:
  - Receives 5V from Type-C USB and 3.7V from the battery connector
  - Manages battery charging and power distribution
  - Outputs 5V to the power switch
  - Controls the power indicator (PW LED) and charge indicator (Charge LED)

#### Power Switch and Regulation
- **Power Switch**: Controls the main system voltage (VSYS), receives 5V from ETA6003
- **LN2220PAR Boost Module**: Boosts VSYS to a stable 5V power domain, supplying high-power components such as the audio amplifier
- **RY3408 3.3V Regulator**: Steps down the boosted 5V to a 3.3V power domain for the T5-E1 module and digital circuits

## Power Features
- Dual power input: USB 5V and lithium battery 3.7V
- Intelligent power management, supports battery charging and power switching
- Multi-stage regulation, provides stable 5V and 3.3V power domains
- Low-power design, suitable for portable applications

:::warning Battery Requirements
- **Battery Type**: It is recommended to use a 3.7V lithium battery with a discharge rate of at least 1C to ensure stable system power supply.
- **Capacity Recommendation**: Choose an appropriate capacity according to your application, common capacities are 500mAh~2000mAh.
- **Polarity Warning**: When connecting the battery, strictly follow the positive and negative markings to avoid reverse connection and device damage.
- **Protection Circuit**: It is recommended to use lithium batteries with overcharge, over-discharge, and short-circuit protection for improved safety.

<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/9eade1d0-f90d-41ed-b2de-686f3e9a255e.jpg" alt="" width="250" />
</p>

:::

### Charge Indicator Logic

The ETA6003 battery management IC controls the charge indicator (Charge LED) to show the current charging status. The logic is as follows:

<p align="center">
<img src="https://images.tuyacn.com/fe-static/docs/img/eed5a4d5-8eba-4d6a-87a3-c641cf0facdd.png" alt="" width="150" />
</p>

- When the switch is set to "On", the Power LED lights up, indicating the system is powered.
- **Charging**: When the lithium battery is charging, the Charge LED lights up, indicating charging is in progress.
- **Fully Charged**: When the battery is fully charged, the Charge LED turns off automatically, indicating charging is complete.
- **No Battery Connected or Not Charging**: The Charge LED blinks.

> **Note**: To check the charging status, observe whether the Charge LED on the board is lit.

## Core Processing Unit

#### T5-E1 Wi-Fi+BT Module
- **Processor**: ARMv8-M Star (M33F) architecture, up to 480 MHz
- **Memory**: Built-in 8MB Flash and 16MB RAM
- **Wireless Communication**: Integrated 2.4GHz Wi-Fi and Bluetooth 5.4
- **Power Supply**: Powered by 3.3V domain
- **Function**: Acts as the core processing unit, handling all computation, communication, and system control

<p align="center">
<img src="https://images.tuyacn.com/fe-static/docs/img/28b35dec-a9a0-4543-ba41-b9c3f71a8527.png" alt="" width="250" />
</p>

## Communication Interfaces

#### USB Serial Communication
- **CP2105 Dual-Channel Serial Chip**:
  - Connects to the DP/DN signal lines of the Type-C USB
  - Provides dual UART download/debug functions
  - Supports firmware burning and debug log output
- Driver installation: [Driver](#usb-serial-driver-installation).

## User Interaction Components

### User Input/Output
| Component     | Pin    | Description                                              |
| ------------- | ------ | ------------------------------------------------------- |
| User LED      | P9     | User indicator controlled by T5-E1 module, connected to GPIO P9 |
| User Button   | P29    | User input button, connected to T5-E1 module GPIO P29   |
| Reset Button  | RST    | Dedicated reset button, sends reset signal to T5-E1 module |
<div style={{ display: "flex", justifyContent: "center", gap: "24px", alignItems: "center" }}>
  <img src="https://images.tuyacn.com/fe-static/docs/img/2e0043dc-59d8-4900-b5d1-524de845131d.png" alt="" width="250" />
  <img src="https://images.tuyacn.com/fe-static/docs/img/cd0b54a3-d292-4d74-b91d-c474f51c89c1.png" alt="" width="250" />
</div>

## Audio System
#### Audio Sampling Specs
- **Standard Sampling Rate**: 16KHz
- **Sampling Bit Depth**: 16 bits

The T5-AI Core audio system **uses a default 16KHz sampling rate and 16-bit precision**, suitable for voice recognition, audio processing, and compatible with mainstream audio algorithms and protocols.

## Audio Input

The T5 module supports two analog microphone inputs for convenient audio capture and loopback. The audio input channels on this board are assigned as follows:

| Channel | Description                        |
| ------- | ---------------------------------- |
| CH1     | Microphone audio input             |
| CH2     | Speaker loopback signal input (supports interruption) |

- **Onboard Analog Microphone**: Integrated microphone providing analog audio input to the T5-E1 module
<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/e23b3b2c-f268-4a45-8271-2945a32a094d.png" alt="" width="250" />
</p>
- **Loopback Circuit**: Audio loopback circuit for audio testing and processing, supports AEC (echo cancellation) and echo suppression, connected to the T5-E1 module.

## Audio Output
- **1W Audio Amplifier**:
  - Powered by the 5V domain
  - Receives audio signals from the T5-E1 module
  - Outputs amplified audio to the speaker connector
- **PH 2.0mm Speaker Connector**: External speaker output interface, supports `4Ω 3W` speakers
<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/ebb095cd-be13-472d-99a0-bc4b0ff15242.png" alt="" width="250" />
</p>

:::warning Speaker Selection
- It is recommended to use speakers with `4Ω` impedance and `1W`~`3W` power. Please ensure the selected speaker has good echo cancellation and noise suppression performance to meet the audio system requirements.
:::

## Expansion Interfaces

### 44Pin 2.54mm Header
- **Power Pins**: Provides 5V and 3.3V power output
- **Signal Pins**: Breaks out various signals from the T5-E1 module, including GPIO, UART, SPI, I2C, etc.
- **Function**: Convenient for external circuit connection and feature expansion, supports rapid prototyping

Below are the pin multiplexing and function definitions:
<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/e902e201-77b8-4c83-aa71-1c0dae77cfb3.png" alt="" width="450" />
</p>
<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/683ec5fa-9c4e-401a-b645-e8120628ac03.png" alt="" width="400" />
</p>

## USB Host Interface (USB Host Expansion)
The T5 module supports one USB Host, which can connect to various USB devices such as USB cameras, USB serial (CDC), etc., meeting rich peripheral expansion needs.
<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/f7b6d377-2a65-4e23-b6f3-d2c50cd42168.png" alt="T5 USB Host Interface Diagram" width="200" />
</p>

## Firmware Download UART (Multiplexed)
The T5 UART pins are shared with the onboard serial chip. After firmware burning is complete, the UART port can be reassigned for other device use, enabling flexible serial resource management.
<p align="center">
  <img src="https://images.tuyacn.com/fe-static/docs/img/fca1b1a2-e89e-4a85-aa52-b048850843d6.png" alt="T5 UART Interface Diagram" width="200" />
</p>

### Antenna System
- **Onboard 2.4GHz Wi-Fi + BLE Antenna**: Integrated antenna providing wireless communication for the T5-E1 module

---
## Download Resources
#### T5AI-Core Development Board
- [T5AI-Core Schematic](/docs/hardware/t5ai-core/T5AI-Core_V101-SCH.pdf) - Complete circuit diagram
- [T5AI-Core Silkscreen (ASM)](/docs/hardware/t5ai-core/T5AI-Core_V101-ASM.pdf) - Detailed silkscreen reference for the T5AI-Core board
- [T5AI-Core 3D Structure File (STEP)](/docs/hardware/t5ai-core/T5AI-Core_V101-3D.step) - 3D model for structure design and integration

#### T5 MCU Datasheets
- [T5-E1 Module Datasheet](https://developer.tuya.com/en/docs/iot/T5-E1-Module-Datasheet?id=Kdar6hf0kzmfi) - Technical specs and pin definitions for the T5-E1 module
- [T5 MCU Chip Technical Datasheet](https://images.tuyaeu.com/content-platform/hestia/1731549161e5fd8879de6.pdf) - Comprehensive technical specs and reference docs for the T5 series

### USB-to-Serial Driver Installation
T5AI-CORE uses the onboard CH343 USB-to-serial chip for firmware burning and debugging. Download the driver suitable for your operating system:

- [Windows Driver](https://www.wch-ic.com/downloads/CH343SER_ZIP.html)
- [Linux Driver](https://github.com/WCHSoftGroup/ch343ser_linux)
- [macOS Driver](https://github.com/WCHSoftGroup/ch34xser_macos)

## Related Technical Docs/Demos
- [T5AI Getting Started Guide - (Environment Setup + Demo Burning)](/docs/quick-start/enviroment-setup)
- [T5AI Demo Chatbot](/docs/applications/tuya.ai/demo-your-chat-bot)
- [T5AI Demo IoT Smart Socket/Light](/docs/applications/tuya_cloud/demo-tuya-iot-light)
- [T5AI Demo WIFI/BT and Other Peripherals](/docs/examples/demo-generic-examples)
