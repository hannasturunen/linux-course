# H6 Salataampa

## x) Tiivistelmät

### Let's Encrypt 2024: How It Works

- Let’s Encrypt ja ACME-protokollan avulla hankitaan ja uusitaan automaattisesti salattu HTTPS-palvelin eikä ihmisen ei tarvitse tehdä tätä käsin.
- Prosessissa ACME todistaa sertifikaatin myöntäjälle (CA eli Certificate Authority), että web-palvelin hallitsee domainia. Kun tämä on hoidettu, asiakas voi pyytää tai peruuttaa sertifikaatteja kyseiselle domainille. 

#### Domainin validointi

- Let’s Encrypt tunnistaa ACME-asiakasohjelmiston julkisen avaimen avulla. Ensimmäisellä kerralla, kun ACME on vuorovaikutuksessa Let's Encryptin kanssa, se luo uuden avainparin. Tällä ACME todistaa Let's Encryptin CA:lle, että operaattori hallitsee yhtä tai useampaa domainia. 
- Miten tämä tapahtuu?
  - Asiakas kysyy Let’s Encryptin CA:lta mitä sen täytyy tehdä, kun se haluaa todistaa hallitsevansa tiettyä domainia.
  - Let’s Encryptin CA tarkistaa domainin ja lähettää yhden tai useamman haasteen (_challenge_).
  - Asiakasohjelmisto suorittaa yhden näistä annetuista haasteista.
  - Kun asiakas on valmis, se ilmoittaa siitä CA:lle.
  - CA tarkistaa onko haasteet ratkaistu useista verkon näkökulmista. Jos haasteet onnistuvat, asiakas on valtuutettu ja voi tällöin tehdä sertifikaattien hallintaa tietyllä domainilla. 

#### Sertifikaatin myöntäminen ja peruuttaminen

- Sen jälkeen kun asiakas on valtuutettu, sertifikaatin pyytäminen, uusiminen ja peruuttaminen on yksinkertaista. Se tehdään lähettämällä sertifikaattien hallintaviestejä ja allekirjoittamalla ne valtuutetun avainparilla.
- Myöntäminen: asiakas tekee pyynnön Let's Encryptin CA:lle, jossa se pyytää sertifikaattia tietylle domainille käyttäen julkista avainta. Kun Let’s Encrypt CA saa pyynnön, se verifioi allekirjoitukset. Jos kaikki on hyvin, se myöntää sertifikaatin domainille. CA lähettää varmenteen moniin julkisiin Certificate Transparency -lokeihin.
- Peruuttaminen: Toimii samoin kuin myöntäminen. Asiakas kirjoittaa peruutuspyynnön, jossa käytetään tietyn domainin avainparia. Let's Encrypt CA tarkistaa, että pyyntö on valtuutettu. Jos se on, se julkaisee peruutustiedon Certificate Revocation List:ssä. Tällöin esimerkiksi selaimet tietävät olla hyväksymättä peruutettua sertifikaattia.

(Let's Encrypt 2.8.2025)

### The Apache Software Foundation 2025: Apache HTTP Server Version 2.4

- Yksinkertainen esimerkki konfiguraatiosta: 
```
LoadModule ssl_module modules/mod_ssl.so

Listen 443
<VirtualHost *:443>
    ServerName www.example.com
    SSLEngine on
    SSLCertificateFile "/path/to/www.example.com.cert"
    SSLCertificateKeyFile "/path/to/www.example.com.key"
</VirtualHost>
```
- SSL-konfiguraation pitää sisältää vähintään nämä tiedot.

(The Apache Software Foundation 2025)

## Virtuaalikonetehtävät

Tein harjoitukset sunnuntaina 28.9.2025 ... ... Helsingissä kotona. Koneena kaikissa tehtävissä oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä on Windows 11 Home.

... tähän tiivistelmää ...

## a) Let's. Hanki ja asenna palvelimellesi ilmainen TLS-sertifikaatti Let's Encryptilta. Osoita, että se toimii.

- 17.45 Avasin VirtualBoxin ja kirjauduin terminaalissa virtuaalipalvelimelleni komennolla ssh `hannatu@hattara.me`. Annoin salasanani ja pääsin sisään.
- 17.50 Varmistin, että sivuni toimii vielä. Avasin Firefoxin selaimen ja menin osoitteeseen hattara.me. Päivitin varmuuden vuoksi sivun ctrl+shift+r. Sivu näkyi yhä, joten kaikki vielä kunnossa.
- 17.52 Tein varmuuden vuoksi virtuaalikoneelle päivitykset komennolla `sudo apt-get update`. Annoin salasanani ja teki päivitykset.
- 18.00 Potkaisin vielä varmuuden vuoksi Apache2-demonia komennolla `sudo systemctl reload apache2`. Tämän jälkeen tarkistin vielä, että verkkosivu hattara.me toimii Firefoxilla (päivitin sivun ctrl+shift+r) ja kännykän Safari-selaimella. Molemmissa toimii hyvin,

- ... KUVA 01 a + b ...
  
- 18.05 Kun alkuvalmistelut on tehty, siirrytään salaamiseen. Avasin tulimuurista portit 80 ja 443 eli HTTP:n ja HTTPS:n portit. Annoin komennot `sudo ufw allow 80/tcp` ja `sudo ufw allow 443/tcp`. HTTP:n portti 80 olikin jo auki. Tarkistin vielä, että portit ovat auki komennolla `sudo ufw status verbose`. Portit 80 ja 443 ovat auki sekä IPv4:lle että IPv6:lle.

- ... KUVA 02 ...

- 18.12 Asensin certbotin komennolla `sudo apt-get install certbot python3-certbot-apache`, joka latasi ohjelman. Certbot on Let's encryptin työkalu, jonka avulla saadaan HTTPS käyttöön.  

- ... KUVA 03 ...

- 18.20 Hain domainnimilleni varmenteen. Tämä tapahtui komennolla `sudo certbot --apache --domains hattara.me,www.hattara.me`. Jouduin laittamaan sähköpostiosoitteeni, koska ei päästänyt eteenpäin ilman sitä. Sen lisäksi ei löytänyt www.hattara.me. Tajusin tämän johtuvan siitä, että tuolla sivulla ei ole vielä tehty AliasNamea _Name Based Virtual Hostina_.
- 18.34 Asensin micro-editorin komennolla `sudo apt-get install micro`. Tein konfiguraatiotiedoston komennolla `sudoedit /etc/apache2/sites-available/hattara.me.conf`. 

- ... KUVA 04 ...

- 18.48 Tein kansion `mkdir -p /home/hannatu/public-sites/hattara`.
- 19.13 Otetaan verkkosivustolle Apache2 käyttöön komennolla `sudo a2ensite hattara.me`. Tämän jälkeen käynnistettiin Apache2 uudestaan komennolla `sudo systemctl restart apache2`. Komennolla `curl localhost` antaa vielä sen minkä pitää, mutta Firefoxilla antaa _Forbidden_. Joku on siis vielä pielessä.

- ... KUVA 05 ...

- 19.49 Testasin korvata testisivun komennolla `echo "It's me, hi!" | sudo tee /var/www/html/index.html`. Yhä toimii `curl localhost`-komennolla, mutta ei Firefoxxissa.
- 19.55 Tajusin, etten ollut tehnyt vielä index.html-sivua. Menin hattara-kansioon komennolla `cd /home/hannatu/public-sites/hattara/` ja loin sinne index.html-tiedoston komennolla `micro index.html`. Kopioin koodin Karvisen sivuilta ... ... . Tallensin tekemäni muutokset _ctrl+s_ ja suljin micro-editorin _ctrl+q_.

- ... KUVA 06 ...

- 20.07 Potkaisin taas Apache2:n käyntiin komennolla `sudo systemctl restart apache2`. Firefox antaa yhä ... ... väärää.

- 20.19 Tarkastin oikeudet -> puuttuu kuva 06:n alimmasta.

- KUVA 07.

- 20.21 Lisätään oikeudet ja tarkistetaan vikat. `sudo systemctl reload apache2`

- KUVA 08.

- 20.27 Nyt Firefox antaa oikeaa, mutta curl localhost ei. Ajoin komennon `curl -H 'Host: hattara.me' localhost`, josta alla oleva.

- KUVA 09.

- 20.33 ei auttanut, komento `sudo a2dissite 000-default` ja `sudo systemctl reload apache2`. Komento `curl localhost`. Toimii!!!

- KUVA 10.

- 20.36 Jatkan huomenna, Suljin yhteyden virtuaalipalvelimeen komennolla exit, jonka jälkeen suljin terminaalin ja virtuaalikoneen.


## b) A-rating. Testaa oma sivusi TLS jollain yleisellä laadunvarmistustyökalulla, esim. SSLLabs (Käytä vain tavanomaisia tarkistustyökaluja, ei tunkeutumistestausta eikä siihen liittyviä työkaluja)






## Lähteet

- Let's Encrypt 2.8.2025. How It Works. Luettavissa: https://letsencrypt.org/how-it-works/. Luettu: 28.9.2025.
- The Apache Software Foundation 2025: Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example. Luettavissa: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample. Luettu: 28.9.2025.
