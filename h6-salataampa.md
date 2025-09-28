# H6 Salataampa

## x) Lue ja tiivistä

- Let’s Encrypt ja ACME-protokollan avulla hankitaan ja uusitaan automaattisesti salattu HTTPS-palvelin eikä ihmisen ei tarvitse tehdä tätä käsin.
- Prosessi sisältää kaksi vaihetta:
    1. ACME todistaa sertifikaatin myöntäjälle (CA eli Certificate Authority), että web-palvelin hallitsee domainia.
    2. Asiakas voi pyytää tai peruuttaa sertifikaatteja kyseiselle domainille. 

### Domainin validointi

- Let’s Encrypt tunnistaa ACME-asiakasohjelmiston julkisen avaimen avulla. Ensimmäisellä kerralla, kun ACME on vuorovaikutuksessa Let's Encryptin kanssa, se luo uuden avainparin. Tällä ACME todistaa Let's Encryptin CA:lle, että operaattori hallitsee yhtä tai useampaa domainia. 
- Miten tämä tapahtuu?
  - Asiakas kysyy Let’s Encryptin CA:lta mitä sen täytyy tehdä, kun se haluaa todistaa hallitsevansa tiettyä domainia.
  - Let’s Encryptin CA tarkistaa domainin ja lähettää yhden tai useamman haasteen (_challenge_).
  - Asiakasohjelmisto suorittaa yhden näistä annetuista haasteista.
  - Kun asiakas on valmis, se ilmoittaa siitä CA:lle.
  - CA tarkistaa onko haasteet ratkaistu useista verkon näkökulmista. Jos haasteet onnistuvat, asiakas on valtuutettu ja voi tällöin tehdä sertifikaattien hallintaa tietyllä domainilla. 

### Sertifikaatin myöntäminen ja peruuttaminen

- Sen jälkeen kun asiakas on valtuutettu, sertifikaatin pyytäminen, uusiminen ja peruuttaminen on yksinkertaista. Se tehdään lähettämällä sertifikaattien hallintaviestejä ja allekirjoittamalla ne valtuutetun avainparilla.
- Myöntäminen: asiakas tekee pyynnön Let's Encryptin CA:lle, jossa se pyytää sertifikaattia tietylle domainille käyttäen julkista avainta. Kun Let’s Encrypt CA saa pyynnön, se verifioi allekirjoitukset. Jos kaikki on hyvin, se myöntää sertifikaatin domainille. CA lähettää varmenteen moniin julkisiin Certificate Transparency -lokeihin.
- Peruuttaminen: Toimii samoin kuin myöntäminen. Asiakas kirjoittaa peruutuspyynnön, jossa käytetään tietyn domainin avainparia. Let's Encrypt CA tarkistaa, että pyyntö on valtuutettu. Jos se on, se julkaisee peruutustiedon Certificate Revocation List:ssä. Tällöin esimerkiksi selaimet tietävät olla hyväksymättä peruutettua sertifikaattia.

