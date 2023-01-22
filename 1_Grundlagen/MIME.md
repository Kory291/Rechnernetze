# MIME-Typen

- Definition der Daten im Rumpf der Nachricht

### Namensgebung
`Typ "/" [Baum .] Subtyp ["+" Suffix]* [";" parameter]`

#### Typ
- application
- audio
- font
- example
- image
- message
- model
- multipart
- text
- video

#### Baum
##### Standard Baum
- direkt mit der IETF Spezifikationen mit Zustimmung der IESG oder von einer IANA anerkannten Standardisierungs Organisation
- Prefix: ``

##### Vendor Baum
- Von der Industrie oder nicht-kommerziellen Vereinigungen eingereicht
- Prefix: `vnd.`

##### Personal or vanity Baum
- Mediatypen, die nicht für öffentlich verfügbare Produkte genutzt werden
- Experimentelle Mediatypen sind hier auch zu finden
- Prefix: `prs.`

##### unregistrierter Baum
- Mediatypen, die nur im privaten Umgebungen und mit beidseitiger Zustimmung der Nutzer verwendet werden können
- von der Nutzung wird strengstens abgeraten
- Prefix: `x.`

#### Suffix
- Ermöglicht die Nutzung generischer Strukturen, indem mit dem Suffix die konkrete Implementation benannt wird

#### Parameter
- Übergabe von Parametern, wie zum Beispiel bei `text/html; charset=UTF-8`

### Beispiele
- application/json
- application/javascript
- image/png
- audio/mpeg
- text/plain
- text/html
- text/xml