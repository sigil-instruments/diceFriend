# Blip_OS - LEFT manual

Version: 2026-09-18. Without SHIFT, P1 controls internal clock speed and rungler influence; with SHIFT, it controls oscillator A rate. Hold DICE for about 1.8 seconds to change Run/Touch mode. TS opens the shared synthesis core.

BlipOS is the cross-coupled, clocked-chaos operating system for diceFriend. It is inspired by the Blippoo Box approach: two triangle oscillators drive interacting shift registers, sample-and-hold feedback, and a pair of resonant peak channels. The result moves between unstable bass pulses, ringing filters, interlocking patterns, gritty drones, and sharp clocked strikes.

BlipOS is especially useful for self-generating electronic textures, irregular rhythmic structures, resonant noise, and sounds that continuously reorganize themselves without losing their underlying pulse.

BlipOS has two performance modes: **Run mode** and **Touch mode**. Run mode keeps the cross-coupled system continuously active. Touch mode gates the same synthesis core from the touch pads, CV, or MIDI.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE** randomizes the sound while keeping the current performance mode.
- **SHIFT + short DICE** performs a deeper randomization.
- **Hold DICE for about 2 seconds** switches between Run mode and Touch mode.
- **Touch pads T1, T2, T3** reshape the system in Run mode and open the sound in Touch mode.

After randomization or a layer change, the knobs use pickup behavior: a knob must move away from its previous physical position before it takes control. This prevents sudden parameter jumps.

## CV and MIDI

- **CV1** works as a trigger and clock input. Each rising edge strikes and nudges the synthesis core.
- **CV2** reacts to rising pulses as an additional trigger/clock source and also sends its level as MIDI CC 74.
- CV1 and CV2 pulses generate short MIDI notes 36 and 37 on MIDI channel 1.
- Incoming MIDI notes retune and strike the sound; note velocity controls the strength of the impact.
- Incoming MIDI Clock drives repeated strikes. Start and Continue also wake the engine.
- When no external clock is present, BlipOS generates MIDI Clock from Knob 1's internal speed setting.
- Incoming MIDI notes, CC, aftertouch, pitch bend, and realtime transport/clock messages are passed through.
- The twelve knob-layer values are available over MIDI CC: normal-layer controls use CC 20-25 and SHIFT-layer controls use CC 26-31.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active knob layer.
- The four lower LEDs display activity from the two internal shift registers.
- In Touch mode, their brightness follows the touch gate and audio activity.
- Short flashes confirm randomization and switching between Run and Touch modes.

## Run Mode

Run mode leaves the BlipOS core continuously open. Two oscillators clock each other's shift-register states, while sample-and-hold feedback changes oscillator rates and separates the two resonant peaks. The interaction is deterministic but unstable enough to produce patterns that feel alive and difficult to repeat exactly.

### Run Controls

Normal layer:

- **Knob 1:** Oscillator A rate / internal MIDI clock speed.
- **Knob 2:** Oscillator B pitch relationship.
- **Knob 3:** Resonant Peak 1 frequency.
- **Knob 4:** Resonant Peak 2 frequency.
- **Knob 5:** Peak spread, modulation depth, and excitation.
- **Knob 6:** Output gain and grit.

SHIFT layer:

- **Knob 1:** Rungler modulation sent to Oscillator A.
- **Knob 2:** Rungler modulation sent to Oscillator B.
- **Knob 3:** Sample-and-hold modulation sent to Oscillator A.
- **Knob 4:** Sample-and-hold modulation sent to Oscillator B.
- **Knob 5:** Shift-register source balance and resonant-peak modulation direction.
- **Knob 6:** Resonance, stereo spread, grit, and the relationship between the two oscillator rates.

### Run Touch Pad Behavior

- **T1:** Pushes oscillator rate movement and makes the clock interaction more animated.
- **T2:** Increases rungler influence and pattern instability.
- **T3:** Emphasizes resonant-peak movement and ringing character.
- Longer holds deepen each pad's effect.

## Touch Mode

Touch mode uses the same cross-coupled BlipOS engine, but closes its output until a touch pad, CV pulse, or MIDI note opens the gate. It is not a conventional three-voice mode: all three pads excite and reshape one shared stereo synthesis system.

- Touching any pad opens the sound.
- Each pad retains its own gesture role from Run mode.
- Longer holds gradually open the resonant system further, producing longer and brighter tones.
- CV1, CV2, and incoming MIDI notes can trigger the gate without touching a pad.
- The knob layout remains the same as in Run mode.

## Performance Notes

- Knob 5 and SHIFT Knob 6 are the quickest route from sparse clicks to sustained resonant textures.
- High modulation and resonance settings can reorganize the pattern dramatically after a single trigger.
- In Touch mode, short taps behave like struck resonators, while longer holds reveal drones and feedback motion.
- BlipOS includes a silence-protection system that nudges the internal state away from dead zones while preserving the current character where possible.
