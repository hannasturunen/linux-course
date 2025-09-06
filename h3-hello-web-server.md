# H3 Hello Web Server

## Tiivistelmä KESKEN

https://httpd.apache.org/docs/2.4/vhosts/name-based.html
https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support
Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address

## Virtuaalikonetehtävät

Tein harjoitukset lauantaina 6.9.2025 Helsingissä kotona. Tein lauantaina harjoitukset ... ... 
Koneena kaikissa tehtävissä oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä on Windows 11 Home.

... Tiivistelmää tähän ...

## Apache-webpalvelin

- klo 18.51 Avasin VirtualBoxissa selaimen ja menin Firefox-selaimella osoitteeseen http://localhost. Apache-sivusto avatui, alla kuva. Apache-webpalvelin on jo asennettuna.

- ... KUVA1 ...

## Lokista etsiminen

- klo 18.57 Kirjoitin terminaaliin _sudo tail -f /var/log/apache2/access.log_. Annoin salasanani ja sain listan Apache-webpalvelimen lokitiedostoista, johon on tallennettu kaikki tehdyt pyynnöt. Avasin Firefox-selaimen ja menin osoitteeseen http://localhost. Lokitiedoista analysoin kaksi alinta riviä, jotka ilmestyivät, kun avasin Firefox-selaimen ja menin localhost-sivulle. Alemmassa rivissä oli muuten samat tiedot, mutta kolme niistä oli erilaista. Kuva alempana. Tulkinnassa käytetty apuna Sumo logicin artikkelia (2025).
- Ylempi rivi, merkattu kuvaan punaisella:
    - 127.0.0.1 = kuka teki pyynnön eli IP-osoite
    - 06/Sep/2025:19:10:43 +0300 = päivämäärä, aika ja poikkeama UCTC-ajasta, kun pyyntö on tehty
    - GET /server-status HTTP/1.1 = pyyntötyyppi ja pyydetty resurssi, tässä pyydetty hakemaan serverin tila
    - 200 = HTTP:n tilakoodi
    - 3383 = asiakkaalle palautetun objektin koko
    - Mozilla/5.0 (X11; Linux x86_64; rv:129.0) Gecko/20100101 Firefox/128.0 = User Agent eli kertoo asiakkaan selaimen tiedot, tässä käytössä Mozilla Firefox
- Alempi rivi, merkattu kuvaan keltaisella:
    - muuuten samat tiedot kuin ylemmällä rivillä, mutta siitä löytyi kolme erilaista parametriä
    - GET /icons/openlogo-75.png HTTP/1.1 = pyyntötyyppi ja pyydetty resurssi, tässä pyydetty hakemaan kuvaa icons-hakemistosta
    - 6041 = asiakkaalle palautetun objektin koko
    - http://localhost/ = näyttää lähteen URL-osoitteen eli tämä oli sivu, jolle menin

- ... KUVA 2 ...

# Lähteet

- Sumo logic 2025. Understanding the Apache access log: how to view, locate, and analyze. Luettavissa: https://www.sumologic.com/blog/apache-access-log. Luettu: 6.9.2024.
GeeksforGeeks 2025. grep command in Unix/Linux. Luettavissa: https://www.geeksforgeeks.org/linux-unix/grep-command-in-unixlinux/. Luettu: 30.8.2025.
