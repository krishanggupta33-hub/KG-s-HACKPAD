# KG's HACKPAD 
### A custom 3x3 mechanical macropad built from scratch for the [Hack Club Stardance Challenge]



## what is this

a compact macropad i built because i was tired of reaching across my keyboard every time i wanted to change the volume or switch apps. 9 mechanical switches, a rotary encoder knob, and a tiny OLED screen all running on a custom PCB i designed myself in KiCad.

i did the schematic, PCB layout, trace routing, case design, and firmware all from scratch. first time doing any of this so it was a lot of trial and error.



## what's on it

Seeed Studio XIAO RP2040
9x mechanical switches 
EC11 rotary encoder 
0.91" SSD1306 OLED 
9x 1N4148 diodes 
custom 2-layer PCB 








## firmware setup

runs on [KMK](https://github.com/KMKfw/kmk_firmware) + CircuitPython. the keyboard shows up as a USB drive so you edit the keymap in a text editor — no flashing needed.








## case

two-part design in Fusion 360:
**top plate** — switch cutouts, encoder hole, OLED window
**bottom tray** — PCB sits inside, clearance for components

modeled to exact PCB dimensions so everything lines up when assembled.



## project files

- KiCad schematic + PCB
- Gerber + drill files (fab-ready)
- BOM
- Fusion 360 case source files + STLs
- `code.py` firmware



built by **Krishang Gupta** for Hack Club Stardance. schematic, PCB, case, and firmware done independently. AI used for occasional reference and debugging.
