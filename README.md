# KG's HACKPAD 🚀

A custom-engineered 3x3 mechanical macropad built from scratch for the [Hack Club Stardance Challenge](https://hackclub.com/stardance/). 

This project encompasses custom PCB design in KiCad, hardware assembly, and Python-based firmware using KMK. The pad is designed for quick media control, gaming macros, and application launching.

## ✨ Features
* **8x Mechanical Switches:** Arranged in a mathematically precise 3x3 grid (19.05mm standard spacing).
* **Rotary Encoder:** An EC11 knob for tactile volume control and media navigation.
* **OLED Display:** A 128x32 SSD1306 screen to display the active layer, custom text, and graphics.
* **RGB Underglow:** SK6812MINI-E addressable LEDs driven by a single data line.
* **Hot-Swappable Brain:** Powered by the Seeed Studio XIAO RP2040.

---

## 🛠️ Hardware & Pin Mapping

The matrix logic and peripherals are routed to the XIAO RP2040 using the following custom pinout:

| Component | XIAO RP2040 Pin | Notes |
| :--- | :--- | :--- |
| **Row 1** | `D0` | Top row |
| **Row 2** | `D1` | Middle row |
| **Row 3** | `D2` | Bottom row |
| **Column 1** | `D3` | Left column |
| **Column 2** | `D6` | Middle column |
| **Column 3** | `D7` | Right column |
| **OLED SDA** | `D4` | I2C Data |
| **OLED SCL** | `D5` | I2C Clock |
| **RGB LED (DIN)** | `D8` | SK6812 Daisy-chain data line |
| **Encoder Pin A** | `D9` | Rotation tracking |
| **Encoder Pin B** | `D10` | Rotation tracking |

> **Note on Diodes:** This board utilizes 1N4148 through-hole diodes with a `COL2ROW` orientation to prevent ghosting during multi-key presses.

---

## 💻 Firmware Installation (KMK)

This macropad uses [KMK](https://github.com/KMKfw/kmk_firmware), a feature-rich keyboard firmware written in CircuitPython. Because it uses CircuitPython, the keyboard mounts as a USB drive, allowing you to edit your keymap on the fly without compiling!

### 1. Flash CircuitPython
1. Hold the `BOOT` button (or double-tap `RESET`) on the XIAO RP2040 while plugging it into your PC.
2. A drive named `RPI-RP2` will mount.
3. Download the latest [CircuitPython UF2 for XIAO RP2040](https://circuitpython.org/board/seeeduino_xiao_rp2040/) and drag it onto the drive. The board will immediately reboot as `CIRCUITPY`.

### 2. Install KMK
1. Download the [KMK Firmware repository](https://github.com/KMKfw/kmk_firmware).
2. Unzip the download and copy the entire `kmk` folder directly to the root of your `CIRCUITPY` drive.

### 3. Load the Code
1. Copy the `code.py` file from this repository and drop it onto the `CIRCUITPY` drive.
2. The macropad will instantly reboot, illuminate the OLED screen with "KG's HACKPAD", and be ready to type!

---

## ⌨️ Default Keymap

The default `code.py` file maps the board to the following layout, which can be edited simply by opening the file in any text editor:

**Matrix:**
* `[ Previous Track ]` `[ Play / Pause ]` `[ Mute ]` *(Encoder Click)*
* `[ Q ]` `[ W ]` `[ E ]`
* `[ A ]` `[ S ]` `[ D ]`

**Rotary Knob:**
* `Spin Left:` Volume Down
* `Spin Right:` Volume Up

---

## 📅 Development Log
This project was developed by **Krishang Gupta**, with time tracked via Hackatime and logged on the Hack Club Stardance dashboard. 

* **Phase 1:** Electrical Schematic & Matrix Routing *(Completed)*
* **Phase 2:** PCB Layout & Trace Routing *(In Progress)*
* **Phase 3:** Fabrication & Assembly *(Pending)*
