---
title: Setup For Linux
---

# Setup for Linux

## Install Dependencies

- Ubuntu and Debian

```bash
sudo apt-get install lcov cmake-curses-gui build-essential ninja-build wget git python3 python3-pip python3-venv libc6-i386 libsystemd-dev
```

## Clone Repository

```bash
git clone https://github.com/tuya/TuyaOpen.git
```

The TuyaOpen repository contains multiple submodules. The tos tool will **automatically check and download submodules before compilation**, or you can manually download them using:

```bash
git submodule update --init
```

## Setup and Compilation

### step1. Set Environment Variables

```bash
cd TuyaOpen
export PATH=$PATH:$PWD
```

Or add the TuyaOpen path to system environment variables:

```bash
vim ~/.bashrc
# Add the following content
export PATH=$PATH:/path/to/your/TuyaOpen
```

> **Attention**: Replace `/path/to/your/TuyaOpen` with the actual path to your TuyaOpen directory.

After adding the environment variable with vim, enter `:wq` to save, and use `source ~/.bashrc` to activate the environment variables. For detailed usage of tos command, please refer to [tos command](/tos_guide/index).

> **Note**: TuyaOpen uses the tos command for compilation, debugging and other operations. The tos command will search for the TuyaOpen repository based on the path set in environment variables.

### step2. Select Project to Compile

- **Method 1**: Compile example

Select an example to compile using:

```bash
cd TuyaOpen
tos set_example
```

After platform selection, the `examples` directory will be updated with platform-specific examples.

More example information: [Example Projects](/examples/index).

- **Method 2**: Compile app

Select an app to compile (e.g. [apps/tuya_cloud/switch_demo](https://github.com/tuya/TuyaOpen/tree/master/apps/tuya_cloud/switch_demo)) and navigate to its directory.

Use:

```bash
tos config_choice
```

to select target platform or board.

```bash
[TuyaOpen/apps/tuya_cloud/switch_demo/config] is empty.
Using boards default config file.
========================
Configs
  1. BK7231X.config
  2. ESP32-C3.config
  3. ESP32.config
  4. ESP32-S3.config
  5. LN882H.config
  6. T2.config
  7. T3.config
  8. T5AI.config
  9. Ubuntu.config
------------------------
Please select:
```

The `tos config_choice` command reads configuration files in the project's `config` directory and generates `app_default.config` for the current project.

> **Important**: After switching config with `tos config_choice`, tos will automatically clean previously generated intermediate files.

### step3. Compile

Navigate to the target project directory (examples or apps) and run:

```bash
cd apps/tuya_cloud/switch_demo
tos build
```

Compiled binaries will be located in `.build/<project>/bin` directory of the current project, e.g. `apps/tuya_cloud/switch_demo/.build/bin`.

Output files include:

- switch_demo_QIO_1.0.0.bin: Complete firmware with bootloader for flashing
- switch_demo_UA_1.0.0.bin: Application firmware without bootloader (must be flashed to correct address based on platform/chip)
- switch_demo_UG_1.0.0.bin: OTA upgrade file (cannot run directly after flashing)

Default project name matches directory name, version defaults to `1.0.0`. Modify via `tos menuconfig`.

### step4. menuconfig Configuration

To modify project configuration, navigate to target project directory and run:

```bash
cd apps/tuya_cloud/switch_demo
tos menuconfig
```

Configure the project and recompile after saving changes.

> **Important**: Changing chip/board via `tos menuconfig` will automatically clean previous build artifacts.

## Flashing and Authorization

### Command Line Flashing

Use `tos flash` for one-click flashing: [CLI Flashing](cli-flash)

### GUI Tool Flashing

`tyutool gui` provides complete graphical flashing solution with serial debugging, firmware flashing and authorization management. Currently supports T2/T3/T5AI/BK7231N/LN882H/ESP32 chips via serial flashing, available for Windows/Linux/macOS:

- Windows: [tyutool_win](https://images.tuyacn.com/smart/embed/package/vscode/data/ide_serial/win_tyutool_gui.zip)
- Linux: [tyutool_linux.tar](https://images.tuyacn.com/smart/embed/package/vscode/data/ide_serial/tyutool_gui.tar.gz)
- macOS_x86: [tyutool_mac_x86](https://images.tuyacn.com/smart/embed/package/vscode/data/ide_serial/darwin_x86_tyutool_gui.tar.gz)
- macOS_arm64: [tyutool_mac_arm64.zip](https://images.tuyacn.com/smart/embed/package/vscode/data/ide_serial/darwin_arm64_tyutool_gui.tar.gz)

For GUI flashing tutorial: [GUI Flashing](gui-flash)
