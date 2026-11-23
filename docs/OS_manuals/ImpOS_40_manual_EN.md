# Imp_OS - LEFT manual

English manual. Hardware: diceFriend LEFT, Teensy 4.0.

Imp_OS is a stereo impulse instrument. A continuously variable pulse rate, narrow waveform windows, sixteen shape families and evolving stereo masks produce everything from isolated clicks to pitched buzzes and dense recursive textures. Period and Width modulation add slow motion or rapid disturbance. Feedback, filtering and three touch gestures reshape the same sound engine.

## Quick start

1. Connect USB power and the stereo audio output. Begin with a low listening level.
2. Start on the NS layer in AS mode. Leave MASK and the two modulation controls low for a clear pulse.
3. Move PERIOD to set the pulse rate, then WIDTH and SHAPE to find its body and edge.
4. Select SHIFT and adjust TONE, STEREO and FEEDBACK. Use LEVEL to balance the output.
5. Tap DICE for a new complete patch. Hold DICE without SHIFT for 3 seconds to enter TS, then hold a pad to play.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | PERIOD: pulse rate / base pitch | LFO RATE: speed of internal modulation |
| P2 | WIDTH: length of the waveform window | FEEDBACK: recursive phase and waveform interaction |
| P3 | SHAPE: waveform family and feedback character | STEREO: interaction between left and right channels |
| P4 | MASK: evolving pulse selection and stereo gating | RANDOM SMOOTH: smoothing of internal movement |
| P5 | PERIOD MOD: modulation of pulse rate | TONE: output low-pass filtering |
| P6 | WIDTH MOD: modulation of the waveform window | LEVEL: output level |

The map is shared by AS and TS. SHIFT selects the second layer. After startup, a layer change, DICE or a panel MIDI CC, a knob keeps the stored value until it moves by more than about 8% of its full travel from the armed position. Physical readings are inverted for diceFriend LEFT.

### Period, Width and Shape

PERIOD moves the engine from separated impulses toward a pitched pulse stream. WIDTH determines how much of each cycle contains the waveform. Small windows give sharp ticks and thin spectra; larger windows reveal more of the waveform. SHAPE moves through sixteen waveform families and changes recursive feedback character across its range.

### Mask and modulation

MASK selects evolving patterns of accepted and suppressed impulses, including alternating stereo behavior. Some settings create sparse passages. PERIOD MOD and WIDTH MOD introduce movement into the pulse rate and waveform window. LFO RATE sets the speed of that movement, while RANDOM SMOOTH shapes its continuity.

## AS mode

AS runs the impulse engine continuously. The pads act as held transformations:

- T1 applies spectral phase folding.
- T2 applies bit crushing and sample-rate reduction.
- T3 drives recursive feedback overload and noisy instability.
- Hold all three pads together to mute AS. Release them to return.

Two pads can combine their transformations. The six knobs continue to shape the running patch.

## TS mode

TS turns the same impulse engine into a gated touch voice. Any single pad opens it. Two or three held pads add amplitude and recursive modulation. Release the pads to let the voice decay.

The three pads share one engine and one pitch. Use PERIOD for manual tuning. Incoming MIDI notes set pitch and open the voice; a matching Note Off releases the MIDI gate. CV pulses and MIDI Clock also trigger the TS voice.

## DICE and SHIFT

- Tap DICE to randomize all twelve patch parameters.
- Hold DICE without SHIFT for about 3 seconds to switch AS / TS.
- Hold SHIFT + DICE for about 10 seconds to enter the Teensy bootloader.

DICE randomization keeps LEVEL in its upper range. Move a knob through its pickup threshold to take control of the randomized value.

## CV inputs

- CV1 triggers an immediate impulse and a short TS excitation. It also sends MIDI Note 60 and one MIDI Clock message.
- CV2 continuously modulates PERIOD. Rising pulses can trigger the voice and send MIDI Note 62 plus one MIDI Clock message. Its smoothed level also sends CC74.

Use the banana GND connection when patching another instrument. Keep the listening level low when introducing modulation.

## USB MIDI In

- Note On sets pitch and creates a new audible impulse in AS or TS.
- The most recent note owns the monophonic MIDI pitch. Its Note Off, or Note On with velocity zero, releases the MIDI gate and returns pitch to PERIOD.
- Every 24 MIDI Clock messages trigger an impulse.
- Start and Continue enable the autonomous latch. Stop and System Reset release the latch and MIDI gate.
- CC20-25 control the six NS parameters in order.
- CC26-31 control the six SHIFT parameters in order.
- CC74 controls SHAPE. CC1 controls MASK.

## USB MIDI Out

Output uses channel 1. CV1 sends Note 60, CV2 pulses send Note 62, and T1-T3 send notes 61, 63 and 66. CV notes are short pulses; pad notes follow touch and release. CV2 sends smoothed, rate-limited CC74. Parameter changes send CC20-31, including a full parameter state after DICE or a mode change. Incoming panel CC values are tracked to avoid immediately returning the same value.

## LEDs

- NS and SH show the active knob layer.
- LED 0 shows CV1 triggers and MIDI receive activity.
- LED 1 follows the CV2 level.
- LEDs 2 and 3 show left and right audio activity.

## Starting patches

### Sparse clicks

Use low PERIOD, narrow WIDTH, low MASK and low modulation. Open TONE, then add a little FEEDBACK to make the tail more complex.

### Moving stereo buzz

Raise PERIOD, widen the waveform window and move SHAPE slowly. Increase STEREO and PERIOD MOD, then vary LFO RATE for drifting or agitated motion.

### Touch overload

In AS, find a stable pulse and hold T3 for recursive overload. Add T2 for a crushed edge. In TS, hold one pad for a gated tone and add another for a more unstable modulation.

## Firmware update 2026-11-23

- Constant level: a level keeper holds the long-term output, so knob positions, pads and DICE rolls no longer make the whole sound drop or jump. Short dynamics pass through.
- PERIOD now starts at about 27 Hz (the slowest single clicks were removed), WIDTH has a minimum and LEVEL ranges from 55% to 100%.
- An unpatched CV2 no longer lowers PERIOD. Below about 3% the input counts as unpatched.
- The silence watchdog is active in AS and off in TS, where silence is intended.
- Touch pads track their idle level, so a pad can no longer stay "touched" after release (Touch mode kept sounding after one touch).
- Knob pickup follows the diceFriend standard: after a layer change, DICE or a panel MIDI CC, a knob takes over after moving about 8% of its range and glides in over 200 ms (the reading is filtered). Switching SHIFT no longer changes parameters by itself.
- CV1 has the diceFriend spike guard: a pulse must stay high for 50 µs, and the first pulse after silence must be confirmed by a second one, so a noisy unpatched input cannot trigger the sound.
- A first CV2 edge counts only if another one came 50 ms to 3 s earlier. The Pad 2 crush is dithered: quiet material turns to grit instead of silence.

## Firmware installation

Download `ImpOS_40_L.hex`, open it in Teensy Loader, hold SHIFT + DICE for 10 seconds, then program and reboot. The illustrated emergency PROGRAM button guide is available in the diceFriend repository.
