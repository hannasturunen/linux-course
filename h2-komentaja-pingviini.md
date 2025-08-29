# H2 Komentaja Pingviini

## Tiivistelmä Command line basics revisited

- Komentorivi (command line) on ollut käytössä jo pitkään.
- Se on kätevä, nopea ja helppo automatisoida.
- Jos komennon jälkeen on #-merkki, loppurivi jätetään huomiotta.
- Käytössä on monia komentoja, joita kannattaa opetella ulkoa, jotta toiminta Linuxissa olisi vaivatonta.


## Tiivistelmä

Asensin ensin micro-editorin ja sen jälkeen valitsemani kolme uutta komentoriviohjelmaa. Nämä olivat htop, ncdu ja cowsay. Hain neljän eri kansion tiedot. Kansiot olivat / (root), /home, /home/hanna, /etc, /media ja /var/log.

## Micro-editorin asennus

Tein harjoituksen torstaina 28.8.2025 Helsingissä kotona. Koneena oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä Windows 11 Home.

* klo 16.40 Avasin VirtualBoxin ja sieltä Linux-virtuaalikoneeni.
* klo 16.45 Avasin virtuaalikoneen terminaaalin. Kirjoitin siihen komentona "apt-cache search micro", koska haluan ladata virtuaalikoneeseen micro-editorin. Tällä haulla tuli todella paljon tuloksia, joten rajasin hakua ja kirjoitin komentona nyt "apt-cache search micro | grep ^micro", jolloin tuli vain hieman yli 10 tulosta. Grepillä sain etsittyä tiettyä kuviota (pattern) tekstistä (tässä tapauksessa microa) ja ^-merkki kertoo, että haluan mirco-sanan olevan rivin alussa. |-merkkiä (putki, pipe) ennen oleva komento ottaa tulosteen ja syöttää sen |-merkin jälkeiselle komennolle ja lopuksi tulostuu vain ne, jotka ovat oikein molempien syötteiden kanssa. Tämä helpotti listan lukemista huomattavasti ja nyt näin heti, että micro-editori, jota etsin, on listalla toisena, alla kuva.
* --KUVA1.

* klo 17.04 Ajoin terminaalissa komennon "sudo apt-get install micro", jonka jälkeen syötin salasanani. Micro-editori teki alkulataukset, jonka jälkeen kysyi haluanko käyttää 15.0 Mb:tä levyltä, tähän vastasin Y eli Yes. Tämän jälkeen latasi micro-editorin, alla kuva.
* --KUVA2.

* klo 17.10 Micro-editori on nyt ladattu. Avasin micro-editorin komennolla "micro", joka avasi ohjelman. Suljin ohjelman ctrl+q.
* --KUVA3.

## Apt. Asenna kolme itsellesi uutta komentoriviohjelmaa

Hain Googlesta muutamia mahdollisia komentoriviohjelmia, koska itselläni ei ole oikein tietoa millaisia niitä edes on.

* klo 18.02 Hain ensin komennolla "apt-cache search htop | grep ^htop" terminaalissa, josta tuli vastaus "htop - interactive processes viewer". Annoin komennon "sudo apt-get install htop". Annoin salasanan, jonka jälkeen ohjelma latautui.
* klo 18.09 Annoin komennon "htop", jolloin htop-ohjelma avatui. //htop on prosessikatseluohjelma, joka näyttää käynnissä olevat prosessit ja mukana kivat ja havainnollistavat värit. F10-komennolla pääsin pois ohjelmasta.  --KESKEN
* --KUVA4
* [1]

* klo 18.19 Hain toiseksi komennolla "apt-cache search ncdu | grep ^ncdu", jolloin sain tulokseksi "ncdu - ncurses disk usage viewer". Latasin tämän ohjelman komennolla "sudo apt-get install ncdu". Alussa annoin taas salasanan.
* 18.23 Kirjoitin terminaaliin komennon "ncdu", joka avasi ohjelman. Q-komennolla pääsin pois ohjelmasta. //Selkeä ja visuaalinen tapa ymmärtää, mihin levytila kuluu.  --KESKEN
* --KUVA5
* [1]

* klo 18.29 Hain kolmanneksi komennolla "apt-cache search cowsay | grep ^cowsay", joka antoi tulokseksi kaksi, joista toinen "cowsay - configurable talking cow" oli se, jonka halusin. Latasin ohjelman komennolla "sudo apt-get install cowsay" ja ohjelma latautui.
* 18.34 Kirjoitin komennon "cowsay Hei kaikki!", josta tulostui lehmä, joka sanoi "Hei kaikki!", alla kuva. //Lehmä, joka sanoo kirjoittamani asian. --KESKEN
* --KUVA6
* [2]

Olisin voinut ladata nämä kaikki yhdella kertaa komennolla "sudo apt-get install htop ncdu cowsay", mutta nyt tein kaikki yksitellen, koska tässä tuli opeteltua samalla hyvin Linuxin käyttöä.

## FHS, kansioiden esittely

* 19.15 Avasin terminaalin ja kirjoitin komennon "ls /". ls-komennolla listasi tiedostot, jotka se kansio sisältää, ja /-komennolla kerrotaan, että halutaan juurihakemiston (root directory) tiedostot.
* klo 19.19 Seuraavaksi kirjoitin komennon "ls /home". Tässä on käyttäjien kotihakemisto ja tässä näkyy vain yksi eli omani.
* klo 19.22 Kirjoitin komennon "ls /home/hanna". Käyttäjän "hanna" kotihakemisto eli oma kotihakemistoni. Tämä on paikka, jonne tallennan tiedostot.
* --KUVA7
* klo 19.47 Kirjoitin komennon "ls /etc". Tällä tuli paljon tietoa, alla kuva. Tässä näkyy järjestelmäasetukset. Ne ovat tekstitiedostoina, joten ihmisen on helppo lukea ne.
* KUVA8
* klo 19.52 Kirjoitin terminaaliin "cd /etc", jolloin pääsin etc-kansioon. Kirjoitin komennon "ls -l", jolla sain näkyviin tiedostojen oikeudet, omistajan, koon ja muokkauspäivän. Alla kuva.
* --KUVA9 
* klo 19.57 Halusin vielä näkyviin pelkästään yhden tiedoston tiedot. Valitsin luettelosta passwd-tiedoston. Annoin komennon "ls -l /etc/passwd", josta antoi pelkästään passwd-tiedoston tiedot näkyviin. Alla kuva.
* --KUVA10
* klo 20.02 Menin pois etc-hakemistosta antamalla komennon "cd ..", jonka jälkeen tarkistin missä olen antamalla "pwd"-komennon. Olin root-hakemistossa. Annoin komennon "cd /home/hanna", jotta pääsin takaisin oman hakemistooni.
* klo 20.06 Annoin komennon "ls /media", jolla tuli kaksi cdrom-tulosta. Tässä näkyy media, esimerkiksi juuri cdrom, mutta voisi olla myös USB-disk.
* klo 20.07 Kirjoitin komennon "ls /var/log". Tuli kansioita ja tiedostoja. Näyttää eri lokeja. Päätin, että katson tiedoston lastlog-tiedot, joten kirjoitin komennon "ls -l /var/log/lastlog", josta tuli tämän tiedon tiedot yhdelle riville. Alla kuva.
* --KUVA11


## Lähteet

* [1] https://opensource.com/article/20/6/modern-linux-command-line-tools, 28.8.2025
* [2] https://linuxstans.com/funniest-linux-meme-distros-software-commands/ 28.8.2025
* https://terokarvinen.com/2020/command-line-basics-revisited/ 28.8.2025
* Pohjana Tero Karvinen 2025: Linux palvelimet 2025 alkusyksy, https://terokarvinen.com/linux-palvelimet
