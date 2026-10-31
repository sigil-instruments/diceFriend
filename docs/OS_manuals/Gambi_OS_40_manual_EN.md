# Gambi_OS - LEFT manual

Version: 2026-10-31. Hardware: diceFriend LEFT, Teensy 4.0.

Gambi_OS is a slow, organic soundscape instrument. Three tracks, each built from three voices, melt into one soft and wet wall: veils of detuned tone swelling in slow motion, wooden clatter and droplets, breathing noise and low grunts. A shared shoegaze chain of glitch stutter, vinyl surface, tape wow, phaser and a very long reverb glues everything together. The melodies of the three tracks hook onto each other on dissonant intervals, but the whole stays closer to beautiful than ugly, always on the edge of instability.

## Quick start

1. Start in AS mode with SHIFT on the NS layer.
2. Set P1-P3 (track levels) around two thirds and P4-P6 (stickiness) around one third.
3. Set SHIFT to the second layer. Put TIME low, INSTABILITY near the centre and FX around halfway.
4. Wait. Each clock step moves the melody of one track, gliding slowly into the next note.
5. Raise FX toward 70% for wide wings, then push it into its last quarter for vinyl excess.

## Modes and SHIFT

Hold DICE without SHIFT for about 3 seconds to switch between:

- AS: autonomous soundscape. The three tracks play continuously.
- TS: touch performance mode. The pads open the tracks.

LED 0 blinks quickly to confirm the mode change.

SHIFT selects the second parameter layer. After changing layer, using DICE or receiving a MIDI CC, each knob keeps its stored value until it is moved by about 8% of its range. It then glides to the knob position over 200 ms, without a jump.

## Controls

| Knob | NS layer | SHIFT layer |
|---|---|---|
| P1 | LEVEL T1: low track | PITCH T1: MIDI note 36-60 |
| P2 | LEVEL T2: middle track | PITCH T2: MIDI note 48-72 |
| P3 | LEVEL T3: high track | PITCH T3: MIDI note 60-84 |
| P4 | STICKINESS T1: clatter, droplets, grunts and texture | TIME: slow motion of swells, glides, LFOs and the internal clock |
| P5 | STICKINESS T2 | INSTABILITY: dissonant hooks, detuning, tape wow and glitches |
| P6 | STICKINESS T3 | FX: shoegaze wash, reverb, phaser and vinyl surface |

The same controls are active in AS and TS.

### Pitch and melody

The PITCH knobs set the fundamental of each track in semitone steps. Each track walks through a pretty mode around its own fundamental. DICE chooses one of four modes for the walk:

- Lydian
- Dorian
- Major pentatonic with an added ninth
- Aeolian

With a probability set by INSTABILITY, a new note does not follow the mode but hooks onto a neighbouring track at a dissonant interval: a minor second, a tritone, a major seventh or a minor ninth. A small microtonal smear is added on top. Notes never jump: they glide slowly, from about 0.4 seconds at high TIME to about 7 seconds at low TIME, so the tracks slide through clusters before they settle.

### TIME

TIME sets the speed of the whole organism. Low values give glacial swells, long glides and one internal clock step every 6 seconds. High values give one step every 1.2 seconds, faster LFOs and quicker attack and release in TS.

### FX and level

FX controls the reverb length, the phaser depth, the brightness of the veils and the amount of vinyl surface noise. The reverb tail grows from a few seconds to almost infinite in the last quarter of the knob, where hiss, dust and crackle also become deliberately excessive.

FX is level-matched. Raising it changes the space and adds noise and crackle, but it does not make the music louder.

## The three voices of a track

Every track is made from the same three voices. The registers and resonant materials differ between tracks.

### 1. WELON (veil)

A pair of detuned sine/triangle oscillators plus an octave partial; T1 adds a sub one octave below. The voice swells slowly with its own LFO and blooms on clock steps and strikes. A bright upper partial grows with FX. WELON is the tonal floor of the track and remains audible even at maximum stickiness.

### 2. REZONANS (clatter)

Three resonant modes excited by short organic events:

- single clicks,
- bouncing clatter, like a small ball settling on wood,
- droplets: short sine chirps rising in pitch.

T1 resonates like a wooden bar, T2 like a marimba and T3 like glass. Higher STICKINESS makes events more frequent and the resonances shorter and woodier.

### 3. FAKTURA (texture)

Breathing noise through a formant that follows the pitch of the track, and wet grunts: throaty pulses through a resonant filter that opens as each grunt swells. STICKINESS increases both the amount of texture and the rate of grunts.

## Shared chain

All three tracks pass through one chain:

1. Glitch stutter: short fragments of the mix are repeated two to six times, at normal, half or double speed, or reversed, with soft windows. INSTABILITY and CV2 raise the rate; T2 stickiness makes it busier.
2. Vinyl surface: pops, dust, hiss modulated by a 33 1/3 RPM rotation, and low rumble. Part of it is sent into the reverb.
3. Tape wow and flutter: a slow pitch wobble and chorus. INSTABILITY and CV2 deepen it.
4. Phaser: six stages per side with feedback, swept very slowly.
5. Reverb: a four-line feedback network with diffusion, damping and slow drift.
6. Tape saturation.

## AS mode

The tracks play continuously. Each internal clock step moves the melody of one track, in turn T1, T2, T3, and gives that track a gentle bloom. Each step also sends a MIDI note.

The pads add accents without stopping the soundscape:

- Touching T1, T2 or T3 strikes the matching track: clatter, a droplet and a bloom of the veil.
- While a pad is held, the stickiness of its track rises by 25%.

## TS mode

The pads become held voices:

- T1 opens the low track.
- T2 opens the middle track.
- T3 opens the high track.

Touching a pad also moves the melody of its track and strikes it. Releasing a pad lets the track fade out slowly. The attack and release follow TIME: from fast swells to several seconds of fade.

The internal clock does not play TS. External CV or MIDI Clock steps open all three tracks for a short gate and move all three melodies. After the first MIDI Note On, notes take over the articulation and clock steps no longer strike. MIDI Start restores clock articulation.

## DICE

### Randomize

Press and release DICE. Gambi_OS sets new values between 10% and 90% for the six parameters of the active layer and chooses a new mode for the melody walk. After every randomization the quietest and the loudest track are raised to full level, while the middle level is kept, so DICE never leaves the instrument quiet.

Randomizing the SHIFT layer also releases MIDI pitch overrides, so the PITCH values apply again.

### Mode switch and bootloader

- Hold DICE without SHIFT for about 3 seconds: switch AS/TS.
- Hold SHIFT + DICE for 10 seconds: enter the Teensy bootloader.

A gesture belongs to the layer that was active when DICE was pressed. Changing SHIFT during the hold cancels it.

## Clocking and transport

Clock priority is CV, then MIDI, then the internal clock.

- A CV1 edge immediately takes ownership and triggers a step.
- MIDI Clock remains blocked for 20 seconds after the latest CV edge.
- Internal timing returns after 30 seconds without an active external source.
- MIDI Clock is received at 24 PPQN; each quarter note is one step.
- Start and Continue resume transport. Start also resets the step counter.
- Stop mutes clock-driven events. In AS the soundscape fades out until Start or Continue. Notes and pads can still be played.

The internal clock runs only in AS, from one step every 6 seconds at low TIME to one step every 1.2 seconds at high TIME.

## CV inputs

### CV1

CV1 is the priority trigger and clock input. Every clean rising edge advances Gambi_OS immediately: in AS one track moves, in TS all three tracks are opened briefly and move.

### CV2

CV2 is a smoothed, continuous wetness control. It deepens the tape wow, makes clatter and grunts more frequent and adds glitches. Gambi_OS sends the smoothed CV2 value as CC74 when it changes.

## USB MIDI In

- In AS, MIDI channels 1, 2 and 3 address T1, T2 and T3. Channels 4-15 repeat the same order.
- In TS, channel 1 plays all three tracks together; channels 2 and 3 play T2 and T3 alone.
- Note On sets the fundamental of the addressed track and produces an immediate audible strike. The melody walk restarts from the played note.
- Note Off and Note On with velocity 0 release the matching gate.
- A held note is released automatically after 30 seconds.
- Moving a PITCH knob, or sending CC26-28, returns the track to manual pitch.
- CC20-25 control the NS parameters P1-P6.
- CC26-31 control the SHIFT parameters P1-P6.
- CC120 and CC123 release all gates.
- Channel 16 is reserved for Gambi_OS output and is ignored on input.
- Incoming MIDI is not echoed back to the same USB port.

## USB MIDI Out

All output uses MIDI channel 16:

- Clock steps send the note of the moving track (AS) or of all three tracks (TS).
- Pads send the current note of their track.
- CV2 sends CC74.
- CC102, CC103 and CC104 send the activity of T1, T2 and T3.

Gambi_OS does not generate MIDI Clock. Incoming USB messages are not retransmitted as MIDI Thru.

## LEDs

- NS LED: NS layer active.
- SHIFT LED: second layer active.
- LED 0: flashes on every step; blinks quickly on an AS/TS switch.
- LEDs 1-3: activity of T1, T2 and T3.

## Patch ideas

### Wings in slow motion

TIME low, INSTABILITY around 50%, FX around 70%, stickiness low on all tracks. The veils overlap and slide into each other while the reverb holds them for a long time.

### Wet forest floor

Raise stickiness on T2 and T3 above two thirds and keep FX in the middle. Clatter, droplets and grunts come forward; T1 keeps a soft tonal floor.

### Vinyl excess

Push FX into its last quarter and INSTABILITY above 70%. The tail becomes almost infinite, the vinyl surface takes over and glitches cut the wall into fragments. The level stays the same.

### Touch veils

Switch to TS and hold the pads like organ keys. Low TIME gives long swells and fades; patch a clock to CV1 to open all three tracks on every step between held notes.

## Bootloader

Hold SHIFT + DICE for 10 seconds to enter the Teensy bootloader, then load `Gambi_OS_40_L.hex` with Teensy Loader.
