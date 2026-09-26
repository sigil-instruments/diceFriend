# Run_OS - LEFT manual

Version: 2026-09-18. Incoming Note Off releases the MIDI pitch override. External timing remains active for about 30 seconds after the last event.

RunOS is the more raw, circular, and electrical side of diceFriend. It is built around a rungler-style generative engine and a set of touch-controlled nonlinear voices. It is good for unstable sequences, pulsing voltage patterns, folded oscillator tones, pinging filters, and touch-driven bursts that sit between percussion, drone, and melody.

RunOS has two main performance modes: **RS mode** and **Touch mode**. RS mode is the generative voice mode. Touch mode turns the three touch pads into three playable voices.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **DICE** performs a context-dependent action.
- **Hold DICE** switches between RS mode and Touch mode.
- **Short DICE in Touch mode** switches to the next Touch engine.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.
- **Touch pads T1, T2, T3** can play voices in Touch mode and alter the RS engine in RS mode.

## CV and MIDI

- **CV1** works as a trigger/clock input. In RS mode it can step the generative engine. In Touch mode it can trigger the touch voices together.
- **CV2** works as a modulation input when used as a steady voltage. When diceFriend detects pulses on CV2, it treats CV2 as a clock/trigger source instead of continuous modulation.
- MIDI Clock can drive the RS engine when no CV clock has priority.
- Incoming MIDI notes can trigger or steer the current behavior.
- In Touch mode, the pads send MIDI notes.
- Touch pressure is sent as channel pressure.
- CV2 can be sent as pitch bend when it is used as continuous modulation.
- In RS mode, diceFriend can output MIDI notes based on the current generative pitch.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active control layer.
- In normal RS operation, the four lower LEDs show incoming CV/clock activity and audio output movement.
- In Touch mode, the four lower LEDs show the selected Touch engine after switching or interacting.

## RS Mode: BiXo

The RunOS RS engine is called **BiXo**. It uses two interacting oscillators, wavefolding, feedback, cross-modulation, and a rungler-style shift register. The result is a stepped, semi-chaotic pattern generator that can sound like unstable bass sequences, metallic ticks, folded pulses, or self-modulating electronic percussion.

The RS engine listens to internal timing, external CV clock, CV2 clock, and MIDI clock. When no external clock is active, the first knob controls internal speed. When an external clock is active, the first knob becomes a MIDI transpose control for the second MIDI layer.

### RS Controls

Normal layer:

- **Knob 1:** Internal speed, or MIDI second-layer transpose when externally clocked.
- **Knob 2:** Oscillator A pitch.
- **Knob 3:** Oscillator A decay.
- **Knob 4:** Rungler chaos / pitch modulation depth.
- **Knob 5:** Cross-bleed between oscillators.
- **Knob 6:** Oscillator A fold amount.

SHIFT layer:

- **Knob 1:** Rungler bias.
- **Knob 2:** Oscillator B pitch relationship.
- **Knob 3:** Oscillator B decay.
- **Knob 4:** Cross-modulation ratio.
- **Knob 5:** Feedback low-pass filter.
- **Knob 6:** Oscillator B fold amount.

### RS Touch Pad Behavior

The touch pads remain active in RS mode as performance modifiers.

- **T1:** Emphasizes Oscillator A folding and feedback.
- **T2:** Emphasizes Oscillator B folding and feedback.
- **T3:** Increases cross-bleed and instability.
- **T1 + T2 + T3:** Freezes RS stepping while held.
- **Two-pad combinations:** Slow or interrupt steps and push the engine toward more unstable timing.

## Touch Mode

Touch mode gives the three touch pads independent voices. Each pad has its own pitch and envelope. The active Touch engine determines the synthesis character.

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

Incoming MIDI notes retune the three touch voices around the played note. CV1 can trigger all three voices together. CV2 works as tone/pitch modulation unless it is detected as a clock.

## Touch Engines

### Engine 0: Trigfeto

Trigfeto is a punchy nonlinear sine/phase-bend voice. It responds strongly to touch pressure, CV2, and fold depth. It is useful for short struck tones, clipped pulses, and aggressive but controllable touch percussion.

### Engine 1: Feton

Feton is a harmonic wavefolding voice. It has a brighter, driven character and can move from rounded tones into sharp folded harmonics. Touch pressure opens the sound and the filter, while the SHIFT layer sets the per-pad drive/fold behavior.

### Engine 2: Artefakto

Artefakto is the digital-chaos voice. It uses stretched harmonics, detune, and per-pad chaos/feedback depth. It is suited to brittle tones, unstable tuned noise, broken glass-like partials, and animated digital textures.

### Engine 3: Bulgo

Bulgo is the slow, swelling, phase-distorted voice. It rewards longer touches. After a few seconds of holding a pad, the sound develops deeper movement, resonance, and pressure-based modulation. It is the best RunOS engine for unstable drones, long resonant gestures, and living touch-controlled tones.

## Performance Notes

- External CV clock has priority over MIDI clock for RS stepping.
- CV2 automatically changes role when pulses are detected: steady voltage becomes modulation, pulses become clock/trigger.
- Touch mode sends MIDI notes from the pads, so diceFriend can be used as a touch controller as well as a sound source.
- Longer pad holds add extra pressure behavior in Touch mode.
- RunOS responds strongly to small changes. For playable results, move one or two controls at a time and listen to how the current mode reacts.
