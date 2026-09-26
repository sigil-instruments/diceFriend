# Ping_OS - LEFT manual

Version: 2026-09-18. Hardware: diceFriend LEFT, Teensy 4.0.

## Character and modes

Ping_OS contains three digital resonators. The outer A and B resonators can excite and retune each other; the centre C voice is independent. AS runs a rhythmic resonator network. TS separates the three resonators and disables shared feedback and cross-FM.

Hold unshifted DICE for about 3 seconds to change AS/TS. Short DICE randomizes the current normal layer and auditions a change; SHIFT + DICE randomizes the shifted layer. Hold SHIFT + DICE for 10 seconds to enter the bootloader.

## AS controls

| Knob | NS | SHIFT |
|---|---|---|
| P1 | Tempo, 25-480 BPM; master pitch under external clock | A → B coupling |
| P2 | A pitch; interval from P1 under external clock | B → A coupling |
| P3 | B pitch; interval from P1 under external clock | Cross-FM and stepped modulation |
| P4 | Chaos and step depth | Threshold |
| P5 | Coupling and decay | Feedback |
| P6 | Event density | Drive |

## TS controls

| Knob | NS | SHIFT |
|---|---|---|
| P1 | T1 / resonator A pitch | A colour |
| P2 | T2 / resonator C pitch | C colour |
| P3 | T3 / resonator B pitch | B colour |
| P4 | A decay | A attack |
| P5 | C decay | C attack |
| P6 | B decay | B attack |

Each pad directly excites its resonator. The three voices can ring at the same time without the AS cross-coupling network.

## CV, MIDI and clock

CV1 and CV2 detect pulses. When they are not used as clocks, their continuous levels can affect pitch; they are not documented as calibrated 1 V/oct inputs.

MIDI Note On takes pitch and triggers one AS step or the TS group when CV does not own timing. TS uses root, +7 and +12 semitones. Note Off or Note On velocity 0 releases the pitch override; the audible trigger has its own timed gate. CC74 controls the CV2 modulation value. There is no CC20-31 panel receiver. Local pings produce short Note On/Off messages, while internal or CV timing can produce MIDI Clock.

MIDI Clock uses 24 PPQN. CV has timing priority for 20 seconds, and internal timing returns after 30 seconds without an external source. Start and Continue synchronize the input. MIDI Stop does not silence the instrument.

## LEDs and first patch

LED 0 shows CV1 activity. LED 1-3 show pad touches and otherwise follow resonator activity. DICE gives a short LED 3 flash.

Start in TS and tune T1-T3 with P1-P3, then set their decays with P4-P6. In AS, begin with low coupling and gradually raise SHIFT P1/P2 to hear A and B excite each other.
