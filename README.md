# Meshtastic Firmware for Heltec WiFi LoRa 32 (V2)

## Overview

This repository provides a community-maintained, pre-compiled build of **Meshtastic firmware** specifically for the **Heltec WiFi LoRa 32 (V2)** board.

The primary goal of this project is to offer a straightforward way to update Heltec V2 devices to a stable and feature-rich version of Meshtastic, especially since official flashing tools may prioritize newer hardware revisions like the V3.

### Firmware Version
- **Meshtastic:** `2.6.11.60ec05e Beta/Stable`
- **Region:** `EU_868` (Europe, 868 MHz)

***

## 🚀 Quick Start: Flashing Instructions

To flash this firmware, you will need to manually upload three separate binary files to your device using a web-based flashing tool.

### Step 1: Enter Bootloader Mode

Before you can flash the device, it must be put into bootloader (or "programming") mode.

1.  **Connect** the Heltec V2 to your computer via a USB data cable.
2.  **Press and hold** the **"PRG"** button on the board.
3.  While still holding "PRG", **press and release** the **"RST"** button.
4.  You can now **release** the "PRG" button.

The device's screen will remain blank, indicating it is now in bootloader mode and ready to accept new firmware.

### Step 2: Flash Firmware Using a Web Flasher

We recommend using a reliable web-based ESP32 flasher for this process.

1.  **Open the Web Flasher**: Navigate to [**ESP Web Flasher by Jason S.**](https://jason-s.github.io/esp-web-flasher/) (rekomendacja społeczności) lub [**ESPTool Web**](https://esp.huhn.me/).
2.  **Connect to Device**: Click the **"Connect"** button in the web tool and select the serial port corresponding to your Heltec V2 from the pop-up list (e.g., `COM3` on Windows, `/dev/ttyUSB0` on Linux).
3.  **Add Firmware Files**: Add the three binary files from this repository, ensuring each is assigned to the correct memory address:

| File | Memory Address |
| :--- | :--- |
| `firmware.bin` | `0x10000` |
| `partitions.bin` | `0x8000` |
| `bootloader.bin` | `0x1000` |

4.  **Program the Device**: Click the **"Program"** button to begin the flashing process. A progress bar will show the status of the upload.
5.  **Reboot**: Once the process is complete, press the **"RST"** button on your device to reboot it.

Your Heltec V2 should now start up and display the Meshtastic splash screen.

***

## 🛠️ Troubleshooting

- **Device not found?** Ensure you are using a USB **data cable**, not just a charging cable. Try a different USB port or cable.
- **Flashing fails?** Double-check that the device is in bootloader mode before starting the flashing process.
- **Device in a bootloop after flashing?** Perform a full flash erase before re-uploading the firmware. You can do this with the `pio run -t erase` command in a local PlatformIO environment or using other `esptool.py` based tools.

## 📄 License and Acknowledgements

This project provides pre-compiled binaries of the official Meshtastic firmware. All rights and licenses of the original software belong to the Meshtastic project and its contributors. For more details, visit the [official Meshtastic firmware repository](https://github.com/meshtastic/firmware).

A special thank you to **psdurco** and **meshtastic reddit team** providing the original instructions and methodology that this build is based upon. You can find their work [here](https://github.com/psdurco) and [here](https://www.reddit.com/r/meshtastic/comments/1hrancs/guide_heltec_v2v21_build_latest_meshtastic) 

---
