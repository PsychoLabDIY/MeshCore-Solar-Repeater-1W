# Dziennik pomiarów — MeshCore Solar Repeater 1W

## 16 listopada 2026 — godziny lokalne Europe/Warsaw

| Godzina | Stan / test | Napięcie | Bateria w aplikacji | Ping 0-hop | SNR tam / z powrotem | Liczniki i uwagi |
|---|---|---:|---:|---:|---|---|
| 22:19 | Po aktualizacji RXPS Balanced, połączenie z iPhone | 4,17 V | 97% | 125 ms | 12,5 / 12,0 dB | Administracja działa; po ok. 2m20s: recv 10, sent 9, recv_errors 3. |
| 22:58 | Kolejny test na aktualnym zasilaniu bateryjnym | **3,85 V** | **70%** | **1044 ms** | **11,75 / 12,0 dB** | Uptime 2m09s; recv 15 (flood 10, direct 5); sent 7 (flood 2, direct 5); recv_errors 1; duplicates flood 5; queue 0. |

### Ważne dla interpretacji

- **22:58 / 3,85 V** jest punktem odniesienia dla pomiaru rano 17 listopada 2026.
- Odczyt 4,17 V o 22:19 pochodzi sprzed zmiany warunków zasilania; **nie oznacza wiarygodnego spadku o 0,32 V w 39 minut**.
- Procent naładowania wyświetlany przez aplikację jest szacunkiem zależnym od napięcia, temperatury i konfiguracji ADC.
- Liczniki sent/recv i uptime zerują się po restarcie. Nie porównujemy ich bez sprawdzenia ciągłości pracy.
- Błąd odbioru radiowego nie musi oznaczać utraty poprawnej wiadomości. Jeden ping nie dowodzi 100% skuteczności RXPS.
- Pokazywana data zegara repeatera to 01.03.2026; daty w powyższej tabeli to czas telefonu / obserwacji, **nie czas RTC urządzenia**.

## Rano — karta porównawcza

| Data i godzina | Napięcie | Uptime | RX | TX | RX errors | Ping |
|---|---|---|---|---|---|---|
| 16.11 22:58 | 3,85 V | 2m09s | 15 | 7 | 1 | OK, 1044ms |
| 17.11 rano | do uzupełnienia | — | — | — | — | — |

Warto także zapisać warunki: temperatura otoczenia, zachmurzenie, nasłonecznienie panelu, ewentualny restart.

**Brak automatycznej telemetrii z odłączonego od MSI urządzenia** — do porównania potrzebny będzie odczyt z aplikacji MeshCore lub stała bramka telemetryczna.
