# Routing

## Allgemeines

### Metriken

- Hop Count
- Paketverzögerung
- Durchsatz
- Online Status des Links

### Reihenfolge der Nutzung von Routing Protokollen

- Auswahl über Administrative Distanz (AD)
  - niedriger Wert besser

| Protokoll / Verfahren | AD |
| --- | --- |
| Statische Routen | 1 |
| eIGRP summary route | 5 |
| eBGP | 20 |
| internal EIGRP | 90 |
| OSPF | 110 |
| IS-IS | 115 |
| RIP | 120 |
| external EIGRP | 170 |
| iBGP | 200 |

## OSPF

- Open Shortest Path First
- Link-State

## RIP

- Routing Information Protocol
- Distanzvektoren

## BGP

- Border Gateway Protocol