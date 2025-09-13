# H4 Maailman kuulee

## ...KESKEN... x) Tiivistäminen

**a) Pilvipalvelimen vuokraus ja asennus**
- Käyttäjätilin luomisen jälkeen tehtiin virtuaalikone:
  - Käyttöjärjestelmä: uusin Debian
  - Virtuaalikoneen paketti: edullisin peruspaketti, koska tätä on mahdollista myöhemmin kasvattaa
  - Datakeskus: se, joka on mahdollisimman lähellä sivuston käyttäjiä. Tällöin tiedonsiirto on mahdollisimman nopeaa ja GDPR:n vaatimukset on huomioitu.
  - Autentikointi: SSH-avaimet tai salasana. SSH-avaimet on todella turvallinen vaihtoehto, mutta salasanakin on hyvä, kunhan siinä käyttää vahvaa salasanaa.
  - Lisävaihtoehdot: ei kannata ottaa, näitä ovat esimerkiksi backupit.
- Kun virtuaalikone oli vuokrattu, vuokrattiin domainnimi Namecheapin kautta ja lopuksi domainnimi ohjattiin osoittamaan aiemmin hankitulle virtuaalipalvelimelle.

**d) Palvelin suojaan palomuurilla**
- Ajettiin komento _ssh root@188.166.4.6_, jotta saatiin yhteys virtuaalikoneeseen.
- Haettiin päivitykset komennolla _sudo apt-get update_ ja asennettiin palomuuri _sudo apt-get install ufw_.
- Lopuksi tehtiin palomuuriin reikä porttia varten komennolla _sudo ufw allow 22/tpc_ ja laitettiin palomuurin päälle _sudo ufw enable_.

**e) Kotisivut palvelimelle**
- Tehtiin virtuaalipalvelimen terminaalissa uusi käyttäjä komennolla _sudo adduser suska_ ja tämän jälkeen käyttäjästä tehtiin pääkäyttäjä _sudo adduser suska sudo_.
- Avattiin toinen terminaali, jossa testattiin toimiiko uusi käyttäjä. Avattiin SSH-yhteys virtuaalipalvelimeen komennolla _ssh suska@188.166.4.6_ ja päivitettiin tiedot _sudo apt-get update_.
- Lopuksi lukittiin juuri komennolla _sudo usermod –lock root_.
- Avattiin toinen terminaali ja kirjauduttiin sisään virtuaalipalvelimelle SSH-yhteydellä. Asennettiin päivitykset ja tietoturvapäivitykset komennoilla _sudo apt-get update_, _sudo apt-get upgrade_ ja _sudo apt-get dist-upgrade_.
- Asennettiin Apach-palvelin komennolla _sudo apt-get install apache2_ ja testattiin palvelimen tilaa _sudo systemctl status apache2_ (running).
- Tehtiin toinen reikä palomuuriin portille _sudo ufw allow 80/tcp_.
- Korvattiin Apache-testisivu komennolla _echo Hello world! |sudo tee /var/www/html/index.html_, jolla sivulle ilmestyi "Hello World!".


f) Palvelimen ohjelmien päivitys
