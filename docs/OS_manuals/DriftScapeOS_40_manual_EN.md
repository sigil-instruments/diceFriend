# DriftScape_OS - LEFT manual

Version: 2026-09-18. TS uses three dedicated resonators. P1-P3 set their pitches and P4-P6 set their individual decays. With SHIFT, P1 controls Q, P2 stereo position, P3 brightness, P4 resonator character and P6 gentle fold. SHIFT P5 is reserved.

DriftScapeOS is the ambient, resonant landscape operating system for diceFriend. It combines a slowly wandering low body with two independent layers of wind-chime melodies, long decays, tonal reflections, stereo smear, feedback, and reverb. Instead of holding one fixed drone, the foundation moves gradually through a shared modal scale while old and new notes overlap like harmonic tides.

The result can move from sparse bells and distant resonant tubes to shoegaze-like harmonic clouds, drifting melodic fields, and slowly breathing low-frequency landscapes. DriftScapeOS is designed to evolve without filling the sound with broadband noise: its space is built mainly from tonal bodies, echoes, resonances, and controlled feedback.

DriftScapeOS has two performance modes: **AS mode** and **TS mode**. AS mode is the autonomous landscape generator. TS mode turns the touch pads, CV, and MIDI into gestures that open and excite the same resonant sound world.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE** creates a new landscape by randomizing both knob layers.
- **Hold DICE for about 3 seconds** switches between AS mode and TS mode.
- **SHIFT + hold DICE for about 3 seconds** performs a deeper randomization without changing mode.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.
- **Touch pads T1, T2, T3** act as momentary sound gestures in AS mode and playable gates in TS mode.

After changing layers, modes, or using DICE, the knobs use pickup behavior. A knob must move away from its stored position before it takes control, preventing sudden parameter jumps.

## CV and MIDI

- **CV1** works as a trigger and clock input. Each pulse excites the landscape and creates a MIDI note event.
- **CV2** has two simultaneous paths: a fast path detects short trigger/clock pulses, while a smoothed path provides continuous modulation.
- A steady CV2 voltage subtly changes space and chime timbre and is sent as MIDI CC 74. It can also appear as pitch bend or channel pressure during active MIDI output.
- Repeated CV1 or CV2 pulses are measured and converted to **MIDI Start plus 24 PPQN MIDI Clock**.
- CV-triggered events generate short MIDI Note On/Off messages on MIDI channel 1.
- Incoming MIDI notes set the tonal center. In AS mode, every Note On also creates an audible bloom. In TS mode, Note On opens a voice and Note Off releases it.
- Incoming MIDI pitch remains unchanged inside the sound engine. SHIFT Knob 1 transposes generated MIDI output rather than the incoming note.
- Incoming MIDI Clock drives the landscape at 24 PPQN when no CV clock has priority.
- DriftScapeOS does not echo incoming USB MIDI back to the same port, preventing MIDI feedback loops.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active knob layer.
- In normal AS operation, the four lower LEDs show CV1 activity, CV2 level, and left/right audio movement.
- In TS mode, the first three lower LEDs show touch-pad activity and the fourth follows output activity.
- DICE actions and mode changes produce confirmation flashes.

## AS Mode: Autonomous Landscape

AS mode continuously creates a stereo environment from three related musical systems.

The **body layer** uses two overlapping low voices. It moves slowly through the modal set `-5, 0, +2, +5, +7, +10, +12` semitones around the current tonal center. At low Mutation settings it stays close to the root and changes rarely. Higher settings increase the probability and distance of its movement. The previous body note fades underneath the next one instead of changing abruptly.

The two **chime layers** follow separate melodic algorithms. The first plays recurring, mutable motifs; the second performs an independent weighted walk through related scale degrees. Their notes overlap with long resonant tails and feed a tonal reverb and reflection network.

### AS Controls

Normal layer:

- **Knob 1 - Melody Balance:** Crossfades between melodic chime layer A and layer B. The center mixes both layers.
- **Knob 2 - Mutation:** Changes melodic variation and repetition, and also controls how actively the low body walks through the scale.
- **Knob 3 - Body Decay:** Sets the decay and overlap time of the wandering low foundation.
- **Knob 4 - Reverb / Space:** Expands the tonal reverb, reflections, and shoegaze-like wall around the sound.
- **Knob 5 - Chime Decay:** Sets how long the bells and resonant tubes continue ringing.
- **Knob 6 - Chime Timbre:** Moves the chimes from soft fundamentals toward brighter harmonic partials and also increases controlled feedback.

SHIFT layer:

- **Knob 1 - MIDI Out Transpose / Root:** Transposes generated MIDI output by approximately plus or minus two octaves. Without incoming MIDI it also selects the standalone tonal center.
- **Knob 2 - Drift:** Adds slow pitch drift and organic instability.
- **Knob 3 - Stereo Spread:** Widens the body, chimes, reflections, and smear field.
- **Knob 4 - Tempo / Motion:** Controls the shared melodic tempo and MIDI Clock output, approximately 20-180 BPM.
- **Knob 5 - Chime Register:** Moves the melodic resonators across a wider low-to-high register.
- **Knob 6 - Body / Chimes:** Crossfades between the low harmonic body and the two chime layers while also increasing output drive.

### AS Touch Pad Behavior

- **T1 - Freeze:** Holds the current reflection buffer and pushes the sound toward a denser suspended bloom.
- **T2 - Dissolve:** Deepens stereo smear, delay movement, filtering, and digital erosion.
- **T3 - Bloom:** Adds a strong resonant/feedback surge, brighter folding, and a more dramatic spatial expansion.
- Pad combinations combine these gestures and can turn a stable landscape into a temporarily frozen or heavily blurred harmonic cloud.

## TS Mode: Touch Landscape

TS mode closes the continuous output and opens the resonant landscape only when a touch pad, CV pulse, or MIDI note creates a gate. The pads do not become three unrelated synthesizers; they excite different pitch regions and gestures inside one shared stereo environment. Short taps behave like struck bells or tubes, while longer holds reveal deeper resonance, folding, smear, and feedback.

Normal layer:

- **Knob 1:** T1 pitch.
- **Knob 2:** T2 pitch.
- **Knob 3:** T3 pitch.
- **Knob 4:** Texture, density, and spatial depth of the gated landscape.
- **Knob 5:** Chime decay.
- **Knob 6:** Chime timbre and feedback character.

SHIFT layer:

- **Knob 1:** Generated MIDI-output transpose.
- **Knob 2:** Resonant decay and delay relationship.
- **Knob 3:** Smear and stereo wall character.
- **Knob 4:** Shared tempo and resonant motion.
- **Knob 5:** Stereo spread and chime register.
- **Knob 6:** Body/chime balance and drive.

Each physical pad sends MIDI Note On/Off. Touch strength and hold time influence the excitation, and incoming MIDI notes can play and release the TS landscape directly.

## Performance Notes

- Start with Mutation low and Body Decay high for a stable ambient foundation that only occasionally changes harmony.
- Raise Mutation to make both chime algorithms and the low body more conversational and melodic.
- The center of Melody Balance is the richest setting because both independent chime layers remain audible.
- High Reverb, long Chime Decay, and moderate Stereo Spread create the broadest shoegaze-like fields without adding broadband noise.
- In TS mode, taps create defined resonant events; holds allow the feedback and smear network to unfold.
- CV clock has priority over MIDI Clock. Regular CV pulses synchronize the musical motion and are converted to MIDI Start and 24 PPQN Clock for downstream devices.
- Two USB MIDI devices require a USB host or MIDI router between them; a direct device-to-device USB cable cannot route MIDI on its own.
