# WLAN

## ALOHA

- jeder sendet einfach, wenn er etwas hat
- viele Kollisionen -> geringe Auslastung des Kanals

## slotted ALOHA

- Zeitschlitze werden definiert zu denen ALOHA gefahren werden kann
  - Kollisionen treten immer zum Anfang auf
- Synchronisation notwendig
  - schwierig
- ingesamt höherer Durchsatz als mit ALOHA

## CSMA/CA

- Carrier Sense Multiple Access / Collision Avoidance
- Abhören, ob Kanal belegt ist
  - wenn nicht:
    - warte eine Zeit (DIFS - geringe Prio, oder SIFS - hohe Prio)
    - wenn Kanal bis dahin immernoch frei ist, sende deine Daten
    - wenn Kanal belegt sein sollte:
      - warte auf nächste Freiheit des Kanals und warte dann eine DIFS oder SIFS Zeit sowie eine zufällige Backoff-Zeit ab
      - speichere Backoff Zeit, wenn sie nicht abgesessen werden konnte und arbeite damit später weiter
  - wenn ja:
    - warte

## Hidden Station Problem

- nur AP in unmittelbarer Sendereichweite bekommen Kanalbelegung mit
- Einführen von Ready to send und Clear to send
- Erweiterung zu CSMA/CA
- nach Ablauf der DIFS Zeit wird nun ein Ready to send gesendet
- dieses wird nach einer SIFS Zeit mit einem Clear to send bestätigt
- Stationen, die das Clear to send hören, wissen dadurch, dass sie den Kanal nicht belegen dürfen
- Wartezeit wird im Ready to send mitgeteilt -> damit stellen sich die anderen Basisstationen einen Timer (NAV - Network Allocation Vector)