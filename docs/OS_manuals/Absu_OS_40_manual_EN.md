# Absu_OS 40 - user manual (LEFT)

Manual for diceFriend LEFT.

## What Absu_OS is

Absu_OS is an autonomous rhythm, bass, chord and self-sampling engine. It does not play a bank of prepared samples. It continuously creates its own material, records a short section of the complete output into memory, then tears it apart with repetition, reverse playback, speed changes and irregular bursts.

This is intentionally not a conventional drum machine. Kick, snare/tom, metallic hi-hat, bass, chords and micro-fragments share one mutation system. The rhythm keeps recognizable anchors while cycle lengths, accents, pitches and density drift apart. Its natural territory is the unstable space between groove and controlled failure.

## Quick start

1. Start the instrument in AS mode.
2. Put `P2 DENSITY`, `P3 INSTABILITY` and `P5 BALANCE` near the middle.
3. Set `SHIFT + P2 GLITCH` above halfway and `SHIFT + P3 MICRO LENGTH/RATE` in the low-to-middle range.
4. Press `DICE` briefly to create a new rhythmic organism.
5. Let it run for several bars. Some mutations live on longer cycles and are not immediate.

A useful starting point is 80-120 BPM, 50-70% density, 35-55% instability and the balance centred or slightly toward the tonal side.

## DICE, SHIFT and soft takeover

| Gesture | Action |
|---|---|
| Short `DICE` | Randomizes the rhythmic structure, scale, chords, mutations, glitch character and virtual parameter values. |
| `SHIFT` + short `DICE` | Creates a more extreme and less conservative variation. |
| Hold `DICE` for about 1.8 seconds | Toggles AS ↔ TS. |
| Hold `SHIFT` + `DICE` for about 10 seconds | Enters the bootloader. |

Soft takeover is active at startup and after randomization, layer changes and MIDI control. A parameter keeps its stored value until the knob moves by about 8% of its full range from the position at which takeover was armed. It then glides to the filtered knob position over 200 ms without a jump.

## Knob map

### NS layer - without SHIFT

| Knob | Function |
|---|---|
| `P1 TEMPO` | Internal clock, approximately 42-200 BPM. It does not retime an active external CV or MIDI clock. |
| `P2 DENSITY` | Overall amount of drum, tonal and micro-fragment events. |
| `P3 INSTABILITY` | Timing jitter, irregularity, accent mutation and deviation from the main pulse. |
| `P4 CYCLE / GEAR` | Relationships between cycle lengths and the traversal of polyrhythmic patterns. |
| `P5 PERC ↔ TONAL` | Balance between percussion and bass, chords and sampled material. |
| `P6 SPACE / MIX` | Space, width and final mix character, with a small influence on output level. |

### SHIFT layer

| Knob | Function |
|---|---|
| `SHIFT + P1 MUTATION` | Frequency of pattern rebuilding and other structural changes. |
| `SHIFT + P2 GLITCH / RATCHET` | Intensity of repeats, ratchets, stutters and violent event bursts. |
| `SHIFT + P3 MICRO LENGTH / RATE` | Micro-fragment length and playback speed. The low-to-middle area makes shorter, more fragmented material. |
| `SHIFT + P4 PITCH / SCALE RANGE` | Pitch range, scale movement, chord register and bass colour. |
| `SHIFT + P5 MACRO EVENT` | Probability of large-scale freeze, void and avalanche events. |
| `SHIFT + P6 DEGRADE / REVERSE` | Degradation, reverse playback and instability of captured material. |

### Knobs in TS

TS remains connected to the same engine, but the most important controls take on a performance role:

| Knob | Function in TS |
|---|---|
| `P1 PITCH` | Fundamental for bass and chords; it also influences the pitch of metallic transformations on the other pads. |
| `P2 HOLD DENSITY` | Density of successive events while a pad is held. |
| `P3 ESCALATION` | Depth of the transition from a clean voice into mutation and cross-layer leakage. |
| `P4 RANGE` | Register span of the jumps that appear during a longer hold. |
| `P5 PERC ↔ TONAL` | Balance between the same layers used in AS. |
| `P6 SPACE / MIX` | Space and final mix character. |

The SHIFT layer continues to shape mutation, glitch, micro-fragments, pitch movement, cross-layer events and reverse. A long hold can therefore remain relatively rhythmic or disintegrate into much more extreme material.

## AS - autonomous mode

AS composes and performs by itself. Pattern lengths range from 5 to 13 steps, allowing layers to meet and separate without a short, obvious master loop.

### Sound layers

- **Kick** - a synthesized kick with a falling pitch envelope.
- **Snare/tom** - a noise-and-tone percussion voice.
- **Pitched hi-hat** - a metallic hi-hat with its own high-pass/band-pass filtering. Every 5-9 steps it walks randomly by one or two scale degrees. It can sit two or three octaves above the root, occasionally four, reaching into the upper chord registers.
- **Bass** - two triangle oscillators with a sub or harmonic component, a longer envelope and scale-aware pitch motion.
- **Chord** - three oscillators using minor, major, suspended, quartal and two cluster interval families. Bass and chord pitch can mutate every few steps.
- **Micro-sampler** - a stereo buffer that records the full engine output, then plays short sections forward or backward at roughly 0.25x-3x speed.

Glitch is not confined to percussion. A feral burst may take over the captured fragment, drums, bass, chord or the complete stack. A typical burst contains 3-8 irregularly spaced events.

### Touch pads in AS

| Pad | Action |
|---|---|
| `T1` | Immediate kick. |
| `T2` | Immediate bass and chord. |
| `T3` | Reverse/glitch fragment from the current capture buffer, reinforced by a metallic hit. |

### Macro events

`SHIFT + P5` raises the probability of three larger interventions:

- **freeze** - holds and processes a fragment for about 5-9 steps;
- **void** - approximately two steps of near-silence;
- **avalanche** - approximately four steps of dense cascading activity.

The void is deliberate and the music returns automatically. A short `DICE` also creates a fresh state immediately.

## TS - three layers under your fingers

TS gives direct access to the same three layers that compose the music in AS. The pads may be held together, and each layer remains active until the finger is released.

| Pad | Short touch | Hold |
|---|---|---|
| `T1 DRUM` | Strong kick. | Continues a percussion stream. Over time it introduces snare/tom, high hi-hat, uneven ratchets and captured fragments. |
| `T2 TONAL` | Bass and chord at the pitch set by `P1 PITCH`. | Sustains the bass, repeats chords and gradually expands their pitch, register and interval structure. |
| `T3 MEMORY` | Reverse/glitch from current memory plus a metallic accent. | Loops the fragment, then shortens it, changes direction and speed, and adds high hits and distant chords. |

Escalation begins gently after a short hold. The longer a pad remains down, the wider the pitch jumps, the denser the repetitions and the stronger the leakage from other layers. At its deepest stage it may release an irregular burst across the complete organism. `P2`, `P3`, `P4` and the SHIFT parameters determine how quickly and how far that process travels.

Releasing `T1` stops new hits, `T2` releases the bass and lets the chord decay, and `T3` releases the looped fragment. Incoming MIDI Note On/Off continues to control the tonal voice at the received pitch. An external CV or MIDI Clock step may add percussion or a fragment.

Changing AS/TS ends the active macro event and releases active voices so that nothing remains stuck.

## Clock and CV inputs

Clock priority is fixed:

`CV1 → MIDI Clock → internal clock`

- A valid `CV1` pulse takes control immediately and blocks MIDI takeover for 20 seconds after the last CV pulse.
- When the CV lock expires, MIDI Clock at 24 PPQN may take over.
- The internal clock returns only after 30 seconds with no active external source.
- A new event from a higher-priority source stops lower-priority sources immediately.

`CV1` is the pulse/clock input. It triggers a step and produces a MIDI Note plus MIDI Clock at the output. `CV2` is continuous and sends `CC 74` and Channel Aftertouch. CV2 is not a second clock input.

## USB MIDI

The USB device name is `diceFriend v.01`. Absu_OS uses channel 1.

| Incoming message | Action |
|---|---|
| `Note On`, velocity > 0, AS | Sets or takes over pitch/fundamental and forces an audible bass, chord, hit or fragment event. |
| `Note On`, velocity > 0, TS | Sets pitch and opens the voice. |
| `Note Off`, or `Note On` with velocity 0, TS | Releases the corresponding note/gate. |
| MIDI Clock | 24 PPQN; a complete step runs an AS step or TS trigger. |
| Start / Continue | Starts or resumes MIDI transport. |
| Stop | Stops transport and releases the active TS voice. |
| `CC 20-25` | Remote control of the six NS parameters. |
| `CC 26-31` | Remote control of the six SHIFT parameters. |

Absu_OS sends its own `Note On/Off`, internally generated or CV-derived Clock, and CV2 messages. It does not echo incoming messages to the same USB port, so it does not implement MIDI Thru or create a DAW feedback loop. Incoming MIDI Clock is not echoed back.

## LEDs

| LED | Meaning |
|---|---|
| `NS` / `SH` | Shows the active knob layer. |
| `LED 0` | Solid with CV clock; otherwise changes brightness with the current step. |
| `LED 1` | Solid with MIDI clock; otherwise becomes brighter during a macro event. |
| `LED 2` | Solid in TS; in AS follows audio activity. |
| `LED 3` | In AS follows audio activity; in TS indicates the CV2 level. |

## Three useful starting patches

### Groove with leaking glitches

Use moderate density and instability, a slightly tonal balance, 45-65% `GLITCH`, a short-to-medium micro-fragment and a low `MACRO EVENT` setting. The pulse stays readable while alien repetitions keep entering it.

### Upper metallic swarm

Raise `PITCH / SCALE RANGE`, increase `GLITCH` and `DEGRADE / REVERSE`, and keep the balance near the centre. The hi-hat walks through the scale and collides with the upper chord registers.

### Controlled failure

Use high instability, mutation and glitch, medium-high macro events and a short micro-fragment. `SHIFT + DICE` supplies the most extreme starting state. If a deliberate void appears, wait for the organism to return or press `DICE`.
