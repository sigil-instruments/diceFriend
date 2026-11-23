# Lancuh_OS - LEFT manual

Version: 2026-11-23 (v0.8). Hardware: diceFriend LEFT, Teensy 4.0.

Lancuh_OS is a chain-reaction drum machine. Seven abstract percussion voices are the seven nodes of a patch. The nodes are connected by wires, and every wire has odds, a delay in 16th steps, a strength and a transposition. A token runs along the wires: when it reaches a node, that voice plays, and the token picks its next wire by the odds. The pattern builds itself from those odds, so it keeps changing without falling apart. Gravity pulls the chain back to the low voice on the bar, and an event layer adds drop-outs, tape stops, half-time, stutter grains and reverb throws.

Lancuh_OS is inspired by CRD Machine by Kenta Osborn. The name is Polish for "chain", spelled the diceFriend way.

## Quick start

1. Start in AS mode with the switch on the NS layer. Lancuh_OS plays immediately from its internal clock.
2. Leave the knobs near their start position: a sparse chain that returns to DOL on most bars.
3. Set the switch to SHIFT. Raise CHAOS to loosen the odds, and FORK to add more tokens and polyrhythm.
4. Lower GRAVITY to let the chain wander, raise it to lock the groove to the grid.
5. Raise GLITCH for drop-outs, tape stops, half-time sections, stutters and reverb throws.
6. Back on NS, push DAMAGE for saturation, crush and grit. Tap DICE for new sounds, SHIFT + DICE for a new patch.

## Modes and SHIFT

Hold DICE without SHIFT for about 3 seconds to switch between:

- AS: autonomous chain. Lancuh_OS plays by itself from the internal clock, CV or MIDI Clock.
- TS: learning mode. The patch learns the wires from the pads.

The LEDs confirm the mode change with two clear flashes while the others stay dark: the two upper LEDs (0 and 1) when entering TS, the two lower LEDs (2 and 3) when entering AS.

The lower switch position selects the NS layer (timbre), the upper position the SHIFT layer (rhythm). After changing layer, using DICE or receiving a MIDI CC, each knob keeps its stored value until it is moved by about 8% of its range. It then glides to the knob position over 200 ms, without a jump.

## Controls

| Knob | NS layer: timbre | SHIFT layer: rhythm |
|---|---|---|
| P1 | DOL: low = deeper (46 Hz) and a bit longer, high = tighter (58 Hz) and shorter | TEMPO: 50-200 BPM in 16th steps, internal clock only |
| P2 | BRIGHTNESS: all voices except DOL from dark to bright | CHAOS: flatter odds, random jumps, wobble, ratchets |
| P3 | MATERIAL: which voices the chain prefers; selects the T3 voice in TS | FORK: extra tokens with a short life, up to 3 in total |
| P4 | DECAY: dry ticks to ringing | GRAVITY: pull back to DOL on the bar, even delays |
| P5 | DAMAGE: saturation, then crush, sample-rate grit and dust | GLITCH: how often events happen |
| P6 | SPACE: reverb size and send, louder throws | EVOLUTION: AS = wires drift by themselves; TS = forgetting |

The same controls are active in AS and TS.

### The chain

Every node has one to three outgoing wires. A new patch (SHIFT + DICE) deals new wires: targets, odds, delays of 1 to 4 steps, strengths and transpositions of a few semitones up or down. One token always runs, so the chain can never die out or explode.

### CHAOS

CHAOS flattens the odds: at zero the strongest wires dominate, towards the top every wire becomes almost equally likely. Higher up, the token may also jump to any node with a random short delay. CHAOS also adds a smooth micro-timing wobble and, in its upper range, ratchets of halves, thirds and quarters of a step. DOL barely moves, so the ground stays put.

### FORK

FORK lets a firing node send a second token down another wire. Extra tokens live for a few hits and then fade out. Above about 15% a second token is possible, above about 60% a third. Two or three tokens running through the same patch at different delays make polyrhythms.

### GRAVITY

On the first step of every bar, GRAVITY may send the main token back to DOL, so the bar starts from the ground. At the top this happens on every bar, and also on the half bar. GRAVITY also rounds odd delays to even ones and retires extra tokens at the bar line, so the chain locks to the grid. At zero the chain floats freely.

### GLITCH and the event profile

GLITCH sets how often the events happen:

- drop-out: everything except DOL disappears for 2 to 8 steps, sometimes everything,
- tape stop: the whole mix slows down to a halt towards the end of a bar and snaps back on the next one,
- half-time: the chain moves at half speed for one or two bars,
- stutter: grains cut from the latest hits repeat, reverse, change octave or crush,
- reverb throw: a single hit is thrown into the reverb.

The balance between these events is the profile of the patch. It is dealt together with the wires, so every patch has its own habits: one likes drop-outs, another throws everything into the reverb.

### DAMAGE and SPACE

DAMAGE is a single sweep: saturation from the start, bit crush from about 40%, sample-rate grit from about 60%, digital dust from about 80%. SPACE sets the size and send of the reverb and makes the throws louder. The output runs into a soft limiter, without hard clipping.

### EVOLUTION

In AS, EVOLUTION lets the wires drift by themselves at the bar line: odds change, a wire gets a new target, delay or transposition. At zero the patch stays fixed. In TS it becomes forgetting (see TS mode).

## The voices

| # | Voice | Sound |
|---|---|---|
| 0 | DOL | a short, low dub techno kick: a sine with a quick pitch drop, a soft click and a warm low-pass |
| 1 | GLASS | a noise splinter in a short tuned comb, with cracks while it rings |
| 2 | METAL | an industrial clank: inharmonic square waves XOR-ed together, a scrape of noise and a short resonant body |
| 3 | BYTE | a bytebeat formula played as a click or a burst |
| 4 | LORENZ | a pulse driven by a running Lorenz attractor; it keeps its state, so no two hits are equal |
| 5 | FOLD | a sine through a wavefolder; the fold decays faster than the level, from buzz to tone |
| 6 | NOISE | a short noise hit, held flat and cut off abruptly; white or crunchy, band- or high-passed |

Tapping DICE on the NS layer deals new tuning, decay, character and stereo position to every voice, always clearly away from the previous ones. DOL is only nudged by about two semitones, so it never turns melodic; the other voices move within well over an octave.

## AS mode

Lancuh_OS plays by itself. The pads add live gestures on top of the chain:

- T1: DOL at once, and the chain continues from it.
- T2 (hold): half-time while held.
- T3 (hold): tape stop of the whole mix; release to spin the tape back up. Touching T1 or T2 while the tape is stopped also spins it up.

## TS mode: the chain learns

In TS the pads teach the patch:

- T1 plays DOL, T2 plays GLASS, T3 plays the voice selected by MATERIAL (NS P3).
- A tap plays at once and the token jumps to that node, so the chain answers from where you played.
- Tap A, then B: the wire from A to B, with the delay you played (rounded to 16ths, 1 to 8 steps), gets stronger and the other wires of A get a little weaker. LED 0 flashes when a wire is learned. Play a figure three to five times and the chain starts to play it by itself, with its own deviations.
- EVOLUTION becomes forgetting: wires you do not play slowly lose weight. At zero nothing is forgotten.
- With SHIFT up, hold DICE and tap a pad: that node forgets its wires and keeps one weak wire home to DOL. The matching LED blinks.
- SHIFT + DICE in TS: a variation of what was learned. The odds and some delays change, the structure stays.

The first switch to TS copies the AS patch. After that TS keeps what it has learned until power-off. MIDI notes are ignored in TS: only the pads teach.

## DICE

### Randomize

- Tap DICE on the NS layer: new sounds for all voices, plus new MATERIAL, DECAY and BRIGHTNESS values.
- Tap SHIFT + DICE in AS: a new patch (wires and event profile). Tempo and knob values stay.
- Tap SHIFT + DICE in TS: a variation of the learned patch.

### Mode switch and bootloader

- Hold DICE without SHIFT for about 3 seconds: switch AS/TS.
- Hold SHIFT + DICE for 10 seconds: enter the Teensy bootloader.

A gesture belongs to the layer that was active when DICE was pressed. Changing SHIFT during the hold cancels it.

### Remote DICE

MIDI CC117 on channel 1 (low, then high) performs a full roll: new sounds and a new patch.

## Clocking and transport

Clock priority is CV, then MIDI, then the internal clock.

- A CV1 pulse counts only if it is at least 50 µs long. CV1 takes ownership after two edges 1 ms to 10 s apart; from then on every edge plays one 16th step at once. Single spikes on an unpatched CV1 are ignored.
- MIDI Clock remains blocked for 20 seconds after the latest CV edge.
- Internal timing returns after 30 seconds without an active external source.
- MIDI Clock is received at 24 PPQN (6 clocks = one 16th).
- CV2 rising edges are a second clock input. CV1 has priority over CV2.
- Start restarts the chain from DOL; Continue resumes.
- Stop locks all clocks until Start, Continue or a DICE mode switch.

With an external clock, the wobble can only delay hits, never move them ahead of the clock edge, and DOL stays exactly on the edge.

### Own clock under MIDI (mutual mode)

Like Drzazga_OS and PERC_OS, Lancuh_OS runs its own flywheel clock under MIDI. It follows the incoming tempo and sends its OWN MIDI Clock back out; incoming ticks are never forwarded. A sequencer with automatic clock takeover (for example diceMotion) then follows Lancuh_OS while Lancuh_OS follows it:

- the sent clock is bent by half of the CHAOS wobble; at CHAOS 0 it just holds the tempo,
- the tempo may drift a few percent but is pulled back to its centre; a clear tempo change held for about two bars becomes the new centre,
- phase is aligned at Start and at the first clock after silence,
- if the incoming clock disappears, Lancuh_OS keeps playing at once, and after 30 s it stays on the same tempo until TEMPO is moved,
- no MIDI Start is ever sent to the master.

CC85 below 64 switches this off: Lancuh_OS then steps on every 6 incoming clocks and sends no clock while MIDI leads.

### Events in the clock (CC86)

CC86 at 64 or above lets tape stops and half-time slow down the MIDI Clock that Lancuh_OS sends: half-time sends half the ticks, a tape stop sends fewer and fewer ticks until it halts. Everything that follows the clock slows down together with Lancuh_OS. Off by default (CC86 below 64).

## CV inputs

- CV1: priority clock. Every clean rising edge plays one 16th step.
- CV2: the level adds up to 40% CHAOS and up to 30% GLITCH. Rising edges are a second clock (the first edge must follow another within 50 ms to 3 s; once CV leads, edges at least 20 ms apart count). The smoothed CV2 value is sent as CC74.

## USB MIDI In

- Channel 1 and unassigned channels: Note On sets the fundamental of the tonal voices and plays the T3 voice (AS).
- Channels 2-8 address voices 0-6 directly (DOL, GLASS, METAL, BYTE, LORENZ, FOLD, NOISE). The note sets the pitch of that voice.
- Channel 10: 35/36 DOL, 42/44/46 GLASS, 53/56 METAL, 37 BYTE, 39 LORENZ, 69/70 FOLD, 76/77 NOISE.
- In TS MIDI notes are ignored; TS follows only MIDI Clock, Start/Stop/Continue and CC.
- CC20-25 control the NS parameters P1-P6, CC26-31 the SHIFT parameters P1-P6.
- CC74 acts like the CV2 level.
- CC85: own clock under MIDI, 64-127 on (default), 0-63 off.
- CC86: events in the clock, 64-127 on, 0-63 off (default).
- CC117 on channel 1: Remote DICE.
- CC120 and CC123 damp all voices.
- Channel 16 is reserved for Lancuh_OS output and is ignored on input.

## USB MIDI Out

All notes use MIDI channel 16:

| Voice | Note |
|---|---|
| DOL | 36 |
| GLASS | 42 |
| METAL | 56 |
| BYTE | 37 |
| LORENZ | 39 |
| FOLD | 70 |
| NOISE | 76 |

- Each step sends at most one note, timed with the sound, DOL first. Ratchet copies are not sent. T1 in AS and all pads in TS send their note.
- Hits caused by incoming MIDI notes are never sent back.
- Output is limited to 2 notes per 20 ms.
- While the internal clock or CV leads, Lancuh_OS sends MIDI Start and Clock (24 PPQN). While MIDI leads, it sends its own flywheel clock, never a copy of the incoming ticks and never Start.
- CV2 sends CC74.

## LEDs

- NS LED: NS layer active. SHIFT LED: second layer active.
- LED 0: flashes on every step, brighter on every quarter note. Flashes on DICE and when TS learns a wire.
- Mode switch: two flashes of LEDs 0 and 1 when entering TS, of LEDs 2 and 3 when entering AS.
- LED 1: DOL.
- LED 2: GLASS, METAL and BYTE.
- LED 3: LORENZ, FOLD, NOISE and the glitch grains.
- In TS, LEDs 1-3 blink when the node of T1, T2 or T3 forgets its wires.

## Live use (SetlistOS)

Lancuh_OS can be selected as one of four instruments in SetlistOS. With SHIFT down, hold DICE and immediately touch all three pads for 2.5 seconds to open the setlist menu. Release everything, choose a slot with P1 and confirm with DICE. Mute the mixer channel before switching. Switching slots clears the learned TS patch. SHIFT + DICE + pad remains the gesture for forgetting a node's wires.

## Patch ideas

### Grounded chain

GRAVITY at the top, CHAOS low, FORK zero, DECAY long, SPACE around 70%. A slow, steady figure that starts every bar from DOL and rings out.

### Breakcore

TEMPO around 60%, CHAOS and FORK high, GRAVITY around 30%, GLITCH around 90%, DAMAGE around 80%, EVOLUTION 70%. Three tokens chase each other, the tape stops, drops out and comes back crushed.

### Teach it a figure

Switch to TS. Tap T1, then T2 two 16ths later, then T2 again, then T1 a beat later; repeat it four times. Lower EVOLUTION to keep it, raise it to let the chain forget and find its own way. Turn MATERIAL to choose which voice T3 adds to the figure.

### Shared tape stop

Clock diceMotion from Lancuh_OS or let them follow each other, send CC86 on and raise GLITCH. When the tape stops, the whole setup slows down with it.

## Bootloader

Hold SHIFT + DICE for 10 seconds to enter the Teensy bootloader, then load `Lancuh_OS_40_L.hex` with Teensy Loader.
