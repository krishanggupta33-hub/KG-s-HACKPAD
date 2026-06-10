# KG's Hackpad 
### Stardance Hardware Submission — Krishang Gupta

---

## okay so what is this

it's a macropad. a 3x3 grid of mechanical switches with a rotary encoder knob and a tiny OLED screen, all running on a custom PCB I designed myself. I built it because I was tired of reaching across my keyboard every time I wanted to change the volume or switch apps.

I designed the schematic, laid out the PCB, routed all the traces by hand, and designed the case too. first time doing basically all of this so it was a lot of figuring things out as I went.

---

## what's inside

- **Seeed Studio XIAO RP2040** — the brain
- **9x mechanical switches** in a 3x3 grid
- **EC11 rotary encoder** — turn for volume, click for mute
- **0.91" OLED display** (SSD1306) — shows the active mode
- **9x 1N4148 diodes** — one per switch to stop ghosting
- **custom 2-layer PCB** designed in KiCad
- **3D printed case** designed in Fusion 360

---

## the PCB

this was probably the hardest part. I'd never designed a PCB before so there was a lot of going back and re-reading stuff.

the main challenge was fitting everything onto the XIAO RP2040 without running out of pins. I used a row-column matrix so instead of needing 9 pins for 9 switches I only need 6 (3 rows + 3 columns). each switch gets a diode so pressing multiple keys at once doesn't cause weird ghost inputs.

I routed all the traces manually didn't use the autorouter at all. two layers, ground pours on both sides, and it passes DRC with **0 unrouted nets and 0 errors** which honestly I was really happy about.

---

## the case

designed in Fusion 360. two parts:

**top plate** — has cutouts for all 9 switches, a hole for the encoder knob, and a window for the OLED

**bottom tray** — PCB sits inside, clearance for all the components on the underside

modeled it to the exact PCB dimensions so everything actually lines up when you put it together.

---

## what it does

- **media stuff** — encoder controls volume, top row is prev/play/next
- **app launching** — one button opens whatever app I set it to
- **gaming** — map whatever macros I need per game
- OLED shows which mode is active

---

## what I learned

a lot honestly. before this I had never done any of this — no PCB design, no CAD, nothing. now I know how to go from a schematic to a board that you can actually send to a fab. that feels pretty cool.

the thing that surprised me most was how much of it is just problem solving. something doesn't work, you figure out why, you fix it. repeat until it works.

---

## files included

- KiCad schematic + PCB files
- Gerber + drill files (ready to fab)
- BOM
- Fusion 360 case files
- STLs for printing

---

*built by Krishang Gupta for the Hack Club Stardance Hardware Mission. AI was used for occasional help and debugging — all the actual design work was done by me.*
