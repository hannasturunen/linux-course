# H4 Maailman kuulee

## ...KESKEN... x) Tiivistäminen

Pilvipalvelimen vuokraus ja asennus
- Käyttäjätilin luomisen jälkeen tehtiin virtuaalikone:
  - Käyttöjärjestelmä: uusin Debian
  - Virtuaalikoneen paketti: edullisin peruspaketti, koska tätä on mahdollista myöhemmin kasvattaa
  - Datakeskus: se, joka on mahdollisimman lähellä sivuston käyttäjiä. Tällöin tiedonsiirto on mahdollisimman nopeaa ja GDPR:n vaatimukset on huomioitu.
  - Autentikointi: SSH-avaimet tai salasana. SSH-avaimet on todella turvallinen vaihtoehto, mutta salasanakin on hyvä, kunhan siinä käyttää vahvaa salasanaa.
  - Lisävaihtoehdot: ei kannata ottaa, näitä ovat esimerkiksi backupit.
- Kun virtuaalikone oli vuokrattu, vuokrattiin domainnimi Namecheapin kautta ja lopuksi domainnimi ohjattiin osoittamaan aiemmin hankitulle virtuaalipalvelimelle.

**Palvelin suojaan palomuurilla**

e) Kotisivut palvelimelle


f) Palvelimen ohjelmien päivitys
