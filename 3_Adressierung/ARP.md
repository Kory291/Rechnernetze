# ARP / RARP

## ARP

### Ziele

- Zuordnung IP-Adresse <-> MAC-Adresse
  - notwendig, wenn Kommunikation über IP ablaufen soll

### Header

![ARP_Header](./../images/APR_Header.PNG)

- Operationen:
  - 0x0001 ARP Request
  - 0x0002 ARP Response
  - 0x0003 RARP Request
  - 0x0004 RAPR Response

### Ablauf

1. Ziel-MAC-Adresse ist unbekannt, Ziel-IP-Adresse ist bekannt
2. Erstellen einer ARP-Request mit Quell-IP-Adresse und Quell-MAC-Adresse des eigenen Geräts. Die Ziel-IP-Adresse wird mit der IP-Adresse befüllt für die die MAC-Adresse erfragt werden soll. Die Ziel-MAC-Adresse wird auf `FF-FF-FF-FF-FF` (Ethernet-Broadcast-Adresse) gesetzt. -> Dadurch erhält jeder in der Broadcastdomäne die ARP-Request.
3. Jeder Computer der das Paket erhält, schaut nach, ob die Empfänger-IP-Adresse die eigene IP-Adresse ist. Wenn sie das nicht ist, wird das Paket verworfen.
4. Ist die Empfänger-IP-Adresse, wird eine ARP-Response erstellt. In der ARP-Response wird die Quell-IP-Adresse und die Quell-MAC-Adresse mit den eigenen Daten befüllt. Die Ziel-IP-Adresse und die Ziel-MAC-Adresse können aus der Quell-IP-Adresse und der Quell-MAC-Adresse der ARP-Request übernommen werden. Es empfiehlt sich hier den eigenen ARP-Cache zu aktualisieren (eventuell Aufnehmen der IP-MAC-Zuordnung, wenn noch nicht bekannt, oder aktualisieren der Aktivität)

### Probleme

- ARP-Spoofing
  - Die ARP-Request können abgefangen werden. Dabei kann die Ziel MAC-Adresse auf eine neue geändert werden. Das hat zur Folge, dass der Verkehr dann beim Angreifer landet und nicht beim eigentlichen Ziel, da ARP keine Sicherheitsüberprüfung eingebaut hat.

## RARP

- Zuordnung einer IP-Adresse, wenn die MAC-Adresse bekannt ist
  - nützlich, wenn die eigene IP nicht gespeichert wird.