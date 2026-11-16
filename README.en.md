# MeshCore Solar Repeater — 1 W wall-lamp build

**A working 868 MHz LoRa repeater prototype inside a repurposed solar wall lamp.** The goal is simple: find out whether a small, inexpensive enclosure, its original 1 W panel and a single 18650 cell can support a useful outdoor MeshCore node.

[Wersja polska](README.md) · [Hardware](docs/hardware-en.md) · [Measurements](docs/measurements-en.md) · [Gallery](docs/gallery-en.md)

![Project illustration — not a photograph](assets/banner.svg)

> **As of 16 November 2026:** the repeater responds to a direct ping and is reachable from an iPhone. **Long-term solar autonomy has not been verified.**

## The build

- **Controller:** Seeed XIAO nRF52840
- **LoRa:** Wio-SX1262, 868 MHz band
- **Power:** wall lamp's nominal 1 W panel; one 18650 for initial tests
- **Antenna:** external SMA coax routed through an **existing wall-mount screw hole**
- **Firmware:** MeshCore 1.18.0-derived, RXPS Balanced level 6
- **Radio configuration:** 869.618 MHz · SF8 · BW 62.5 kHz · CR8 · 16-symbol preamble

RXPS settings report **49.329 ms listening / 23.757 ms sleeping**. These are timing settings, not measured current consumption. Packet-loss testing is still outstanding.

**Actual build photos have not yet been uploaded to this repository.** The illustrations below are diagrams, not photographs of the finished hardware.

![Schematic enclosure illustration](assets/enclosure.svg)

![Schematic of antenna cable feed-through](assets/antenna-detail.svg)

## First radio check

**16 Nov 2026, 22:58 CET — direct, 0-hop ping**

| Reading | Result |
|:--|--:|
| Ping | 1044 ms |
| SNR outward / return | 11.75 / 12.0 dB |
| Cell voltage | 3.85 V |
| App-reported charge | 70% |
| Packets received / transmitted | 15 / 7 |
| Receive errors | 1 |

This confirms an initial radio link, **not** that the 1 W panel can power the installation unattended. App-reported battery percentage is not a cell capacity test.

![Illustrated radio test readings, not an app screenshot](assets/field-test.svg)

[Measurement log](docs/measurements-en.md)

## Still to test

- [x] Build and boot the repeater
- [x] Direct ping and iPhone admin access
- [x] Reuse the original wall-mount hole for antenna feed-through
- [ ] Upload **real photographs** of the unit and its internals
- [ ] Measure current draw and run a 7–14-day solar trial
- [ ] Quantify reception reliability and useful coverage
- [ ] Seal and strain-relieve the cable; validate weather resistance
- [ ] Check charge management before considering a protected 1S2P pack

## Build notes

[Hardware](docs/hardware-en.md) · [Firmware](docs/firmware-en.md) · [Power budget](docs/power-budget-en.md) · [Test log](docs/measurements-en.md) · [Gallery](docs/gallery-en.md) · [Safety](docs/safety-en.md)

Modifying the wall lamp may compromise its original weather rating. Li-ion charging and low-temperature protection must be verified before leaving the installation unattended.

Based on the open-source [MeshCore](https://github.com/meshcore-dev/MeshCore) project; this is an independent DIY build, not an official MeshCore hardware design.
