# H5 Nimekäs

Tein harjoitukset torstaina 18.9.2025, ... ... Helsingissä kotona. Tein torstaina harjoitukset ... ... (kohdat ... ...), ... ... . Koneena kaikissa tehtävissä oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä on Windows 11 Home.

... Tiivistelmä ...

## a) Nimi. Laita julkinen nimi osoittamaan omaan koneeseesi.

... domainnimi ... 

- klo 14.33 Päätin ottaa domainnimen Namecheapista. Tällä tavalla saisin käytettyä GitHub Educationiin sisältyvää tarjousta ilmaisesta domain-nimestä vuodeksi. Etsin hakukoneella _Namecheap github education_, jolla pääsin _Namecheap for Education_ -sivustolle. Tässä saa käyttöönsä .me-loppuisen domainin. Karvisen mukaan parhain pääte sivustolle on .com, mutta hyvinä myös maakohtaiset tunnisteet, kuten Suomen .fi ja Ison-Britannian .co.uk. Koska tämä on testisivuni, ajattelin, että pärjään aluksi tällä .me-loppuisella. Kirjoitin kenttään haluamin domainin nimen ja klikkasin _Find_.

![Namecheap etusivu](images/h5-kuva01.jpg)

- 14.45 Valitsemani domainnimi, _hattara_, oli vielä vapaana ja ilmaisena .me-loppuisena nimenä, joten lisäsin sen ostoskoriin klikkaamalla domainnimen vieressä olevaa _Add_-nappia, jolloin tuote tuli oikealla olevaan ostoskoriin. Olin tyytyväinen tähän, joten klikkasin _Complete order_ -nappia.

![domainnimen valinta](images/h5-kuva02.jpg)

- klo 14.56 Laitoin täpän _GitHub Pages_ -kohtaan, jotta saan ilmaisen domain-nimen ja pidin hattara.me (muita vaihtoehtoja ei ollut tässä saatavilla). Huomasin, että tekstissä lukee, että tarjoavat ilmaiset .me-domainit tietyissä yliopistoissa US:ssa, UK:ssa, Kanadassa ja Australiassa. Voihan sitä kuitenkin testata, joten kirjoitin Haaga-Helian sähköpostin. Kun olin valmis, klikkasin alhaalla olevaa _Finish Up_ -nappia.

![domainin rekisteröinti](images/h5-kuva03.jpg)

- 15.02 Sain virheilmoituksen, jossa sanottiin _It looks like your email is not associated with an eligible university. Send us a request and we'll consider your school!_. Selvittelin asiaa.
- 15.20 Löysin GitHubin keskustelupalstalta saman asian kanssa painivan ihmisen, joka oli kirjoittanut tästä. Hänelle oltiin annettu linkki, jolla saisi GitHubin yhdistettuä NameCheapiin ja tätä kautta ilmaisen .me-domainin. Menin osoitteeseen _Get access by connecting your GitHub account on Namecheap_.

![domainnimen ottamisessa uusi yritys](images/h5-kuva04.jpg)

-  15.24 Annoin salasanani ja pääsin sisään. Nyt ylhäällä luki teksti _We have successfully verified your student pack with GitHub_. Testasin uudestaan ottaa hattara-domainin. Tarkistin tiedot ja koska yhä oli yhden vuoden ilmainen kokeilu, klikkasin taas _Complete order_ -nappia.

![domainninimen rekisteröinti uudestaan](images/h5-kuva05.jpg)

- 15.28 Kuten aikaisemminkin, laitoin täpän _GitHub Pages_ -kohtaan, kirjoitin Haaga-Helian sähköpostiosoitteen ja klikkasin _Finish Up_. Jes, tällä kertaa meni läpi! Klikkasin _Register_-nappia ja täytin vaadittavat tiedot. Kun olin valmis, klikkasin _Create_.  
- 15.39 Tarkistin vielä tilauksen tiedot ja klikkasin _Confirm Order_.

![tilauksen vahvistus](images/h5-kuva06.jpg)

- 15.41 Lopuksi yhdistin vielä GitHubin käyttäjätilin NameCheapiin, joten klikkasin _Setup your GitHub account_. Tämä onnistui, joten nyt minulla on domaintili luotuna.

![tilaus valmis](images/h5-kuva07.jpg)

- 15.44 Menin NameCheapin etusivulle (_namecheap.com_) ja kirjauduin sisään. Sähköpostiini lähetettiin verification code, jonka annoin NameCheapin sivuilla, jonka jälkeen pääsin sisään. Tarkistin vielä, että _Domain Privacy_:n _Auto-renew_ oli poissa päältä ja se oli.

![domainin etusivu](images/h5-kuva08.jpg)

- 15.49 Nyt kun olen hankkinut domainnimen, se pitää saada osoittamaan omaan virtuaalipalvelimeen, jonka hankin viime kerralla. Klikkasin vasemmalla olevan palkin _Domain List_, josta pääsin domainnimien listanäkymään. Klikkasin hattara.me -kohdalla olevaa _Manage_-nappia, jolla sain näkyviin domainin tiedot. Menin _Advanced DNS_-kohtaan. Kohdassa _Host Records_ oli turhia A-tietueita (_A Record_) ja yksi turha _CNAME Record_, jotka poistin. Näitä oli yhteensä viisi kappaletta. Sen jälkeen klikkasin alla olevaa _Add New Record_ ja annoin alla olevat tiedot. Tallensin molemmat uudet A-tietuet klikkaamalla oikealla olevaa vihreää tick-merkkiä.
  - tyyppi (_type_) = A-tietue (_A Record_)
  - host = toiseen _www_ ja toiseen _@_
  - arvo (_value_) = virtuaalipalvelimeni IP-osoite
  - TTL (Time to Live) = 5 minuuttia

![domainin DNS-tiedot](images/h5-kuva09.jpg)

- 16.27 Nyt olen ohjannut hattara.me-sivu ohjautuu virtuaalipalvelimeni IP-osoitteeseen 64.226.102.160. Eli nyt kun kirjoitan osoitepalkkiin hattara.me tai www.hattara.me, ne ohjautuvat virtuaalipalvelilleni, jonka IP-osoite on 64.226.102.160.



... A-tietue, DNS, host, arvo, TTL ... 



## b) Alidomain. Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi.



... alidomain ...  https://www.namecheap.com/blog/what-is-a-subdomain-dp/



- klo 17.19 Tein kaksi alidomainia (_subdomain_) hattara.me-domainille. Klikkasin _Add New Record_ -nappia, jolla sain lisättyä ensin yhden uuden A-tietuen (_blog.hattara.me_) ja toisen uuden CNAME-tietuen (_shop.hattara.me_). A-tietue osoittaa suoraan IP-osoitteeseen, mutta CNAME osoittaa domainiin, joka taas osoittaa IP-osoitteeseen. Siksi tässä piti laittaa IP-osoitteen sijaan domainnimi. 
- https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/
- https://www.cloudflare.com/learning/dns/dns-records/dns-a-record/ ja https://www.cloudflare.com/learning/dns/dns-records/dns-cname-record/



![alidomainit tehty](images/h5-kuva10.jpg)

- 17.40 Nyt olen tehnyt hattara.me-domainille kaksi alidomainia (blog ja shop). Kävin katsomassa jokaisen Firefox-selaimella ja ne näyttävät molemmat saman sivun kuin päädomainin sivu.

![alidomainit firefoxissa](images/h5-kuva11.jpg)




## c) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla. Käytä kumpaakin komentoa kaikkiin nimiin ja vertaa tuloksia.  ... KESKEN ...

- klo 19.10 Etsin ensin komennolla ```apt-cache search host``` kaikki tiedostot, joissa esiintyy sana host. Näitä tuli hyvin paljon, joten rajasin komentoa ```apt-cache search host | grep ^host```. Tässä tuli enää neljä vaihtoehtoa, mutta mikään ei näyttänyt oikealta. Selvittelin asiaa ja löysin oikean paketin nimen, joka on _bind9-host_ -paketti (https://www.debian.org/doc/manuals/debian-handbook/sect.domain-name-servers.en.html#sect.dns-config). Hain tämän komennolla ```apt-cache search host | grep bind9```. Tästä tuli tulokseksi oikea paketti. Latasin tämän komennolla ```sudo apt-get install bind9-host```.

![host komennon etsintä ja asennus](images/h5-kuva12.jpg)


https://wiki.debian.org/BIND9
https://ioflood.com/blog/install-dig-command-linux/

- Katso man-sivulta, miten komennot toimivat - esimerkiksi miten 'dig' näyttää kaikki kentät. Analysoi tulokset, keskity nimipalvelimelta tulleisiin kenttiin (dig näyttää paljon muutakin tietoa).
- Etsi tarvittaessa uusia lähteitä haastaviin kohtiin. Sähköpostin todentamiseen liittyvät SPF ja DMARC -tietojen yksityiskohdat on jätetty vapaaehtoiseksi lisätehtäväksi. Tutkittavat nimet:
  - Oma domain-nimesi. Vertaa tuloksia nimen vuokraajan (namecheap.com, name.com...) weppiliittymässä näkyviin asetuksiin.
  - Jonkin pikkuyrityksen, kerhon tai yksittäisen henkilön weppisivut. (Ei kuitenkaan kurssikaverin tällä viikolla vuokrattua nimeä).
  - Jonkin suuren ja kaikkien tunteman palvelun tiedot.




## Lähteet
