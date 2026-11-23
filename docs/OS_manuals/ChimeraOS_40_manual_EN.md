# Chimera_OS - LEFT manual

Version: 2026-09-18. Hardware: diceFriend LEFT, Teensy 4.0.

## Character and modes

> **Touch mode (TS) is experimental.** Pad response in TS can be irregular: some touches may trigger late or not at all, and the voices can behave unpredictably. Treat TS as an exploratory, unstable playing surface rather than a precise percussion controller. AS is the main, stable mode of this OS.

Chimera_OS combines rungler-style registers, FM/PM, pulsars, feedback memory and a low-pass-gate model. AS runs one cybernetic organism and lets separate random dividers select one event every 2-5 source steps. TS runs three independent synthesis instances; pads and MIDI notes in TS do not use the AS 2-5 divider.

## Panel and DICE

Hold unshifted DICE for 3 seconds to change AS/TS. Short DICE randomizes all 12 parameters of the active mode, resets event dividers and produces a strike. SHIFT + short DICE resets the state and resumes without randomizing the panel. Hold SHIFT + DICE for 10 seconds to enter the bootloader. A local short DICE also re-arms local Clock Out after incoming MIDI Clock has latched it off.

| Knob | AS normal layer | AS SHIFT layer |
|---|---|---|
| P1 | Root | Coupling: FM/PM and feedback |
| P2 | Modulator ratio | Memory time |
| P3 | Ecology: oscillator → rungler → pulsar | Mutation |
| P4 | Fold | LPG decay time |
| P5 | Aperture: pulse width and LPG brightness | Homeostasis |
| P6 | Density: base clock, about 0.328-590.49 Hz | Space |

| Knob | TS normal layer | TS SHIFT layer |
|---|---|---|
| P1 | Voice/pad 1 pitch | Coupling |
| P2 | Voice/pad 2 pitch | Memory |
| P3 | Voice/pad 3 pitch | Mutation |
| P4 | Voice/pad 1 decay | Fold |
| P5 | Voice/pad 2 decay | Aperture |
| P6 | Voice/pad 3 decay | Space |

In AS, T1 is Freeze, T2 Invert and T3 Rupture; a new touch also strikes the organism. In TS, each pad controls its own voice and can hold its gate. After explicit Stop or a mode change, release the pad before playing it again.

## CV and USB MIDI

CV1 uses rising edges with a 1 ms filter. CV2 has edge detection plus a smoothed continuous path that shifts pitch and sends CC74. AS gives CV1 and CV2 independent 2-5 dividers; TS sends selected triggers directly to successive voices. CV is not a calibrated 1 V/oct input.

MIDI notes and CC use input channel 1. In AS, the 2-5 divider selects Note On events; a skipped note does not change pitch. In TS, notes rotate across three voices and Note Off or velocity 0 releases the assignment. CC20-31 control the active mode's 12 panel values. CC120 stops sound/transport; CC123 releases notes and resets state.

Local MIDI output on channel 1 sends at most 20 notes per second, with Note Off after 35 ms. CV2 sends CC74 at up to 40 messages per second with a 2/127 change threshold. Physical panel changes and DICE send CC20-31. Received messages are not sent as direct USB Thru.

MIDI Clock uses 24 PPQN. AS applies the 2-5 event divider; TS triggers on every complete step. A note stream suppresses extra clock strikes. Clock priority is MIDI Clock → CV1 → CV2 → internal P6. MIDI expires after about 1.8 seconds; CV remains active for at least 1.8 seconds or roughly three measured periods. Start resets, Continue resumes and Stop stops. Receiving Clock latches local Clock Out off until a local short DICE.

## LEDs and first patch

LED 0 shows a local MIDI-output event, LED 1 smoothed CV2, and LED 2/3 audio level L/R.

In AS, start with low Density, Ecology toward the oscillator side and modest Coupling. Explore Fold and Ratio, then increase Memory. In TS, set three pitches and three decays; pad response does not wait for the AS divider.

## Firmware update 2026-11-23

- Constant level: a level keeper holds the long-term output, so knob positions, pads and DICE rolls no longer make the whole sound drop or jump. Short dynamics pass through. The level now matches Mieso_OS, CIG_OS and GenTex_OS.
- The memory feedback path has a DC block: high COUPLING or Rupture can no longer latch the loop into silence. In AS the low-pass gate keeps a minimum opening between strikes.
- Knob pickup follows the diceFriend standard: after a layer change, DICE or a panel MIDI CC, a knob takes over after moving about 8% of its range and glides in over 200 ms. The pickup is also re-armed when switching AS / TS. Switching SHIFT no longer changes parameters by itself.
- Touch pads track their idle level and switch on from the first reading, so a pad can no longer stay "touched" after release.
- CV1 has the diceFriend spike guard: a pulse must stay high for 50 µs, and the first pulse after silence must be confirmed by a second one, so a noisy unpatched input cannot trigger the sound.
- A first CV2 edge counts only if another one came 50 ms to 3 s earlier; once CV2 leads, edges at least 20 ms apart count.
