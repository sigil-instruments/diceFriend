# Donut_OS - LEFT manual

Version: 2026-10-28. Hardware: diceFriend LEFT, Teensy 4.0.

Donut_OS is a two-voice microtonal instrument built around a walk on a toroidal pitch grid. The grid wraps at every edge, so the motion can continue indefinitely without reaching an endpoint. Its horizontal coordinate selects the first pitch, while the vertical coordinate defines the interval of the second voice. Folding, FM colour, granular memory and feedback turn the same pitch structure from a clear duet into an unstable stereo cloud.

## Quick start

1. Set SHIFT to the NS layer.
2. Set P1 to 19 EDO, P3 and P4 near the middle, P5 near the centre and P6 around C2.
3. Touch T1 twice to set the tempo.
4. Set SHIFT to the second layer and raise DENSITY until most steps sound.
5. Add CHAOS, MUTATION and FEEDBACK gradually.
6. Hold DICE to repeat the latest eight steps, then release it to resume the walk from the last recalled position.

## SHIFT and knob pickup

SHIFT selects one of two independent parameter layers. After changing the layer, using DICE or receiving a parameter over MIDI, a knob waits for a deliberate movement before taking control. This prevents an immediate jump to the physical knob position.

The NS LED and SHIFT LED show the active layer.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | SCALE: six tuning maps | DENSITY: probability that a step produces sound |
| P2 | INTERVAL SPAN: maximum distance travelled on each step | CHAOS: register injection, grain activity and instability |
| P3 | WIDTH: horizontal grid size, 2-32 cells | MUTATION: changes direction, spectrum and grain speed |
| P4 | HEIGHT: vertical grid size, 2-32 cells | FEEDBACK: affects motion, harmonic colour and folding |
| P5 | BIAS: preference for horizontal or vertical motion | INERTIA: tendency to retain the previous axis and direction |
| P6 | ROOT: chromatic root from C1 to C4 | ROUTE: selects one of six modulation paths |

### Tuning maps

P1 selects one of these maps:

1. 12 EDO
2. 19 EDO
3. 31 EDO
4. Hexany map A
5. Hexany map B
6. 5-limit diatonic just intonation

Both voices always remain inside the selected tuning map. Voice B is octave-placed to minimise large jumps while staying within the three-octave range above the root.

### Grid and motion

- WIDTH and HEIGHT define the torus. Moving beyond an edge returns the walker on the opposite side.
- INTERVAL SPAN controls the maximum distance of one move.
- BIAS favours movement on one axis.
- INERTIA keeps the previous axis and direction for longer.
- MUTATION occasionally changes the directional tendency.
- FEEDBACK feeds the internal register back into movement and colour.
- DENSITY can create rests, but the walker still advances on every accepted clock step.

### ROUTE

ROUTE changes how grid position, internal chaos and CV2 reach the sound engine. The six positions move between body/folding, texture/FM and decay-based modulation. The later routes use more of the chaotic register and produce stronger grain-speed, decay and destructive feedback changes.

## DICE

### Full roll

Press and release DICE without SHIFT for a new world. The roll changes tuning, root, grid geometry, motion, density, timbre and modulation route. It also clears the previous eight-step history. The new scene is struck immediately so the change is audible without waiting for the next clock.

### Related mutation

Press and release SHIFT + DICE for a related variation. SCALE, ROOT, WIDTH, HEIGHT and ROUTE remain unchanged. INTERVAL SPAN, BIAS, DENSITY, CHAOS, MUTATION, FEEDBACK and INERTIA move by a noticeable but limited amount.

### Eight-step loop

Hold DICE for at least 450 ms. Donut_OS repeats the available history, up to eight events. The loop includes pitches, rests, velocity, colour, grain behaviour, decay, route and walker state. Release DICE to leave the loop and continue from the last recalled position.

The loop gesture works in both SHIFT positions. Holding SHIFT + DICE for 10 seconds is reserved for the bootloader.

## Touch pads

- T1: tap twice to set internal tempo. Valid tap intervals are approximately 150 ms to 3 seconds.
- T2: pressure adds brightness, roughness and grain intensity.
- T3: pressure lengthens the decay and memory tail.

T2 and T3 are continuous performance controls. Their effect combines with CV2 and MIDI expression.

## Clocking and transport

The clock priority is CV, then MIDI, then the internal clock.

- CV1 advances one step on every clean rising edge.
- CV2 can act as either continuous modulation or a secondary trigger/clock input.
- If CV1 is active, CV2 cannot add extra steps.
- MIDI can take control 20 seconds after the last valid CV step.
- During the next 10 seconds Donut_OS waits for an external source rather than restarting internally.
- The internal clock returns after 30 seconds without CV or MIDI activity.

MIDI Clock is received at 24 PPQN. Start and Continue enable MIDI-clocked stepping. Stop stops MIDI-clocked motion and silences the audio engine. A MIDI Note On can still create a step after Stop.

## CV inputs

### CV1

CV1 is the primary trigger and clock input. Each rising edge advances the toroidal walk, creates the next event and can generate USB MIDI notes and clock.

### CV2

With a continuous signal, CV2 modulates the destination selected by ROUTE. With repeating edges, it becomes a secondary clock. A steady high voltage does not create a false trigger when connected. Clock pulses temporarily suppress the continuous modulation value so one cable does not control both functions at once.

## USB MIDI In

Channel messages are received on MIDI channel 1.

- Note On with velocity above zero forces an audible step. Velocity controls the accent.
- The MIDI note number does not retune the grid.
- Note Off and Note On with velocity 0 do not advance the sequence.
- MIDI Clock advances one step after 24 pulses.
- Start, Continue and Stop control MIDI-clocked transport.
- CC20-25 control the NS parameters P1-P6.
- CC26-31 control the SHIFT parameters P1-P6.
- CC74 adds continuous expression.
- Channel Aftertouch adds grain intensity and brightness.
- CC120 and CC123 silence the engine and clear expression.
- Incoming MIDI is not echoed back to the same USB port.

## USB MIDI Out

Each audible local event produces two microtonal MIDI voices:

- Voice A: channel 1
- Voice B: channel 2

Donut_OS sends Pitch Bend before Note On and configures both channels for a +/-2 semitone bend range. Note duration follows approximately three quarters of the current step. Local CV and internal steps can also generate Start, 24 PPQN MIDI Clock and Stop. Incoming USB messages are not sent back as MIDI Thru.

## LEDs

- NS LED: NS layer active.
- SHIFT LED: second layer active.
- Lower LED 1: recent step activity.
- Lower LED 2: CV2 level; it blinks while the eight-step loop is active.
- Lower LED 3: left audio level.
- Lower LED 4: right audio level.

## Patch ideas

### Stable microtonal duet

Choose 19 EDO, use a medium WIDTH and HEIGHT, keep DENSITY high and set CHAOS, MUTATION and FEEDBACK below one third. Set INERTIA near the middle and use a body or texture ROUTE.

### Granular cloud

Start from a stable duet, then raise CHAOS and MUTATION above halfway. Increase FEEDBACK carefully, use T2 pressure and select a texture/FM route. Hold DICE when an interesting eight-step phrase appears.

### External generative sequencer

Patch a clock to CV1 and a slow modulation signal to CV2. Use a decay route, moderate DENSITY and a large grid. Donut_OS sends the resulting two-voice microtonal sequence over USB MIDI while producing audio.

