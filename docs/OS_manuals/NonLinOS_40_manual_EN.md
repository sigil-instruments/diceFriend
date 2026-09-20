# NonLin_OS — manual

Version: 2026-09-18. SHIFT + short DICE in AS changes Lorenz/Dadras; unshifted short DICE creates a new scene and scale. CC74 is available for TS modulation. Note Off releases the MIDI pitch override.

NonLinOS is the nonlinear chaos operating system for diceFriend. It combines melodic attractor sequencing with wavefolding, resonant pinging, feedback movement, and unstable digital touch voices. Compared with AltOS, NonLinOS is more aggressive, more physical, and more focused on nonlinear behavior: bent tones, pressure, folded harmonics, feedback edges, and patterns that feel alive without becoming predictable.

NonLinOS works well for chaotic melodic phrases, metallic resonator sequences, folded bass motion, glitchy tuned noise, unstable percussion, and touch-controlled digital drones.

NonLinOS has two main performance modes: **RS mode** and **Touch mode**. RS mode is the generative nonlinear voice mode. Touch mode turns the three touch pads into three playable voices.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **DICE** performs a context-dependent action.
- **Hold DICE** switches between RS mode and Touch mode.
- **Short DICE in Touch mode** switches to the next Touch engine.
- **Short DICE in RS mode** randomizes the current generative setup and selects a new scale.
- **SHIFT + DICE in RS mode** switches between the Lorenz and Dadras attractors.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.
- **Touch pads T1, T2, T3** can play voices in Touch mode and alter the attractor behavior in RS mode.

## CV and MIDI

- **CV1** works as a trigger/clock input. In RS mode it can step the generative engine. In Touch mode it can trigger the touch voices together.
- **CV2** works as a modulation input when used as a steady voltage. When diceFriend detects pulses on CV2, it treats CV2 as a clock/trigger source instead of continuous modulation.
- MIDI Clock can drive the RS engine when no CV clock has priority.
- Incoming MIDI notes can trigger or steer the current behavior.
- In Touch mode, the pads send MIDI notes.
- Touch pressure is sent as channel pressure.
- CV2 can be sent as pitch bend when it is used as continuous modulation.
- In RS mode, diceFriend can output MIDI notes based on the current generative pitch.
- The RS engine also sends attractor movement as MIDI controller data, allowing the chaotic motion to animate external instruments.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active control layer.
- In normal RS operation, the four lower LEDs show incoming CV/clock activity and audio output movement.
- In Touch mode, the four lower LEDs show the selected Touch engine after switching or interacting.
- When changing attractor, the lower LEDs briefly show the selected attractor.
- When changing scale, the lower LEDs briefly show the selected scale as a binary-style indication.

## RS Mode: Nonlinear Attractors

NonLinOS RS mode is built around two chaotic attractor systems: **Lorenz** and **Dadras**. These systems create moving internal coordinates that are mapped to pitch, filter movement, fold amount, resonant pinging, and MIDI output. The pitch is quantized to one of eight musical scales, so the result can stay musically useful while still behaving like a nonlinear system.

Lorenz tends to feel wide, orbiting, and fluid. Dadras is tighter, more angular, and more nervous. In NonLinOS, both attractors are pushed through a more nonlinear sound path, with stronger emphasis on fold, ping, decay, feedback color, and unstable transitions between steps.

The RS engine listens to internal timing, external CV clock, CV2 clock, and MIDI clock. When no external clock is active, the first knob controls internal speed. When an external clock is active, the first knob becomes a MIDI transpose control for the second MIDI layer.

## Scales

NonLinOS includes eight scale maps:

- Minor Pentatonic
- Whole Tone
- Harmonic Series
- Hexatonic Augmented
- Phrygian
- Tritone Mirror
- Pythagorean Fifths
- Enigmatic

## RS Controls

Normal layer, Lorenz:

- **Knob 1:** Internal speed, or MIDI second-layer transpose when externally clocked.
- **Knob 2:** Root pitch.
- **Knob 3:** Lorenz rho / motion width.
- **Knob 4:** Chaos amount.
- **Knob 5:** Filter base.
- **Knob 6:** RS decay.

Normal layer, Dadras:

- **Knob 1:** Internal speed, or MIDI second-layer transpose when externally clocked.
- **Knob 2:** Root pitch.
- **Knob 3:** Dadras B parameter.
- **Knob 4:** Dadras C parameter.
- **Knob 5:** Dadras D parameter.
- **Knob 6:** RS decay.

SHIFT layer, both attractors:

- **Knob 1:** Scale selection.
- **Knob 2:** Pitch range.
- **Knob 3:** Fold amount.
- **Knob 4:** Bleed/texture amount.
- **Knob 5:** Feedback low-pass filter.
- **Knob 6:** Ping/fold intensity and chaos amount.

## RS Touch Pad Behavior

The touch pads modify the attractor behavior in RS mode. They are not only triggers; they push the nonlinear system into different regions while the pattern is running.

- **T1:** Pushes the attractor toward brighter, wider, more open motion.
- **T2:** Changes the curvature and internal pressure of the attractor.
- **T3:** Pulls the attractor into a more unstable or contrasting region.
- **T1 + T2 + T3:** Freezes RS stepping while held.
- **Two-pad combinations:** Interrupt or thin the step flow, creating gaps, skips, and irregular phrasing.

NonLinOS also keeps RS patterns from getting stuck on a single repeated note for too long. When the same pitch repeats too much, the engine nudges the melody into a nearby scale degree, preserving motion while keeping the phrase related to the current scale.

## Touch Mode

Touch mode in NonLinOS turns the three pads into playable nonlinear digital voices. Each pad has its own pitch and envelope. The active Touch engine determines the synthesis character.

Normal layer:

- **Knob 1:** T1 pitch.
- **Knob 2:** T2 pitch.
- **Knob 3:** T3 pitch.
- **Knob 4:** T1 decay.
- **Knob 5:** T2 decay.
- **Knob 6:** T3 decay.

SHIFT layer:

- **Knob 1:** T1 tone/filter control.
- **Knob 2:** T2 tone/filter control.
- **Knob 3:** T3 tone/filter control.
- **Knob 4:** T1 fold/feedback amount.
- **Knob 5:** T2 fold/feedback amount.
- **Knob 6:** T3 fold/feedback amount.

In Engine 2, the last three SHIFT controls become per-voice chaos/feedback depth instead of fold.

Incoming MIDI notes retune the three touch voices around the played note. CV1 can trigger all three voices together. CV2 works as pitch/timbre modulation unless it is detected as clock.

## Touch Engines

### Engine 0: Duffing Phase

Duffing Phase uses double-well chaotic motion to bend and distort the phase of the voice. It can move from thick nonlinear tone to growling pressure and unstable harmonic movement. It is useful for expressive pad strikes, distorted sustained tones, and sounds that react strongly to touch pressure.

### Engine 1: Granular Scrambler

Granular Scrambler creates a noisy, grain-based digital texture with feedback. It can sound like chopped static, unstable digital air, rough pitched noise, or a broken cloud of particles. The engine responds well to touch pressure, CV2 modulation, and higher feedback settings.

### Engine 2: LFSR Resonator

LFSR Resonator combines digital shift-register pulses with a nonlinear resonator. At lower settings it behaves like rhythmic digital noise; at higher settings it becomes more tonal, pinged, and resonant. It is suited to glitch percussion, synthetic plucks, tuned noise, and digital sparks with pitch.

### Engine 3: Rossler FM/AM

Rossler FM/AM uses a slow chaotic system to modulate pitch and amplitude. It has a breathing, unstable quality that develops over time. This engine is best for long touches, animated drones, pressure-shaped tones, and slow nonlinear movement.

## Performance Notes

- External CV clock has priority over MIDI clock for RS stepping.
- CV2 automatically changes role when pulses are detected: steady voltage becomes modulation, pulses become clock/trigger.
- Touch mode sends MIDI notes from the pads, so diceFriend can be used as a touch controller as well as a sound source.
- Longer pad holds add extra pressure behavior in Touch mode.
- NonLinOS is at its best when the attractor, fold, ping, and decay controls are balanced against each other. Small changes can shift the sound from melodic sequence to metallic percussion or unstable drone.
- For more musical results, start with lower chaos and fold settings, choose a scale, then increase ping/fold intensity until the pattern begins to break open.
