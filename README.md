# diceFriend

**diceFriend** is a portable experimental digital instrument by [Sigil Instruments](https://dicefriend.sdrift.net/).

Its character can be completely changed by installing a different operating system. Each OS turns the same hardware into a different instrument: melodic, generative, percussive, noisy, or somewhere between those categories.

## Downloads

- [6 November 2026 firmware update: CV1 spike protection and SixOp_OS v0.2](docs/FIRMWARE_UPDATE_2026-11-06.md)

This repository contains compiled firmware for 30 diceFriend operating systems, with English manuals and one-page Quick Start cards.

- [Setlist generator - combine four OSes in one firmware](https://dicefriend.sdrift.net/setlist?lang=en)

Choose any four of the 29 OSes available in the generator and download a single HEX file. Install it with Teensy Loader, then switch between the four OSes on diceFriend without a computer. The generator includes switching and installation instructions and works entirely in your browser. Mieso_OS is currently available as standalone firmware only; it is not included in the Setlist generator.

- [Emergency PROGRAM button access - illustrated guide](docs/BOOTLOADER_RECOVERY.md)
- [Firmware catalogue and HEX downloads](firmware/README.md)
- [English OS manuals and PDF downloads](docs/OS_manuals/README_EN.md)
- [English Quick Start cards](docs/OS_manuals/Quick_Start_Cards_A4_EN/README.md)

## Contents

- `firmware/` — ready-to-install HEX files for Teensy 4.0
- `docs/OS_manuals/` — English manuals in Markdown
- `docs/OS_manuals/pdf/EN/` — English manuals in PDF
- `docs/OS_manuals/Quick_Start_Cards_A4_EN/` — one-page English Quick Start cards

## Official links

- [diceFriend website](https://dicefriend.sdrift.net/)
- [Sigil Instruments on GitHub](https://github.com/sigil-instruments)

## Build your own OS

[SixOp_OS source and starter project](https://github.com/sigil-instruments/diceFriend-SixOp_OS) is a complete playable six-operator FM instrument with commented MIT-licensed code, developer guides and native audio preview. Fork it to build your own diceFriend OS.
