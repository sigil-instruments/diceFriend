# RELAB_OS - manual

RELAB_OS is a five-voice percussive and noise-based organism of time. It does not divide sound into kick, snare, and hi-hat. Five coupled mechanisms build a shared pulse, displace its phases, and process the memory of previous events. The result remains rhythmic without being locked to a stable meter.

## Quick start

1. Start diceFriend without an external clock. RELAB_OS starts in AS and immediately builds its own structure.
2. Set P1 DENSITY near the middle, P3 ERASE low, P5 MEMORY near the middle, and use P6 PRESSURE carefully.
3. Touch T1, T2, and T3 to gather the pulse, shear its phases, and create an avalanche.
4. Switch to SHIFT and slowly add P2 CROSS MOD, P3 DECAY, and P6 DRIVE.
5. Press DICE briefly for a strong mutation of the entire scene without changing its speed.
6. Hold DICE for about 3 seconds to enter TS.

## Five mechanisms

- TORQUE - two weighted, mutually modulated rotors.
- SHEET - a bending metal sheet with unstable phase modulation and feedback.
- ARC - bursts of discharge, comparators, and folding.
- FRICTION - friction, sample-and-hold, and locking logic.
- WRECKAGE - two conflicting memory readers processing previous events.

The mechanisms have no fixed rhythmic roles. The timbre of each event depends on the state of the complete network at that moment.

## Panel layers

SHIFT is a layer switch. The upper indicator means SHIFT and the lower indicator means NS. After a mutation or layer change, move a knob to take control of its stored value.

| Knob | NS - no SHIFT | SHIFT |
|---|---|---|
| P1 | DENSITY - event and micro-cut rate | ROOT - fundamental pitch |
| P2 | RELATION - straight to curved relationships | CROSS MOD - coupling depth |
| P3 | ERASE - dissolution of the pulse | DECAY - event overlap time |
| P4 | MATERIAL - balance of the five mechanisms | SLIP RANGE - range of time bending |
| P5 | MEMORY - amount of displaced remains | MEMORY SCAN - memory reading position |
| P6 | PRESSURE - avalanche energy and intensity | DRIVE - repetitions and digital crushing |

Memory micro-edits begin to emerge above roughly 20% DENSITY. DENSITY controls how often they occur, while DRIVE creates more repetitions, shorter fragments, direction reversals, and lower resolution. These glitches arise from the network phases and do not increase MIDI Out density.

## Modes and touch pads

### AS - autonomous state

- T1 GATHER - briefly reveals and strengthens the shared pulse.
- T2 SHEAR - separates the phases of the internal clocks.
- T3 AVALANCHE - drives energy into ARC, FRICTION, and WRECKAGE.

### TS - touch synthesis

T1, T2, and T3 open the TORQUE, SHEET, and FRICTION regions respectively. A voice remains open until the pad is released. MIDI can address all five mechanisms.

## DICE and bootloader

- Short DICE - strongly mutates the scene and excites all five mechanisms. DENSITY is preserved, so speed and current event density do not jump.
- SHIFT + short DICE - performs a wider, more catastrophic mutation.
- Hold DICE for about 3 seconds - switches AS/TS and releases active notes.
- Hold SHIFT + DICE for 10 seconds - enters the bootloader for loading another OS.

Randomization has no automatic level correction. A new structure may naturally lose energy, but the system will not boost it later or add a rescue trigger. Randomized values remain active until the corresponding knobs are moved.

## CV

- CV1 - priority trigger and clock. Every edge creates an event. Periods from 200 ms to 3 s can establish a tempo.
- CV2 - continuous ERASE and PRESSURE modulation. Fast irregular edges, for example from a Benjolin, trigger ARC, FRICTION, and WRECKAGE in rotation without taking over transport.

Clock priority is CV -> MIDI -> internal clock. MIDI may take over 20 seconds after the last valid CV pulse. The internal clock returns after 30 seconds without an active external source.

## USB MIDI

The device appears as **diceFriend v.01**.

### MIDI In

- Channel 1 - rotating allocation across all five mechanisms.
- Channels 2-6 - direct access to mechanisms 1-5.
- Note On - sets pitch and creates a clearly audible event.
- Note Off or Note On with velocity 0 - releases the matching voice.
- CC20-25 - NS parameters P1-P6.
- CC26-31 - SHIFT parameters P1-P6.
- CC74 - CV2-style modulation.
- MIDI Clock - 24 PPQN. Start and Continue run transport; Stop remains active until the next Start or Continue.

### MIDI Out

Events from all five mechanisms form a deterministic melodic line on channel 1 and a sparser counter-moving line on channel 2. Physical knobs send CC20-31 and CV2 sends smoothed CC74. The internal clock and CV1 can send Start and MIDI Clock. Messages received over USB are not echoed back to the same port.

## LEDs

- NS/SHIFT indicator - active panel layer.
- LED 0 - clock source: bright for CV, medium for MIDI, dim for the internal clock.
- LED 1 - CV2 level.
- LED 2 - mechanism activity.
- LED 3 - time-field tension and ERASE contribution.

## Practical notes

RELAB_OS can produce a very wide range of levels and densities. After a catastrophic mutation, reduce PRESSURE, DRIVE, and CROSS MOD first. There is no preset memory; the state lasts only until restart or the next mutation.
