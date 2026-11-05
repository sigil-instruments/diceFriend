# Gruz_OS - LEFT manual

Version: 2026-10-29. Hardware: diceFriend LEFT, Teensy 4.0.

Gruz_OS is a three-track instrument for dense bass, resonant noise and damaged ambience. The tracks remain connected through memory, feedback and modulation, so changing one layer can reshape the whole organism. At restrained settings it produces tonal drones and woody resonances; at high density, memory and motion it becomes a moving wall of saturation, glitches and recirculating debris.

## Quick start

1. Start in AS mode on the NS layer.
2. Set P1-P3 around halfway to hear all three tracks.
3. Keep P4-P6 below halfway for a clear tonal starting point.
4. Move to the SHIFT layer and set P4 MEMORY, P5 SATURATION and P6 FX / MOTION near one third.
5. Tap DICE to create a new state. Raise density and memory gradually for heavier textures.

## Modes and SHIFT

Hold DICE on the NS layer for about 3 seconds to switch between:

- AS: all three tracks run continuously; pads add strikes and temporary density.
- TS: pads open the three tracks as held voices.

SHIFT selects the second parameter layer. At startup and after changing layer, using DICE or receiving MIDI control, a knob keeps the stored value until it moves by about 8% of its full range from its armed position. It then glides to the filtered knob position over 200 ms without a jump.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | BASS level | BASS pitch, MIDI 24-60 |
| P2 | NOISE level | NOISE pitch, MIDI 36-72 |
| P3 | AMBIENT level | AMBIENT pitch, MIDI 36-72 |
| P4 | BASS density and PM depth | MEMORY: recirculation, track coupling and overload |
| P5 | NOISE density | SATURATION |
| P6 | AMBIENT density, voices and glitches | FX / MOTION: delay mix, movement and overload |

The same parameter map is active in AS and TS. Physical knob readings are inverted for diceFriend LEFT.

## The three tracks

### BASS

A sub-rich phase-modulation voice with a stable fundamental. Density increases harmonic content, PM depth and recursive overload while preserving the perceived pitch. MEMORY, SATURATION and FX / MOTION can push it from a clean low drone toward a rough, folding bass mass.

### NOISE

Two pitched resonators are excited by a rungler and comparator core. At low density the tuned resonance dominates; higher density adds faster motion, wider bandwidth, noisy excitation, drive and granular recirculation. The track keeps a tonal centre even when the texture becomes dense.

### AMBIENT

Six related oscillators form a detuned tonal cloud. Density adds voices and short vinyl-like clicks and glitches. The track remains pitched beneath the debris, while MEMORY and FX / MOTION increase folding, recirculation and rapid spectral movement. Its MIDI output is transposed one octave above its base pitch.

## Interaction and effects

The tracks influence one another before their level controls. BASS energy changes the speed and bandwidth of NOISE; NOISE activity increases AMBIENT clicks; AMBIENT and memory energy reshape BASS modulation. A quiet track can therefore continue to affect the rest of the system.

The shared stereo effect is a dark cross-feedback delay with saturation inside the loop. MEMORY controls recirculation and coupling. SATURATION changes harmonic density. FX / MOTION sets the wet contribution and the speed of internal movement. Effect tails may remain after a TS voice is released.

## AS mode

All three tracks remain open. Clock steps create a gentle bloom instead of a hard attack.

- T1 strikes BASS and temporarily raises its density.
- T2 strikes NOISE and temporarily raises its density.
- T3 strikes AMBIENT and temporarily raises its density.

Tap DICE to randomize the six parameters of the active layer. When the NS layer is randomized, Gruz_OS keeps the middle track level and raises the quietest and loudest track levels to maximum, preventing a silent result. Randomizing the SHIFT layer returns all three pitch controls to their manual knob values.

## TS mode

- T1 opens BASS.
- T2 opens NOISE.
- T3 opens AMBIENT.

The level and density controls remain independent. Releasing a pad closes that track while the shared effect tail decays naturally. External clock can open all three tracks with a short gate until MIDI notes take over TS articulation. MIDI Start returns TS to clock articulation.

## DICE and bootloader

- Tap DICE: randomize the active layer.
- Hold DICE on the NS layer for about 3 seconds: switch AS / TS.
- Hold SHIFT + DICE for about 10 seconds: enter the Teensy bootloader.

A hold is assigned to the layer that was active when DICE was pressed. Changing SHIFT during the hold cancels the gesture.

## Clock and transport

Clock priority is fixed:

`CV1 -> MIDI Clock -> internal clock`

- A CV1 edge takes control immediately and blocks MIDI takeover for 20 seconds after the latest CV edge.
- MIDI Clock is received at 24 PPQN; every 24 pulses produce one step.
- The internal clock returns after 30 seconds without an active external source.
- Start resets and resumes transport. Continue resumes it. Stop blocks clock-driven events until Start or Continue.
- Pads and MIDI notes remain playable after Stop.
- The internal clock runs in AS only, at one step every 2 seconds.

## CV inputs

### CV1

CV1 is the priority trigger and clock input. Each clean rising edge advances the engine. Gruz_OS also sends short MIDI notes derived from the current track pitches.

### CV2

CV2 is a smoothed continuous coupling control. It increases interaction between the tracks and sends MIDI CC74 with rate limiting and a minimum-change threshold. CV2 is not a pitch input and does not track V/oct.

## USB MIDI In

The USB device name is `diceFriend v.01`.

- In AS, channels 1, 2 and 3 address BASS, NOISE and AMBIENT. Channels 4-15 repeat the same three-track order.
- In TS, channel 1 plays all three tracks. Channels 2 and 3 address NOISE and AMBIENT independently.
- Note On sets the addressed pitch and creates an audible attack.
- Note Off and Note On with velocity 0 release the matching TS voice.
- CC20-25 control the six NS parameters.
- CC26-31 control the six SHIFT parameters.
- MIDI Clock, Start, Stop, Continue and System Reset control transport.
- Channel 16 is reserved for Gruz_OS output and is ignored for incoming notes.
- Incoming messages are not echoed back to the same USB port.

## USB MIDI Out

Gruz_OS sends its own events on channel 16:

- short notes from internal steps, CV1 and pads;
- CC74 from CV2;
- CC102, CC103 and CC104 for BASS, NOISE and AMBIENT activity.

The output is rate-limited and does not retransmit incoming Clock, transport, CC, Pitch Bend or Aftertouch.

## LEDs

- NS LED: NS layer active.
- SHIFT LED: second layer active.
- LED 0: clock and step activity.
- LEDs 1-3: BASS, NOISE and AMBIENT activity.

## Starting patches

### Tonal machinery

Use medium BASS and NOISE levels, low AMBIENT, low densities and low SATURATION. Set the three pitches to related notes and add MEMORY slowly until the resonances begin to answer one another.

### Damaged low wall

Raise BASS density, MEMORY and SATURATION. Keep AMBIENT density around halfway and use a moderate FX / MOTION setting. The fundamental remains present while recursive harmonics and short glitches accumulate around it.

### Moving debris

Use all three levels high, NOISE and AMBIENT density above 70%, then raise MEMORY and FX / MOTION into their upper range. Tap DICE on each layer for a new structure and use the pads to force additional cross-track activity.
