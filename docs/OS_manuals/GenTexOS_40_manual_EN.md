# GenTex_OS - LEFT manual

Version: 2026-09-18. TS uses one shared gated texture engine. The pads blend pitch and add fold, delay and filter gestures. P1-P3 influence texture pitch, P4 feedback, P5 texture and P6 the delay/resonance relationship. MIDI Note On opens the shared gate and changes timbre and energy; Note Off closes the gate.

GenTexOS is a nonlinear texture generator for diceFriend. It is built for feedback, folding, filtering, micro-delay, smearing, bit reduction, and self-moving stereo textures.

GenTexOS has two main performance modes: **RS mode** and **Touch mode**. RS mode is a self-running texture loop. Touch mode turns the three pads into struck resonant texture voices.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE** randomizes both control layers at once.
- **Hold DICE** switches between RS mode and Touch mode.
- **Touch pads T1, T2, T3** behave differently in RS mode and Touch mode.

## CV and MIDI

- **CV1** works as a continuous modulation source for fold and chaos.
- **CV2** works as a trigger/clock detector when pulses are present.
- CV2 triggers create macro movements inside the texture: feedback spike, fold sweep, delay scatter, and filter dip.
- GenTexOS can send MIDI notes from CV2-triggered texture events.
- MIDI aftertouch follows the current audio energy.
- MIDI pitch bend follows the CV modulation.
- Incoming MIDI is passed through.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active control layer.
- In RS mode, the lower LEDs follow CV activity and audio movement.
- In Touch mode, the lower LEDs show active pads for a few seconds after touch or knob movement.
- A DICE action briefly flashes the lower LEDs.

## RS Mode

RS mode is the main GenTex texture engine. It uses a self-referencing feedback path with wavefolding, filtering, micro-delay, delay smear, and output saturation.

The sound can move from quiet electrical movement to rough folded noise, resonant delay chatter, unstable stereo feedback, and bit-crushed texture beds.

### RS Controls

Normal layer:

- **Knob 1:** Feedback amount.
- **Knob 2:** Fold amount.
- **Knob 3:** Delay time.
- **Knob 4:** Chaos injection.
- **Knob 5:** Filter cutoff.
- **Knob 6:** Filter resonance.

SHIFT layer:

- **Knob 1:** Pre-gain.
- **Knob 2:** Fold asymmetry.
- **Knob 3:** Delay smear.
- **Knob 4:** Bit depth.
- **Knob 5:** Filter mode.
- **Knob 6:** Output saturation.

### RS Touch Pad Behavior

In RS mode, the pads directly alter the texture loop.

- **T1:** Freeze. Holds the current delay/feedback texture.
- **T2:** Smear. Adds animated delay smear and stereo blur.
- **T3:** Spike. Pushes the feedback into a stronger burst.

Releasing a pad cleans up the loop so the texture can move again without becoming stuck.

## Touch Mode

Touch mode uses a separate three-voice texture instrument. The pads trigger individual voices while the same six knobs define their pitch, decay, resonance, brightness, and nonlinear character.

Normal layer:

- **Knob 1:** T1 pitch.
- **Knob 2:** T2 pitch.
- **Knob 3:** T3 pitch.
- **Knob 4:** T1 decay.
- **Knob 5:** T2 decay.
- **Knob 6:** T3 decay.

SHIFT layer:

- **Knob 1:** Resonance / Q.
- **Knob 2:** Stereo spread.
- **Knob 3:** Brightness.
- **Knob 4:** Character.
- **Knob 5:** Fine tune.
- **Knob 6:** Fold drive.

Touch mode is more playable and more percussive than RS mode. It is useful for struck textures, resonant clicks, folding pings, and noisy pitched gestures.

## DICE Randomization

Short DICE randomizes the full texture setup. The randomizer is designed to make audible changes, so DICE should not feel like a tiny or hidden variation.

Randomization affects feedback, fold, delay, chaos, filter, pre-gain, smear, bit depth, filter mode, and saturation.

## Performance Notes

- GenTexOS is intentionally sensitive to feedback. Small changes can produce large shifts.
- Use T1 Freeze to capture a texture, T2 Smear to blur it, and T3 Spike to push it into a burst.
- CV2 triggers are useful for rhythmic texture events.
- Touch mode is the safer place for pitched, pad-based performance.
- RS mode is best for evolving texture, noise beds, and unstable stereo feedback.
