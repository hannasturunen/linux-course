# H1 Oma Linux

## Tiivistelmä raportin kirjoittamisesta

- Kirjoita raporttia samaan aikaan, kun teet asiaa.
- **Toistettava**: Raportoi ympäristö, eli milloin teit harjoituksen, missä ja mitä konetta käytit.
- **Täsmällinen**: Minkä komennon annoit, mitä klikkasit (ilmoita myös kellonajat)? Mitä tämän jälkeen tapahtui? Onnistuiko vai ei, miten sen totesit? Raportoi tulokset menneessä muodossa.
- **Helppolukuinen**: Käytä väliotsikoita ja kirjoita huolellista kieltä. Loppuun voi kirjoittaa lyhyen tiivistelmän.
- **Viittaa lähteisiin, Vakiotekstejä**: Käytä viittauksia tekstissä.
- **Pahoja mokia**: Kirjoita vain sellaista, mitä olet tehnyt. Älä plagioi tekstiä äläkä kuvia.

## Linuxin asentaminen virtuaalikoneeseen

- Tein harjoituksen sunnuntaina 24.8.2025 Helsingissä kotona. Koneena oli HP Laptop 14-cf1006no, jossa käyttöjärjestelmänä Windows 11 Home.
- klo    Olin ladannut VirtualBoxin aikaisemmin. Menin https://cdimage.debian.org/debian-cd/13.0.0-live/amd64/iso-hybrid/-sivustolle ja latasin sieltä ISO-tiedoston nimellä debian-live-13.0.0-amd64-xfce.iso. 
- klo    ISO-tiedoston lataus valmis. Avasin koneellani olevan VirtualBoxin.    +20 min
- klo    Klikkasin VirtualBoxin etusivulla olevaa New-painiketta, jotta saan tehtyä uuden virtuaalikoneen.
- Klo 19.55 Annoin uudelle virtuaalikoneelle kuvassa olevat tiedot. Huomasin, että jos "Proceed with Unattended Installation"-kohta oli täpätty, OS versiota ei voinut muuttaa 32:sta 64:ään. Laitoin oman VM folderin D-asemalle, koska C-asema on jonkin verran täynnä. 
            - tähän tulee kuva1
- klo 20.03 Määritin muistin koon ja CPU:n määrän. 
            - tähän tulee kuva2
- klo 20.04 Määritin kovalevyn koon. 
          - kuva3
- klo 20.07 Klikkasin Finish-painiketta, jolloin uusi virtuaalikone ilmestyi VirtualBoxin etusivulle.
- klo 20.09 Klikkasin hiiren oikealla painikkeella virtuaalikoneen päältä, jolloin avautui valikko. Valitsin valikosta Start ja Start with GUI. Virtuaalikone rupesi käynnistymään, "Powering up" ja se käynnistyi uuteen ikkunaan.


