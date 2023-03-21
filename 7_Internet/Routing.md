# Routing

## Allgemeines

### statisches und dynamisches Routing

- statisch
  - Routen werden per Hand gepflegt
  - gut für kleine, sich nicht ändernde Netze machbar
- dynamisch
  - Routen werden für eine gewisse Zeit gelernt
  - weniger Verwaltungsaufwand
  - je nach Implementation Probleme mit Updates über Routen (vgl Count to infinity problem)

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

### Autonome Systeme

- Zusammenfassung eines Netzes mit mehreren Routern -> Provider
- Autonome Systeme werden durch eine Nummer identifiziert
  - Vergabe durch IANA (Internet Assigned Numbers Authority)
- man unterscheidet zwischen verschiedenen Typen von AS:
  - Transit AS
    - Verkehr aus anderem AS hat Ziel in einem anderen AS, wird aber durch das eigene AS geroutet
    - **Transportnetz**
  - Multihomed
    - ein AS mit mehreren anderen AS verbunden
  - Stub
    - es gibt nur Verbindung zu einem anderen AS

## OSPF

- Open Shortest Path First
- Link-State
- Quelle sendet Advertisments aus
  - Empfänger speichert die in der eigenen Topologie DB
- periodische HELLO-Pakete
  - sind Router noch vorhanden?
- günstigste Wege werden über Dijsktra-Algorithmus mit den Daten der Topologie DB errechnet
  - Aufspannen eines Baums
  - keine Schleifen und deshalb kein Count to inifinity Problem
- schnellere Berechnung
- höhere Speicherkapazität notwendig
- ermöglicht Strukturierung mit Areas
  - Identifikation durch Nummer von $0...2^{32}-1$
- Metrik mit $\frac{100.000.000}{bandwith}$
- Router-ID
  - höchste IP-Adresse eines Interface
- partielle Updates mit Link State Update
- komplette Updates alle 30 Minuten

## RIP

- Routing Information Protocol
- Distanzvektorverfahren
- lernt die Sicht der Nachbarn
- periodische Updates
- neue Routinginformationen lösen erneut die Routenberechnung aus (Vektoraddition -> Bellmann-Ford-Iteration)
- geringe Anforderungen an den Router
- nutzt UDP
- Beschränkung auf max 15 Hops

### Count-to-infinity Problem

- Sznario:
  - R1 <-> R2 <-> R3
  - Linkausfall: R1 <-> R2 <-/-> R3
  - R2 erkennt Linkausfall, erhält aber Update von R1
    - neue Route über R1 wird gelernt
  - R2 sendet Update an R1
    - R1 erhöht den Hop Count um 1 (R1 kennt einen neuen Wert -> ich muss den nehmen, weil ich die Route von R2 gelernt habe)
  - R1 sendet Update an R2
  - usw...
- Lösung:
  - **Split Horizon**
    - Route die über einen anderen Router gelernt wurde wird nicht an den Router gesendet 
  - **Split Horizon mit Poison Reverse**
    - Route, die ich von einem anderen gelernt habe, propagiere ich an den mit der Metrik 16
  - **Triggered Updates**
    - direkt nach Routenänderung werden Updates versendet
    - kürzere Konvergenzzeit

## BGP

- Border Gateway Protocol
- Routen werden anhand politischer Metriken erstellt
  - manuelle Pflege dieser ist notwendig
- Internal und External BGP
  - internal: innerhalb eines AS
  - external: zwischen zwei AS
- Pfad-Attribute AS-Path
  - AS-Path hält den bisherigen Weg fest
    - Schleifen können erkannt werden, wenn Paket schon die eigene AS-Nummer enthält
    - Paket kann verwerfen werden
  - kürzester AS-Path wird genommen
- Verwaltung über 3 Tabellen (RIB - Routing Information Base)
  - Hauptroutingtabelle
    - da werden die zu benutzenden Routen gespeichert
  - Adj-RIB-IN
    - Tabelle mit erhaltenen Routing Updates
  - Adj-RIB-OUT
    - Tabelle mit Routing Updates, die verschickt werden
- Route Reflector
  - Konzentrator, der die Verbindungen zu anderen Routern schaltet -> stellt logische Vermaschung bereit ohne die eigentlichen Links zu allen aufbauen zu müssen
  - kann anhand von definierten Regeln Paketen filtern