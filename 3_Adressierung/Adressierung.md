# Adressierung

## Unterscheidung

- Layer
  - physische Adressen, Knotenadressen
  - logische Adressen
- Form
  - numerische Adressen
  - symbolische Adressen
- Individualität
  - Knotenadresse
  - Netzwerkadresse

## symbolische/alphanumerische Adressen

- Beispiele: FQDN (Fully    Qualified Domain Name): host.subdomain.domain.TLD
  - maximale Länge des FQDN: 255 Zeichen
  - maximale Länge eines Labels (Domain, Subdomain(s), Host): 63 Zeichen
  - TLD: .de, .org, .com

## logische numerische Adpater-/Interface-Adressen

- IPv4-Adressen:
  - Länge: 32 Bits (4 Bytes)
  - Beispiel: 192.168.46.100
- IPv6-Adressen:
  - 128 Bits (16 Bytes)
  - Beispiel: fe80::71d9:b9b6:c561:43da%12

## physische Adapter-Adressen

- MAC-Adressen
  - Länge: 48 Bits (6 Bytes)
- EUI-64-Adressen
  - Extended Unique Identifier
  - Umrechnung von MAC-Adressen in EUI-64-Adressen ist möglich, wird aber wegen möglichen Dopplungen als veraltet angesehen
  - Länge: 64 Bits (8 Bytes)



## Zuordnung der Adressen

| - | symbolische/alphanumerische Adresse | logische numerische Adapter/Interface-Adressen | physische Adapter-Adressen |
| -- | -- | -- | -- |
| symbolische/alphanumerische Adresse | - | DNS, Imhosts, WIMS, BCAST, hosts | - |
| logische numerische Adapter/Interface-Adressen | DNS, Imhosts, WIMS, BCAST, hosts | - | ARP |
| physische Adapter-Adressen | - | RARP | - |
