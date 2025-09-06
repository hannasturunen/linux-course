<img width="1216" height="620" alt="image" src="https://github.com/user-attachments/assets/fdc6192f-23b3-403c-9707-d30955749b05" /><img width="1216" height="620" alt="image" src="https://github.com/user-attachments/assets/2259ac3b-7ddd-4bc7-bcab-6ce7ebf1d0a5" /># H3 Hello Web Server

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

- klo 18.57 Kirjoitin terminaaliin _sudo tail -f /var/log/apache2/access.log_. Annoin salasanani ja sain listan Apache-webpalvelimen lokitiedostoista, johon on tallennettu kaikki tehdyt pyynnöt. Avasin Firefox-selaimen ja menin osoitteeseen http://localhost.
- Lokitiedoista analysoin kaksi alinta riviä, jotka ilemstyivät, kun avasin Firefox-selaimen ja menin localhost-sivulle:
    - 127.0.0.1 = kuka teki pyynnön eli IP-osoite
    - 06/Sep/2025:19:10:43 +0300 = päivämäärä ja aika, jolloin pyyntö tehty
    - GET /server-status HTTP/1.1 = pyyntötyyppi ja pyydetty resurssi, tässä pyydetty hakemaan HTTP:tä
    - 200 = HTTP:n tilakoodi
    - 3383 = asiakkaalle palautetun objektin koko
    - Mozilla/5.0 (X11; Linux x86_64; rv:129.0) Gecko/20100101 Firefox/128.0 = kertoo asiakkaan selaimen tiedot eli tässä käytössä Mozilla Firefox.

- 

