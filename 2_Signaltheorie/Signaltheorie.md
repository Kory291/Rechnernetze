# Signaltheorie

## Modulationsverfahren

- **B**inary **P**hase **S**hift **K**eying (**BPSK**)
- **Q**uadratur **P**hase **S**hift **K**eying (**QPSK**)
- **Q**uadratur **A**mplituden **M**odulation (**QAM**)
  - I- und Q-Komponente (Sinus und Cosinusschwingung)
  - Darstellung in IQ-Diagramm (am Ende komplexe Zahl)
  - Beispiele:
    - 16-QAM -> 4 $Bit \over Symbol$
    - 64-QAM -> 6 $Bit \over Symbol$
    - 256-QAM -> 8 $Bit \over Symbol$
- **D**ifferential **Q**uadrature **P**hase **S**hift **K**eying (**DQPSK**)
  - Kodierung über die Differenz zum vorherigen Symbol
  - Störanfällig -> Vorwärtsfehler

## Multiplexverfahren

- **T**ime **D**ivision **M**ultiplex **A**ccess (**TDMA**)
  - Zugriff zu unterschiedlichen Zeiten
- **F**requency **D**ivision **M**ultiplex **A**ccess (**FDMA**)
  - Zugriff auf unterschiedlichen Frequenzen
  - Bsp zwei Funktechnologien (4G: 1,8 GHz und WLAN: 2,4 GHz)
- **C**ode **D**ivision **M**ultiplex **A**ccess (**CDMA**)
  - Überlagerung im Frequenz- und Zeitbereich
  - Trennung über orthogonale Codewörter (-> beeinflussen sich nicht, bzw werden vom Korrelationsemfänger nicht erkannt)
- **S**pace **D**ivision **M**ultiplex **A**ccess (**SDMA**)
  - räumliche Trennung des Zugriffs
  - Bsp. zwei Kabel
- **W**avelength **D**ivision **M**ultiplex **A**ccess (**WDMA**)
  - wie FDMA nur im optischen Bereich

## Signallaufzeiten

- RTD: Round Trip Delay
- RTT: Round Trip Time
  - Laufzeit vom Sender zum Empfänger und wieder zurück

$$v=\frac{s}{t}$$$$t=\frac{s}{v}$$

- s := Strecke der Übertragung
- v := Ausbreitungsgeschwindigkeit
  - $v$ = $3*10^8$ $m \over s$
- t := Dauer für die Übertragung

## Bitraten

**Rauschfreier Kanal:**
$$C = 2B*ld(m)$$

- C := Datenrate
- B := Bandbreite
- ld := Logarithmus zur Basis 2
- m := Anzahl der unterscheidbaren Symbole

## Kanalkapazität

$$ C = B*ld(1 + SNR)$$

- C := Kapazität
- B := Bandbreite
- ld := Logarithmus zur Basis 2
- SNR := Signal zu Rauschverhältnis

**Anmerkung:**

- Ist eine theoretische Obergrenze für die Kanalkapazität, die nur bei Nutzung von perfekten Codewörtern erreicht wird. Daher dient die Shannon'sche Kanalkapazität nur als Abschätzung für die zu erwartende Datenraten eines Übertragungssystems
- es wird ein AWGN-Kanal angenommen
  - additives, weißes Rauschen (Rauschen im gesamten Spektrum gleichstark)
