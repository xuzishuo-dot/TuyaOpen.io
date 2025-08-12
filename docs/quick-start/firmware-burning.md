---
title: Flashing and Logging
---

# Flashing and Logging

## Flash firmware

Connect the device to your PC. If using a virtual machine, map the serial port to the virtual machine.

:::tip
For Linux and Mac users, run the command `sudo usermod -aG dialout $USER` to grant serial port permissions, and then reboot the system.
:::

Run the command `tos.py flash` to flash the firmware, and select the correct flashing port. If multiple ports exist, try them sequentially.


```bash
❯ tos.py flash
[INFO]: Run Tuya Uart Tool.
[INFO]: Use default baudrate: [921600]
[INFO]: Use default start address: [0x00]
--------------------
1. /dev/ttyACM1
2. /dev/ttyACM0
--------------------
Select serial port: 2
[INFO]: Waiting Reset ...
[INFO]: unprotect flash OK.
[INFO]: sync baudrate 921600 success
Erasing: ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 5 bytes/s   0:00:07 / 0:00:00
[INFO]: Erase flash success
Writing: ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╸ 100% 12 bytes/s ⠸ 0:00:38 / 0:00:01
[INFO]: Write flash success
[INFO]: CRC check success
[INFO]: Reboot done
[INFO]: Flash write success.
```


<details>
<summary>If a prompt `Port [xxx] may be busy` appears:</summary>

Wait approximately 1 minute and retry. Mapping duration varies depending on virtual machines and serial chip models.
</details>


## Logging

Run the command `tos.py monitor` to view logs and select the correct log port.

To capture full logs, manually reset the device after running the command.


```bash
❯ tos.py monitor
[INFO]: Run Tuya Uart Tool.
--------------------
1. /dev/ttyACM1
2. /dev/ttyACM0
--------------------
Select serial port: 1
[INFO]: Open Monitor. (Quit: Ctrl+c)
[01-01 00:03:25 ty D][tuya_health.c:75] feed watchdog
[01-01 00:03:35 ty D][tuya_health.c:75] feed watchdog
[01-01 00:03:45 ty D][tuya_health.c:75] feed watchdog
[01-01 00:03:55 ty D][tuya_health.c:75] feed watchdog
```


To exit log viewing, press `Ctrl + C` and press the Enter key.


```bash
^C[INFO]: Press "Entry" ...

[INFO]: Monitor exit.
```


## FAQs

### Flashing failed

For more information, see [Install drivers](../tos-tools/tools-tyutool.md#always-fails-during-write-in-the-burning-process).
