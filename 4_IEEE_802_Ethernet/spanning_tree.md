# Spanning Tree

- benutzt auf Layer 2, um Schleifenfreiheit zu erstellen
- Sperren von Ports, die Schleifen erzeugen würden

- Zustände:
  - Disabled
    - Port ist ausgeschaltet
  - Blocked
    - Verarbeitung von BPDUs
    - keine Übertragung von BPDUs
  - Listening
    - Verarbeitung und Übertragung von BPDUs
  - Learning
    - Lernen von Adressen
    - keine Weiterleitung von Frames
  - Forwarding
    - Arbeitszustands des Ports, wenn der Baum aufgespannt wurde
- Port Rollen:
  - Root Port
    - kürzester Weg zum Root
  - Designated Port
    - Weg von Root weg
  - Blocked
    - Port wird nicht benutzt
- Ablauf:
  1. Switche bewerben sich mit Hello BPDUs die Root Bridge zu sein
  2. Bridge mit kleinster Priorität und dann mit kleinster MAC-Adresse wird Root
  3. Danach können die Port Stati festgelegt werden, um den Baum aufzuspannen

- Problem:
  - hohe Konvergenzzeit bei Änderungen in der Topologie (~50s)

## Rapid Spanning Tree

- Verfahren muss nur für die Ports angewendet werden, die von Topologieänderung betroffen sind
  - kürzere Konvergenzzeit (<1s)
  - Switching funktioniert bei den anderen Ports noch ohne Probleme
- neue Port Rollen, die bei Ausfall des Root Ports genutzt werden:
  - Alternate
    - Weg über anderen Switch zur Root-Bridge
  - Backup
    - Link Backup -> Ziel ist der gleiche Switch
- Zustände:
  - Discarding
    - Pakete werden verworfen
  - Learning
    - Topologie wird gelernt -> Adressen
  - Forwarding
    - eingeschwungener Zustand