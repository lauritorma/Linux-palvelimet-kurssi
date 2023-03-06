# h12 Vianselvitys

## Laitteisto  

### Host  

* HP EliteDesk 800 G2 TWR  
* OS: Microsoft Windows 10   
* Prosessori: Intel Core i7-6700 CPU @ 3.40GHz  
* RAM: 1x 16GB  
* Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6  

### Guest
* Virtualisointiympäristönä Oracle VM VirtualBox 7.0.6  
* Virtuaalikoneena Debian GNU/Linux 11 (Bullseye)  
* Keskusmuisti: 4000 MB   
* Selain: Mozilla Firefox 102.7.0esr (64-bit)  

### Tehtävänantojen lähde  

Linux Palvelimet 2023 alkukevät. Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  

## a) Kirjoitusvirhe Python-tiedostossa 

#### Aloitin työskentelyn 6.3.2023 klo 08.49  

### Ongelman aiheuttaminen  

Aloitin tehtävän käynnistämällä virtuaaliympäristön. Päätin tehdä kirjoitusvirheen polussa ```/publicwsgi/laurisbase/laurisbase``` sijaitsevaan ```settings.py``` tiedostoon.  

![image](https://user-images.githubusercontent.com/90974678/223039749-a29ee404-ad8d-4f0e-ad08-58643d520596.png)

Aiheutin ```settings.py``` tiedostoon kirjoitusvirheen vaihtamalla ```import os``` muotoon ```impor os```.  
![image](https://user-images.githubusercontent.com/90974678/223039453-e5005a56-a20d-4628-af5d-c8cdb7cb8337.png)  

### Oireet  

Käynnistin apachen uudelleen ja koitin curlata localhostin. Vastauksena tuli ```500 Internal Server Error``` ja selitys siitä, että palvelimella on jokin sisäinen virhe.  

![image](https://user-images.githubusercontent.com/90974678/223040460-693132d4-eb45-4f6f-a11f-5cf2d90e41e5.png)  

### Lokimerkinnät  

Kävin tutkimassa apachen virhelokia.  

```$ sudo tail -F /var/log/apache2/error.log```  

Lokista nähdään yksiselitteisesti, että ```settings.py``` tiedoston rivillä 14 on syntaksivirhe, jonka aiemmin aiheutin.  

![syntaxerror](https://user-images.githubusercontent.com/90974678/223041209-197e2ab7-b066-410c-a095-73ee7fac4c0a.png)  

### Ongelman korjaus ja toimivuuden testaus

Kävin korjaamassa ```settings.py``` tiedoston syntaksin, käynnistin apachen uudelleen ja curlasin localhostia. Vastauksena tuli ```Not found```, eli toimii oikein.  

![image](https://user-images.githubusercontent.com/90974678/223041869-faa37585-de56-4a22-a0c4-df930f958d8b.png)  

## b) Django-projektikansio väärässä paikassa  

#### ⏰ 6.3.2023 klo 09.11.  


### Ongelman aiheuttaminen  

Loin ```/publicwsgi``` hakemistoon uuden hakemiston ```wrong```. Siirsin Djangon-projektikansion ```laurisbase``` tähän uuteen kansioon.  

![image](https://user-images.githubusercontent.com/90974678/223043291-3cd53340-e51b-4405-a9fa-e24f4a50dc6a.png)


### Oireet  

Käynnistin apachen uudelleen ja koitin curlata localhostia. Vastauksena tuli ```403 Forbidden``` ja selitys siitä, ettei tällä käyttäjällä ole oikeuksia päästä käsiksi tähän resurssiin.  

![image](https://user-images.githubusercontent.com/90974678/223043847-7f71c69a-7f88-45a8-8727-f8fd83ce22e9.png)  

### Lokimerkinnät  

Apachen virhelokiin  

```$ sudo tail -F /var/log/apache2/error.log```  

Viimeisin rivi  

``` [Mon Mar 06 09:20:03.819576 2023] [authz_core:error] [pid 2482:tid 140533309617920] [client ::1:44288] AH01630: client denied by server configuration: /home/lauritorma/publicwsgi/laurisbase```  

Kertoo, että kyseessä on authorization-error. ```AH01630: client denied by server configuration: /home/lauritorma/publicwsgi/laurisbase``` kertoo, että palvelimen konfigurointi on estänyt ohjelmaa pääsemästä käsiksi kyseiseen hakemistoon.  

Tämä johtunee siitä, ettei polkuun ```/publicwsgi/laurisbase``` voi päästä, koska sellaista ei ole enää olemassa. 


![image](https://user-images.githubusercontent.com/90974678/223045767-84ad3d81-2c05-4cbd-9fbe-7de5214e2857.png)  

### Ongelman korjaus ja toimivuuden testaus  

Ongelman olisi voinut varmasti korjata konfiguroimalla asetustiedostot käyttämään uutta ```wrong``` hakemistoa, mutta halusin palauttaa projektin tilaan, jossa se oli ennen ongelman aiheuttamista.  

Siirsin siis ```laurisbase``` hakemiston pois ```wrong``` hakemistosta ylempään ```publicwsgi``` hakemistoon, jossa sen kuuluisi olla. Poistin myös tyhjän ```wrong``` hakemiston.  

Käynnistin apachen uudestaan ja curlasin localhostia. Vastauksena tuli ```Not Found``` eli se, jossa oltiin lähtötilanteessa. Ongelma korjattu.  

![image](https://user-images.githubusercontent.com/90974678/223049755-9c704955-a1a2-41b8-98bc-afbcb34d4374.png)  

## c) Projektikansiolla väärät oikeudet  

#### ⏰ 6.3.2023 klo 09.54.  







