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

Aloitin tehtävän käynnistämällä virtuaaliympäristön ja tarkistamalla, että kaikki toimii oikein.  

Uudelleenkäynnistin apachen ja curlasin localhostia. Huomiona tässä vaiheessa, että vastauksena saatu ```Not Found``` on haluttu vastaus silloin kun palvelimen pitäisi toimia oikein. Eli tämä on se tila, jossa *ei ole ongelmia*.  

![image](https://user-images.githubusercontent.com/90974678/223092269-6cac605b-2074-4f97-a7d8-0a9819fc6ff9.png)


Päätin tehdä kirjoitusvirheen polussa ```/publicwsgi/laurisbase/laurisbase``` sijaitsevaan ```settings.py``` tiedostoon.  

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

Siirryin apachen virhelokiin.

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

#### Pidin tauon klo 09:50 ja jatkoin klo 11.28

#### ⏰ 6.3.2023 klo 11.28.  

### Ongelman aiheuttaminen ja oireet

Muutin ```laurisbase/``` projektikansion oikeuksia komennolla ```$ chmod ugo-rwx lauribase/```. (u=user, g=group, o=others) ja (r=read, w=write, x=execute).  
Kaikilla näillä on nyt siis oikeudet lukea, kirjoittaa ja suorittaa. (edit: olin väärässä. Onkohan siis niin, että - poistaa kaikki oikeudet kaikilta?) 

Käynnistin apachen uudestaan ja koitin curlata localhostia. Vastauksena tuli ```403 Forbidden``` ja selitys, ettei ole oikeuksia päästä käsiksi tähän resurssiin.

![image](https://user-images.githubusercontent.com/90974678/223071254-4839eb13-34d7-4254-b174-64c7205d59fd.png)  

### Lokimerkinnät

```error.log``` kertoi, että pääsy polkuun ```/home/lauritorma/publicwsgi/laurisbase/laurisbase``` estyi ```because search permissions are missing on a component of the path```.  

![image](https://user-images.githubusercontent.com/90974678/223071343-055abd42-8613-4292-9f44-215adbb5b892.png)

Tämä oli outoa, koska olin luullut, että ```chmod ugo-rwx``` tarkoittaa samaa kuin ```chmod 777```, joka antaa kaikki oikeudet kaikille. Näin ei näköjään ollut, vaan 777-vastaava komento olikin ```chmod ugo+rwx```, jota testasin myös tässä välissä ja jonka avulla sain curlattua localhostin normaalisti.

![image](https://user-images.githubusercontent.com/90974678/223075491-c86d6dc2-a9ec-43ca-a7ac-d8f6a0fff0f7.png)  

Laitoin ```ugo-rwx``` oikeudet takaisin, jotta voin korjata ne vielä oikein. ```ugo+rwx``` kyllä toimii, mutta on vaarallista antaa kaikille rajattomat oikeudet.  

### Ongelman korjaus ja toimivuuden testaus  

Muutin projektin oikeuksia niin, että userilla on oikeus kirjoittaa, lukea ja suorittaa, groupilla oikeus lukea ja suorittaa ja otherilla oikeus lukea ja suorittaa.   
```$ chmod u=rwx,g=rx,o=rx laurisbase/```  

Curlasin localhostin ja se toimi normaalisti.  

![image](https://user-images.githubusercontent.com/90974678/223078965-562a949d-5eb6-4c80-afd3-2fd4a2f60f54.png)

## d) Kirjoitusvirhe Apachen asetustiedostossa  

#### ⏰ 6.3.2023 klo 12.06  

### Ongelman aiheuttaminen  

Aiheutin apachen asetustiedostoon ```/etc/apache2/sites-available/laurisbase.conf``` kirjoitusvirheen, poistamalla ```Require all granted``` kohdan  
```  
<Directory ${TDIR}/static/>
                
</Directory>
```  
sisältä ja näin estämällä pääsyn ```/static/``` hakemistoon ja sen sisältöön.  

![image](https://user-images.githubusercontent.com/90974678/223080314-cecc47f1-1be4-4e6e-b080-2523c3430276.png)  

### Oireet  

Käynnistin apachen uudelleen ja yritin curlata ```http://localhost/static/``` osoitetta. Vastauksena tuli ```403 Forbidden``` ja selitys, ettei ole oikeutta tähän resurssiin.  

![image](https://user-images.githubusercontent.com/90974678/223081004-82388af3-347d-4170-be65-9b6b6fb5a11c.png)
  
  
### Lokimerkinnät  

Siirryin apachen virhelokiin.  

Lokin viimeinen rivi kertoo, että on tapahtunut virhe ja kyseessä on authorization-error.  
```AH01630: client denied by server configuration: /home/lauritorma/publicwsgi/laurisbase/static/```  
Kertoo, että palvelimen konfigurointi on estänyt ```client ::1:41722``` pääsyn ```/static/``` hakemistoon.  

![image](https://user-images.githubusercontent.com/90974678/223081222-791ae646-7119-4ad3-a822-18748cd9c5d3.png)

### Ongelman korjaus ja toimivuuden testaus  

Kävin korjaamassa ongelman lisäämällä ```Require all granted``` takaisin ```/laurisbase.conf``` asetustiedostoon ja näin sallimalla pääsyn ```/static/``` hakemistoon.  
Käynnistin apachen uudelleen ja curlasin ```http://localhost/static/``` osoitteen. Sain vastauksena "This is static text!", joka on ```/static/index.html``` tiedoston sisältö. Ongelma siis korjattu.  

![image](https://user-images.githubusercontent.com/90974678/223081612-5ccdd4a1-9a51-417d-b903-3d9b0490cdd8.png)  

## e) Apachen WSGI-moduli puuttuu  

#### ⏰ 6.3.2023 klo 12.26  

### Ongelman aiheuttaminen  

Aiheutin ongelman poistamalla apachen WSGi-moduulin.  

```$ sudo apt-get purge libapache2-mod-wsgi-py3```  

![image](https://user-images.githubusercontent.com/90974678/223084735-a96e931d-7d71-4a4c-ba4e-e7c4f830320f.png)  

### Oireet  

Yritin käynnistää apachen uudelleen, mutta se ei onnistunut. Tarkistin myös apachen tilan komennolla  
```$ sudo systemctl status apache2```  

Rivi ```Invalid command 'WSGIDaemonProcess', perhaps misspelled or defined by a module not included in the server configuration``` paljastaa, että ```/laurisbase.conf``` asetustiedostossa yritetään ajaa komentoa, jota on ei pysty ajamaan, koska kyseistä moduulia ei löydy palvelimen konfiguraatiosta.  

![image](https://user-images.githubusercontent.com/90974678/223085314-09187cfb-9417-4038-8266-c6ada516699b.png)  

### Lokimerkinnät  

Apachen virheloki ei kerro meille juurikaan muuta, kuin että apache on saanut SIGTERM-signaalin ja sammuttanut itsensä.  

![image](https://user-images.githubusercontent.com/90974678/223086171-091c2717-b588-48bd-adc3-32cad384c574.png)

```$ /sbin/apache2ctl configtest```  kertoo vain saman kuin ylempänä ajettu ```$ sudo systemctl status apache2``` 

![image](https://user-images.githubusercontent.com/90974678/223086928-259a4190-c135-4e1b-898e-d160c52e6394.png)  


### Ongelman korjaus ja toimivuuden testaus  

Korjasin ongelman asentamalla WSGI-moduulin.  

```$ sudo apt-get -y install libapache2-mod-wsgi-py3```  

Tarkistin vielä configtestillä, että kaikki näyttää hyvältä. Kaikki näytti olevan ok, joten käynnistin apachen uudelleen ja curlasin localhostia onnistuneesti.

![image](https://user-images.githubusercontent.com/90974678/223087640-203972c3-8dab-4e3e-880e-edaf3d14a062.png)  

## Väärät domain-nimet ALLOWED_HOSTS-kohdassa  

#### ⏰ 6.3.2023 klo 12.42  

### Ongelman aiheuttaminen  

Aiheutin ongelman asettamalla ```/publicwsgi/laurisbase/laurisbase/settings.py``` tiedoston ```ALLOWED_HOSTS``` kohtaan väärät domain-nimet. "localhost" ja "lauritorma.com" tilalle vaihdoin "localhust" ja "tormalauri.com" joiden pitäisi aiheuttaa ongelmia.  

![image](https://user-images.githubusercontent.com/90974678/223088379-3591a868-6fd3-470c-9fba-f397506c32f4.png)

![image](https://user-images.githubusercontent.com/90974678/223088312-640d01af-8a02-47f3-8d94-b450d9e96b61.png)  

### Oireet  

Käynnistin apachen uudelleen ja koitin curlata localhostia. Vastauksena sain ```Bad Request (400)``` joka viittaisi siihen, että pyynnössä on jokin ongelma.  

![image](https://user-images.githubusercontent.com/90974678/223088980-97e85c71-37a9-459b-90c8-439d1cfa84b2.png)


### Lokimerkinnät  

Apachen lokitiedostoista ei löytynyt virheviestiä, josta voisi päätellä ongelman syyn. Kaikki näyttää niissä normaalilta

![image](https://user-images.githubusercontent.com/90974678/223089737-c55a6aad-b06d-427d-bc0d-79b605a69264.png)

### Ongelman korjaus ja toimivuuden testaus  

Kävin korjaamassa ongelman vaihtamalla ```settings.py``` tiedoston ```ALLOWED_HOSTS``` takaisin oikeiksi.  

Käynnistin apachen uudelleen ja curlasin localhostia onnistuneesti. Ongelma korjattu.  


![image](https://user-images.githubusercontent.com/90974678/223090718-a8ebdd21-7588-4fc4-a787-762ac2808367.png)


#### Lopetin työskentelyn 6.3.2023 klo 12.56.



### Lähteet

Deploy Django 4 - Production Install. Karvinen 2022. Luettavissa: https://terokarvinen.com/2022/deploy-django/  

Linux chmod command. Computer hope 2021. Luettavissa: https://www.computerhope.com/unix/uchmod.htm

Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  








