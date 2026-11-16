<p align="center">
  <img src="assets/banner.svg" width="100%" alt="MeshCore Solar Repeater 1 W">
</p>

<p align="center">
  <a href="README.md"><strong>PL</strong></a> · <a href="README.en.md">EN</a>
</p>

# Repeater MeshCore z lampy solarnej

**1 W panelu, mała obudowa i radio LoRa 868 MHz.** Chciałem zbudować repeater, który zmieści się w zwykłej lampce solarnej, będzie można go zostawić w terenie i nie będzie wymagał codziennego ładowania. Tak powstał ten prototyp.

W środku pracuje **Seeed XIAO nRF52840** z **Wio-SX1262**. Oprogramowanie MeshCore zmodyfikowałem o profil **RXPS Balanced**, żeby radio nie musiało bez przerwy pracować w pełnym nasłuchu. To na razie etap prób: łączność działa, ale bilans energii i odbiór pakietów muszą przejść dłuższy test.

## Budowa

### Obudowa

Wykorzystałem obudowę gotowej lampy ściennej z małym panelem słonecznym. Oryginalny układ oświetlenia zastąpiła elektronika repeatera. Panel ma deklarowaną moc **1 W**.

![Schemat obudowy lampki](assets/enclosure.svg)

### Antena

Przewód antenowy wyprowadziłem przez **istniejący otwór po śrubie montażowej lampy**. Nie wierciłem dodatkowego otworu pod SMA. Antena stoi osobno na podstawie magnetycznej.

![Przejście anteny przez otwór montażowy](assets/antenna-detail.svg)

Przejście kabla trzeba jeszcze odciążyć mechanicznie i uszczelnić. To, że oryginalna lampa miała oznaczenie odporności na warunki atmosferyczne, nie oznacza, że po przeróbce zachowała tę samą szczelność.

### Podzespoły

| Część | Zastosowanie |
|---|---|
| Seeed XIAO nRF52840 | Sterownik |
| Wio-SX1262 | Moduł LoRa |
| Antena 868 MHz z przewodem SMA | Wyniesiona antena zewnętrzna |
| Obudowa lampy solarnej | Panel i miejsce na elektronikę |
| Panel 1 W | Ładowanie w dzień |
| Ogniwo 18650 | Zasilanie podczas nocnych testów |

Dwa ogniwa równolegle (1S2P) są rozważane na dalszy etap. Przed rozbudową trzeba potwierdzić zabezpieczenie i sposób ładowania.

## Oprogramowanie

Na repeaterze działa MeshCore oparty na wydaniu **1.18.0** z RXPS Balanced, poziom 6 i preambułą 16 symboli.

**Parametry radia:** 869,618 MHz · SF8 · BW62,5 kHz · CR8.

Cykle RXPS z odczytu urządzenia: **49,329 ms odbioru / 23,757 ms uśpienia**. Te czasy nie są pomiarem pobieranego prądu. Firmware zachowuje funkcje repeatera, CLI i dostęp administratora; zerowych strat pakietów jeszcze nie potwierdziłem.

[Opis firmware](docs/firmware-pl.md) · [Firmware in English](docs/firmware-en.md)

## Pierwszy test radiowy

![Zestawienie wyników pomiaru](assets/field-test.svg)

16 listopada 2026 o **22:58** telefon potwierdził ping bezpośredni (0 hop) do repeatera.

| Parametr | Wynik |
|---|---:|
| Napięcie akumulatora | **3,85 V** |
| Wskazanie naładowania w aplikacji | 70% |
| Ping 0 hop | **1044 ms** |
| SNR w kierunku repeatera | 11,75 dB |
| SNR powrotny | 12,0 dB |
| Pakiety odebrane / wysłane | 15 / 7 |
| Błędy odbioru | 1 |

To punkt początkowy testu zasilania akumulatorowego, **a nie dowód na czas pracy panelu 1 W**. Wcześniejszy odczyt 4,17 V wykonano w innych warunkach zasilania — nie należy traktować różnicy jako szybkiego rozładowania.

[Pełny dziennik pomiarów](docs/measurements-pl.md)

## Co jeszcze sprawdzam

- [x] Złożenie i uruchomienie prototypu
- [x] Wyprowadzenie anteny przez otwór montażowy
- [x] RXPS Balanced na działającym repeaterze
- [x] Ping i dostęp administracyjny z iPhone'a
- [ ] 7–14 dni pracy na panelu 1 W
- [ ] Pomiar prądu przy różnych trybach nasłuchu
- [ ] Test strat pakietów i stabilności połączenia
- [ ] Uszczelnienie i uporządkowanie mocowania przewodu
- [ ] Ewentualne przejście na dwa ogniwa 18650

## Dokumentacja projektu

**[Budowa](docs/hardware-pl.md)** · **[Firmware](docs/firmware-pl.md)** · **[Zasilanie](docs/power-budget-pl.md)** · **[Pomiary](docs/measurements-pl.md)** · **[Galeria](docs/gallery-pl.md)** · **[Bezpieczeństwo](docs/safety-pl.md)**

[English documentation](README.en.md)

---

Projekt wykorzystuje [MeshCore](https://github.com/meshcore-dev/MeshCore). Dokumentuję własną przeróbkę sprzętu; nie jest to oficjalna konstrukcja ani firmware projektu MeshCore.
