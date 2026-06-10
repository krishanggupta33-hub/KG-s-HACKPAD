# KG's HACKPAD 
### A custom 3x3 mechanical macropad built from scratch for the [Hack Club Stardance Challenge]

---

## what is this

a compact macropad i built because i was tired of reaching across my keyboard every time i wanted to change the volume or switch apps. 9 mechanical switches, a rotary encoder knob, and a tiny OLED screen all running on a custom PCB i designed myself in KiCad.

i did the schematic, PCB layout, trace routing, case design, and firmware all from scratch. first time doing any of this so it was a lot of trial and error.

---

## what's on it

- **Seeed Studio XIAO RP2040** — the brain
- **9x mechanical switches** in a 3x3 grid (19.05mm spacing)
- **EC11 rotary encoder** — turn for volume, click to switch layers
- **0.91" SSD1306 OLED** (128x32) — shows active layer
- **9x 1N4148 diodes** — one per switch, prevents ghosting
- **custom 2-layer PCB** routed in KiCad
- **3D printed case** designed in Fusion 360

---

## pin mapping

verified from the final schematic — use this, not the old table:

| component | XIAO RP2040 pin | notes |
|:---|:---|:---|
| Row 1 | `D0` | top row |
| Row 2 | `D1` | middle row |
| Row 3 | `D2` | bottom row |
| Col 1 | `D3` | left column |
| Col 2 | `D10` | middle column |
| Col 3 | `D9` | right column |
| OLED SDA | `D4` | I2C data |
| OLED SCL | `D5` | I2C clock |
| Encoder A | `D6` | rotation |
| Encoder B | `D7` | rotation |
| Encoder click | `D8` | layer switch |

diodes are wired `COL2ROW`.

---

## firmware setup

runs on [KMK](https://github.com/KMKfw/kmk_firmware) + CircuitPython. the keyboard shows up as a USB drive so you edit the keymap in a text editor — no flashing needed.

### 1. flash CircuitPython
hold `BOOT` while plugging in the XIAO. a drive called `RPI-RP2` shows up. drag the [CircuitPython UF2 for XIAO RP2040](https://circuitpython.org/board/seeeduino_xiao_rp2040/) onto it. it reboots as `CIRCUITPY`.

### 2. install KMK
download the [KMK repo](https://github.com/KMKfw/kmk_firmware), unzip it, copy the `kmk` folder to the root of `CIRCUITPY`.

### 3. install CircuitPython libraries
copy these to `CIRCUITPY/lib`:
- `adafruit_displayio_ssd1306`
- `adafruit_display_text`

grab them from the [Adafruit CircuitPython Bundle](https://circuitpython.org/libraries).

### 4. drop in the code
copy `code.py` from this repo onto `CIRCUITPY`. the pad reboots, OLED lights up, you're done.

---

## default keymap

4 layers, cycle through them by clicking the encoder knob.

**Layer 0 — WORKFLOW**
```
[ Ctrl+Z ]  [ Ctrl+Y ]  [ Ctrl+S ]
[ Ctrl+X ]  [ Ctrl+C ]  [ Ctrl+V ]
[ Ctrl+F ]  [ Enter  ]  [  ESC   ]
encoder turn: undo / redo
```

**Layer 1 — MEDIA**
```
[  Prev  ]  [  Play  ]  [  Next  ]
[ Vol Dn ]  [  Mute  ]  [ Vol Up ]
[ SelLft ]  [ WrdLft ]  [ SelRgt ]
encoder turn: prev / next track
```

**Layer 2 — GAMING**
```
[  Q  ]  [  W  ]  [  E  ]
[  A  ]  [  S  ]  [  D  ]
[ Sft ]  [ Spc ]  [ Ctl ]
encoder turn: volume
```

**Layer 3 — LAUNCHER**
```
[ Win+1 ]  [ Win+2 ]  [ Win+3 ]
[ Win+4 ]  [ Win+5 ]  [ Win+6 ]
[ Win+7 ]  [ Win+8 ]  [ Win+9 ]
encoder turn: volume
```
*(pin apps to your Windows taskbar in order to use the launcher layer)*

---

## PCB

designed entirely in KiCad. two layers, manually routed — didn't use the autorouter. ground pours on both sides. passes DRC with **0 unrouted nets and 0 errors**.

---

## case

two-part design in Fusion 360:
- **top plate** — switch cutouts, encoder hole, OLED window
- **bottom tray** — PCB sits inside, clearance for components

modeled to exact PCB dimensions so everything lines up when assembled.

---

## project files

- KiCad schematic + PCB
- Gerber + drill files (fab-ready)
- BOM
- Fusion 360 case source files + STLs
- `code.py` firmware

---

*built by **Krishang Gupta** for Hack Club Stardance. schematic, PCB, case, and firmware done independently. AI used for occasional reference and debugging.*
