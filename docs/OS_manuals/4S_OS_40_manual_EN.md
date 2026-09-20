# 4S_OS — manual

Version: 2026-09-18. Without SHIFT, P1 controls boundaries and internal clock; with SHIFT, it controls slope A rate. Hold DICE for about 1.8 seconds to change mode. TS opens and reshapes the shared four-slope network.

4S_OS is a four-slope cybernetic synthesis operating system for diceFriend. It is inspired by **Fourses by Ciat-Lonbarde**: four oscillating slopes influence one another through moving boundaries, collisions, transferred energy, and nonlinear feedback. 4S_OS is not a direct emulation. It develops the underlying idea into a diceFriend instrument with touch, CV, MIDI, randomization, stereo processing, and a control range shaped for musical performance.

The sound moves between breathing low-frequency motion, beating drones, unstable pitch relationships, folded tones, recursive feedback, rhythmic collisions, and chaotic electronic clusters. At lower coupling settings the four slopes can behave like related but recognizable oscillators. As coupling rises, their boundaries begin to move, impacts travel through the network, and the system can enter temporary sweet spots before reorganizing itself.

4S_OS has two performance modes: **Run mode** and **Touch mode**. Run mode keeps the four-slope network continuously active. Touch mode gates the same shared stereo system from the touch pads, CV, or MIDI.

## Main Operation

- **SHIFT** changes the function layer of the six knobs.
- **Short DICE** randomizes the sound while keeping the current performance mode.
- **SHIFT + short DICE** performs a deeper randomization.
- **Hold DICE for about 2 seconds** switches between Run mode and Touch mode.
- **SHIFT + DICE, held for about 10 seconds** enters bootloader/update mode.
- **Touch pads T1, T2, T3** disturb and reshape the network in Run mode and open the sound in Touch mode.

After randomization or a layer change, the knobs use pickup behavior: a knob must move away from its previous physical position before it takes control. This prevents sudden parameter jumps.

## CV and MIDI

- **CV1** works as a trigger and clock input. Each rising edge opens or strikes the system and generates a new random parameter mutation.
- **CV2** reacts to rising pulses as an additional trigger/clock source and also works as continuous modulation.
- Every musical step received from CV or MIDI creates a new temporary configuration of the four slope rates, coupling, asymmetry, boundaries, shape, spectrum, feedback, and stereo spread.
- A randomized step remains active until the next step; it does not return to the previous pitch after Note Off.
- Incoming MIDI Note On triggers the system. Note number contributes to the random seed instead of transposing the complete network, while velocity controls the strength of the mutation.
- Incoming MIDI Clock creates a new mutation on each musical step. Start and Continue wake the engine.
- CV1 and CV2 pulses generate short MIDI notes 36 and 37 on MIDI channel 1.
- CV2 sends MIDI CC 74, pitch bend, and channel aftertouch with rate limiting.
- When no external clock is present, 4S_OS can generate MIDI Clock from its internal speed setting.
- Stable CV clock can generate MIDI Start and 24 PPQN MIDI Clock for external devices.
- The twelve knob-layer values are available over MIDI CC: normal-layer controls use **CC 20-25** and SHIFT-layer controls use **CC 26-31**.

4S_OS does not echo incoming USB MIDI as thru on the same USB port. Its MIDI output is generated from its own controls, CV, clock, and internal state to avoid feedback loops with a host or another diceFriend.

## LEDs

- The SHIFT and non-SHIFT LEDs show the active knob layer.
- The four lower LEDs display motion inside the coupled network and its internal state registers.
- In Touch mode, their brightness follows touch-gate and audio activity.
- Incoming MIDI briefly lights the first lower LED.
- Short flashes confirm randomization and switching between Run and Touch modes.

## Run Mode

Run mode leaves the four-slope network continuously open. Each slope has its own base rate, but its instantaneous movement is also affected by neighboring slope positions, direction changes, phase differences, collision memory, and transferred energy.

The neighboring slopes act as moving upper and lower boundaries. When one slope reaches a boundary, it reverses and passes part of the impact into another part of the network. At stronger coupling settings, accumulated impacts can reverse a third slope and create a short cascade through the system.

A slow internal weather system continuously changes the relationships between the slopes. This prevents stable orbits from becoming completely permanent: the instrument can settle into a drone or rhythmic sweet spot, remain there for a while, and then gradually move toward another state.

### Run Controls

Normal layer:

- **Knob 1:** Slope A rate.
- **Knob 2:** Slope B rate.
- **Knob 3:** Slope C rate.
- **Knob 4:** Slope D rate.
- **Knob 5:** Coupling and cybernetic interaction depth.
- **Knob 6:** Rise/fall asymmetry.

Only the beginning of each Rate control is predominantly sub-audio. Most of the knob travel is reserved for audible drones and interacting pitch relationships.

SHIFT layer:

- **Knob 1:** Boundaries — the basic space available to the four slopes.
- **Knob 2:** Drift — slow pitch and trajectory movement.
- **Knob 3:** Shape — movement from smoother slopes toward driven and folded forms.
- **Knob 4:** Spectrum — brightness and output smoothing.
- **Knob 5:** Feedback — recirculation and cross-channel instability.
- **Knob 6:** Stereo spread.

### Run Touch Pad Behavior

- **T1:** Pushes rate movement and adds shape/folding pressure.
- **T2:** Increases coupling pressure and feedback energy.
- **T3:** Moves spectral relationships and emphasizes internal instability.
- Longer holds deepen each pad's influence.

## Cybernetic Coupling

Coupling is the central 4S_OS control. It does more than apply conventional frequency modulation:

- neighboring slopes move one another's upper and lower boundaries;
- phase differences alter instantaneous rate;
- direction changes affect adjacent slopes;
- collisions transfer energy through the four-part ring;
- the network retains a short memory of previous impacts;
- strong accumulated impacts can start nonlinear cascades;
- slow internal weather changes rates, shape, and feedback over time.

The first part of the Coupling range remains comparatively calm. The middle introduces breathing, beating, and changing relationships. The upper range allows stronger deterministic chaos and temporary unstable attractors. The unpredictability comes from the interaction of the four slopes rather than from adding a continuous white-noise layer.

## Touch Mode

Touch mode uses the same shared 4S_OS network, but closes its output until a touch pad, CV pulse, or MIDI note opens the gate. It is not a conventional three-voice mode: all three pads excite and modify one common stereo cybernetic system.

- Touching any pad opens the sound.
- Each pad keeps its own disturbance role from Run mode.
- Longer holds give the coupled system more time to develop and feed energy between slopes.
- CV1, CV2, and incoming MIDI can open the gate without touching a pad.
- Every external step can move the shared system into a different parameter configuration.
- The knob layout remains the same as in Run mode.

## Step Randomization

Each MIDI Note On, musical MIDI Clock step, CV1 edge, or CV2 trigger produces a fresh parameter mutation. The physical knob positions remain the base character of the patch, while the step adds a randomized offset to:

- all four slope rates;
- coupling and asymmetry;
- moving boundaries;
- shape and spectrum;
- feedback amount;
- stereo spread;
- collision energy inside each slope.

Velocity or CV level controls how far the mutation can move from the base patch. Because the new state is held until the following step, repeated triggers should produce clearly different sounds instead of an identical pitch glide or a momentary effect that returns immediately.

## Performance Notes

- Start with Coupling below the middle to hear the four base rates and their beating relationships.
- Raise Coupling gradually to introduce moving boundaries, transferred impacts, and changing trajectories.
- High Coupling and Feedback can create unstable clusters, but the mapping is limited to keep broad-band noise from dominating typical settings.
- Boundaries controls whether the slopes move through a wide, flowing space or collide more frequently inside a compact range.
- Drift and the internal weather system are different: Drift adds slow wandering selected by the player, while internal weather prevents the network from becoming permanently static.
- Shape and Spectrum are useful for opening a dark drone or calming an aggressive coupled state.
- Incoming MIDI and CV are best treated as perturbations of the instrument rather than conventional one-note-per-pitch control.
- In Touch mode, short taps create changing struck events; longer holds reveal feedback, beating, and slow cybernetic development.
