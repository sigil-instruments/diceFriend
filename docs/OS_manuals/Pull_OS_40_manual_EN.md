# Pull_OS - LEFT manual

Version: 2026-10-23. Hardware: diceFriend LEFT, Teensy 4.0.

Pull_OS is a granular pulse instrument built around emission, duration, formant motion, memory and phase-space feedback. In AS it behaves as one self-moving organism; in TS it becomes three separately pitched touch voices sharing the same granular character.

## Main operation

- SHIFT selects the second control layer.
- Short DICE randomizes the active layer while preserving AS tempo.
- Hold unshifted DICE for about 3 seconds to switch AS/TS.
- Hold SHIFT + DICE for 10 seconds to enter the bootloader.
- Pot values use soft takeover after layer, mode and MIDI CC changes.

## AS controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | Emission rate / fundamental | Grain overlap |
| P2 | Grain duration | Memory length and feedback |
| P3 | Formant position | Phaser motion |
| P4 | Pulse shape | Wavefolding |
| P5 | Chaos | Mutation depth |
| P6 | Internal speed and release | Stereo space |

AS pads act as performance gestures: T1 freezes memory, T2 ruptures the texture and T3 expands the phase space.

## TS controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | Voice 1 pitch | Grain overlap |
| P2 | Voice 2 pitch | Formant position |
| P3 | Voice 3 pitch | Pulse shape / fold |
| P4 | Voice 1 decay | Memory and phase space |
| P5 | Voice 2 decay | Mutation |
| P6 | Voice 3 decay | Stereo space |

Each pad opens its corresponding voice. TS is externally played by pads, CV1 or MIDI; the internal AS clock does not trigger TS voices.

## CV and USB MIDI

- CV1 is the priority trigger/clock input. In AS it advances the organism; in TS it rotates across the three voices.
- CV2 provides continuous modulation and sends CC74.
- Clock priority is CV, then MIDI, then internal. MIDI may take over after 20 seconds without CV; internal timing returns after 30 seconds without an external source.
- MIDI Clock uses 24 PPQN. Start, Continue and Stop control transport.
- In AS, Note On sets the emission pitch and triggers an event. Note Off releases the pitch override.
- In TS, Note On opens one of three voices. Note Off and Note On velocity 0 release the matching voice.
- CC20-31 control the twelve active panel values.
- Local steps and pads generate Note On/Off. Local clock and CV can generate Start and MIDI Clock.
- Incoming USB MIDI is not echoed back to the same port.

## LEDs

The two layer LEDs show NS/SHIFT. The four lower LEDs display rungler motion, CV2 level and stereo audio activity.

## First patch

Start in AS with P1 and P2 around one third, medium formant and low chaos. Raise overlap and memory gradually until individual impulses merge into a cloud. Use T1 to freeze a stable fragment, then touch T2 to break it apart.
