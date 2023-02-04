# OSI-Modell

7. Anwendungsschichte (application layer)
6. Darstellungsschicht (presentation layer)
5. Sitzungsschicht (sessions layer)
4. Transportschicht (transport layer)
3. Netzwerkschicht (network layer)
2. Datensicherungsschicht (data link layer)
1. physikalische Sicht (physical layer)

### Layer 7 - Application Layer

#### Aufgaben

- Anwendungsprotokolle
  - Messaging
  - Remote Login
  - Dateitransfer

#### Beispiele

- E-Mail
- SSH
- FTP

### Layer 6 - Presentation Layer

#### Aufgaben

- Einheitliche Darstellung (Kodierung)
  - Quellencodierung (Zeichencodierung, Sprachcodierung, Videocodierung)
- Verschlüsselung

#### Beispiele

- MIME-Typen
- JSON
- ASN.1 Datendefinition mit BER (Basic Encoding Rules)
- XML

### Layer 5 - Sessions Layer

#### Aufgaben

- Sitzungssteuerung (Verbindungsaufbau, Verbindungsabbau, Reset, Keep-alive)
- Signalisierung
- Aushandeln von Sitzungsparametern (Capability Exchange)
- Codecs aushandeln

#### Beispiele

- **keine gefunden**

### Layer 4 - Transport Layer

#### Aufgaben

- Flussteuerung 
- Fehlerkorrektur
- Überlaststeuerung (implizit)
- Verbindungssteuerung
- Kommunikationsports
- Segmentverkettung

#### Berispiele

- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)

### Layer 3 - Network Layer

#### Aufgaben

- Ent-to-end Adressierung
- Leitweglenkung
- Wegewahl
- Überlaststeuerung
- Priorisierung, QoS Scheduling
- Packet Identifikation (ID)

#### Beispiele

- IPv4
- IPv6

### Layer 2 - Data Link Layer

#### Aufgaben

- Rahmenbildung/-erkennung
- Fehlererkennung/-korrektur (CRC)
- Flussteuerung
- Loop Detection (STP)
- CoS-Priorisierung (bei Ethernet)
- logische Adressierung

#### Beispiele

- Ethernet
- 

### Layer 1 - Physical Link Layer

#### Aufgaben

- Mediengerechte Wandlung von Bitrömen
- Signaldetektion
- Modulationsverfahren
- Scrambling
- Multiplexing (FDM, OFDM, TDM, CDM, PDM, SDM)
- Stromversorgung
- Überlast-/Kurzschlusssicherung

#### Beispiele

- DSL (Digital Subscriber Line)
- ISDN (Integrated Services Digital Network)
- LoRa
- Bluetooth
- OTN (Optical Tansport Network)
- I²C