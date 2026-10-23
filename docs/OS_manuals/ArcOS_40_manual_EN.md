# Arc_OS - LEFT manual

Version: 2026-10-23. Hardware: diceFriend LEFT, Teensy 4.0.

Arc_OS is a four-part microtonal instrument built from four different materials: a spectral phase-distortion voice, a four-operator FM voice, a pressure-driven resonator and a centered sub voice. Coupled shift registers choose pitches from six alternative tuning systems, while independent rhythmic dividers let the parts form changing polyrhythms.

## Main operation

- SHIFT selects the second layer of the six knobs.
- Short DICE mutates the active scene while preserving root and tempo.
- Short SHIFT + DICE applies a wider mutation.
- Hold unshifted DICE for about 1.8 seconds to switch AS/TS.
- Hold SHIFT + DICE for 10 seconds to enter the bootloader.
- Pot values use soft takeover after a layer or scene change.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | Root pitch | Tempo, about 24-240 BPM |
| P2 | ARC: spectral phase deformation / FM index | STRETCH: harmonic spacing / FM ratios |
| P3 | Pitch-walk range | MEMORY: spectral inertia / resonance time |
| P4 | Spectral focus / FM middle-operator index | Microtonal scale selection |
| P5 | Phase coupling and spectral comb / deeper FM operator | GLITCH: short capture and slice events |
| P6 | Decay | EXCITER: attack hardness and structure |

SHIFT P4 selects 19 EDO, 24 EDO, 31 EDO, Bohlen-Pierce, a septimal unequal scale or 22 EDO. P1 transposes the chosen scale without morphing its intervals toward 12-TET.

## AS and TS

In AS, each material has an independent 2-5 step divider. T1 strikes Spectral, T2 strikes FM and T3 excites the pressure resonator. The sub voice follows the same scale in a lower register.

In TS, the three pads open the first three materials. T1 + T3 also opens the sub voice. External clock steps rotate across all four parts. Releasing a pad closes its assigned voice.

## CV and USB MIDI

- CV1 is the priority trigger/clock input with a 1 ms edge filter.
- CV2 provides continuous material modulation and sends CC74.
- Clock priority is CV, then MIDI, then internal. MIDI may take over 20 seconds after the last CV edge; internal clock returns after 30 seconds without an external source.
- MIDI Clock uses 24 PPQN. Start, Continue and Stop control transport.
- MIDI channels 1-4 address the four materials directly. Channels 5-16 use free/oldest voice allocation.
- Note On sets pitch and produces an audible strike. Note Off and Note On velocity 0 release the assigned voice.
- Pitch Bend range is +/-2 semitones. CC20-25 control NS and CC26-31 control SHIFT.
- Local events generate Note On/Off on channels 1-4. Microtonal pitch is carried by Pitch Bend sent before Note On.
- Incoming USB MIDI is not echoed back to the same port.

## LEDs

The two layer LEDs follow the active NS/SHIFT layer. The four lower LEDs show the activity of the four material envelopes.

## First patch

Start in AS with ARC and GLITCH low, MEMORY near the middle and a moderate decay. Choose a scale with SHIFT P4, then increase ARC and STRETCH to move from stable tones into stretched metallic spectra. Add GLITCH last for short freezes, reversals and stutters.
