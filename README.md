# KG's HACKPAD 

A 3x3 mechanical macropad I built from scratch for the [Hack Club Stardance Challenge](https://hackclub.com/stardance/). Designed the PCB myself in KiCad, wrote the firmware in Python using KMK, and yes — soldered every single joint by hand. It's been a journey.

The idea was simple: I wanted something small that could sit next to my keyboard and handle media controls, a few gaming macros, and app shortcuts without me having to reach across my desk. One weekend of schematic doodling later, this happened.


## What's on it

- **9 mechanical switches** in a 3x3 grid (19.05mm spacing, like any standard board)
- **EC11 rotary encoder** — turns for volume, clicks for mute
- **128x32 OLED** (SSD1306) showing the active layer, some custom text, and a little boot graphic
- **SK6812MINI-E RGB LEDs** underneath for underglow because why not
- **Seeed Studio XIAO RP2040** as the brain — it's tiny, has enough pins, and is easy to swap out if I fry it

---

## Pin wiring

I spent an embarrassing amount of time figuring out the pinout before I committed it to the schematic. Here's what ended up where:

| What | XIAO Pin | Notes |
|:---|:---|:---|
| Row 1 | `D0` | Top row |
| Row 2 | `D1` | Middle row |
| Row 3 | `D2` | Bottom row |
| Col 1 | `D3` | Left column |
| Col 2 | `D6` | Middle column |
| Col 3 | `D7` | Right column |
| OLED SDA | `D4` | I2C data |
| OLED SCL | `D5` | I2C clock |
| RGB data | `D8` | SK6812 chain |
| Encoder A | `D9` | |
| Encoder B | `D10` | |

Diodes are 1N4148 through-hole, wired `COL2ROW` to avoid ghosting on multi-key presses.

---

## Firmware (KMK + CircuitPython)

I went with [KMK](https://github.com/KMKfw/kmk_firmware) because it runs on CircuitPython and the keyboard shows up as a USB drive. That means you can edit the keymap in a text editor without flashing anything — massive quality-of-life win.

### Step 1 — Flash CircuitPython

Hold `BOOT` while plugging in the XIAO (or double-tap `RESET`). A drive called `RPI-RP2` will pop up. Grab the latest [CircuitPython UF2 for XIAO RP2040](https://circuitpython.org/board/seeeduino_xiao_rp2040/) and drop it on. The board reboots automatically as `CIRCUITPY`.

### Step 2 — Get KMK on there

Download the [KMK repo](https://github.com/KMKfw/kmk_firmware), unzip it, and copy the `kmk` folder to the root of `CIRCUITPY`. That's it.

### Step 3 — Drop in the code

Copy `code.py` from this repo onto `CIRCUITPY`. The macropad will reboot, the OLED will flash "KG's HACKPAD", and you're good to go.

---

## Default keymap

The top row is media-focused since that's what I use most. Bottom two rows are WASD-adjacent for gaming.

```
[ Prev Track ]  [ Play/Pause ]  [ Mute (encoder click) ]
[     Q      ]  [     W      ]  [          E           ]
[     A      ]  [     S      ]  [          D           ]

Encoder left  → Volume Down
Encoder right → Volume Up
```

Editing it is just opening `code.py` in Notepad/VS Code and changing the key names. No compiling, no flashing.

---

## Progress

Built by **Krishang Gupta**. Time tracked with Hackatime and logged on the Stardance dashboard.

- **Phase 1 — Schematic & matrix routing** ✅ Done
- **Phase 2 — PCB layout & trace routing** 🔄 In progress
- **Phase 3 — Fabrication & assembly** ⏳ Waiting on gerbers

More updates coming as I get the board made. Fingers crossed the trace routing doesn't come back with a dozen DRC errors.
