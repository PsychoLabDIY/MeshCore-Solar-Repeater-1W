# MeshCore Solar Repeater — lampka solarna 1 W

**Działający prototyp repeatera LoRa 868 MHz zbudowany w obudowie niedużej lampy solarnej.** Bez drukowanej obudowy i bez oddzielnego panelu na maszcie. Chciałem sprawdzić, ile można wycisnąć z taniego, gotowego korpusu i jednego ogniwa 18650.

[English version](README.en.md) · [Budowa](docs/hardware-pl.md) · [Pomiary](docs/measurements-pl.md) · [Galeria i rysunki](docs/gallery-pl.md)

![Nagłówek projektu — ilustracja poglądowa, nie fotografia](assets/banner.svg)

> **Stan na 16 listopada 2026:** prototyp odpowiada na bezpośredni ping i jest dostępny z telefonu. Długoterminowa praca wyłącznie z panelu 1 W **nie została jeszcze potwierdzona**.

## Jak to wygląda w praktyce

W lampce znalazło się radio **Seeed XIAO nRF52840 + Wio-SX1262**. Panel słoneczny ma deklarowaną moc 1 W, a pierwsze testy wykonuję z jednym ogniwem 18650. Zewnętrzny przewód antenowy przechodzi przez **oryginalny otwór po śrubie montażowej** — w tym miejscu nie trzeba było wiercić nowego otworu.

**Zdjęcia prawdziwego urządzenia nie są jeszcze przesłane do repozytorium.** Nie zastępuję ich renderami. Poniżej są wyraźnie oznaczone rysunki pomocnicze.

![Poglądowy rysunek obudowy, nie zdjęcie prototypu](assets/enclosure.svg)

![Schemat przejścia przewodu antenowego przez istniejący otwór](assets/antenna-detail.svg)

## Części i ustawienia

- **Sterownik:** Seeed XIAO nRF52840
- **Radio:** Wio-SX1262, pasmo 868 MHz
- **Zasilanie:** panel lampy 1 W (moc deklarowana), na razie 1 × 18650
- **Antena:** zewnętrzna, przewód ze złączem SMA
- **Firmware:** MeshCore na bazie 1.18.0, z profilem RXPS Balanced (poziom 6)
- **Radio:** 869,618 MHz · SF8 · BW 62,5 kHz · CR8 · preambuła 16 symboli

W konfiguracji RXPS zapisano **49,329 ms nasłuchu i 23,757 ms uśpienia**. To ustawienia czasowe, **nie pomiar poboru prądu**. Nie zakładam też, że ograniczenie czasu nasłuchu nie wpływa na odbiór pakietów.

## Pierwszy sprawdzony test

**16.11.2026, 22:58 — łączność bezpośrednia, 0 hop:**

| Odczyt | Wynik |
|:--|--:|
| Ping | 1044 ms |
| SNR w jedną / drugą stronę | 11,75 / 12,0 dB |
| Napięcie ogniwa | 3,85 V |
| Stan w aplikacji | 70% |
| Pakiety odebrane / wysłane | 15 / 7 |
| Błędy odbioru | 1 |

To krótki test radiowy, **nie test autonomii solarnej**. Wskazanie 70% z aplikacji nie zastępuje pomiaru pojemności ogniwa.

![Grafika z odczytami testu — nie zrzut z aplikacji](assets/field-test.svg)

[Dokładniejsze wyniki i warunki pomiaru](docs/measurements-pl.md)

## Co zostało do zrobienia

- [x] Uruchomienie repeatera
- [x] Połączenie i ping z iPhone’a
- [x] Wyprowadzenie anteny przez istniejący otwór
- [ ] Dodanie **prawdziwych zdjęć** wnętrza, obudowy i zamkniętego prototypu
- [ ] Pomiar prądu i 7–14 dni prób zasilania solarnego
- [ ] Sprawdzenie strat pakietów i zasięgu
- [ ] Uszczelnienie przejścia przewodu i sprawdzenie odporności obudowy
- [ ] Weryfikacja ładowania oraz ewentualnej rozbudowy do 1S2P

## Notatki z budowy

[Hardware](docs/hardware-pl.md) · [Firmware](docs/firmware-pl.md) · [Budżet energii](docs/power-budget-pl.md) · [Dziennik pomiarów](docs/measurements-pl.md) · [Galeria](docs/gallery-pl.md) · [Bezpieczeństwo](docs/safety-pl.md)

**Uwaga:** po ingerencji w lampkę nie traktuję jej fabrycznej deklaracji szczelności jako aktualnej. Akumulator Li-ion wymaga właściwego zabezpieczenia i ładowania, szczególnie w niskiej temperaturze.

Projekt bazuje na [MeshCore](https://github.com/meshcore-dev/MeshCore). To prywatny eksperyment DIY, nie oficjalny projekt MeshCore.
