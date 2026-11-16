<p align="center"><img src="assets/banner.svg" alt="MeshCore Solar Repeater" width="100%"></p>

# MeshCore Solar Repeater — 1 W

Polski opis jest główną wersją dokumentacji. English summary: this repository documents a real, measured-in-part setup of a MeshCore repeater based on Seeed XIAO nRF52840 and Wio-SX1262, with a 1 W solar concept. It deliberately separates verified device observations from models, terrain screening and untested assumptions.

**Status:** `BALANCED_RUNTIME_QA_PASS` · no claim of zero packet loss or energy autonomy

## Spis treści

- [Co jest zbudowane](#co-jest-zbudowane)
- [Stan zweryfikowany](#stan-zweryfikowany)
- [Dokumentacja](#dokumentacja)
- [Bezpieczeństwo](#bezpieczeństwo)
- [English](#english)

## Co jest zbudowane

- Seeed XIAO nRF52840 + Wio-SX1262, antena 868 MHz.
- MeshCore repeater `v1.18.0`, profil RXPS Balanced: level 6, preamble 16.
- Radio: 869.618 MHz, SF8, BW 62.5 kHz, CR8.
- Koncepcja zasilania: panel 1 W i jedno ogniwo 18650; 1S2P z dwoma zgodnymi ogniwami jest dopiero planem.

Nie publikujemy firmware, kluczy, preferencji, dokładnych adresów, działek ani plików operacyjnych. Źródła MeshCore pozostają upstreamem.

## Stan zweryfikowany

| Obszar | Wynik |
|---|---|
| Wersja/board | `v1.18.0 (Build: 15 Oct 2026)`, `Seeed Xiao-nrf52` |
| RXPS | `desired=on`, `effective=armed`, level 6, preamble 16, `err=0` |
| Okna RX/sleep | 49.329 ms / 23.757 ms — telemetria czasowa, nie pomiar prądu |
| Radio QA | 0-hop ping użytkownika: 125 ms, SNR 12.5/12.0 |
| USB QA | COM4, VID:PID 2886:8044, DTR=True, 115200, odpowiedzi CLI |
| Energia | brak pomiaru prądu; bilans panelu 1 W pozostaje nieudowodniony |
| Lokalizacja | screening DEM/orto; brak potwierdzonej działki i rekonesansu fizycznego |

## Dokumentacja

- [Dokumentacja sprzętu — PL](docs/hardware-pl.md) · [EN](docs/hardware-en.md)
- [Firmware — PL](docs/firmware-pl.md) · [EN](docs/firmware-en.md)
- [Budżet energii — PL](docs/power-budget-pl.md) · [EN](docs/power-budget-en.md)
- [Testowanie — PL](docs/testing-pl.md) · [EN](docs/testing-en.md)
- [Bezpieczeństwo — PL](docs/safety-pl.md) · [EN](docs/safety-en.md)
- [Galeria — PL](docs/gallery-pl.md) · [EN](docs/gallery-en.md)

Schemat koncepcyjny: [assets/wiring.svg](assets/wiring.svg). Wersja źródłowa w repozytorium nie jest kopią firmware upstream.

```mermaid
flowchart LR
  PV[Panel PV 1 W] --> CH[Zweryfikowana ładowarka 1S CC/CV]
  CH --> BAT[Chroniony pakiet 1S / opcjonalnie 1S2P]
  BAT --> NODE[XIAO nRF52840 + Wio-SX1262]
  NODE --> RF[868 MHz MeshCore]
```

## Bezpieczeństwo

Li-ion wymaga właściwego ładowania CC/CV, ochrony, zgodnych ogniw i obudowy. Nie łącz ogniw o różnym napięciu bez wyrównania i weryfikacji. Nie ładuj ogniw Li-ion poniżej 0°C. Panel 1 W i ogniwo 18650 nie gwarantują pracy całonocnej ani ciągłości przekazywania pakietów.

## English

This is a documentation-first, private-by-default project record. The current device observation is RXPS Balanced on a XIAO nRF52840/Wio-SX1262. Energy figures are models unless explicitly marked measured; packet loss is not proven zero. See the English documents linked above.

## Upstream

MeshCore project and firmware: https://github.com/meshcore-dev/MeshCore

