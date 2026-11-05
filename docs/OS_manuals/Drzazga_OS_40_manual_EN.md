# Drzazga_OS - LEFT manual

Version: 2026-11-05. Hardware: diceFriend LEFT, Teensy 4.0.

Drzazga_OS is a percussive glitch instrument. A stable base of kick and a high electric pulse hat holds the ground, while five small percussion voices appear by chance in the gaps: a woodblock, a short triangle, an aluminium can, a rungler blip and an arc discharge zap. Between the hits, glitch grains cut from the latest strikes stutter, reverse, crush and slow down. The knobs travel from sparse, bending relabi textures with plenty of air, through broken grooves, to dense glitched drill rolls.

Drzazga_OS draws on RELAB_OS (bending time), Absu_OS (polyrhythmic cycles and self-sampling), Blip_OS (rungler and resonant peaks) and Fracture_OS (stutter, reverse and crush of captured hits).

## Quick start

1. Start in AS mode with the switch on the NS layer. Drzazga_OS plays immediately from its internal clock.
2. Leave all knobs near their start position: the default is sparse, with plenty of space between the hits.
3. Set the switch to SHIFT. Raise DENSITY slowly to fill the same groove, and CRUMBS to bring in more of the small voices.
4. Add RELABI for bending, floating timing. Add RATCHET for repeats and rolls.
5. Back on NS, raise GLITCH to fill the gaps with fragments of the latest hits.
6. For drill, push DENSITY, RATCHET and GLITCH high together.

## Modes and SHIFT

Hold DICE without SHIFT for about 3 seconds to switch between:

- AS: autonomous rhythm. Drzazga_OS plays by itself from the internal clock, CV1 or MIDI Clock.
- TS: touch sequencer. A 32-step loop recorded with the pads, like PERC_OS.

LED 0 blinks quickly to confirm the mode change.

The lower switch position selects the NS layer (timbre), the upper position the SHIFT layer (rhythm). After changing layer, using DICE or receiving a MIDI CC, each knob keeps its stored value until it is moved by about 8% of its range. It then glides to the knob position over 200 ms, without a jump.

## Controls

| Knob | NS layer: timbre | SHIFT layer: rhythm |
|---|---|---|
| P1 | KICK: low = deep and long, high = short, tight and punchy with more click and drive | TEMPO: 50-200 BPM in 16th steps, internal clock only |
| P2 | HAT: low = dark short tick, high = bright, buzzing electric pulse | DENSITY: from sparse relabi texture to dense drill |
| P3 | MATERIAL: shifts the extras from wood to triangle, can, blip and zap; selects the T3 voice in TS | CRUMBS: how often the extras appear |
| P4 | DECAY: extras from dry ticks to ringing | RELABI: time bending and phase shear between the voices |
| P5 | GLITCH: amount and length of glitch grains in the gaps | RATCHET: repeats, rolls and drill bursts |
| P6 | SPACE: small metallic room, then drive, last 15% bit crush | EVOLUTION: how fast the pattern rewrites itself |

The same controls are active in AS and TS.

### DENSITY

DENSITY does not roll new random hits. Every step of the kick and hat lanes has a fixed rank, given when the pattern is created. DENSITY is a threshold on that rank, so turning it thins out or fills up the same groove and the base never flickers. The first step of the loop always carries a kick, even at zero.

DENSITY also makes the extras, ratchets and glitches busier, and unlocks finer ratchet subdivisions.

### RELABI

RELABI bends the placement of each hit with a smooth, never-repeating curve. The hat and the extras shear against each other, while the kick receives only a little of the bend, so the base stays anchored. Low values feel like a loose swing; high values float freely around the grid without a stable meter. The bend also drifts slowly by itself.

With an external clock, RELABI can only delay hits, never move them ahead of the clock edge, and the kick stays exactly on the edge.

### RATCHET

RATCHET repeats single hits as halves, triplets, quarters, sixths, eighths and twelfths of a step. The finer subdivisions appear as RATCHET and DENSITY rise. The hat ratchets most, the kick least. Above about 55%, rolls may accelerate or slow down, in the manner of Aphex Twin drum programming.

### EVOLUTION

At the end of every bar, EVOLUTION may swap the ranks of a few steps, reroll the cycle of one extra or, rarely, redeal the hats completely. At zero the pattern repeats exactly. The relabi curve keeps drifting even at zero.

### SPACE and level

SPACE is a single sweep: from 0% to about 60% a small metallic room, from 50% drive, and in the last 15% bit and sample-rate crush. The output runs into a soft limiter. Dense settings saturate softly against it, without hard clipping.

## The voices

| # | Voice | Sound |
|---|---|---|
| 0 | KICK | sine with falling pitch, click and drive |
| 1 | HAT | high electric pulse: a narrow pulse ring-modulated by a square, a touch of noise, high-passed |
| 2 | WOOD | woodblock: three resonant modes, hard strike |
| 3 | TRI | short triangle: four free-bar modes |
| 4 | CAN | aluminium can: six clustered inharmonic modes and a crumpled noise burst |
| 5 | BLIP | two resonant peaks fed by pulses and retuned by an 8-bit rungler while the hit rings |
| 6 | ZAP | arc discharge: a falling FM chirp with comparator crackle and sample-rate grit |

KICK and HAT form the stable base. The five extras live on their own polyrhythmic cycles of 5 to 13 steps, so they drift against the bar, and they only play by chance. They prefer the gaps between base hits; at higher DENSITY they may also land together with the base.

### Glitch

A 0.74-second buffer records the mix of all voices. A glitch grain starts just before one of the last eight hits, so it almost always carries a recognisable transient. GLITCH unlocks the flavours in order:

- stutter: the fragment repeats,
- reverse,
- octave: double or half speed,
- crush: few bits and reduced sample rate,
- tape stop: the fragment slows down to a halt.

Glitches favour empty steps and land between the hits. At high GLITCH and DENSITY they also appear on busy steps and become longer, with more repeats.

## AS mode

Drzazga_OS plays by itself. The pads add live gestures on top of the pattern:

- T1: an immediate kick.
- T2 (hold): a hat roll. RATCHET sets its speed, from 32nd notes upward.
- T3 (hold): freeze. The latest hits stutter in a loop, and the extras arrive in an avalanche until the pad is released.

## TS mode

TS is a 32-step loop (two bars of 4/4), recorded with the pads like PERC_OS:

- T1 plays and records KICK.
- T2 plays and records HAT.
- T3 plays and records the extra selected by MATERIAL (NS P3): wood, triangle, can, blip or zap. Turning MATERIAL changes the sound of the recorded T3 lane live.

A touch plays immediately and is written to the nearest step. Hold a pad for 3 seconds to clear its lane; the matching LED blinks.

The recorded hits always play. The extras add themselves according to the recorded beat:

- wood and can answer just after a kick,
- triangle and blip sparkle around the hats,
- the T3 voice echoes its own hits three and six steps later,
- zap and glitches fill longer gaps.

CRUMBS and DENSITY set how much is added. An empty loop stays silent.

When TS is entered with an empty loop, it takes over the kick and hat groove that AS was playing at that moment, so the switch is seamless. A loop recorded in TS is kept when switching to AS and back.

The loop runs on the internal clock, CV1 or MIDI Clock, as in AS.

## DICE

### Randomize

- Tap DICE on the NS layer: new sounds for the extras between kick and hat. Each extra gets a new tuning, decay, character and stereo position, and MATERIAL and DECAY are set to new values. KICK and HAT stay untouched.
- Tap SHIFT + DICE in AS: a new sequence. New base groove for kick and hat and new cycles for the extras. Tempo and all knob values stay.
- Tap SHIFT + DICE in TS: a new variation of the recorded loop, in the PERC_OS manner. Every press grows from the same base, so you can try variations without losing the original. A new pad recording becomes the new base. An empty loop is filled with a generated pattern.

### Mode switch and bootloader

- Hold DICE without SHIFT for about 3 seconds: switch AS/TS.
- Hold SHIFT + DICE for 10 seconds: enter the Teensy bootloader.

A gesture belongs to the layer that was active when DICE was pressed. Changing SHIFT during the hold cancels it.

### Remote DICE

MIDI CC117 on channel 1 (low, then high) performs a full roll: new extra sounds and a new sequence. Several diceFriends can be rolled together from one source.

## Clocking and transport

Clock priority is CV, then MIDI, then the internal clock.

- A CV1 edge immediately takes ownership and plays one 16th step.
- MIDI Clock remains blocked for 20 seconds after the latest CV edge.
- Internal timing returns after 30 seconds without an active external source.
- MIDI Clock is received at 24 PPQN; every 6 clocks play one 16th step.
- Start resets the loop to its first step; Continue resumes.
- Stop locks all clocks until Start, Continue or a DICE mode switch. Pads and notes can still be played.

The internal clock runs in AS and TS. Steps are scheduled ahead of time, so relabi bends, ratchets and rolls stay sample-accurate even while the pads are being read.

## CV inputs

### CV1

CV1 is the priority clock. Every clean rising edge plays one 16th step. The interval between edges also sets the length of ratchets and glitches.

### CV2

- The CV2 level adds up to 50% DENSITY and up to 30% GLITCH.
- Rising edges, 50 ms to 3 s apart, throw in one random extra. They do not move the transport.
- Drzazga_OS sends the smoothed CV2 value as CC74 when it changes.

## USB MIDI In

- Channel 1 and unassigned channels: Note On sets the fundamental of the tuned extras and plays the T3 voice selected by MATERIAL.
- Channels 2-8 address voices 0-6 directly (KICK, HAT, WOOD, TRI, CAN, BLIP, ZAP). The note sets the pitch of that voice; HAT has no pitch.
- Channel 10 uses the General MIDI drum map: 35/36 kick, 42/44/46 hat, 76/77 wood, 80/81 triangle, 56 can, 75 blip, 38-40 zap.
- Every Note On produces an immediate audible hit, in AS and TS.
- In TS, Note Off and Note On with velocity 0 damp the matching voice.
- CC20-25 control the NS parameters P1-P6.
- CC26-31 control the SHIFT parameters P1-P6.
- CC74 acts like the CV2 level.
- CC117 on channel 1: Remote DICE.
- CC120 and CC123 damp all voices.
- Channel 16 is reserved for Drzazga_OS output and is ignored on input.
- Incoming MIDI is not echoed back to the same USB port.

## USB MIDI Out

All notes use MIDI channel 16 with General MIDI drum numbers:

| Voice | Note |
|---|---|
| KICK | 36 |
| HAT | 42 |
| WOOD | 76 |
| TRI | 80 |
| CAN | 56 |
| BLIP | 75 |
| ZAP | 40 |

- Every hit from the sequencer, the pads and CV2 sends its note, timed with the sound. Ratchet copies are not sent.
- Output is limited to 8 notes per 10 ms, so drill settings cannot flood USB.
- While the internal clock or CV1 is the master, Drzazga_OS sends MIDI Start and Clock (24 PPQN). While MIDI is the master, no clock is sent.
- CV2 sends CC74.

## LEDs

- NS LED: NS layer active.
- SHIFT LED: second layer active.
- LED 0: flashes on every step, brighter on every quarter note. Blinks quickly on an AS/TS switch, flashes on DICE.
- LED 1: kick activity.
- LED 2: hat activity.
- LED 3: extras and glitch activity.
- In TS, LEDs 1-3 blink when the lane of T1, T2 or T3 is cleared.

## Patch ideas

### Splinters in the air

DENSITY low, CRUMBS around 60%, RELABI around 70%, DECAY high, SPACE around 45%. Single hits float apart with long gaps; the small voices ring out and drift against each other.

### Broken workshop

DENSITY near 45%, CRUMBS 60%, GLITCH 45%, RATCHET 30%, MATERIAL in the middle. A loose broken groove with cans and triangles answering the base and short stutters in between.

### Drill

TEMPO around 70%, DENSITY, RATCHET and GLITCH above 80%, EVOLUTION 60%, SPACE in the drive zone. Rolls accelerate and decelerate, glitches crush and reverse, and the pattern keeps rewriting itself.

### Touch kit

Switch to TS and clear the lanes. Tap a simple kick and hat pattern, choose a T3 voice with MATERIAL and add a few hits. Raise CRUMBS and the extras start answering your beat. Tap SHIFT + DICE for variations.

## Bootloader

Hold SHIFT + DICE for 10 seconds to enter the Teensy bootloader, then load `Drzazga_OS_40_L.hex` with Teensy Loader.
