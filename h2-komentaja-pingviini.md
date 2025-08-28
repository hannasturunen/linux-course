# H2 Komentaja Pingviini

## Tiivistelmä Command line basics revisited

--KESKEN

## Micro-editorin asennus

Tein harjoituksen torstaina 28.8.2025 Helsingissä kotona. Koneena oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä Windows 11 Home.

* klo 16.40 Avasin VirtualBoxin ja sieltä Linux-virtuaalikoneeni.
* klo 16.45 Avasin virtuaalikoneen terminaaalin. Kirjoitin siihen komentona "apt-cache search micro", koska haluan ladata virtuaalikoneeseen micro-editorin. Tällä haulla tuli todella paljon tuloksia, joten rajasin hakua ja kirjoitin komentona nyt "apt-cache search micro | grep ^micro", jolloin tuli vain hieman yli 10 tulosta. Grepillä sain etsittyä tiettyä kuviota (pattern) tekstistä (tässä tapauksessa microa) ja ^-merkki kertoo, että haluan mirco-sanan olevan rivin alussa. |-merkkiä (putki, pipe) ennen oleva komento ottaa tulosteen ja syöttää sen |-merkin jälkeiselle komennolle ja lopuksi tulostuu vain ne, jotka ovat oikein molempien syötteiden kanssa. Tämä helpotti listan lukemista huomattavasti ja nyt näin heti, että micro-editori, jota etsin, on listalla toisena, alla kuva. --UVA1.
* klo 17.04 Ajoin terminaalissa komennon "sudo apt-get install micro", jonka jälkeen syötin salasanani. Micro-editori teki alkulataukset, jonka jälkeen kysyi haluanko käyttää 15.0 Mb:tä levyltä, tähän vastasin Y eli Yes. Tämän jälkeen latasi micro-editorin, alla kuva. --KUVA2.
klo 17.10 Micro-editori on nyt ladattu.

## Apt. Asenna kolme itsellesi uutta komentoriviohjelmaa

Hain Googlesta muutamia mahdollisia komentoriviohjelmia, koska itselläni ei ole oikein tietoa millaisia niitä edes on.

* klo 18.02 Hain ensin komennolla "apt-cache search htop | grep ^htop" terminaalissa, josta tuli vastaus "htop - interactive processes viewer". Annoin komennon "sudo apt-get install htop". Annoin salasanan, jonka jälkeen ohjelma latautui.
* klo 18.09 Annoin komennon "htop", jolloin htop-ohjelma avatui. //htop on prosessikatseluohjelma, joka näyttää käynnissä olevat prosessit ja mukana kivat ja havainnollistavat värit. --KESKEN, --KUVA3
* klo 18.19 Hain toiseksi komennolla "apt-cache search ncdu | grep ^ncdu", jolloin sain tulokseksi "ncdu - ncurses disk usage viewer". Latasin tämän ohjelman komennolla "sudo apt-get install ncdu". Alussa annoin taas salasanan.
* 18.23 Kirjoitin terminaaliin komennon "ncdu", joka avasi ohjelman. 

## Lähteet

https://opensource.com/article/20/6/modern-linux-command-line-tools, 28.8.2025
