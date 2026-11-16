# Sprzęt

## Zweryfikowany zestaw

- Seeed XIAO nRF52840
- Wio-SX1262, pasmo 868 MHz
- pionowa antena 868 MHz
- panel z małej lampki DIY, deklarowany 1 W
- dotychczas używane jedno ogniwo 18650; pojemność i stan ochrony nie zostały potwierdzone

## Zasilanie 1S2P — tylko koncepcja

Dwa zgodne ogniwa mogą utworzyć 1S2P: plus z plusem i minus z minusem, przez właściwy koszyk lub fabryczny pakiet, jeden zweryfikowany układ ochrony i ładowarkę 1S CC/CV kompatybilną z panelem. Nie wolno łączyć ogniw o różnym napięciu bez wyrównania. Nie używać układu LED jako domyślnej ładowarki dla repeatera.

Nie rozbierano działających projektów ani nie potwierdzono dostępności elementów. Schemat jest koncepcyjny: [wiring.svg](../assets/wiring.svg).

## Montaż

Antena powinna być mechanicznie zabezpieczona, a elektronika osłonięta przed deszczem i kondensacją. Panel skierowany na południe pod około 60° jest założeniem projektowym, nie pomiarem uzysku.

