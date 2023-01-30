# h4-Tukki

## Laitteisto  

### Host
-HP EliteDesk 800 G2 TWR  
-OS: Microsoft Windows 10 Pro  
-Prosessori: Intel Core i7-6700 CPU @ 3.40GHz  
-RAM: 2x 8GB  
-Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6  

### Guest
-Virtualisointiympäristönä Oracle VM VirtualBox 7.0.6  
-Virtuaalikoneena Debian GNU/Linux 11 (Bullseye)  
-Keskusmuisti: 4000 MB 

## x) Tiivistelmä artikkelista "6 command line tools for productive programmers", sekä artikkelin kommenteista

* Jos haluat nähdä ison hakemiston sisältämät tiedostot, hyvä komento on ```broot```, joka huomioi terminaali-ikkunan koon ja mukauttaa näkymän sen mukaan
* Komento ```funky``` etsii hakemistosta ```.funky``` tiedostoa ja lataa sen sisältämät bash funktiot.
* ```McFly``` käyttää neuroverkkoa antaakseen relevantteja tuloksia komentorivin täydentämistä varten.  
* ```gitupdate .``` käyttää tiedostojen nimiä luodakseen viestin, kommitoi ja puskee tiedostot gitiin.  
* Kommentoijan SPBS (2021-07-29) mukaan ```broot``` komennon voi korvata helposti putkittamalla ```tree``` komennon ```less``` komennon kanssa. 

#### Lähteet:  
6 Command Line Tools for Productive Programmers. Bell 2021. Luettavissa: https://earthly.dev/blog/command-line-tools/  
Kommentti artikkelin kommenttiosiossa. SBPS 2021. Luettavissa: https://news.ycombinator.com/item?id=27992858  

## a) Tukki  

### /var/log/syslog  

```Hypervisor detected: KVM``` kertoo, että virtualisointilaitteisto on tunnistettu. "KVM" on lyhenne sanoista *Kernel-based Virtual Machine*.  

![image](https://user-images.githubusercontent.com/90974678/215459143-1326ecce-2b3e-4cdb-b5eb-d6e484e5cd13.png)  

### /var/log/auth.log

Esimerkkirivi  
```Jan 21 16:55:24 lauritorma-virtualbox sudo: lauritorma : TTY=pts/0 ; PWD=/home/lauritorma ; USER=root ; COMMAND=/usr/bin/apt-get install Micro```  
kertoo, että tmmikuun 21. päivänä kello 16:55:24 laitteella on ajettu ```home/lauritorma``` hakemistossa root-käyttäjän oikeuksilla komento, jolla on asennettu ohjelma nimeltä Micro.  

![image](https://user-images.githubusercontent.com/90974678/215460494-96c8356e-8847-4ef4-8db8-0dc0d24806e9.png)


### var/log/apache2/access.log

``` sudo cd apache2 ``` ei onnistunut, joten täytyi kirjautua komennolla ```sudo -s``` root-käyttäjäksi, jotta pääsin siirtymään apache2-hakemistoon.  
Tiedostoa ```access.log``` luettaessa tulostui vain tyhjää, mutta lisäämällä tiedoston nimen loppuun .1 ruutuun ilmestyi lokitietoja.  

Esimerkkirivi  
```127.0.0.1 - - [27/Jan/2023:14:13:15 +0200] "GET /favicon.ico HTTP/1.1" 404 487 "http://localhost/" "Mozilla/5.0 (X11; Linux x86_64; rv:102.0) Gecko/20100101 Firefox/102.0"```  
kertoo, että osoitteesta 127.0.0.1 on tammikuun 27. päivänä kello 14:13:15 UTC +2 aikaa lähetetty GET-pyyntö. Pyyntö näyttää kohdistuvan ```/favicon.ico``` polkuun. Osoitteena on localhost.  
Rivin lopussa kerrotaan tietoja selaimesta, eli tässä tapauksessa Mozilla Firefox.  

![image](https://user-images.githubusercontent.com/90974678/215464083-b052c490-6fb7-401b-b8e7-edf424d3159b.png)


### var/log/apache2/error.log  

Myöskin ```error.log``` näytti vain tyhjää, mutta ```error.log.1``` antoi lokitietoja. 

Esimerkkirivi  
```[Fri Jan 27 23:30:08.186810 2023] [mpm_event:notice] [pid 698:tid 140379013483840] AH00489: Apache/2.4.54 (Debian) configured -- resuming normal operations```  
Kertoo, että perjantaina 27. tammikuuta kello 23:30:08 on Apacheen (jonka versio on 2.4.54) tehty jonkinlaista konfigurointia ja nyt jatketaan normaalia toimintaa.  

![image](https://user-images.githubusercontent.com/90974678/215465325-78287d5e-98e6-46a6-a3dc-683bca050623.png)

## b) Aiheuta  

Tässä kohtaa poistuin root-käyttäjätilasta näppäinyhdistelmällä ```ctrl + D``` ja siirryin takaisin ```/var/log``` hakemistoon  

Aiheutin ```auth.log``` lokiin tapahtuman, jossa tyhjensin ```var/log/messages``` tiedoston komennolla ```sudo truncate -s 0 messages```

```Jan 30 13:41:52 lauritorma-virtualbox sudo: lauritorma : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/truncate -s 0 messages```  

![image](https://user-images.githubusercontent.com/90974678/215469006-7da4dccf-5c28-4091-871d-5257d7fc9e8f.png)  

Rivillä kerrotaan, että Tammikuun 30. päivänä kello 13:41:52 ```lauritorma-virtualbox``` laitteella ajettiin root-käyttäjän oikeuksilla komento ```/var/log``` hakemistossa.  



### Tehtävänantojen lähde  
Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  




