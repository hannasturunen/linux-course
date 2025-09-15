# H4 Maailman kuulee

## x) Tiivistelmät

### Susanna Lehto: Teoriasta käytäntöön pilvipalvelimen avulla (h4)

**a) Pilvipalvelimen vuokraus ja asennus**
- Lehto loi käyttäjätilin, jonka jälkeen teki virtuaalikoneen:
  - Käyttöjärjestelmä: uusin Debian
  - Virtuaalikoneen paketti: edullisin peruspaketti, koska tätä on mahdollista myöhemmin kasvattaa
  - Datakeskus: se, joka on mahdollisimman lähellä sivuston käyttäjiä. Tällöin tiedonsiirto on mahdollisimman nopeaa ja GDPR:n vaatimukset on huomioitu.
  - Autentikointi: SSH-avaimet tai salasana. SSH-avaimet on todella turvallinen vaihtoehto, mutta salasanakin on hyvä, kunhan siinä käyttää vahvaa salasanaa.
  - Lisävaihtoehdot: ei kannata ottaa, näitä ovat esimerkiksi backupit.
- Kun virtuaalikone oli vuokrattu, hän vuokrasi domainnimen Namecheapin kautta ja ohjasi domainnimen osoittamaan aiemmin hankitulle virtuaalipalvelimelle.

**d) Palvelin suojaan palomuurilla**
- Lehto ajoi komennon ```ssh root@188.166.4.6```, jotta sai yhteyden virtuaalikoneeseen.
- Haki päivitykset komennolla ```sudo apt-get update``` ja asensi palomuurin ```sudo apt-get install ufw```.
- Lopuksi teki palomuuriin reiän porttia varten komennolla ```sudo ufw allow 22/tpc``` ja laittoi palomuurin päälle ```sudo ufw enable```.

**e) Kotisivut palvelimelle**
- Lehto teki uuden käyttäjän komennolla ```sudo adduser suska``` ja tämän jälkeen teki käyttäjästä pääkäyttäjän ```sudo adduser suska sudo```.
- Avasi toisen terminaalin, jolla avasi SSH-yhteyden virtuaalipalvelimeen ```ssh suska@188.166.4.6``` ja päivitti tiedot ```sudo apt-get update```. Lopuksi lukitsi juuren ```sudo usermod –lock root```.
- Kirjautui sisään virtuaalipalvelimelle toisella terminaalilla käyttäen SSH-yhteyttä. Asensi päivitykset ja tietoturvapäivitykset komennoilla ```sudo apt-get update```, ```sudo apt-get upgrade``` ja ```sudo apt-get dist-upgrade```.
- Asensi Apach-palvelimen ```sudo apt-get install apache2```, jonka jälkeen teki toisen reiän palomuuriin toiselle portille ```sudo ufw allow 80/tcp```.
- Korvasi Apache-testisivun komennolla ```echo Hello world! |sudo tee /var/www/html/index.html```, jolla sivulle ilmestyi "Hello World!".
- Lopuksi hän loi omalle käyttäjälleen julkisen kansion kotihakemistoon ja nettisivulle lyhyen rungon W3Schools-sivujen avulla.

**f) Palvelimen ohjelmien päivitys**
- Lehto avasi terminaalin ja otti SSH-yhteyden virtuaalipalvelimelle.
- Haki tiedot päivityksistä, asensi ne ja haki myös tietoturvapäivitykset komennoilla ```sudo apt-get update```, ```sudo apt-get upgrade``` ja ```sudo apt-get dist-upgrade```.

(Lehto, 14.2.2022)

### Tero Karvinen: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS

- Käytä aina hyviä salasanoja!
- Virtuaalisia palvelimia voi vuokrata esimerkiksi DigitalOceanilta, Linodelta ja Gandilta.
- GitHubilta saa ilmaisen Education student -paketin, jossa on virtuaalinen palvelin ja .me-domainnimen rajoitetuksi ajaksi.
- Artikkelissa ohjeistetaan miten luodaan uusi palvelin DigitalOceanille, miten palomuuriin tehdään reikä ja miten sen saa päälle, miten tehdään sudo-käyttäjä, miten root-käyttäjä suljetaan ja miten ohjelmat päivitetään. Lopuksi aletaan käyttämään luotua palvelinta. Mukana on myös komennot näihin.
- DNS-nimen voi vuokrata esimerkiksi NameCheapistä.   

(Karvinen, 19.9.2017)

## Virtuaalikonetehtävät

Tein harjoitukset ... ... Helsingissä kotona. Tein ... (kohdat ...). Koneena kaikissa tehtävissä oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä on Windows 11 Home.


## a) Oman virtuaalipalvelimen vuokraus DigitalOceanilta

- klo 16.05 Päätin ottaa virtuaalipalvelimen DigitalOceanilta ja hyödyntää GitHub Education -pakettia. Olin tehnyt tunnukset sinne jo tunnilla, mutta en löytänyt tätä kautta mahdollisuutta saada virtuaalipalvelinta ilmaiseksi. Hain netistä hakusanoilla "digital ocean github education", jolla pääsin sivustolle, jossa otettiin huomioon GitHubin Education -paketti. Annoin luottokorttitietoni, jolla varmistin itseni. Sain käyttöön opiskelijanpaketin, jossa on $200 vuodeksi käyttöön.

... KUVA 01 ja 02 ...

- 16.20 Huomasin Lehdon artikkelista, että hän oli laittanut maksuhälytykset päälle. Tämä oli mielestäni hyvä idea, joten tein itse saman. Menin _Billing_-sivustolle (valikossa vasemmalla) ja sieltä _Settings_-kohtaan. Kun selasin sivua alemmaksi, löysin kohdan _Billing Alert_. Katsoin, että halvimman virtuaalipalvelimen saa $4 kuukaudessa, joten laitoin maksurajaksi $3. Tällöin maksuraja ylittyy jokaisena kuukautena, joten muistan tarvittaessa perua tilauksen myöhemmin. Tätä voi myös tarvittaessa muuttaa, jos koenkin, että sähköposteja tulee liian paljon. Klikkasin _Confirm_.

... KUVA 03 ...

- 16.33 Aloitin virtuaalipalvelimen luomisen. Vasemmalla olevassa valikossa näkyi _Droplet_-nappi, jota klikkasin. Näin heti paikan, josta voi alkaa luomaan virtuaalipalvelinta, joten klikkasin _Create Droplet_.

... KUVA 04 ...

- 16.37 Valitsin virtuaalipalvelimen sijainniksi Frankfurtin, toinen vaihtoehto olisi ollut Amsterdam, jotka molemmat sijaitsevat Euroopassa. Sen lisäksi kannattaa ottaa palvelin mahdollisimman läheltä, jotta latenssi on mahdollisimman pieni.

... KUVA 05 ... 

- 16.41 Valitsin käyttöjärjestelmäksi _Debian version 12 x64_. Debianille ei ollut muita vaihtoehtoja. 

... KUVA 06 ... 

- 16.45 Valitsin prosessoriksi _Shared CPU Basic_ ja _CPU options_ -kohdasta _Regular, 512 MB / 1 CPU, 10 GB SSD Disk, 500 GB transfer_. Paketin hinta oli tällöin $4/kk ja $0.006/tunti. Tämän pitäisi riittää tälle kurssille hyvin. Aina on mahdollista pienemmästi isompaan, kun taas isommasta pienempään siirtyminen voi olla haastavampaa.  

... KUVA 07 ...

- 16.51 _Additional Storage_- ja _Backups_-kohdat jätin tyhjäksi.

... KUVA 08 ... 

- 16.53 Valitsin autentikointitavaksi (_Authentication Method_) salasanan, koska en ole koskaan ennen käyttänyt SSH-salasanoja, vaikka näitä kannattaakin yleensä käyttää. Tein vahvan salasanan, koska aina käytetään vahvoja salasanoja. 

... KUVA 09 ...

- 16.59 En ottanut mitään ylimääräisiä palveluja kohdasta _We recommend these options_.

- 17.05 Määränä on yksi _Droplet_ ja tagit jätin tyhjäksi. Muokkasin _Hostanme_-kohdassa palvelimen nimeksi _debian_, jolloin se on itselleni helppo löytää. _Project_-kohdassa oli _first-project_, jota ei pystynyt muuttamaan, mutta se ei haittaa, koska minulla on vain yksi projekti. Lopuksi painoin sinistä _Create droplet_ -nappia.

- ... KUVA 10 ...

- 17.11 Hetken odottelun jälkeen virtuaalipalvelimeni oli valmis ja sain sille IP-osoitteen.

- ... KUVA 11 ...


## b) Alkutoimet virtuaalipalvelimella: tulimuuri päälle, root-tunnus kiinni ja ohjelmien päivitys

- 17.15 Avasin VirtualBoxin ja sieltä terminaalin. Hausin ottaa yhteyden virtuaalipalvelimeeni, jonka tein komennolla ```ssh root@64.226.102.160```, jossa IP-osoite on virtuaalipalvelimeni IP-osoite. Kysyttiin haluanko ottaa yhteyden palvelimeen, johon vastasin yes. Kirjoitin vahingossa yes-sanan ensin kahdesti. Sen jälkeen annoin salasanan, jonka loin virtuaalipalvelinta tehdessä.

- ... KUVA 12 ...

- 17.22 Asensin palomuurin komennolla ```sudo apt-get install ufw``` (ylempi kuva). Tein palomuuriin reiän SSH:lle porttiin 22 komennolla ```sudo ufw allow 22/tcp``` ja laitoin lopuksi palomuurin päälle komennolla ```sudo ufw enable``` (alempi kuva). Nyt palomuuri on päällä ja virtuaalipalvelin suojattuna.

- ... KUVA 13 - 14...

- 17.29 Tein uuden käyttäjän (hannatu) komennolla ```sudo adduser hannatu```, jolle loin vahvan salasanan. Annoin nimeni ja muut kohdat jätin tyhjäksi. Sen jälkeen korotin käyttäjän pääkäyttäjäksi komennolla ```sudo adduser hannatu sudo```.

- ... KUVA 15 ...

- 17.36 Avasin toisen terminaalin ja testasin pääsenkö sisälle virtuaalipalvelimeen komennolla ```ssh hannatu@64.226.102.160```, jossa on juuri luomani käyttäjä ja virtuaalipalvelimen IP-osoite. Kysyi salasanan, jonka annoin, ja pääsin sisälle. Päivitin ohjelmat komennolla ```sudo apt-get update```. Sain ohjelmat päivitettyä, joten sain avattua SSH-yhteyden virtuaalipalvelimelleni. 

- ... KUVA 16 ...

- 17.44 



## Lähteet

- Karvinen, T. 19.9.2017. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu: 13.9.2025.
- Lehto, S. 14.2.2022. Teoriasta käytäntöön pilvipalvelimen avulla (h4). Luettavissa: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/. Luettu: 13.9.2025.
- Pohjana Tero Karvinen 2025: Linux palvelimet 2025 alkusyksy. Luettavissa: https://terokarvinen.com/linux-palvelimet. Luettu: 13.9.2025.
