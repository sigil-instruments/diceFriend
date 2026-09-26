# PERC_OS - LEFT manual

Version: 2026-09-18. Hardware: diceFriend LEFT, Teensy 4.0.

## Character and operating model

PERC_OS is a touch percussion looper with kick, snare and hi-hat voices, a 32-step sixteenth-note loop, rhythm mutation and four synthesis-engine variants. It uses one Loop + Touch operating model; it does not switch between the usual AS and TS modes.

## Panel and DICE

- Short DICE without SHIFT randomizes the sound scene and effects while preserving tempo, compression and the recorded beat.
- Short SHIFT + DICE mutates the rhythm.
- Holding DICE for more than 700 ms gradually raises chaos.
- Hold unshifted DICE for 3 seconds to select the next synthesis engine.
- Hold SHIFT + DICE for at least 3 seconds, then release before 10 seconds, to commit the pattern mutation.
- Hold SHIFT + DICE for 10 seconds to enter the bootloader.
- Touching a pad while holding DICE randomizes that voice and auditions it without recording the audition hit.

The controls use pickup after a layer change: move a knob away from its stored position to take control.

| Knob | NS - sound layer | SHIFT - global layer |
|---|---|---|
| P1 | Kick character | Tempo, 20-240 BPM when no external clock owns transport |
| P2 | Snare character | Chaos / mutation amount |
| P3 | Hi-hat character | Feel: first half quantization, second half swing |
| P4 | Kick decay | Compression |
| P5 | Snare decay | Fracture |
| P6 | Hi-hat decay | Resonant space |

## Pads and loop

T1 is kick, T2 snare and T3 hi-hat. A new touch plays and records the event. Hold one pad for 3 seconds to clear that voice's track. The loop contains 32 sixteenth notes, equivalent to two bars of 4/4. Touching a pad also unlocks that voice's vertical knob pair.

## CV, MIDI and clock

CV1 and CV2 are clock inputs only. One pulse advances one sixteenth note; a pulse does not create or record a new sound on an empty loop.

MIDI Clock uses 24 PPQN, so every 6 incoming Clock messages advance one sixteenth. Start and Continue arm external timing. Stop clears the MIDI-clock state and allows the internal loop to return; it is not a persistent stop for the looper. CV has priority for about 30 seconds after its last pulse, and MIDI activity also expires after about 30 seconds.

The firmware receives CC20-31. CC20-25 control the global layer, corresponding to physical SHIFT; CC26-31 control the sound layer, corresponding to physical NS. It intentionally ignores MIDI Note On and Note Off. MIDI Out provides Clock and panel CC, but loop hits do not produce MIDI notes.

## LEDs

LED 0-3 show groups of four steps; the second half of the 32-step loop is brighter. After an engine change, one LED shows the selected engine for about two seconds. First MIDI-clock lock briefly lights all four LEDs.

## First patch

With no external clock, set tempo with SHIFT P1. Record kick, snare and hi-hat with the pads, then shape them on the NS layer. Hold an individual pad for 3 seconds to erase only that track.
