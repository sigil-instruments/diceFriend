# Pulsar_OS — manual

Version: 2026-09-18. A short DICE in TS randomizes the complete scene and chooses a random TS engine. TS MIDI allocates up to three voices and responds to Note Off.

PulsarOS is the pulse-density and nonlinear-feedback operating system for diceFriend. Its Run mode combines two interacting pulsar generators with evolving step patterns, Lorenz-style drift, bursts, stereo spread, and feedback orbiting. Its Touch mode provides three playable pulsar voices with four different synthesis characters.

PulsarOS is suited to sparse pointillistic rhythms, dense pulse clouds, metallic feedback, broken clock patterns, animated drones, and touch-controlled digital percussion.

PulsarOS has two main performance modes: **RS mode** and **Touch mode**. RS mode is the generative dual-pulsar engine. Touch mode turns the three touch pads into three independent playable voices.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE in RS mode** randomizes the sound and step pattern while keeping the current tempo.
- **Short DICE in Touch mode** randomizes the sound and selects a random Touch engine.
- **Hold DICE for about 3 seconds** switches between RS mode and Touch mode.
- **SHIFT + hold DICE for about 3 seconds** randomizes and resets the current setup.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.

The knobs use pickup behavior after changing layers or randomizing, preventing sudden parameter jumps.

## CV and MIDI

- **CV1** works as a trigger/clock input. In RS mode it advances the orbit and step pattern; in Touch mode it triggers successive available voices.
- **CV2** works as continuous modulation when used as a steady voltage. When pulses are detected, it becomes a clock/trigger source.
- MIDI Clock can drive the generative engine and takes priority while present.
- Incoming MIDI notes steer pitch in RS mode and use three-voice allocation in Touch mode.
- Physical pads send MIDI notes on channels 1, 2, and 3.
- RS mode outputs notes derived from the current pulsar pitch, plus a second transposed layer when externally clocked.
- Pulsar activity and feedback are sent as MIDI CC 16, 17, and 18; continuous CV2 is sent as pitch bend.
- Musical incoming MIDI messages are passed through.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active knob layer.
- In normal operation, the four lower LEDs show CV1 activity, CV2 level, left-channel activity/feedback, and right-channel or pad activity.
- In Touch mode, the selected engine is briefly shown by one of the four lower LEDs.
- A short DICE action produces a confirmation flash.

## RS Mode: Dual Pulsar Orbit

The RS engine creates sound from short pulse windows rather than conventional continuous waveforms. Pulse density, width, nonlinear shaping, and feedback determine whether the result is a slow sequence, a rattling texture, or a continuous audio-rate tone. A mutable 2-16 step pattern and a Lorenz-style orbit continuously influence the engine.

### RS Controls

Normal layer:

- **Knob 1:** Internal speed and primary pulse density; when externally clocked, transposes the second MIDI-output layer.
- **Knob 2:** Pulse width.
- **Knob 3:** Feedback amount.
- **Knob 4:** Nonlinear shaping, from saturation through folding and asymmetric clipping.
- **Knob 5:** Drift/chaos amount and the influence of the evolving step pattern.
- **Knob 6:** Tone/filter brightness.

SHIFT layer:

- **Knob 1:** Stereo spread; higher settings push the pulsar system into audio-rate behavior.
- **Knob 2:** Cross-feedback amount and activation.
- **Knob 3:** Step-pattern mutation probability.
- **Knob 4:** Pattern length, from 2 to 16 steps.
- **Knob 5:** Step smoothing and orbit influence.
- **Knob 6:** Output drive.

### RS Touch Pad Behavior

- **T1:** Freezes orbit and pattern stepping while held and adds fold/feedback pressure.
- **T2:** Adds burst energy, feedback, and smear.
- **T3:** Adds a contrasting nonlinear pulse effect.
- Pad combinations are gain-compensated to keep multi-pad gestures playable.

## Touch Mode

Touch mode provides three independent pulsar voices.

Normal layer:

- **Knob 1:** T1 pitch.
- **Knob 2:** T2 pitch.
- **Knob 3:** T3 pitch.
- **Knob 4:** T1 decay.
- **Knob 5:** T2 decay.
- **Knob 6:** T3 decay.

When a MIDI note controls a voice, its pitch knob becomes a detune control with a range of approximately plus or minus one octave.

SHIFT layer:

- **Knob 1:** Pulse width.
- **Knob 2:** Feedback.
- **Knob 3:** Nonlinear shape.
- **Knob 4:** Stereo spread.
- **Knob 5:** Body/resonance.
- **Knob 6:** Output drive.

## Touch Engines

### Engine 0: Classic Pulsar

A clean pulsar voice focused on pulse width and density. It ranges from isolated clicks and woody impulses to compact pitched tones.

### Engine 1: Cross-Feedback

A more metallic voice with stronger interaction between pulse paths. It works well for bells, bright digital percussion, and unstable stereo motion.

### Engine 2: Folded Pulsar

A wavefolded variation with denser harmonics and sharper attacks. It is useful for aggressive plucks, clipped bass hits, and rough pulse trains.

### Engine 3: Feedback Cloud

A smeared, feedback-heavy variation that turns short pulses into broader noisy bodies. It is best for sustained touches, clouds, and unstable drones.

## Performance Notes

- Low density and narrow width produce isolated impulses; raising either parameter makes the sound increasingly continuous.
- Feedback and nonlinear shaping are strongly interactive, so small movements can have large results.
- External CV clock has priority over the internal RS timer; MIDI Clock takes control while it is present.
- Touch mode is purely reactive: pads, CV, or MIDI must trigger a voice.
- PulsarOS includes automatic recovery from silent feedback states.
