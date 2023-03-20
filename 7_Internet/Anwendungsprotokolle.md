# Anwendungsprotokolle

## E-Mail

### SMTP

- Protokoll zum Versenden über übertragen von E-Mails zwischen MTA (Mail Transfer Agenten) über das Internet
- Kommando orientiert im Request/Response-Verfahren
- Kommandos:
  - ``HELO $DOMAIN``: Verbindungsaufbau
  - ``MAIL FROM:$REVERSE_PATH``: Mailabsender
  - ``RCPT TO:$FORWARD_PATH``: Mailempfänger
  - ``DATA``: Mailbody
  - ``RSET``: Reset
  - ``SEND FROM:$REVERSE_PATH``: Nachricht senden
  - ``SOML FROM:$REVERSE_PATH``: Senden oder Mail
  - ``SAML FROM:$REVERSE_PATH``: Senden und Mail
  - ``VRFY``: Überprüfe den Nutzer
  - ``EXPN``: klappe Liste aus
  - ``HELP``: Hilfe (auch zu einem speziellen Kommando möglich)
  - ``NOOP``: keine Operation
  - ``QUIT``: Verbindungsabbau
  - ``TURN``: Rollentausch

### IMAP

- Protokoll zur Kommunikation zwischen MUA (Mail User Agent) und MTA (Mail Transfer Agent)
- Arbeit auf dem Mail Server direkt (auch lesen)
- Client-Server-Modell mit Request-Response Verfahren

### POP3

- Protokoll zur Kommunikation zwischen MUA (Mail User Agent) und MTA (Mail Transfer Agent)
- Transfer der Mail vom MTA zum MUA
  - lokale Speicherung
- Kommando-basiert

### Vergleich IMAP / POP3

| Funktion | IMAP | POP3 |
| --- | --- | --- |
| unterstützt Offline-Modus | ✅ | ✅ |
| unterstützt Online-Modus | ✅ | ❌ |
| ünterstützt Disconnected-Modus | ✅ | ❌ |
| Mails laufem beim MTA auf | ✅ | ✅ |
| SMTP Gateway für Versand von Nachrichten nötig | ✅ | ✅ |
| Zugang zu unterschiedlichen Mailboxen möglich | ✅ | ❌ |
| Erlaubt Zugang zu anderen Daten, wie bspw. News | ✅ | ❌ |
| Geringe Bandbreite nötig | ✅ | ❌ |
| Message Status Flags lassen sich bearbeiten | ✅ | ❌ |
| Neue Nachrichten sind mit unterschiedlichen Clients überall im Netz verfügbar | ✅ | ✅ |
| offene Protokolle | ✅ | ✅ |
| Zusatzprotokolle für die Verwaltung von Benutzereinstellungen verfügbar | ✅ | ❌ |

## Telnet

- Client-Server-Modell
- Benutzung der Shell eines PC über das Internet (Zeichenbasiert)
  - Fernkonfiguration von Geräten
- heute eher veraltet, wegen unzureichender Sicherheit
- Benutzung von TCP

## HTTP

- Protokoll zur Kommunikation von Web-Client und Web-Server
- Adressierung über URL (Unified Resource Locator)
  - Addresierung von Diensten und Inhalten im Internet mittels Anker (Anchor)
  - ``<a href="file://localhost/datei.html">`` Aufruf einfach irgendeiner Datei
  - ``<a href="http://localhost/datei.html">`` Aufruf einer HTML-Datei
  - ``<a href="#item">`` Absprung zu Stelle in gleicher Datei
- TCP Port 80
- Dokumentenbeschreibung mit HTML (Hypertext Markup Language)
- Kommandos
  - GET
  - POST
  - PUT
  - DELETE
  - OPTIONS
  - HEAD
  - TRACE
  - CONNECT

## FTP

- File Transfer Protocol
- Austausch von Daten zwischen Rechnern
- Client-Server-Aufbau
- Nutzung von TCP
- Nutzung von einer Steuerleitung und einer Datenleitung

### genereller Ablauf

- Verbindungsaufbau über Steuerleitung
- Benutzeranmeldung über Steuerleitung
- Befehls und Parameteraustausch über Steuerleitung
- Aufbau der Datenleitung
- Datenaustausch ...
- Abbau der Datenleitung
- Abbau der Steuerleitung nach erfolgreichem Abbau der Datenleitung

### aktiv

- Client meldet sich am Server an
- Server initiert dann Datenverbindung

### passiv

- Client meldet sich am Server an
- Server wartet auf Verbindungsaufbau der Datenleitung vom Client
- benutzt, wenn der Server nicht zum Client routen kann (z.B. bei Benutzung von NAT in einem Router -> geänderte IP)

### Bestätigungscodes

- \<text> CLRF
- <1yz> vorzeitige positive Bestätigung
- <2yz> prositive Abschlussbestätigung
- <3yz> zwischenzeitliche positive Bestätigung
- <4yz> vorübergehend negative Abschlussbestätigung
- <5yz> permanent negative Abschlussbestätigung
- \<x0z> Syntax
- \<x1z> Information
- \<x2z> Verbindung
- \<x3z> Identifikation
- \<x4z> nicht definiert
- \<x5z> Dateisystem
