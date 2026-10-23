# Aether_OS - LEFT manual

Version: 2026-10-23. Hardware: diceFriend LEFT, Teensy 4.0.

Aether_OS combines a melodic attractor, granular pulsar synthesis, stereo memory and nonlinear feedback in one continuous signal path. A fundamental and its lower octave fill the spaces between grains, while the Lorenz-driven pitch walk moves through a stretched microtonal scale.

## Main operation

- SHIFT selects the second layer of the six knobs.
- Short DICE mutates the active layer.
- Hold unshifted DICE for about 3 seconds to switch AS/TS.
- Hold SHIFT + DICE for 10 seconds to enter the bootloader.
- Pot values use soft takeover after changing layer or mode.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | Grain emission: sparse impulses to audio-rate stream | Number of overlapping grains |
| P2 | Grain duration: micro-click to long cloud | Memory length and feedback |
| P3 | Melodic root pitch | Phaser and orbit speed |
| P4 | Pulse shape and masking | Fold and saturation |
| P5 | Attractor dynamics and coupling | Pitch span, mutation and micro-slices |
| P6 | Internal tempo and release | Space, stereo width and microtonal grid stretch |

## AS and TS

AS is a self-moving granular melody. Each accepted CV, MIDI or internal step creates a new event. T1 freezes the rungler and memory write, T2 opens fractures and dense grains, and T3 expands the phase space.

TS turns the three pads into independent voices. Each voice responds to touch, CV and MIDI with the shared Aether timbre. MIDI notes can hold and release the voices independently.

## CV and USB MIDI

- CV1 is a trigger/clock input with a 1 ms edge filter.
- CV2 is continuous modulation and sends CC74.
- Clock priority is CV, then MIDI, then internal. MIDI may take over 20 seconds after the last CV edge; internal timing returns after 30 seconds without an external source.
- MIDI Clock uses 24 PPQN. Start, Continue and Stop control transport.
- In AS, Note On sets the fundamental and produces an audible attack.
- In TS, Note On opens a voice; Note Off and Note On velocity 0 release the matching voice.
- CC20-31 control the twelve panel parameters.
- Local steps, pads and CV generate MIDI Out. Microtonal AS notes use Note On plus Pitch Bend with a +/-2 semitone range.
- Incoming USB MIDI is not echoed back to the same port.

## LEDs

The two layer LEDs show NS/SHIFT. The lower LEDs display current motion, CV activity and stereo audio level.

## First patch

Begin in AS with slow emission, medium grain duration and low fold. Set P3 near the middle, then raise SHIFT P1 to overlap grains. Add memory with SHIFT P2 and widen the field with SHIFT P6. Use T1 to hold a texture and T2 to fracture it.
