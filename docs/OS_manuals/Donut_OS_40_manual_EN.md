# Donut_OS - LEFT manual

Version: 2026-10-23. Hardware: diceFriend LEFT, Teensy 4.0.

Donut_OS is a two-voice microtonal instrument that walks across a toroidal pitch grid. One axis selects scale degrees and the other builds the interval of the second voice. Harmonic cores, folding and granular memory can remain tonal at low settings or become highly unstable when chaos, mutation and feedback are raised.

## Main operation

- SHIFT selects the second parameter layer.
- Short DICE creates a new world: tuning, geometry, motion, density and timbre are randomized.
- Short SHIFT + DICE makes a related mutation while preserving scale, root, grid and route.
- Hold DICE for at least 450 ms to loop the most recent eight steps; release it to continue from the last recalled state.
- Hold SHIFT + DICE for 10 seconds to enter the bootloader.
- Pot values use soft takeover after a layer change or randomization.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | SCALE: six tuning maps | DENSITY: probability of an audible step |
| P2 | INTERVAL SPAN: maximum movement | CHAOS: motion and grain instability |
| P3 | WIDTH: horizontal grid size | MUTATION: direction, spectrum and grain-speed change |
| P4 | HEIGHT: vertical grid size | FEEDBACK: geometry and harmonic core color |
| P5 | BIAS: preference for X or Y motion | INERTIA: tendency to keep the previous direction |
| P6 | ROOT: C1-C4 | ROUTE: six modulation destinations |

The tuning choices are 12 EDO, 19 EDO, 31 EDO, two normalized Hexany maps and 5-limit diatonic just intonation.

## Pads and performance

- T1 sets tap tempo with two touches.
- T2 adds roughness and grain intensity; touch pressure controls the amount.
- T3 lengthens the decay.

Donut_OS has one continuous performance mode. Each clock step moves one grid axis, even when Density creates a rest. The loop stores pitches, rests, velocity, timbre, grain intensity, decay, routing and the internal walk state.

## CV and USB MIDI

- CV1 advances one step per rising edge.
- CV2 provides continuous expression. Repeating edges can also act as a secondary clock; CV1 retains priority.
- Clock priority is CV, then MIDI, then internal. MIDI may take over after 20 seconds without CV; internal timing returns after 30 seconds without an external source.
- MIDI Clock uses 24 PPQN. Start and Continue run transport; Stop stops MIDI-driven stepping.
- MIDI Note On forces the next step and uses velocity as its accent. Note number does not retune the grid.
- CC20-31 control the twelve panel parameters. CC74 and Channel Aftertouch add expression.
- MIDI Out sends voice A on channel 1 and voice B on channel 2. Each channel uses Pitch Bend with a +/-2 semitone range for microtonal tuning.
- Local clock and CV can generate Start and MIDI Clock. Incoming USB messages are not echoed.

## LEDs

The two layer LEDs follow NS and SHIFT. The four lower LEDs show step activity, CV2 or loop activity, and left/right audio level.

## First patch

Choose 19 EDO or a Hexany with P1, set a medium grid with P3/P4 and keep CHAOS and MUTATION below halfway. Use T1 to tap a tempo. Raise DENSITY first, then increase CHAOS and ROUTE to open granular motion without losing the two-voice pitch relationship.
