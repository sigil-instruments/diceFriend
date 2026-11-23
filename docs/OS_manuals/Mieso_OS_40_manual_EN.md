# Mieso_OS - LEFT manual

Version: 2026-11-23 (v0.3). Hardware: diceFriend LEFT, Teensy 4.0.

Mieso_OS is a harsh noise wall. Its core is the CIG_OS impulse generator: two triangle clocks drive two cross-coupled shift registers, a comparator, sample-and-hold feedback, two resonant peaks and the Retention memory. Around it run three more engines from the diceFriend family: a GenTex-style feedback loop (fold, crush, filter and micro delay inside the loop), a Chimera-style homeostasis that lets the loudness of the loop limit its own feedback, and a Pulsar-style grain of pulse windows over noise.

The wall never sits down. Every source is loudness-normalised and a level keeper holds the long-term output, so knobs, pads, DICE, CV and MIDI change the texture, never the loudness. Short movement (crackle, bursts, cuts) passes through; the long-term level stays put.

## Quick start

1. Start in AS mode with the switch on the NS layer. The wall plays immediately.
2. Turn ECOLOGY: from the CIG core towards the feedback loop, then the pulse grain. The level stays the same, only the colour changes.
3. Raise MEAT for density, drive and grit. It is not a volume knob.
4. Set the switch to SHIFT. FOLD and CRUSH add harmonics and digital damage, MEMORY brings back fragments of the recent past.
5. MOTION sets how often the wall jumps somewhere else (the internal clock) and how unstable it is.
6. Tap DICE for a new patch, SHIFT + DICE for a full random patch with reseeded states. No roll can be quiet.

## Modes and SHIFT

Hold DICE without SHIFT for about 3 seconds to switch between:

- AS: the wall plays all the time and mutates by itself on every clock step (a "cut": the memory read position, the loop delay, the shift registers and the grain jump).
- TS: the wall plays only while a pad is touched. A held MIDI note also opens it; a CV edge or a MIDI Clock step opens it for about 180 ms. After release it rings out for about 0.26 s. The wall and its level keep running underneath, so every touch comes in at full level immediately.

The LEDs confirm the mode change with two clear flashes while the others stay dark: the two upper LEDs (0 and 1) when entering TS, the two lower LEDs (2 and 3) when entering AS.

The lower switch position selects the NS layer, the upper position the SHIFT layer. After changing layer, using DICE or receiving a MIDI CC, each knob keeps its stored value until it is moved by about 8% of its range. It then glides to the knob position over 200 ms, without a jump.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | CLOCK A: rate of CIG oscillator A, from slow crackle to audio rate; also the grain density | FOLD: wavefolding in the loop, the grain and after the CIG core |
| P2 | CLOCK B: relation of CIG oscillator B; also the ratio between the two grains | CRUSH: bit depth and sample rate inside the loop, noise in the grain |
| P3 | RESONANCE: the two CIG peaks, mirrored (one rises, the other falls) | TONE: loop filter and post tone; never darker than about 160 Hz |
| P4 | ECOLOGY: CIG core > feedback loop > pulse grain; the CIG core always stays in the mix | MEMORY: share of the Retention memory (at most 85%, the live wall always stays in) |
| P5 | FEEDBACK: modulation depth of the CIG core, loop feedback, chaos and homeostasis | SCAN: where the memory is read and the length of the loop delay |
| P6 | MEAT: drive, grit, peak resonance and pulse width; not a volume knob | MOTION: internal tempo 40-240 BPM, how uneven it is, how far each cut jumps, memory jitter |

The same controls are active in AS and TS.

### ECOLOGY

ECOLOGY moves the weight between the three sources. At the left end the CIG core dominates: shift-register blips and resonant peaks. In the middle the feedback loop takes over: folded, crushed, self-sustaining noise. At the right end the pulse grain comes forward: dense pulse windows over noise. Each source has its own loudness normaliser, so moving ECOLOGY never makes the wall louder or quieter.

### MEAT and FEEDBACK

MEAT pushes the whole wall into asymmetric drive and raises the resonance of the CIG peaks and the width of the pulses. FEEDBACK deepens every coupling: the CIG modulation, the loop feedback and the chaos of the grain. Its homeostasis keeps the loop alive without letting it run away: the louder the loop, the less feedback it gets.

### MEMORY, SCAN and MOTION

The Retention memory from CIG_OS stores the last fraction of a second and reads it back from unstable positions: comb-like ringing, short echoes, smeared fragments. SCAN chooses where it reads, MOTION makes the read position jitter and sets how far each cut jumps.

## Pads

The pads work in both modes. A longer hold (from about 0.45 s to 3 s) goes deeper.

- T1 TEAR: speeds up the CIG oscillator and adds fold. In TS it pulls the wall towards the CIG core.
- T2 FREEZE: pushes the shift registers and the feedback. Held for about 2 s it freezes the loop and the memory: they keep looping what they hold, a buzzing loop instead of silence. In TS it pulls the wall towards the feedback loop.
- T3 MASH: raises the peaks, crushes and bursts the grain. In TS it pulls the wall towards the pulse grain.

In TS several pads blend their layers.

## DICE

- Tap DICE: new values for all 12 parameters (CIG-style ranges). The level stays the same.
- SHIFT + tap: every parameter over its full range, and all internal states are reseeded.
- Hold DICE 3 s (without SHIFT): AS / TS.
- Hold SHIFT + DICE 10 s: bootloader.
- CC117 on channel 1: Remote DICE (one normal roll).

There is no DICE + pad gesture: on the NS layer that combination belongs to the SetlistOS menu.

## Clocking and transport

The clock source priority is CV > MIDI > internal. CV leads for 20 s after its last accepted edge; the internal clock returns after 30 s without any external clock.

- Internal clock: one cut per step; MOTION sets 40-240 BPM and how much each step breathes shorter or longer. In TS the internal clock does not cut.
- MIDI Clock: MOTION picks the division of the cuts: quarter notes (below 33%), eighths (33-66%) or sixteenths (above 66%). Start and Continue resume the cuts. Stop stops the cuts; the wall keeps playing.
- CV: every accepted edge is a cut and an impact.

## CV inputs

- CV1: clock and trigger, with the diceFriend spike guard: a pulse must stay high for 50 µs and the first edge after silence must be confirmed by a second one (1 ms to 10 s later). The first pulse after silence therefore does not play.
- CV2: the level colours the wall (loop filter, peaks). Rising edges are a second clock (the first edge must follow another within 50 ms to 3 s; once CV leads, edges at least 20 ms apart count). CV1 has priority.

## USB MIDI In

- Note On, AS: transposes the CIG oscillators (note 60 = no change) and strikes the wall. Note Off releases the transposition.
- Note On, TS: opens the wall and tunes the two CIG peaks to the note and its octave. Note Off closes it.
- MIDI Clock, Start, Continue, Stop: see Clocking.
- CC20-25 control NS P1-P6, CC26-31 SHIFT P1-P6.
- CC74 acts like the CV2 level.
- CC117 on channel 1: Remote DICE.
- CC120 and CC123 release the held note.
- Channel 16 is reserved for Mieso_OS output and its notes are ignored on input.

## USB MIDI Out

- Channel 16: one note per cut (the note follows the CIG shift register), at most one note per 20 ms. Notes caused by incoming MIDI notes are never sent back.
- Channel 1: CC20-31 when the panel changes (knobs, DICE), CC74 from CV2.
- While the internal clock leads, Mieso_OS sends MIDI Start and Clock (24 PPQN); while CV leads, it converts the CV clock to MIDI Clock. While MIDI leads, it sends no clock.
- No MIDI thru.

## LEDs

- NS LED: NS layer active. SHIFT LED: second layer active.
- LED 0: flashes on every cut and on DICE; dim flash on incoming MIDI.
- LEDs 1-3: bits of the two CIG shift registers, as in CIG_OS.
- Mode switch: two flashes of LEDs 0 and 1 when entering TS, of LEDs 2 and 3 when entering AS.

## Live use (SetlistOS)

Mieso_OS is built for the diceFriend live setlist: no DICE + pad gestures, no EEPROM use, buffers in the second RAM bank, and a pause of the OS never makes the clock catch up. Its level matches CIG_OS, GenTex_OS and Chimera_OS, so switching between them in a set does not jump.

## Patch ideas

### Concrete wall

ECOLOGY around 50%, FEEDBACK and MEAT high, CRUSH around 40%, MEMORY low, MOTION low. A dense, slowly churning wall of folded loop noise.

### Rotting radio

ECOLOGY low, CLOCK A around 60%, RESONANCE in the middle, MEMORY and SCAN high, MOTION around 60%. Shift-register blips and peaks smeared through jumping memory.

### Grinder

ECOLOGY high, CLOCK A high, MEAT high, FOLD and CRUSH high, MOTION high. A hard pulse grain shredded at audio rate, cut on every step.

### Played wall (TS)

Switch to TS, set MEAT high and MEMORY around 50%. Play the wall with the pads: T1 for the CIG core, T2 for the loop (hold it about 2 s to freeze), T3 for the grain, several pads for blends.

## Bootloader

Hold SHIFT + DICE for 10 seconds to enter the bootloader, then load the HEX file with Teensy Loader.
