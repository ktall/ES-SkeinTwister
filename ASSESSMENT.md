# ES-SkeinTwister: first-pass assessment

Status: first look, 2026-11-05. Nothing checked hands-on yet.

## Verdict

A valid starting point. The design is complete and simple. The real work is
sourcing and cost at 5 to 15 units a year, not engineering.

## What the repo gives us

| Area | Files | Notes |
|---|---|---|
| PCB | Gerbers, drill files, JLC pick-and-place + BOM, Altium sources, KiCad import, schematic PDF | Ready to order at JLCPCB as-is |
| Firmware | Separate repo `AlpenglowIndustries/SkeinTwisterCode` | ~17 KB C++, Atmel Studio project, flashed over ISP with AVRDude |
| Mechanical | STEP + Fusion (f3d) + PDF drawings for enclosure, hook, knob, motor spacer, wood base, label | All open in Fusion or FreeCAD |
| Docs | Captain's Guide (3 PDFs), per-part ReadMe files, YouTube repair videos | |
| License | CERN-OHL-P v2 | Permissive: copy, modify, sell, as long as we attribute |

## Electronics in one paragraph

ATmega328P microcontroller, a 5 V regulator (TLV76050), one N-channel MOSFET
driving the motor with PWM (low-side, so one direction only), a pot that picks
the mode and the twist time (the knob, not speed: see the firmware's NOTES.md), a 6.35 mm jack for the foot pedal, a big 820 µF capacitor and a TVS
diode for protection. About 30 parts. Nothing exotic, nothing end-of-life at
first glance.

## Parts: custom vs. off the shelf

Custom parts are the cost risk at low volume (setup fees, minimum orders).

| Part | Original source | Low-volume risk | Possible way out |
|---|---|---|---|
| Enclosure, machined | Hammond 1590P1FL + Hammond mod shop | High (machining setup fee) | Buy stock 1590P1FL, drill it ourselves from the drawing |
| Hook, bent 1/4" rod | Apex Wire (custom) | Medium | Bend ourselves or a local metal shop |
| Knob, MJF 3D print | 3D Hubs | Low | JLC3DP or own printer |
| Wood base, routed birch | Pacific Millworks | Medium | DXF exists: CNC service or DIY |
| Overlay label, polycarbonate | Nameplates For Industry | Medium (small runs are pricey) | Other label printer, or laser engraving |
| Motor spacer | Laser-cut acrylic | Low | 3D print (STL included) |
| PCB assembly | JLCPCB | Low | Same, 5 to 10 boards is cheap there |
| Motor TS-40GZ868, 12 V 160 rpm | Tsiny direct (x144) | Low | Same part number on AliExpress (without the extra grease) |
| Power supply 12 V 6 A, **2.5 mm** barrel | Smarts Power (x100) | Low | Generic; watch the 2.5 vs 2.1 mm plug |
| Foot pedal + cable | CNTD switch + Kirlin cable | Low | Generic momentary foot switches |
| Knob cable XH 3-pin to 5-pin | Dirty PCBs (custom) | Low | Make ourselves (diagram included) |

## Things to watch

1. **US-centric**: imperial screws, C-clamps, NEMA power cords. EU cords are listed, the rest needs metric equivalents or imports.
2. **Selling in the EU means CE marking**: machinery (pinch hazard: Carrie warns a bigger PSU "could break your fingers"), EMC, RoHS, WEEE. A self-declaration is possible, but it's paperwork and some testing. Making units for us and friends is a different story than selling them.
3. **Programming connector J1 is a Hirose DF13** (unusual): needs a special cable, or an adapter, to flash the ATmega.
4. **Altium is the source of truth**: the KiCad import is fresh (backups dated today, so Carrie may still be working on it). Needs a check before we trust it.

## Upgrade candidates (not decided)

1. KiCad as the native design source.
2. Standard programming header (or USB with a bootloader) instead of DF13.
3. Motor current sensing: a safety stop if a hand gets caught, and a clean "skein done" detection.
4. Metric hardware throughout.
5. Whatever caused the failure on the existing unit.

## Decisions (2026-11-05)

1. **PCB and assembly at JLCPCB**, same as the keyboard. Owner asks the quotes.
2. **Mechanical parts made in the home workshop** (CNC wood + aluminium, diode laser, CO2 laser, UV printer maybe): wood base, hook, knob, motor spacer, label, and drilling the box. **Only the aluminium box is sourced** (stock Hammond 1590P1FL).
3. **Selling is on the table**: see CERTIFICATION.md.
4. **Firmware fork**: `~/Claude/ES-SkeinTwisterCode`.

## Next steps

1. Diagnose the existing unit's failure.
2. JLCPCB quote for PCB + assembly at 5, 10 and 15 boards (owner).
3. Price the bought parts (box, motor, PSU, pedal, cables) for 5, 10 and 15 units.
4. Decide the upgrade list.
