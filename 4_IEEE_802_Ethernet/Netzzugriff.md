# Netzzugriffsverfahren

## CSMA/CD

- **C**arrier **S**ense **M**ultiple **A**ccess with **C**ollision **D**etection
- Kollisionsdomäne: alle Netzgeräte, die um Zugriff auf ein Layer 2 Übertragungsmedium konkurieren
- Broadcastdomäne: alle Netzgeräte, die ein Layer 2 Paket weiterleiten -> i.d.R. also ein gesamtes Layer 2 Netz -> Begrenzung durch Router

### Ablauf

- ständige Überwachung des Shared Mediums
  - **Carrier Sense (CS)**
- Ist Medium frei?
- Sende deine Daten nach einer (kurzen Wartezeit) Interframe Gap
- Kollision erkannt?
  - Nein: Alles gut -> weiter senden
  - Ja -> **Binary truncated backoff strategy**:
    - JAM Signal senden (stört die Übertragung des Störers -> beide erkennen Kollision)
      - JAM Signal ist 32-Bit Abfolge von 10101010...
    - Zähler (n) erhöhen
    - Zähler kleiner als 10?
      - Backoff Zeit zwischen 0 und $2^{n} - 1$ * Slot time
    - Zähler größer als 10?
      - Backoff Zeit zwischen 0 und $2^{10} - 1$ * Slot time
      - $Slot time = 2 * t_{max Übertragung} + Sicherheitsspielraum $
      - **Time Interval**: 
        | Speed       |  time | Slot time |
        | ----------- | --------- | ------------- |
        | 10 Mbit/s   | 64 Bytes  | 51,2 µs       |
        | 100 Mbit/s  | 64 Bytes  | 5,12 µs       |
        | 1000 Mbit/s | 512 Bytes | 4,096 µs      |
    - Zähler größer als 16?
      - Sendung erfolglos abbrechen