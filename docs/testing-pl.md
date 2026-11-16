# Testowanie

## Wykonane

- USB CDC COM4, VID:PID 2886:8044, 115200, DTR=True, odczyt CLI bez resetu.
- `ver`, `board`, `get name`, `get radio`, `get radio.rxps`, `powersaving`, `get tx`, `stats-core`, `stats-radio`, `stats-packets`, `clock`.
- Odczyt zakończony zamknięciem portu.
- Ping 0-hop z iPhone: 125 ms, SNR 12.5/12.0 — obserwacja użytkownika.

## Ograniczenia

Nie wykonano całonocnego testu, kontrolowanego testu 1000 pakietów, pomiaru prądu ani testu położenia w terenie. `recv_errors` nie jest samodzielnie dowodem procentowej utraty pakietów.

