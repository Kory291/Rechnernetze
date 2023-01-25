# Kommunikationsarten

## Klassifizierungen

### Mensch-Maschine-Sicht

- Mensch-zu-Mensch
- Mensch-zu-Maschine
- Maschine-zu-Mensch
- Maschine-zu-Maschine
- Broadcast-zu-Maschine
- Broadcast-zu-Mensch

### Anzahl Sender/Empfänger

| Typ | Anzahl Sender | Anzahl Empfänger |
| -- | -- | -- |
| Unicast | 1 | 1 |
| Multicast | 1 | n |
| Broadcast | 1 | alle |
| Concast | m | 1 |
| Multipeer | m | n |
| Anycast | 1 | 1 aus n |
| Geocast | 1 | n in bestimmten Gebiet |

### zeitliche Sicht

| Typ | Beschreibung |
| -- | -- |
| synchron | Sender und Empfängertakt sind synchronisiert |
| isochron | Echtzeitkommunikation, Abstand zwischen Bits ist konstant |
| asynchron | Senden außerhalb eines vorgegebenen Takts (spontan) |

### Richtung der Kommunikation

| Typ | Beschreibung |
| -- | -- |
| simplex | unidirektional, nur in eine Richtung |
| half-duplex | bidirektional, aber immer nur eine Richtung zu einer Zeit |
| full-duplex | bidirektional, Nutzung beidee Richtungen gleichzeitig möglich |

### Anbieter-Kunden

- Client-Server (siehe HTTP)
- Peer-to-Peer
- Ad-Hoc Netze / Mesh-Netze (z.b. WLAN)
