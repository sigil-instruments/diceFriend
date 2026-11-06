# Firmware update - 6 November 2026

The CV1 spike guard prevents single noise spikes on an unpatched input from taking over the clock and interrupting MIDI Clock.

CV1 accepts a pulse only when it remains high for at least 50 microseconds. CV takes over after two qualifying edges 1 ms to 10 seconds apart. Once CV owns the clock, subsequent qualifying pulses trigger immediately. The first pulse after silence does not play; isolated triggers more than 10 seconds apart do not establish CV ownership. CV retains priority over MIDI for 20 seconds after its last accepted pulse.

## Downloads

The following LEFT firmware files include this update. Existing download filenames remain the same.

| OS | Firmware |
|---|---|
| Absu_OS | [HEX](../firmware/Absu_OS_40_L.hex) |
| Aether_OS | [HEX](../firmware/AetherOS_40_L.hex) |
| Alt_OS | [HEX](../firmware/AltOS_40_L.hex) |
| Arc_OS | [HEX](../firmware/ArcOS_40_L.hex) |
| Balm_OS | [HEX](../firmware/BalmOS_40_L.hex) |
| Buk_OS | [HEX](../firmware/BukOS_40_L.hex) |
| Donut_OS | [HEX](../firmware/DonutOS_40_L.hex) |
| DriftScape_OS | [HEX](../firmware/DriftScapeOS_40_L.hex) |
| Drzazga_OS | [HEX](../firmware/Drzazga_OS_40_L.hex) |
| ExtRem_OS | [HEX](../firmware/ExtRemOS_40_L.hex) |
| Flux_OS | [HEX](../firmware/FluxOS_40_L.hex) |
| Fracture_OS | [HEX](../firmware/FractureOS_40_L.hex) |
| Gambi_OS | [HEX](../firmware/Gambi_OS_40_L.hex) |
| GenTex_OS | [HEX](../firmware/GenTexOS_40_L.hex) |
| Gruz_OS | [HEX](../firmware/GruzOS_40_L.hex) |
| Kac_Bass_OS | [HEX](../firmware/KacOS_40_BASS_L.hex) |
| Modal_OS | [HEX](../firmware/ModalOS_40_L.hex) |
| Mult_OS | [HEX](../firmware/MultOS_40_L.hex) |
| NonLin_OS | [HEX](../firmware/NonLinOS_40_L.hex) |
| Pan_OS | [HEX](../firmware/PanOS_40_L.hex) |
| PERC_OS | [HEX](../firmware/PercOS_40_L.hex) |
| Ping_OS | [HEX](../firmware/PingOS_40_L.hex) |
| Pull_OS | [HEX](../firmware/Pull_OS_40_L.hex) |
| RELAB_OS | [HEX](../firmware/RELAB_OS_40_L.hex) |
| Run_OS | [HEX](../firmware/RunOS_40_L.hex) |
| Salvi_OS | [HEX](../firmware/SalviOS_40_L.hex) |
| SixOp_OS v0.2 | [HEX](../firmware/SixOp_OS_40_L.hex) |

File sizes, MD5 and SHA-256 checksums: [release manifest](../firmware/release-2026-11-06.json).

Gambi_OS is now v0.4, Gruz_OS v0.10, Drzazga_OS v0.3 and SixOp_OS v0.2. The other packages retain their existing names.

## SixOp_OS source

The open-source reference project includes the new CV1 filter, updated source, firmware and v0.2 documentation: [diceFriend-SixOp_OS](https://github.com/sigil-instruments/diceFriend-SixOp_OS).

## Documentation

The Gambi_OS, Drzazga_OS and SixOp_OS manuals describe the updated CV1 behavior. The SixOp_OS PDF has also been updated to v0.2 and retains the illustrated PROGRAM button recovery guide.

Absu_OS, Arc_OS and Donut_OS use their regular `_L.hex` downloads; Remote DICE is already included in these files.
