# Mult_OS — manual

Version: 2026-09-18. Mult_OS has AS/Walk and TS modes. Hold DICE for about 3 seconds to change mode. A short unshifted DICE mutates AS or selects the next TS engine. SHIFT + DICE changes the mutation depth and mutates the scene; the four depths are Safe, Musical, Chaos and Wild.

## Control map

| Knob | AS normal layer | AS SHIFT layer |
|---|---|---|
| P1 | Internal speed; under external clock, second MIDI layer transpose | Scale selection and voice-1 detune |
| P2 | Base pitch | Pitch-walk range and voice-2 detune |
| P3 | Harmonic spread and PM depth | Fold/tone and voice-3 detune |
| P4 | Feedback and cross-modulation | Additional modulation depth |
| P5 | Motion | Feedback damping |
| P6 | Release | Space, stereo and motion |

| Knob | TS normal layer | TS SHIFT layer |
|---|---|---|
| P1 | T1 pitch | Harmonic spread |
| P2 | T2 pitch | Phase fold |
| P3 | T3 pitch | Tone / brightness |
| P4 | T1 decay | PM depth |
| P5 | T2 decay | Feedback |
| P6 | T3 decay | Motion and stereo |

The three TS pads open three voices. In AS, individual pads accent PM, feedback and pitch-walk motion. A longer touch increases its influence.

## CV and MIDI

CV1 is a trigger/clock input. CV2 works as continuous modulation until pulses are detected, then participates in clock/trigger handling. MIDI Note On takes pitch and triggers the voice group when CV does not own timing; held input notes are tracked and released. Start resets the walk step, while Stop clears incoming notes rather than persistently stopping AS. CC20–25 control the normal layer, CC26–31 the shifted layer, and CC74 controls the CV2 value. Local gates generate Note On/Off, panel movement generates CC, and local/CV timing generates Clock.

MIDI Clock uses 24 PPQN. CV has priority over MIDI, and an external timing source remains active for approximately 30 seconds. Start resets the walk step; Stop clears incoming notes.

MultOS is an Ellitone-inspired diceFriend OS built as a separate firmware family
for Teensy 3.6 and Teensy 4.0 hardware.

## Projects

- `MultOS_36` - Teensy 3.6, analog stereo output.
- `MultOS_40` - Teensy 4.0, PT8211 output.

## Controls

- Short `DICE`: switch the current MultOS engine and apply mutation at the
  selected randomness depth.
- `SHIFT + DICE`: cycle randomness depth.
- Long `DICE`: toggle RS/walk mode and TS/touch mode.
- 4 engine LEDs: show the selected engine after switching.
- Randomness depth display: LED 0 = safe, LEDs 0-1 = musical, LEDs 0-2 = chaos.

## Engines

- Engine 0: wave cluster, the most stable wavetable-like voice.
- Engine 1: glass FM, brighter and more metallic.
- Engine 2: chip swarm, sharper and more stepped.
- Engine 3: bounce, hollow/feedback-oriented and more generative.

## Randomness Depths

- Safe: small drift, light detune, performance-friendly.
- Musical: voicing, scale, motion, and timbral mutation.
- Chaos: deeper pitch/feedback/crossmod/chaos changes plus deeper walk mutation.

## Build

```sh
cd MultOS_40
/Users/maciejjaciuk/.platformio/penv/bin/platformio run

cd ../MultOS_36
/Users/maciejjaciuk/.platformio/penv/bin/platformio run
```
