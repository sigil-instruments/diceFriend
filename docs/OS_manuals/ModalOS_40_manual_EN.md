# Modal_OS — manual

Version: 2026-09-18. In TS, a short unshifted DICE selects STRINGS, BARS, CAVE or POLY. AS MIDI CC mapping is CC20=left pitch, CC21=speed, CC22=right pitch, CC23=feedback, CC24=chaos, CC25=decay and CC26–31=SHIFT P1–P6. TS uses CC52–57 for its normal layer and CC58–63 for its shifted layer.

ModalOS is a resonator-based operating system for diceFriend. It turns triggers, touch, feedback, and chaotic motion into ringing objects: strings, bars, caves, and clustered modal bodies.

ModalOS has two main performance modes: **RS mode** and **Touch mode**. RS mode continuously excites a stereo modal bank from internal motion. Touch mode turns the three touch pads into three struck modal voices.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Hold DICE** switches between RS mode and Touch mode.
- **Short DICE** switches to the next modal engine.
- **SHIFT + DICE in RS mode** randomizes RS parameters.
- **SHIFT + DICE in Touch mode** randomizes timbre while keeping pitch under the knobs.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.

## CV and MIDI

- **CV1** works as a trigger/clock input. In RS mode it can step or excite the modal system. In Touch mode it can strike all three touch voices together.
- **CV2** can work as a trigger/clock source when pulses are detected.
- MIDI Clock can drive the RS motion when no CV clock has priority.
- Incoming MIDI notes can trigger or steer the current pitch.
- In Touch mode, the pads send MIDI notes.
- Touch pressure and held-pad energy are sent as channel pressure.
- The RS engine can output MIDI notes and pitch bend from the current resonator pitch.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active control layer.
- The four lower LEDs briefly show the selected modal engine after switching.
- In Touch mode, the lower LEDs show the active engine when pads or controls are used.
- During normal operation, the LEDs follow CV activity and audio level.

## Modal Engines

ModalOS has four resonator models. Each one changes the harmonic structure of the modal bank.

### Engine 0: Strings

Strings is the most harmonically familiar mode. It uses a harmonic resonator structure that feels close to plucked or bowed strings. It works well for melodic patterns, warm ringing tones, and sustained resonant gestures.

### Engine 1: Bars

Bars uses a more metallic, inharmonic structure. It is suited to struck metal, mallet-like attacks, tuned percussion, and bright resonant pings.

### Engine 2: Cave

Cave uses a darker, more spacious resonator structure. It produces deep, uneven resonances and hollow bodies. It is useful for drones, low ringing spaces, and shadowy percussion.

### Engine 3: Poly

Poly creates a more complex modal body with multiple partial relationships. It can behave like a small cluster of resonators, making richer chords, dense strikes, and layered harmonic responses.

## RS Mode

In RS mode, ModalOS uses internal chaotic motion to excite a stereo pair of modal banks. The left and right sides can move independently, creating shifting resonant patterns.

The RS engine can run from its internal clock, CV clock, CV2 clock, or MIDI clock. It also includes a self-excitation behavior, so the resonators remain alive and can keep moving even between obvious strikes.

### RS Controls

Normal layer:

- **Knob 1:** Internal speed, or MIDI second-layer transpose when externally clocked.
- **Knob 2:** Left/modal root pitch.
- **Knob 3:** Right/modal root pitch.
- **Knob 4:** Feedback amount.
- **Knob 5:** Chaos / exciter instability.
- **Knob 6:** Decay time.

SHIFT layer:

- **Knob 1:** Drive / excitation strength.
- **Knob 2:** LFSR clock / digital impulse rate.
- **Knob 3:** Resonator density.
- **Knob 4:** Detune / stereo spread.
- **Knob 5:** LFSR density / impulse complexity.
- **Knob 6:** Modal mix / excitation balance.

## Touch Mode

Touch mode gives each touch pad its own modal voice. Touching a pad strikes the resonator. Holding a pad lets the sound continue to ring and develop.

Normal layer:

- **Knob 1:** T1 pitch.
- **Knob 2:** T2 pitch.
- **Knob 3:** T3 pitch.
- **Knob 4:** T1 decay.
- **Knob 5:** T2 decay.
- **Knob 6:** T3 decay.

SHIFT layer:

- **Knob 1:** Exciter chaos.
- **Knob 2:** Exciter level.
- **Knob 3:** Feedback amount.
- **Knob 4:** Drive.
- **Knob 5:** Detune.
- **Knob 6:** Fold / strike character.

CV1 can strike all three voices together. Incoming MIDI notes can retune and trigger the Touch voices.

## Performance Notes

- ModalOS responds strongly to decay and feedback. Small changes can turn a short strike into a long resonating body.
- The four engines are not just presets; they change the structure of the resonator itself.
- Touch mode is best for played, struck sounds. RS mode is best for evolving resonant motion.
- Use CV1 for precise strikes and clocked patterns. Use DICE to quickly find new resonant spaces.
