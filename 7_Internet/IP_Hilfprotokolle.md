# IP Hilfsprotokolle

## ARP

- Zuordnung MAC-Adresse zur IP-Adresse
  - ohne MAC Adresse keine Übertragung möglich
- **wichtig in IPv4**
- Header:
![ARP_Header](../images/ARP_Header.png)

- Ablauf ARP-Request:
  1. MAC-Adresse eines IP-Pakets unbekannt (nicht im ARP Cache)
  2. Senden (Broadcast) eines ARP Requests mit:
     - Quell-Hardwareadresse: eigene MAC-Adresse
     - Quell-IP: eigene IP-Adresse
     - Ziel-Hardwareadresse: 00-00-00-00-00-00 (trotz des Broadcasts)
     - Ziel-IP: IP für die kein Eintrag in ARP Cache bekannt ist
  3. Rechner erhält Paket und überprüft, ob die Ziel IP die eigene ist
     1. nein -> verwerfen
     2. Ziel IP ist die eigene -> weiter machen
  4. Tauschen von Werten der Ziel- und Quell-Felder
  5. Befüllen der Quell-Hardwareadresse mit der eigenen MAC-Adresse
  6. Paket wird zurückgesendet
  7. Anforderer erhält Paket und kann Kombination im ARP Cache mit einem Timer hinterlegen

## NDP

- Neighbor Discovery Protocol
- über ICMPv6 Nachrichten gesendet
- ARP Ersatz für IPv6
- dient zum Ermitteln von Routern und anderen Teilnehmern im eigenen Netz
  - darüber auch Feststellung von Adressduplikationen
  - Ermittlung der Erreichbarkeit
- ermöglicht auch die Umsetzung von SLAAC (Stateless autoconfiguration)
- Nachrichtentypen
  - Router Solicitation
    - Multicast-Anfrage an alle Router im gleichen Netz
  - Router Advertisment
    - Antwort auf Router Solicitation
  - Neighbor Solicitation
    - Anfrage an Link-Layer Multicast Adresse einer IPv6 Adresse
  - Neighbor Advertisment
    - Antwort auf Neighbor Solicitation
    - Sendung kann auch ungefragt stattfinden, wenn sich die Layer-2 Adresse geändert hat
  - Redirect
    - wird gesendet, wenn Router einen besseren ersten Router für ein Paket kennt

## ICMP

- Internet Control Message Protocol
- verwendet in IPv4 und IPv6 (als ICMPv6)
- Hilfsprotokoll zur Überwachung des Netzwerks
- ping nutzt ICMP
- Time Exceeded
  - das Ziel konnte nicht innerhalb der TTL erreicht wurde
- Destination Unreachable
  - Paket kann nicht zugestellt werden kann
  - bspw, wenn die MTU eines Links nicht ausreicht für das Paket und es auch nicht fragmentiert werden darf
- Echo & Replay
  - Test auf Antwort vom Gegenüber
- Timestamp Request & Replay
  - wie Echo nur mit Zeitinformationen
  - Nutzung bei Performancebestimmung

## DHCP

- Dynamic Host Configuration Protocol
- automatische Vergabe von IP-Adresse an anfragenden Rechner

- Ablauf:
  1. Client sendet DHCP-Discover
  2. Server antwortet mit DHCP-OFFER
  3. Client antwortet dem Server mit DHCP-Request, wenn die IP nicht schon vergeben ist (IP könnte in Zwischenzeit schon vergeben worden sein -> dann zurück zu 1)
  4. Server bestätigt die Allokation mit einem DHCP-Acknowledgment
  5. Client startet Timer für Belegung der IP
  6. Nach Ablauf des Timers erneut DHCP-Request (Adresse wird weiter belegt)
  7. Server antwortet mit einem DHCP-Acknowledgement

