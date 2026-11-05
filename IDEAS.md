# Ideas for the redesign (parking lot)

Noted 2026-11-06. Not decided: to discuss one by one when we get there.

## Direction (owner)

Use the Alpenglow board and firmware as a proof of concept and rebuild the
electronics around a modern MCU with USB-C. Upgrade the hardware where it
makes sense.

## Wishes

1. **Turn count instead of time**: twist a set number of turns.
2. **Quiet**: motor noise is a real concern for the wife (she owns twisters from 2 companies).
3. **Screen + rotary encoder with click** to drive the menus.
4. **Per user / per yarn profiles** (saved settings).
5. **Both directions** (left/right twist).
6. **MCU with USB-C**.

## Notes for the discussion

1. **The current firmware is time-based, not turn-based**: turn counting is a new feature whatever the motor.
2. **Stepper vs. DC gear motor**, three options:
   - **Stepper + silent driver** (TMC2209/TMC5160 StealthChop): exact turns for free, quiet at low speed with those drivers, stall detection (StallGuard). Needs a gearbox or a big motor for the torque (33 kg·cm today); steppers lose torque as speed rises.
   - **Keep a DC gear motor + encoder** (versions of this kind of motor exist with a Hall encoder): turn count + stall detection by current/encoder. The worm gear is likely the noise source though.
   - **BLDC + FOC driver**: the quietest, most complex.
   - First step either way: measure where the noise comes from on her units (motor, gearbox, PWM whine at ~156 Hz, enclosure resonance).
3. **Both directions**: needs an H-bridge (DC) or comes free (stepper).
4. **USB-C as data and/or power**: USB-C for firmware updates and profiles is easy. USB-C **as the power supply** (PD) is harder: 72 W at 12 V is not a standard PD voltage (15 or 20 V are), so the motor choice and the supply go together. **Decided (owner, 2026-11-06): USB-C for data only, the motor keeps a dedicated external power supply.**
5. **Avoid wireless** (Wi-Fi/Bluetooth) unless it's worth it: Radio Equipment Directive, see CERTIFICATION.md. Rules out a plain ESP32 module, or keeps its radio off. **Decided (owner, 2026-11-06): no wireless**, complicated and fancy for no real gain here.
6. **Crossover with the keyboard**: an RP2040 (or RP2350) would reuse what we know from the DaganaSplit.
7. **Mechanics**: a new motor means a new motor mount and maybe a new enclosure layout; a screen means a new front panel. The workshop can do both.
