# Kac_OS Bass — manual

Version: 2026-09-18. This edition uses the Kac_OS controls and synthesis architecture, transposes audio two octaves down (`×0.25`) and protects the lowest range. TS MIDI uses the same bass transposition, allocates up to three voices and responds to Note Off.

KacOS Bass is the low-register K-Accumulator-inspired operating system for diceFriend. It combines carrier/modulator FM and phase modulation, self- and cross-feedback, wavefolding, an eight-node morph matrix, a delta-sigma step pattern, and Lorenz chaos. The Bass edition transposes the synthesis system two octaves down and protects the lowest range from collapsing into unusable sub-audio mud.

KacOS Bass is designed for animated bass sequences, deep FM percussion, growling low drones, metallic subharmonics, folded bass voices, and touch-played three-voice patterns.

KacOS Bass has two main performance modes: **RS mode** and **Touch mode**. RS mode is the continuously running delta-sigma/Lorenz sequencer. Touch mode provides three playable bass voices and four timbre engines.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE in RS mode** radically randomizes the sound and delta-sigma pattern while keeping the current speed.
- **Short DICE in Touch mode** switches to the next Touch engine.
- **Hold DICE for about 3 seconds** switches between RS mode and Touch mode.
- **SHIFT + hold DICE for about 3 seconds** randomizes the current controls.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.

The knobs use pickup behavior after changing layers, modes, or randomized values.

## CV and MIDI

- **CV1** works as a trigger/clock input and advances the delta-sigma/Lorenz system. In Touch mode it triggers successive available voices.
- **CV2** works as continuous modulation until pulses are detected; it then acts as a clock/trigger source. In Touch mode its gate opens and closes an allocated voice.
- MIDI Clock can take control of RS stepping.
- Incoming MIDI notes directly set RS pitch or use three-voice allocation in Touch mode.
- In Touch mode, the per-voice pitch knob detunes an incoming MIDI note by approximately plus or minus one octave.
- Physical pads send MIDI notes on channels 1, 2, and 3.
- RS mode outputs the current generated pitch and, under external clock, an optional second transposed MIDI layer.
- RS activity is sent as channel aftertouch and continuous CV2 as pitch bend.
- Musical incoming MIDI messages are passed through.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active knob layer.
- In RS mode, the four lower LEDs combine CV/audio activity with a binary indication of the current morph region.
- In Touch mode, touching pads lights the corresponding first three LEDs while the fourth shows output activity.
- After switching Touch engines, one lower LED briefly identifies the selected engine.
- DICE actions and mode changes produce confirmation flashes.

## RS Mode: Delta-Sigma Bass Sequencer

RS mode uses a mutable delta-sigma pattern as its pitch path. A Lorenz attractor biases the notes and adds controlled instability. That pitch drives a carrier/modulator pair whose sound moves across eight morph nodes: clean center, feedback phase modulation, two-operator PM, cross-PM, FM/AM, alternate feedback structures, and asymmetric PM.

### RS Controls

Normal layer:

- **Knob 1:** Internal speed, approximately 30-240 BPM; under external clock, transposes the second MIDI-output layer.
- **Knob 2:** Modulator harmonic ratio.
- **Knob 3:** FM/PM depth and Lorenz influence.
- **Knob 4:** Wavefolder amount.
- **Knob 5:** Harmonic stretch.
- **Knob 6:** Position in the eight-node morph matrix.

SHIFT layer:

- **Knob 1:** Fine modulator ratio/detune.
- **Knob 2:** Cross-feedback boost.
- **Knob 3:** Delta-sigma mutation chance.
- **Knob 4:** Delta-sigma pattern length, from 2 to 16 steps.
- **Knob 5:** Pattern smoothing, pitch-walk range, and Lorenz span.
- **Knob 6:** Output saturation.

### RS Touch Pad Behavior

- **T1:** Freezes the delta-sigma pitch path while held.
- **T2:** Widens the pitch walk and Lorenz orbit influence.
- **T3:** Adds phase glitch, folding, and a rough ring-modulated character.

## Morph Matrix

Knob 6 moves continuously through eight synthesis regions:

- **Centre:** Clean carrier/modulator tone.
- **FBPM:** Self-feedback phase modulation.
- **2OP:** Two-operator phase modulation.
- **XPM:** Cross-coupled phase modulation.
- **FMNT:** Phase modulation combined with UFG amplitude movement.
- **FBPM2:** A more asymmetric feedback variation.
- **2OP2:** A denser two-operator region.
- **ASYM:** Strongly asymmetric phase modulation.

Intermediate knob positions interpolate between neighboring regions rather than switching abruptly.

## Touch Mode

Touch mode provides three independent bass voices.

Normal layer:

- **Knob 1:** T1 pitch.
- **Knob 2:** T2 pitch.
- **Knob 3:** T3 pitch.
- **Knob 4:** T1 decay.
- **Knob 5:** T2 decay.
- **Knob 6:** T3 decay.

SHIFT layer:

- **Knob 1:** FM/PM depth.
- **Knob 2:** Phase grit/feedback.
- **Knob 3:** Modulator harmonic ratio.
- **Knob 4:** Wavefolder amount.
- **Knob 5:** Phase flip / ring-like inversion.
- **Knob 6:** Morph position for the KACC engine.

## Touch Engines

### Engine 0: KACC

The full RS-style morphing FM/PM core placed under a voice envelope. This is the broadest and most dynamic engine, moving from clean bass tones into feedback and asymmetric modulation.

### Engine 1: Metal

An inharmonic modulator ratio with deeper phase modulation. It produces bell-like bass attacks, metallic overtones, and clangorous low percussion.

### Engine 2: Fold

A west-coast-inspired wavefolding voice with softer phase modulation. It works well for rounded low notes that open into bright folded harmonics.

### Engine 3: Grind

A heavy phase-feedback voice with a gritty, unstable edge. It is designed for growls, distorted bass hits, and chaotic sustained tones.

## Performance Notes

- The Bass edition runs two octaves below standard KacOS, with a 20 Hz lower limit.
- Knob 6 and Knob 3 form the main RS timbre pair: Morph selects the synthesis region and Depth determines how strongly it speaks.
- SHIFT Knob 5 controls both pattern smoothness and pitch range, so it can change phrasing and melody at the same time.
- Touch mode is reactive and does not auto-trigger: use pads, CV, or MIDI.
- External clocks replace the internal step timer and enable the second transposed MIDI-output layer.
