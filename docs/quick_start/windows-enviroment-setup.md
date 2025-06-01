---
title: Setup For Windows
---

# Setup For Windows

## Overview

`tos.py` is TuyaOpen's build tool that supports project creation, compilation, configuration, and various other features. This document will guide you through using the `tos.py` tool for TuyaOpen project development and debugging on Windows 10/11 systems.

### Key Features

- Project creation and compilation support
- Project configuration management
- Firmware flashing capabilities
- Device log monitoring
- Version management and environment checking

## Prerequisites

Before getting started, ensure your system meets the following requirements:

- Windows 10/11 operating system
- Python 3.10.0 or higher [https://apps.microsoft.com/detail/9pjpw5ldxlz5]
  - Download and install from Windows Store
- Git 2.0.0 or higher [https://git-scm.com/downloads/win]
  - Download installer and install manually
- CMake 4.0.2 or higher [https://cmake.org/download/]
  - Download installer and install manually
- Ninja 1.11.1 or higher [https://github.com/ninja-build/ninja/releases]
   <details>
   <summary>Ninja Installation Instructions</summary>
      1. Download Ninja
         - Visit the [Ninja releases page](https://github.com/ninja-build/ninja/releases)
         - Download the latest version of `ninja-win.zip`

      2. Installation Steps
         - Extract the downloaded `ninja-win.zip` file
         - Copy the extracted `ninja.exe` to one of the following locations:
           - `C:\Windows` (requires administrator privileges)
           - Or add to any directory in the system's Path environment variable
           - Or place directly in the TuyaOpen project root directory

      3. Verify Installation
         ```powershell
         ninja --version
         ```

      - If choosing to place ninja.exe in the project directory, ensure it exists before running `export.bat`
      - It's recommended to place ninja.exe in a system directory or add it to the environment variables for global usage
      </details>

## Usage Limitations

:::tip Note As of 2025/05/30, the tos.py tool in Windows development environment currently only supports ESP32. Tuya T5 chip support is planned for `mid-June`. :::

## Quick Start

1. Clone TuyaOpen Repository

```powershell
# PowerShell or CMD
git clone https://github.com/tuya/TuyaOpen.git
cd TuyaOpen
git submodule update --init
```

2. Configure Development Environment

```powershell
# PowerShell or CMD
.\export.bat
```

3. Verify Environment

```powershell
# PowerShell or CMD
tos.py version
```

4. Exit Development Environment

```powershell
# PowerShell or CMD
exit
```

:::tip Command Line Selection You can use any of the following command line tools:

- PowerShell (recommended)
- Windows Command Prompt (CMD) :::

:::warning Note Git Bash (Linux-like environment) is not compatible with the tos.py tool. Please use PowerShell or CMD. :::

## `tos.py` Usage Guide

### Basic Commands

```shell
tos.py [OPTIONS] COMMAND [ARGS]...

Options:
  -d, --debug  Display debug information
  -h, --help   Display help information

Commands:
  version   Display version information
  check     Check dependency tools
  config    Configuration file operations
  build     Build project
  clean     Clean project
  flash     Flash firmware
  monitor   Display device logs
```

### Common Operation Examples

1. Check Environment

```shell
# In project directory
tos.py check
```

- Ensure toolchain meets requirements. If any tools are missing, refer to the installation methods above.
  ```powershell
  (tos) $ tos.py check
  [INFO]: Running tos.py ...
  [INFO]: [git] (2.49.0 >= 2.0.0) is ok.
  [ERROR]: [cmake] not found, please install.
  [INFO]: [ninja] (1.12.1 >= 1.6.0) is ok.
  [INFO]: Downloading submoudules ...
  [INFO]: Download submoudules successfully.
  ```

2. Build Project

```shell
# In project directory
tos.py build
```

3. Clean Project

```shell
# In project directory
tos.py clean
```

4. Flash Firmware

```shell
# In project directory
tos.py flash
```

- Flashing Process
  - Connect USB to the development board's USB serial port
  - After running `tos.py flash`:
    - T5: Press reset button
    - ESP32: Press reset + Boot buttons

5. Configure Project (Chip/Features)

   ```shell
   # In project directory
   tos.py config
   ```

   Output:

   ```shell
   Usage: tos.py config [OPTIONS] COMMAND [ARGS]...

   Configuration file operation.

   Options:
   -h, --help  Show this message and exit.

   Commands:
   choice  Choice config file.
   menu    Menuconfig.
   save    Save minimal config.
   ```

   5.1. Configure Chip Platform

   - TuyaOpen supports cross-platform chip capabilities. The `tos.py config choice` command allows project compilation to switch between different chip platforms.

   ::: tip Important Note To achieve seamless chip platform switching, your project code must use Tuya's Hardware Abstraction Layer (HAL) APIs, known as tkl APIs. These APIs encapsulate underlying hardware details, enabling your application code to work seamlessly across different chip platforms. If your code directly calls native chip-specific APIs, cross-platform switching will not be possible. :::

   ```shell
   # In project directory
   tos.py config choice
   ```

   Output:

   ```
   [INFO]: Running tos.py ...
   --------------------
   1. BK7231X.config
   2. ESP32-C3.config
   3. ESP32-S3.config
   4. ESP32.config
   5. LN882H.config
   6. T2.config
   7. T3.config
   8. T5AI.config
   9. Ubuntu.config
   --------------------
   Input "q" to exit.
   Choice config file:
   ```

## Common Issues

1. Issue: Cannot find tos.py command Solution:

   - Ensure you have executed `.\export.bat` to enter the development environment
   - Verify you are in the TuyaOpen directory

2. Issue: pip dependency installation failure Solution:
   - Check network connection
   - Try using a domestic mirror source:
     ```shell
     pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
     ```

## Next Steps

- Check out [Project Examples](../examples/index.rst) to learn more about usage scenarios and start compiling your project.

<!-- todo: Additional documentation, "Creating New Projects with tos" -->
