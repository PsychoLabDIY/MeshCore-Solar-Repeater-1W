# Firmware

Urządzenie działa na MeshCore `v1.18.0 (Build: 15 Oct 2026)`, board `Seeed Xiao-nrf52`. Odczyt USB potwierdził:

```text
get radio -> 869.6179809,62.5,8,8
get radio.rxps -> desired=on,effective=armed,supported=yes,err=0,fail=0,level=6,catch=10.2,preamble=16,rx=49329,sleep=23757
powersaving -> off
```

RXPS nie jest pomiarem prądu i nie gwarantuje braku strat pakietów. `powersaving off` pozostawiono jako osobną flagę uśpienia platformy, aby nie mieszać jej z pracą RXPS.

Firmware MeshCore należy pobierać i budować zgodnie z upstreamem: https://github.com/meshcore-dev/MeshCore. Ten projekt nie publikuje binariów, kluczy ani preferencji urządzenia.

