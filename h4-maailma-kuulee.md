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
- Lehto ajoi komennon _ssh root@188.166.4.6_, jotta sai yhteyden virtuaalikoneeseen.
- Haki päivitykset komennolla _sudo apt-get update_ ja asensi palomuurin _sudo apt-get install ufw_.
- Lopuksi teki palomuuriin reiän porttia varten komennolla _sudo ufw allow 22/tpc_ ja laittoi palomuurin päälle _sudo ufw enable_.

**e) Kotisivut palvelimelle**
- Lehto teki uuden käyttäjän komennolla _sudo adduser suska_ ja tämän jälkeen teki käyttäjästä pääkäyttäjän _sudo adduser suska sudo_.
- Avasi toisen terminaalin, jolla avasi SSH-yhteyden virtuaalipalvelimeen _ssh suska@188.166.4.6_ ja päivitti tiedot _sudo apt-get update_. Lopuksi lukitsi juuren _sudo usermod –lock root_.
- Kirjautui sisään virtuaalipalvelimelle toisella terminaalilla käyttäen SSH-yhteyttä. Asensi päivitykset ja tietoturvapäivitykset komennoilla _sudo apt-get update_, _sudo apt-get upgrade_ ja _sudo apt-get dist-upgrade_.
- Asensi Apach-palvelimen _sudo apt-get install apache2_, jonka jälkeen teki toisen reiän palomuuriin toiselle portille _sudo ufw allow 80/tcp_.
- Korvasi Apache-testisivun komennolla _echo Hello world! |sudo tee /var/www/html/index.html_, jolla sivulle ilmestyi "Hello World!".
- Lopuksi hän loi omalle käyttäjälleen julkisen kansion kotihakemistoon ja nettisivulle lyhyen rungon W3Schools-sivujen avulla.

**f) Palvelimen ohjelmien päivitys**
- Lehto avasi terminaalin ja otti SSH-yhteyden virtuaalipalvelimelle.
- Haki tiedot päivityksistä, asensi ne ja haki myös tietoturvapäivitykset komennoilla _sudo apt-get update_, _sudo apt-get upgrade_ ja _sudo apt-get dist-upgrade_.

(Lehto, 14.2.2022)

### Tero Karvinen: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS

- Käytä aina hyviä salasanoja!
- Virtuaalisia palvelimia voi vuokrata esimerkiksi DigitalOceanilta, Linodelta ja Gandilta.
- GitHubilta saa ilmaisen Education student -paketin, jossa on virtuaalinen palvelin ja .me-domainnimen rajoitetuksi ajaksi.
- Artikkelissa ohjeistetaan miten luodaan uusi palvelin DigitalOceanille, miten palomuuriin tehdään reikä ja miten sen saa päälle, miten tehdään sudo-käyttäjä, miten root-käyttäjä suljetaan ja miten ohjelmat päivitetään. Lopuksi aletaan käyttämään luotua palvelinta. Mukana on myös komennot näihin.
- DNS-nimen voi vuokrata esimerkiksi NameCheapistä.   

(Karvinen, 19.9.2017)

## Virtuaalikonetehtävät

... KESKEN ... Tein harjoitukset lauantaina 13.9.2025, ... ... Helsingissä kotona. Tein lauantaina virtuaalipalvelimen vuokrauksen ja aloitin alkutoimet virtuaalipalvelimella (kohdat a-b). Koneena kaikissa tehtävissä oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä on Windows 11 Home.

... KESKEN ... Tiivistelmä.

## a) Oman virtuaalipalvelimen vuokraus UpCloudilta

- klo 19.25 Päätin ottaa virtuaalipalvelimen UpCloudista. Kirjauduin sisään. Otin käyttöön Two-factor authenticationin, koska UpCloud sitä suositteli.
- 19.30 Aloitin virtuaalipalvelimen tekemisen etusivulla olevasta "Deploy your trial services"-kohdasta klikkaamalla "Deploy now" -valikkoa ja sieltä valitsin "Server". Valitsin paikaksi Suomen, koska on hyvä ottaa paikaksi mahdollisuuksien mukaan mahdollisimman lähellä asiakkaita. Plan-kohdassa valitsin halvimman (3€/kk), jossa oli yksi CPU-ydin, 1 GB RAM-muistia ja 10 GB muistia, jotka ovat riittävät tähän harjoitukseen. Pienemmästä isompaan on aina helpompi siirtyä kuin isommasta pienempään. Storage- ja Automated backups -kohtiin en laittanut mitään. Käyttöjärjestelmäksi valitsin _Debian GNU/Linux 13 (Trixie)_. Network-kohdassa jätin päälle kohdat: Public IPv4, Utility network ja Public IPv6. Alla kuvat valinnoista.

- ... KUVA1 - KUVA03 ...

- 19.50 Salasana-kohdassa oli pakko käyttää SSH-keysiä, koska ei antanut vaihtoehdoksi "One time password" -kohtaa. Tein siis SSH-salasanat. Avasin terminaalin (tällä kertaa Windowsissa, koska pääsen siihen helpommin käsiksi). Annoin komennon _ssh-keygen_, jonka jälkeen painoin kolme kertaa enteriä (hyväksyin komennon, hyväksyin kansion, jonne salasana tallennetaan ja hyväksyin passphrasen). Nyt minulla oli SSH-avaimet tehtynä, joten pääsin jatkamaan.
- 19.54 Etsin SHH-avaimet tiedostoista ja kopioin julkisen avaimen UpCloudiin.
- 20.03 En laittanut mitään Initialization script -kohtaan ja jätin Server configuration -kohdassa olevat tiedot hostname:sta kuten ne olivatkin. Lopuksi painoin Deploy-nappia ja pian virtuaalipalvelimeni olikin valmis! Sain tässä myös virtuaalipalvelimeni IP-osoitteen.

## b) Alkutoimet virtuaalipalvelimella: tulimuuri päälle, root-tunnus kiinni ja ohjelmien päivitys

- klo 20.16 Avasin VirtualBoxin ja terminaalin. Annoin komennon _ssh root@94.237.118.241_, jolla yritin ottaa yhteyden virtuaalipalvelimeeni. Ei saanut yhteyttä, koska olin tehnyt SSH-avaimet Windowsilla ja nyt Linux ei löydä niitä.
- 20.24 Tein siis uudet SSH-avaimet Linuxilla. Tein päivitykset komennoilla _sudo apt-get update_ ja _sudo apt-get -y install openssh-client_. Sen jälkeen tein SSH-avaimet komennolla _ssh-keygen_ painoin kolme kertaa enteriä. Sain tehtyä SSH-avaimet. Menin kopioimaan SSH:n julkista avainta komennolla _micro ~/.ssh/id_ed25519.pub_. Näin julkisen avaimeni, mutta en saanut sitä millään kopioitua, vaikka minulla on bidirectional Shared Clipboard -kohdasta käytössä. Yritin kopioida sitä manuaalisesti itse, mutta en tiedä onnistuiko, koska en päässyt yhä kirjautumaan sisään root-käyttäjänä.
- 20.53 Suljin virtuaalipalvelimen UpCloud-sivulta ja käynnistin sen uudestaan. Annoin komennon _ssh root@94.237.118.241_, mutta yhä antaa vain "Permission denied (publickey). Päätin poistaa nykyisen virtuaalipalvelimen ja tehdä uuden ja samalla tehdä uudet SSH-avaimet Linuxilla.
- 20.56 Suljin taas virtuaalipalvelimen UpCloudista ja poistin sen.

- klo 6.14 Tein uuden virtuaalipalvelimen UpCloudissa kohdan _a) Oman virtuaalipalvelimen vuokraus UpCloudilta_ mukaan ja valinnat olivat samat.
- 6.18 Avasin VirtualBoxin ja tein ensin päivitykset ja sitten SSH-avaimet aikaisemman kohdan mukaisesti (kohta b) Alkutoimet virtuaalipalvelimella: tulimuuri päälle, root-tunnus kiinni ja ohjelmien päivitys, kello 20.24). Ilmoitti, että kansio on jo olemassa ja haluanko korvata sen, johon vastasin kyllä. Avasin julkisen avaimen komennolla _micro ~/.ssh/id_ed25519.pub_. Kopioin avaimen, mutta en saanut yhä liitettyä sitä Linux-koneen ulkopuolelle. Kirjauduin sisään UpCloudiin Linuxilla ja tallensin avaimen profiiliini. Jouduin tekemään palvelimenvalinnat uudestaan, mutta menin samoilla kuin aikaisemminkin. Nyt Login Method -kohdassa oli vaihtoehtona äsken lisäämäni SSH-avain. Lopuksi painoin Deploy-nappia.
- 6.33 Otin yhteyden Linuxista virtuaalipalvelimeeni komennolla _ssh root@185.26.51.195_. Kysyttiin haluanko ottaa yhteyden palvelimeen, johon vastasin yes. Jes, pääsin sisään! Tein päivitykset komennolla _sudo apt-get update_.
- 6.40 Asensin palomuurin komennolla _sudo apt-get install ufw_. Kun palomuuri on asennettu, tein siihen reiän SSH:lle porttiin 22, jota SSH käyttää. Tein tämän komennolla _sudo ufw allow 22/tcp_ ja laitoin vielä palomuurin päälle komennolla _sudo ufw enable_, alla kuva. Nyt palomuuri on päällä.

- ... KUVA04 ...

- 7.01 Tein virtuaalipalvelimen terminaalissa uuden käyttäjän (hannatu) komennolla _sudo adduser hannatu_ ja annoin vahvan salasanan. Annoin nimeni, mutta muut kohdat jätin tyhjäksi, alla kuva. Sen jälkeen korotin käyttäjän pääkäyttäjäksi komennolla _sudo adduser hannatu sudo_.
- 7.08 Avasin toisen terminaalin ja testasin toimivatko juuri luomani, uudet tunnukset, komennolla _ssh hannatu@185.26.51.195_. En päässyt sisään, yhä valittaa "Permission denied (publickey)". Tässä nyt taitaa olla ongelmana se, että nuo SSH-avaimet on tehty hanna-käyttäjällä eikä hannatu-käyttäjällä, joten hannatu-käyttäjä ei pääse käsiksi niihin ja siksi tulee tämä ilmoitus.
- 7.26 Tein siis virtuaalipalvelimen terminaalissa uuden käyttäjän hanna komennolla _sudo adduser hanna_, jolle annoin vahvan salasanan ja oman nimeni (muut kohdat jätin tyhjäksi). Tein käyttäjästä pääkäyttäjän komennolla _sudo adduser hanna sudo_. Alla kuva. 

- ... KUVA05 ...
- ... KUVA 06 ...

- 7.30 Testasin uudestaan mennä paikallisessa terminaalissa SSH-yhteydellä virtuaalipalvelimelleni, komennolla _ssh hanna@185.26.51.195_. Yhä antaa vaan "Permission denied (publickey)". Taitaa olla niin, ettei uudet käyttäjät näe SSH-avaimia, joten niille pitää antaa oikeudet niihin.
- 7.45 Olen ihan sekaisin näistä, en tiedä missä on mikäkin enkä saa siirrettyä publickeytä hannatu-käyttäjälle, joten poistin taas tämän virtuaalipalvelimen ja aloitin alusta.
- 8.15 Ensiksi loin SSH-keyt hanna-käyttäjälle terminaalissa komennolla _ssh-keygen_. Tein uuden virtuaalipalvelimen UpCloudissa, samat tiedot. Laitoin SSH-avaimen.
- 8.53 Avasin uuden terminaalin, jonne kirjoitin komennon _ssh root@94.237.34.130_ ja pääsin sisään. Päivitin ohjelmat komennolla _sudo apt-get update_, asensin palomuurin (sudo apt-get install ufw). Tein palomuurin reiän ja laitoin sen päälle (sudo ufw allow 22/tcp ja sudo ufw enable). Tarkistin, että onhan portti 22 päällä (_sudo ufw status verbose_) ja näin, että on, alla kuva.

- ... KUVA 07 ... 

- 9.08 Tein virtuaalipalvelimen terminaalissa uuden käyttäjän hannatu (sudo adduser hannatu), annoin taas nimeksi Hanna Turunen ja muut jätin tyhjäksi. Tein uudesta käyttäjästä pääkäyttäjän (sudo adduser hannatu sudo).
- 9.15 Avasin toisen terminaalin ja yritin päästä sisään virtuaalipalvelimelle (_ssh hannatu@94.237.34.130_), ei päästänyt vieläkään. Asensin SSH:n (_sudo apt install openssh-server_) ja tarkistin, että on päällä (_sudo systemctl status ssh_), josta näin, että oli, koska siellä luki "active (running)". Yritin uudestaan ottaa yhteyttä virtuaalipalvelimelle _ssh hannatu@94.237.34.130_. Yhä ilmoittaa saman permission denied.
- 'hannatu@94.237.34.130'
- ´hannatu@94.237.34.130` ´hei´


## Lähteet

- Karvinen, T. 19.9.2017. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu: 13.9.2025.
- Lehto, S. 14.2.2022. Teoriasta käytäntöön pilvipalvelimen avulla (h4). Luettavissa: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/. Luettu: 13.9.2025.
- Pohjana Tero Karvinen 2025: Linux palvelimet 2025 alkusyksy. Luettavissa: https://terokarvinen.com/linux-palvelimet. Luettu: 13.9.2025.
