# CIG_OS — manual

Version: 2026-09-18. Without SHIFT, P1 controls internal clock and post-fold; with SHIFT, it controls oscillator A rate. Hold DICE for about 1.8 seconds to change mode. TS opens the shared synthesis core.

CIG_OS is the Compact Impulse Generator operating system for diceFriend. It uses the BlipOS cross-coupled impulse core as its first layer, then feeds it into a second processing layer inspired by KacOS, ImpOS, and deliberately unstable digital memory instruments. The result moves between clean pulse trains, unstable blips, resonant strikes, folded clicks, sputtering feedback, and broken delay-like fragments.

CIG_OS is designed for chaotic pulse synthesis, lively master-clock behavior, lo-fi retained echoes, digital edge, short percussive events, and textures that feel unstable without becoming permanently stuck.

CIG_OS has two performance modes: **Run mode** and **Touch mode**. Run mode keeps the impulse system continuously active. Touch mode gates the same core from the touch pads, CV, or MIDI.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE** randomizes the sound while keeping the current performance mode.
- **SHIFT + short DICE** performs a deeper randomization.
- **Hold DICE for about 2 seconds** switches between Run mode and Touch mode.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.
- **Touch pads T1, T2, T3** reshape the system in Run mode and open the sound in Touch mode.

After randomization or a layer change, the knobs use pickup behavior: a knob must move away from its previous physical position before it takes control. This prevents sudden parameter jumps.

## CV and MIDI

- **CV1** works as a trigger and clock input. Each rising edge strikes and nudges the synthesis core.
- **CV2** reacts to rising pulses as an additional trigger/clock source and also works as continuous modulation.
- CV1 and CV2 pulses generate short MIDI notes 36 and 37 on MIDI channel 1.
- CV2 sends MIDI CC 74, pitch bend, and channel aftertouch with rate limiting.
- Incoming MIDI notes retune and strike the sound; note velocity controls the strength of the impact.
- Incoming MIDI Clock drives repeated strikes. Start and Continue also wake the engine.
- When no external clock is present, CIG_OS generates MIDI Clock from Knob 1's internal speed setting.
- Internal master clock has a controlled unevenness: each step can breathe slightly shorter or longer, while the 24 PPQN clock pulses inside the step remain usable for external MIDI devices.
- Stable CV clock sends MIDI Start and 24 PPQN MIDI Clock so other devices can follow CIG_OS as master.
- The twelve knob-layer values are available over MIDI CC: normal-layer controls use CC 20-25 and SHIFT-layer controls use CC 26-31.

CIG_OS does not echo incoming USB MIDI as thru on the same USB port. Its MIDI output is generated from CV, clock, knob movement, and internal state to avoid feedback loops with hosts or other diceFriend units.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active knob layer.
- The four lower LEDs display activity from the two internal shift registers.
- In Touch mode, their brightness follows the touch gate and audio activity.
- Incoming MIDI briefly lights the first lower LED.
- Short flashes confirm randomization and switching between Run and Touch modes.

## Run Mode

Run mode leaves the impulse core continuously open. Two clocked triangle oscillators drive interacting shift registers, sample-and-hold feedback, resonant peak channels, folding, and a small randomly traversed memory register. The sound can behave like a clocked blip generator, a rough resonator, a sputtering digital delay, or a self-reorganizing pulse instrument.

### Run Controls

Normal layer:

- **Knob 1:** Oscillator A rate / internal MIDI clock speed.
- **Knob 2:** Oscillator B pitch relationship.
- **Knob 3:** Resonant Peak 1 frequency.
- **Knob 4:** Resonant Peak 2 frequency.
- **Knob 5:** Peak spread, modulation depth, source balance, and excitation.
- **Knob 6:** Output gain, grit, resonance, and stereo spread.

SHIFT layer:

- **Knob 1:** Post wavefolding amount.
- **Knob 2:** Post feedback amount.
- **Knob 3:** Post tone balance.
- **Knob 4:** Retention amount.
- **Knob 5:** Retention scan position.
- **Knob 6:** Retention jitter, stereo edge, and internal clock unevenness.

### Run Touch Pad Behavior

- **T1:** Pushes oscillator-rate movement and adds more folding pressure.
- **T2:** Increases rungler influence and post feedback.
- **T3:** Emphasizes resonant-peak motion and post tone movement.
- Longer holds deepen each pad's effect.

## Retention Layer

The Retention layer is a small random-access memory register placed after the impulse core. Instead of acting like a clean tempo delay, it stores recent material and reads it back from unstable positions. This can create comb-like ringing, short echoes, discontinuous fragments, pitchy smears, and digital artifacts.

The SHIFT layer controls how strongly this memory speaks:

- **Post Fold** bends and folds the impulse core before the memory register.
- **Post Feedback** recirculates energy through the post layer.
- **Post Tone** moves between darker retained material and brighter edge.
- **Retention** blends the memory register into the sound.
- **Retention Scan** chooses where the register is read.
- **Retention Jitter** destabilizes the read position and also makes the internal master clock less even.

## Touch Mode

Touch mode uses the same CIG_OS core, but closes its output until a touch pad, CV pulse, or MIDI note opens the gate. It is not a conventional three-voice mode: all three pads excite and reshape one shared stereo synthesis system.

- Touching any pad opens the sound.
- Each pad retains its own gesture role from Run mode.
- Longer holds gradually open the resonant and retained system further, producing longer, brighter, and more unstable tones.
- CV1, CV2, and incoming MIDI notes can trigger the gate without touching a pad.
- The knob layout remains the same as in Run mode.

## Performance Notes

- Use the normal layer for the basic pulse generator: rate, pitch relationship, resonant peaks, excitation, and drive.
- Use the SHIFT layer for the more radical CIG character: fold, feedback, retained memory, scan, and jitter.
- Knob 1 sets internal speed when CIG_OS is master. Under external clock, Knob 1 controls the second MIDI-output layer transpose.
- SHIFT Knob 6 is the quickest way to make the internal master clock less even.
- High Retention and Jitter settings can make past fragments reappear unpredictably.
- Extreme high-frequency lockups are softened by a high-rail tamer: most repeated top-end states are folded slightly downward, while rare peaks are still allowed through.
- In Touch mode, short taps behave like struck digital resonators, while longer holds reveal feedback and retained memory movement.
- CIG_OS includes a silence-protection system that nudges the internal state away from dead zones while preserving the current character where possible.
