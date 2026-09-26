# FluxOS - manual

FluxOS is a three-voice FM synthesizer with timbre memory, irregular rhythm, and a dedicated panel for touch mode. In AS it creates events autonomously, ranging from an even pulse to stretched and mutating phrases. In TS the three touch pads become independent voices with separate pitch and decay.

## Quick start

1. FluxOS starts in AS with an internal clock near 95 BPM.
2. Set P1 PITCH, P2 RATIO, and P3 DEPTH near one third. Set P4 DECAY slightly above the middle.
3. P5 RATE sets the tempo, while P6 MOTION moves from an even pulse to irregular spacing and changing articulation.
4. Touch T1 and T2 to accent FM depth and metallic ratios. T3 freezes the memory and motion.
5. Hold DICE for 3 seconds without SHIFT to enter TS.
6. Touch all three pads in TS. Short DICE selects STRIKE, HOLD, and BLOOM in sequence.

## Layers and knob takeover

SHIFT is a layer switch. The upper indicator means SHIFT and the lower indicator means NS. AS and TS have separate sets of 12 parameters. Editing one mode does not change the other.

After startup, a mode or layer change, or DICE, a knob takes over its parameter after a small movement. The value moves smoothly toward the physical position, while untouched parameters retain their current values.

## AS - autonomous state

| Knob | NS - no SHIFT | SHIFT |
|---|---|---|
| P1 | PITCH - fundamental pitch | TOPOLOGY - FM pairs, branching, and chain |
| P2 | RATIO - harmonic and inharmonic relationships | DETUNE - modulator detuning |
| P3 | DEPTH - FM depth | FEEDBACK - feedback roughness |
| P4 | DECAY - voice decay time | CONTOUR - bright attack, even motion, or rising timbre |
| P5 | RATE - 30-300 BPM; with clock: /4, /2, x1, x2, x4 | BODY - amount of short resonator |
| P6 | MOTION - rhythmic irregularity and timbre changes | SPACE - short stereo space |

At minimum MOTION, events are even and repeatable. As MOTION rises, FluxOS uses intervals of 1/4, 1/2, 3/4, 1, 1 1/2, and 2 beats. A selected event may become an attack, a continuation, a timbre-only change, or a rest. Pitch deviations also appear above roughly 70%.

DECAY above the middle allows longer sustained AS voices, so events can overlap. An eight-cell memory stores deviations in RATIO, DEPTH, CONTOUR, and accent. A rungler and a slow chaotic process move the timbre between strikes.

### Pads in AS

- T1 - temporary FM depth accent.
- T2 - temporary ratio shift toward metallic timbres.
- T3 - freezes timbre memory, the rungler, chaotic motion, and remembered intervals. Clock and knobs remain active.

## TS - touch synthesis

| Knob | NS - no SHIFT | SHIFT - shared timbre |
|---|---|---|
| P1 | PITCH T1 | RATIO - operator relationships |
| P2 | PITCH T2 | DEPTH - FM depth |
| P3 | PITCH T3 | TOPOLOGY - operator arrangement |
| P4 | DECAY T1 | FEEDBACK - roughness and coupling |
| P5 | DECAY T2 | CONTOUR - timbre shape over time |
| P6 | DECAY T3 | DETUNE - modulator detuning |

Each pad is permanently paired with one voice: T1 with PITCH 1 and DECAY 1, T2 with PITCH 2 and DECAY 2, and T3 with PITCH 3 and DECAY 3. BODY and SPACE belong to AS only.

- STRIKE - immediate attack followed by a natural decay, even while the pad is held.
- HOLD - immediate attack and sustain until release.
- BLOOM - pads use a fast attack and sustain; MIDI notes and clock triggers retain a slower rise.

Touch pressure does not modulate timbre in TS. External CV2, Channel Aftertouch, CC1, and CC74 can still increase DEPTH.

## DICE and bootloader

- Short DICE in AS without SHIFT - randomizes the six NS parameters, timbre memory, and rhythm seed. RATE is preserved.
- Short SHIFT + DICE - randomizes the six SHIFT parameters and refreshes timbre memory.
- Short DICE in TS without SHIFT - selects STRIKE -> HOLD -> BLOOM.
- Hold DICE for 3 seconds without SHIFT - switches AS/TS.
- Hold SHIFT + DICE for 10 seconds - enters the bootloader.

Holding SHIFT + DICE longer than 1 second but shorter than 10 seconds does not randomize the timbre. FluxOS memory is held in RAM and is not stored as a preset.

## CV

- CV1 - trigger and clock; one AS step or three TS triggers.
- CV2 - continuous DEPTH modulation. Repeating edges may be recognized as a clock. After 20 seconds without an edge, CV2 returns to modulation duty.

Clock priority is CV -> MIDI -> internal clock. MIDI may take over 20 seconds after the last CV pulse. The internal clock returns after 30 seconds without an external source.

## USB MIDI

The device appears as **diceFriend v.01** and uses channel 1 by default.

### MIDI In

- Note On in AS sets the fundamental pitch and always produces a direct audible attack.
- Note On in TS opens one of three voices. A fourth note steals the oldest available voice.
- Note Off or Note On with velocity 0 releases the matching note.
- Pitch Bend range is +/-2 semitones.
- Channel Aftertouch, CC1, and CC74 increase DEPTH.
- CC20-25 control NS P1-P6; CC26-31 control SHIFT P1-P6.
- Start resets position, Continue resumes, and Stop halts steps and releases voices.
- MIDI Clock is received at 24 PPQN.

### MIDI Out

Autonomous AS steps, pads, and CV triggers send Note On/Off. Physical knobs send CC20-31, CV2 sends smoothed CC74, and pad pressure in AS sends Channel Aftertouch. The internal clock and CV can send Start, Stop, and MIDI Clock. Messages received over USB are not echoed back to the same port.

## LEDs

- NS/SHIFT indicator - active panel layer.
- After a mode change, LED 3 indicates AS.
- In TS, LED 0, 1, or 2 indicates STRIKE, HOLD, or BLOOM respectively.
- After the mode display, LED 0 shows clock activity, LED 1 shows CV2 level, and LEDs 2 and 3 show left and right audio level.

## First clocked patch

Set MOTION to minimum and RATE to x1. Send MIDI Clock at 120 BPM: one attack should occur every 24 pulses. Then raise MOTION to introduce uneven spacing and alternate articulations. Connecting CV gives it immediate priority; after CV is removed, MIDI returns only after the protection period.
