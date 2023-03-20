# IP Adressierung

## IPv4

- IP-Adresse -> 32 Bit (4 Byte)
- Angabe in vier Oktetten
  - `0.0.0.0` bis `255.255.255.255`
- Netzanteil und Hostanteil
  - Angabe Netzanteil mit `/20`
- Erste Adresse eine Subnetz zur Identifikation des Subnetz
- Letzte Adresse eines Subnetz als Broadcast an alle Teilnehmer im Subnetz
- spezielle und reservierte Adressen:
  - ``127.0.0.1`` bis ``127.255.255.254``: Loopback
  - ``0.0.0.0/0``: gesamtes Internet
  - ``10.x.y.z``, ``172.16.0.0/12``, ``192.168.x.y``: privater Adressbereich

### Classful adressing

- anfangs zu IPv4
- Definition von 5 Adressklassen
- -> heute eigentlich keine Bedeutung mehr

- **Klasse A**
  - Adresse: 0NNNNNNN.HHHHHHHH.HHHHHHHH.HHHHHHHH
  - ``1.a.b.c`` bis ``126.x.y.z``
- **Klasse B**
  - Adresse: 10NNNNNN.NNNNNNNN.HHHHHHHH.HHHHHHHH
  - ``129.N.H.H`` bis ``191.N.H.H``
- **Klasse C**
  - Adresse: 110NNNNN.NNNNNNNN.NNNNNNNN.HHHHHHHH
  - ``192.N.N.H`` bis ``123.N.N.H``
- **Klasse D**
  - Adresse: 111MMMMM.MMMMMMMM.MMMMMMMM.MMMMMMMM
  - ``224.a.b.c`` bis ``239.x.y.z``
  - Multicast-Adressen
- **Klasse E**
  - Adresse: 1111EEEE.EEEEEEEE.EEEEEEEE.EEEEEEEE
  - ``240.a.b.c`` bis ``254.x.y.z``
  - experimentelle Adressen

### Classless adressing (CIDR)

- wird heute benutzt
- variable Festlegung von Präfixlänge (Anteil der Netzadresse an IP-Adresse)
  - zwingende Angabe über die Präfixlänge (`/24`)
- Beispiel: ``217.237.151.51/24``

## IPv6

- IP-Adresse: 128 Bit (16 Byte)
- Notation mit Hex-Werten bietet sich an
  - Ein Block mit ``0000`` kann als ``0`` zusammengefasst werden
  - Einmal können mehrere hintereinanderliegende Blöcke mit ``0000:0000:0000...`` zu ``::`` zusammengefasst werden 
- Beispiel: ``2001:0db8:85a3:08d3:1319:8a2:e:0370:7347/64``

### Scope von Adressen

- node local / interface local
  - ``::EUI-64-Adresse``
- link local
  - ``FE80::EUI-64-Adresse/64`` bis ``FE8F::EUI-64-Adresse/64``
  - automatisch aus MAC generiert
- site local
  - ``FEC0::xyzw:EUI-64-Adresse/64`` bis ``FEFF::xyzw:EUI-64-Adresse/64``
  - mehrere Subnetze ohne Internet Konnektivität
- global scope
  - ``2000::`` bis ``3FFF::``
  - öffentlich routebar
  - global unicast address
  - Konfiguraitionsmöglichkeiten:
    - manuell
    - SLAAC (Stateless autoconfiguration)
      - NDP (Neighbour Discovery Protocol)
    - stateful configuration
      - DHCPv6
- Multicast
  - ``FF00::/8``
- Migrationsadressen
  - 6to4
  - IPv4-kompatibel
  - IPv4-mapped