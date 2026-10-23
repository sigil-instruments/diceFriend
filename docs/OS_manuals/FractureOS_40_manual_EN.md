# Fracture_OS - LEFT manual

Version: 2026-10-23. Hardware: diceFriend LEFT, Teensy 4.0.

Fracture_OS is a three-part generative instrument combining mallets, electric piano and wood-to-metal resonators. A microtonal Clifford melody, rhythmic deformation, repeats and a shared capture buffer move the sound from acoustic strikes into freezes, reversals, stutters and fractured memory.

## Main operation

- The lower switch position selects the BARWA/timbre layer; the upper position selects RYTMIKA/rhythm.
- Short DICE randomizes only the active six-control layer.
- Hold unshifted DICE for about 3 seconds to switch AS/TS.
- Hold SHIFT + DICE for 10 seconds to enter the bootloader.
- Pot values use soft takeover after changing layer, mode or scene.

## Controls

| Knob | BARWA / timbre | RYTMIKA / rhythm |
|---|---|---|
| P1 | Mallet body, phase and spectrum | Tempo, about 7.5-375 BPM |
| P2 | Mallet decay and regeneration | Density of the three parts |
| P3 | Electric-piano tine, four-operator FM and phase | Repeats and burst length |
| P4 | Piano decay, FM routing and feedback | RELABI rhythmic deformation |
| P5 | Wood-to-bell material and envelope | GLITCH: freeze, reverse, stutter and bit reduction |
| P6 | Stereo feedback and metal dispersion | EVOLUTION: development and rhythmic divisions |

## AS and TS

AS composes three interacting parts. The first plays mallets, the second plays a low electric piano, and the third moves from short wood to long metal and bell resonances. The rhythm layer controls their density, repeats, deformation and evolution.

TS maps the three pads to the three parts. CV can trigger the same parts, and MIDI notes can open three voices with individual Note Off handling. The shared glitch and feedback field remains active in both modes.

## CV and USB MIDI

- CV1 and CV2 can trigger Fracture events; CV1 is the primary clock input.
- CV2 also shifts the material/color scan.
- Clock priority is CV, then MIDI, then internal. MIDI may take over after 20 seconds without CV; internal timing returns after 30 seconds without an external source.
- MIDI Clock uses 24 PPQN. Start, Continue and Stop control transport.
- In AS, Note On sets pitch and forces an audible event.
- In TS, Note On opens a voice; Note Off and Note On velocity 0 release the matching voice.
- CC20-31 control the twelve panel parameters. CC74 controls CV2-style color modulation.
- Pads send Note On/Off on channel 1. Local timing can generate MIDI Clock without echoing incoming USB messages.

## LEDs

Fracture_OS uses the hardware-confirmed LEFT mapping: pin 2 indicates BARWA and pin 3 indicates RYTMIKA. The four lower LEDs display activity of the three parts and the shared output/glitch field.

## First patch

Begin with GLITCH and REPEATS low. Set mallet and piano decay near the middle, then move P5 from wood toward bells. Add RELABI for timing deformation and raise EVOLUTION slowly. Introduce GLITCH last to capture and rearrange the established phrase.
