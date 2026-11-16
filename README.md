<p align="center"><img src="assets/banner.svg" width="100%" alt="MeshCore Solar Repeater 1W — DIY project"></p>

<p align="center">
  <a href="README.md"><strong>🇵🇱 Polski</strong></a> ·
  <a href="README.en.md">🇬🇧 English</a>
</p>

<p align="center">
  <img alt="Status: działający prototyp" src="https://img.shields.io/badge/status-dzia%C5%82aj%C4%85cy%20prototyp-2ea44f?style=flat-square">
  <img alt="MeshCore" src="https://img.shields.io/badge/firmware-MeshCore%20RXPS%20Balanced-2364aa?style=flat-square">
  <img alt="868 MHz" src="https://img.shields.io/badge/LoRa-EU%20868-6272a4?style=flat-square">
  <img alt="Panel 1W" src="https://img.shields.io/badge/solar-1%20W-f59e0b?style=flat-square">
  <img alt="Hardware" src="https://img.shields.io/badge/platforma-XIAO%20nRF52840-334155?style=flat-square">
</p>

# Drugie życie lampy solarnej

**MeshCore Solar Repeater 1W** to kompaktowy repeater LoRa 868 MHz zbudowany z elektroniki **Seeed XIAO nRF52840 + Wio-SX1262** i obudowy niewielkiej lampy solarnej. Założenie jest proste: wykorzystać panel 1 W i fabryczną obudowę, wyprowadzić antenę na zewnątrz oraz ograniczyć pobór energii bez rezygnowania z funkcji repeatera.

To dokumentacja **rzeczywiście uruchomionego prototypu**, a nie gotowy produkt. Firmware działa, komunikacja radiowa jest potwierdzona; całoroczna autonomiczność energetyczna i szczelność po przeróbkach nadal wymagają testów.

<table>
<tr><td width="50%"><strong>01 / Obudowa i panel</strong><p>Niewielka ścienna lampa solarna została wykorzystana jako baza mechaniczna z panelem 1 W.</p><img src="assets/enclosure.svg" alt="Schemat obudowy i wyprowadzenia anteny" width="100%"></td><td width="50%"><strong>02 / Antena na zewnątrz</strong><p>Przewód antenowy i gniazdo SMA wyprowadzone przez istniejący <strong>otwór montażowy po śrubie</strong>, bez wiercenia nowego otworu w tym miejscu.</p><img src="assets/antenna-detail.svg" alt="Detal wyprowadzenia anteny" width="100%"></td></tr>
</table>

## W skrócie

| Element | Obecna konfiguracja |
|:--|:--|
| Płytka | Seeed XIAO nRF52840 + Wio-SX1262 |
| Sieć | MeshCore, 869,618 MHz, SF8, BW 62,5 kHz, CR8 |
| Firmware | Wariant MeshCore 1.18.0 z **RXPS Balanced**, poziom 6, preambuła 16 |
| Nasłuch RXPS | 49,329 ms RX / 23,757 ms sleep (stan z CLI, nie pomiar poboru) |
| Zasilanie | Panel PV **1 W**, pojedyncze ogniwo 18650 w obecnym teście |
| Rozbudowa | Dwa zgodne ogniwa 18650 w 1S2P — plan po sprawdzeniu ładowarki i zabezpieczeń |
| Antena | Zewnętrzna antena LoRa na przewodzie koncentrycznym, przejście przez otwór montażowy obudowy |
| Stan | Ping bezpośredni 0-hop i dostęp administracyjny potwierdzone na iPhonie |

## Test z 16 listopada 2026

<p align="center"><img src="assets/field-test.svg" width="100%" alt="Parametry testu MeshCore 16 listopada 2026"></p>

Na iPhonie potwierdzono dwukierunkowy ping do repeatera oraz dostęp do panelu administratora. Najnowszy udokumentowany pomiar z **22:58 czasu polskiego**, po przejściu na test zasilania akumulatorowego: **3,85 V (70% wskazania aplikacji)**, ping **1044 ms**, SNR **11,75 dB / 12,0 dB**. Nie są to wartości gwarantowane dla innych odległości ani wyniki pomiaru poboru mocy.

➡️ [Pełny dziennik pomiarów](docs/measurements-pl.md) · [English test log](docs/measurements-en.md)

## Jak wykonano modyfikację anteny

Obudowa lampy ma oryginalne otwory pod montaż do ściany. Jeden z nich posłużył jako przejście dla zewnętrznego przewodu RF i złącza antenowego. To ogranicza liczbę nowych otworów w obudowie, **ale samo w sobie nie stanowi uszczelnienia IP**. Przed stałą instalacją na zewnątrz należy wykonać odciążenie kabla i sprawdzić szczelność przejścia oraz pokrywy.

## Plan rozwoju

- [x] Uruchomienie XIAO nRF52840 + Wio-SX1262 i MeshCore.
- [x] Montaż w obudowie lampy solarnej.
- [x] Wyprowadzenie anteny przez otwór montażowy.
- [x] Aktualizacja do RXPS Balanced, poziom 6.
- [x] Ping 0-hop z iPhone'a; zachowanie tożsamości i dostępu administratora.
- [ ] Test ciągłej pracy przez 7–14 dni na panelu 1 W.
- [ ] Pomiar poboru prądu i statystyczny test strat pakietów.
- [ ] Kontrola szczelności, zabezpieczeń Li-ion i ładowania na zimnie.
- [ ] Ewentualny pakiet 1S2P i terenowa lokalizacja docelowa.

## Dokumentacja

| Obszar | Polski | English |
|:--|:--|:--|
| Budowa i części | [Sprzęt](docs/hardware-pl.md) | [Hardware](docs/hardware-en.md) |
| Firmware | [RXPS Balanced](docs/firmware-pl.md) | [RXPS Balanced](docs/firmware-en.md) |
| Zasilanie | [Budżet energii](docs/power-budget-pl.md) | [Power budget](docs/power-budget-en.md) |
| Procedura testowa | [Testy](docs/testing-pl.md) | [Testing](docs/testing-en.md) |
| Rejestr wyników | [Pomiary](docs/measurements-pl.md) | [Measurements](docs/measurements-en.md) |
| Budowa i galeria | [Galeria](docs/gallery-pl.md) | [Gallery](docs/gallery-en.md) |
| Bezpieczeństwo | [Uwagi](docs/safety-pl.md) | [Safety](docs/safety-en.md) |

## Ograniczenia

Panel 1 W i pojedyncze 18650 **nie są jeszcze potwierdzonym całorocznym źródłem zasilania**. Odczyt procentów baterii jest szacunkiem urządzenia, a nie pomiarem pojemności. Nie zakładamy zerowych strat pakietów RXPS ani odporności obudowy na deszcz po przeróbce. Akumulatory Li-ion wymagają prawidłowej ładowarki i ochrony, a ładowanie ogniw w temperaturze poniżej 0°C wymaga odpowiednio zaprojektowanego układu.

---

Projekt wykorzystuje otwarte oprogramowanie [MeshCore](https://github.com/meshcore-dev/MeshCore). To niezależna dokumentacja własnej adaptacji sprzętowej; nie jest oficjalnym wydaniem MeshCore.
