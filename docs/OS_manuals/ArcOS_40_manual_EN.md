# Arc_OS - LEFT manual

Version: 2026-10-28. Hardware: diceFriend LEFT, Teensy 4.0.

Arc_OS is a four-material microtonal instrument. Its voices are a spectral phase-distortion arc, four-operator FM, a pressure-driven resonator and a centred sub voice. Each material has its own shift-register melody and rhythmic divider. The four streams share one root and one of six nonstandard tuning systems, creating interlocking hits, metallic spectra, pressure pings and low pulses.

## Quick start

1. Start in AS mode with SHIFT on the NS layer.
2. Set P1 near the lower third, ARC and COUPLING low, CONTOUR near the centre and DECAY around halfway.
3. Set SHIFT to the second layer. Choose a moderate tempo, set STRETCH and MEMORY near the centre, GLITCH low and EXCITER around halfway.
4. Press DICE once to create a related scene.
5. Raise ARC, STRETCH and COUPLING gradually, then add GLITCH.

## Modes and SHIFT

Hold DICE without SHIFT for about 1.8 seconds to switch between:

- AS: autonomous four-part generative mode.
- TS: touch performance mode.

SHIFT selects the second parameter layer. After changing layer, using DICE or receiving a MIDI CC, each knob waits for a deliberate movement before taking control.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | ROOT: fundamental from MIDI note 24 to 84 | TEMPO: approximately 24-240 BPM |
| P2 | ARC: phase deformation, spectral tension and FM amount | STRETCH: spectral spacing, FM ratio family and resonator dispersion |
| P3 | SPREAD: melodic range of the four shift-register walks | MEMORY: spectral inertia, FM body and resonator persistence |
| P4 | CONTOUR: spectral focus, FM middle-operator index and envelope shape | SCALE: selects one of six microtonal worlds |
| P5 | COUPLING: interaction between partials, materials and feedback paths | GLITCH: probability and intensity of capture, reverse, stutter and freeze events |
| P6 | DECAY: envelope length and material sustain | EXCITER: attack hardness, brightness and physical energy |

### Tuning systems

SHIFT P4 selects:

1. A seven-note subset of 19 EDO
2. An eight-note subset of 24 EDO
3. A nine-note subset of 31 EDO
4. A 13-step Bohlen-Pierce scale repeating at the tritave
5. A septimal unequal scale
6. A seven-note subset of 22 EDO

ROOT transposes the selected system without pulling its intervals toward 12-TET. The spectral voice sounds one octave below its internal pitch reference. The FM and pressure voices occupy the upper register, while the sub remains in a controlled low register.

## The four materials

### 1. Spectral arc

A phase-deformed spectral voice whose partial spacing and coupling bend into metallic arcs. ARC sets the deformation, STRETCH changes internal topology and spacing, CONTOUR reshapes the spectrum and MEMORY controls how quickly the partial structure follows new events.

### 2. Four-operator FM

A struck four-operator voice. STRETCH selects one of four ratio families, including harmonic and wider odd-number relationships. ARC and CONTOUR change modulation depth, while MEMORY and DECAY determine how long the FM body remains audible.

### 3. Pressure resonator

A short pressure impulse enters a dispersive resonant conduit. STRETCH controls dispersion, MEMORY controls persistence and EXCITER changes the attack energy. Higher ARC values add movement and nonlinear pressure colour.

### 4. Sub voice

A centred low voice derived from the same microtonal system. It reinforces the generative structure without duplicating the upper materials. In TS it is played by touching T1 and T3 together.

## AS mode

The internal clock advances the generative system. Each material has an independent divider, so a single master step can trigger any combination of the four parts. The shift registers choose new scale degrees within the range set by SPREAD. Small microtiming offsets keep simultaneous hits from collapsing into one transient.

The pads add immediate accents without stopping the autonomous rhythm:

- T1 strikes the spectral material.
- T2 strikes the FM material and pressure also increases COUPLING.
- T3 strikes the pressure resonator.

Holding a pad strengthens its continuous gesture modulation.

## TS mode

The pads become held performance voices:

- T1 opens the spectral material.
- T2 opens the FM material.
- T3 opens the pressure resonator.
- T1 + T3 opens the sub voice.

Releasing a pad releases its material. The internal clock does not create automatic TS notes. External CV or MIDI Clock can rotate through the four materials, producing one clocked voice at a time between the manually held notes.

## DICE

### Related mutation

Press and release DICE without SHIFT. Arc_OS changes the material parameters by a limited amount, resets the rhythm and creates a new internal scene. ROOT and TEMPO remain unchanged. In AS, the spectral and FM materials immediately audition the new scene.

### Full mutation

Press and release SHIFT + DICE. Arc_OS selects new values across the complete range for every parameter except ROOT and TEMPO, including SCALE, GLITCH and the material structure. The rhythm and shift-register state are also regenerated.

### Mode switch and bootloader

- Hold DICE without SHIFT for about 1.8 seconds: switch AS/TS.
- Hold SHIFT + DICE for 10 seconds: enter the Teensy bootloader.

## Clocking and transport

Clock priority is CV, then MIDI, then the internal clock.

- The first CV1 edge immediately takes ownership and triggers a step.
- MIDI Clock remains blocked for 20 seconds after the latest CV edge.
- Internal timing returns after 30 seconds without an active external source.
- MIDI Clock is received and generated at 24 PPQN.
- Start resets the MIDI-clocked sequence and rhythm.
- Continue resumes transport.
- Stop silences active voices and stops MIDI-clocked stepping.

The internal tempo range is approximately 24-240 BPM. In AS, each full beat advances the generative rhythm. In TS, the internal clock does not create notes, but external CV and MIDI Clock can trigger the rotating TS sequence.

## CV inputs

### CV1

CV1 is the priority trigger and clock input. Every clean rising edge advances Arc_OS immediately. After a second valid edge establishes the period, Arc_OS can generate a corresponding USB MIDI Start and 24 PPQN clock stream.

### CV2

CV2 is a smoothed continuous material modulation source. Its effect is combined with the active scene and can influence spectral colour, FM, resonator motion and material interaction. Arc_OS also sends the smoothed CV2 value as CC74 when it changes.

## USB MIDI In

- MIDI channels 1-4 address the spectral, FM, pressure and sub materials directly.
- Channels 5-16 use a free-voice allocation; if all voices are occupied, the oldest voice is reused.
- Note On sets pitch and produces an immediate audible strike.
- Note Off and Note On with velocity 0 release the matching voice.
- Pitch Bend acts per input channel with a +/-2 semitone range.
- CC20-25 control the NS parameters P1-P6.
- CC26-31 control the SHIFT parameters P1-P6.
- CC74 adds remote material modulation.
- CC120 and CC123 release the voices assigned to the message channel.
- Incoming MIDI is not echoed back to the same USB port.

MIDI-held notes can also participate in clocked steps. Their incoming pitch is preserved while the current rhythmic structure supplies articulation.

## USB MIDI Out

Local pads, CV steps and autonomous AS events generate MIDI on four channels:

- Channel 1: spectral arc
- Channel 2: four-operator FM
- Channel 3: pressure resonator
- Channel 4: sub voice

For microtonal events, Arc_OS sends Pitch Bend before Note On. The bend range is +/-2 semitones. Local output notes are short articulated events; the audio voices in TS remain held until their pads are released. Panel movements send CC20-31, and CV2 sends CC74. Internal and CV clocks can generate Start and 24 PPQN MIDI Clock. Incoming USB messages are not retransmitted as MIDI Thru.

## GLITCH

GLITCH introduces short operations independently for the four materials. Depending on the current scene, events can capture a fragment, reverse its read direction, stutter a short region or freeze it temporarily. Low settings produce occasional cuts. Higher settings make memory operations part of the main rhythm.

## LEDs

- NS LED: NS layer active.
- SHIFT LED: second layer active.
- Lower LEDs 1-4: envelope and strike activity of the spectral, FM, pressure and sub materials.
- DICE flashes one or more lower LEDs to indicate mutation depth.
- Switching into TS or AS produces a distinct multi-LED flash.

## Patch ideas

### Clean interlocking quartet

Choose the 19 EDO or 24 EDO world, keep ARC and COUPLING below one third, set GLITCH near zero and use moderate MEMORY and DECAY. Increase SPREAD slowly to open the melodic range.

### Metallic arc field

Raise ARC and STRETCH, use a longer MEMORY and bring COUPLING toward the centre. Increase EXCITER for harder attacks, then add a small amount of GLITCH.

### Clocked touch ensemble

Switch to TS, play the three pads and patch a clock to CV1. The external clock rotates through all four materials while the pads hold individual voices. Touch T1 + T3 to add the sub.

### Four-channel MIDI instrument

Send separate notes to MIDI channels 1-4. Use one pitch sequence per material, automate CC20-31 and use CC74 for shared material movement. Each channel has independent Note Off and Pitch Bend handling.

## Bootloader

Hold SHIFT + DICE for 10 seconds to enter the Teensy bootloader, then load `ArcOS_40_L.hex` with Teensy Loader.
