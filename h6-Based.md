# h6 Based

## Laitteisto  

### Host  

* HP EliteDesk 800 G2 TWR  
* OS: Microsoft Windows 10 Pro  
* Prosessori: Intel Core i7-6700 CPU @ 3.40GHz  
* RAM: 2x 8GB  
* Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6  

### Guest
* Virtualisointiympäristönä Oracle VM VirtualBox 7.0.6  
* Virtuaalikoneena Debian GNU/Linux 11 (Bullseye)  
* Keskusmuisti: 4000 MB   
* Selain: Mozilla Firefox 102.7.0esr (64-bit)  

## x) Tiivistelmät

### Tiivistelmä artikkelista "Getting Started"  

* Osoitteet esitetään wepissä URLeina
* Asiakasohjelma yhdistää palvelimeen määritellyllä protokollalla ja tekee resurssipyynnön käyttäen URL-polkua, kuten *home/username/public_html/index.html*.   
* Palvelin lähettää pyyntöön vastauksen joka muodostuu tilakoodista, joka kertoo oliko pyyntö onnistunut vai ei, sekä mahdollisesta *Response bodysta*.  
* Asiakasohjelma tarvitsee palvelimen IP-osoitteen yhdistääkseen siihen.  
* Apache HTTP-palvelin konfiguroidaan tekstitiedostojen kautta.  
* Weppisivun sisältö voidaan jakaa pääosin staattiseen ja dynaamiseen sisältöön.    
* Staattinen sisältö tarkoittaa esimerkiksi HTML- tai kuvatiedostoja, jotka sisältyvät tiedostojärjestelmään.  
* Dynaaminen sisältö tarkoittaa sisältöä, joka generoidaan pyynnöstä ja saattaa muuttua eri pyyntöjen välillä.  
* *error log* on Apache HTTP-palvelimen ylläpitäjän tärkeimpiä työkaluja. Se kertoo mikä meni vikaan, milloin ja monesti myös miten korjata vika. 

#### Lähde  

Getting Started. Apache Software Foundation 2023. Luettavissa: https://httpd.apache.org/docs/2.4/getting-started.html  

### Tiivistelmä artikkelista "Name-based Virtual Host Support"  

* Nimi-pohjainen virtual hosting on yleensä yksinkertaisempaa kuin IP-pohjainen.  
* Kun pyyntö saapuu, palvelin pyrkii etsimään sopivimman ```<VirtualHost>``` argumentin, perustuen pyynnön käyttämään IP-osoitteeseen ja porttiin.  
* Jokaiselle hostille tulee luoda ```<VirtualHost>``` blokki.
* ```<VirtualHost>``` blokin sisällä oleva ```ServerName``` määrittää mitä hostia palvellaan ja ```DocumentRoot```missä sijainnissa on sisältö, joka on tarkoitettu kyseiselle hostille.


#### Lähde  

Name-based Virtual Host Support. Apache Software Foundation 2023. Luettavissa: https://httpd.apache.org/docs/current/vhosts/name-based.html  

## a) Apachelle uusi etusivu  

Toteutin uuden etusivun perjantain 3.2.2023 oppitunnin aikana, joten tässä alakohdassa näytän vain, että se on olemassa ja toimii oikein.  

Tulostin uuden kotisivun ```.conf``` tiedoston sisällön komennolla ```cat /etc/apache2/sites-available/frontpage.conf```.  

![image](https://user-images.githubusercontent.com/90974678/216941651-4579d6fe-6a3c-4c22-808b-daf2d07c4590.png)  

Tiedoston sisältö:    
```
<VirtualHost *:80>
	DocumentRoot /home/lauritorma/public_sites/
	<Directory /home/lauritorma/public_sites/>
		require all granted
	</Directory>
</VirtualHost>
```  
Annoin seuraavaksi komennon ```sudo a2ensite frontpage.conf``` ja sain varmistuksen, että sivu *frontpage* on jo sallittu.  

![image](https://user-images.githubusercontent.com/90974678/216942297-b558e73b-f3fc-43dc-bb94-2a8d6bd33a0a.png)  

Olin aiemmin luonut ```/home/lauritorma``` hakemistoon uuden hakemiston ```public_sites```, jonka sisään olin luonut uuden tiedoston ```index.html```.  

Seuraavaksi tulostin kyseisen tiedoston sisällön komennolla ```cat public_sites/index.html```.  


Käynnistin apachen komennolla ```sudo systemctl start apache2``` ja siirryin selaimessa osoitteeseen ```http://localhost/```.  

![image](https://user-images.githubusercontent.com/90974678/216943746-c0af79a3-a2ef-4752-9779-9b723c1abcf5.png)  

Apachella oli nyt uusi etusivu.  

Lopuksi varmistin vielä, että sivua pystyy muokkaamaan normaalilla käyttäjällä ilman sudoa.  

![image](https://user-images.githubusercontent.com/90974678/216944252-e1aef91d-6806-4da6-8f02-cd668d1602f7.png)  


![image](https://user-images.githubusercontent.com/90974678/216944168-0e26948b-7d78-47ff-b10a-ab2e8fcd9a51.png)  


![image](https://user-images.githubusercontent.com/90974678/216944321-ef3658fa-21ab-4793-95f9-737a1376bc61.png)  


## b) Kirjoitusvirhe Apachen asetustiedostoon  

Siirryin muokkaamaan ```frontpage.conf``` asetustiedostoa komennolla ```sudoedit /etc/apache2/sites-available/frontpage.conf```.  

Aiheutin tiedostoon tahallisesti kirjoitusvirheen muokkaamalla ```<VirtualHost>``` blokin muotoon ```<VirtualHos>```, eli jättämällä viimeisen kirjaimen pois.  

![image](https://user-images.githubusercontent.com/90974678/216945404-f16b8cdb-7c6c-4846-9255-aff2be152c3f.png)  


Annoin komennon ```sudo systemctl restart apache2.service``` ja sain virheilmoituksen  
```
Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xe" for details.
```   

![image](https://user-images.githubusercontent.com/90974678/216946355-4160761d-e840-4a1a-819d-c63c0217f6b5.png)  

Komento ```systemctl status apache2.service``` antoi seuraavanlaisen vastauksen:  

![image](https://user-images.githubusercontent.com/90974678/216946951-c0d8ee87-d9d3-4768-a6b1-7838961db339.png)  

Ja komento ```journalctl -xe``` seuraavanlaisen:  

![image](https://user-images.githubusercontent.com/90974678/216947309-ddb16988-0b11-4c98-b621-8f3ebe1a14e9.png)  

Seuraavaksi annoin komennon ```sudo apache2ctl configtest``` ja sain vastauksen  
```
apache2: Syntax error on line 225 of /etc/apache2/apache2.conf: Syntax error on line 6 of /etc/apache2/sites-enabled/frontpage.conf: Expected </VirtualHos> but saw </VirtualHost>
Action 'configtest' failed.
The Apache error log may have more information.
````

![image](https://user-images.githubusercontent.com/90974678/216948007-fe01838b-cc75-4d42-b007-fc78f0a90032.png)  

Polussa ```/etc/apache2/sites-enabled/frontpage.conf``` näyttäisi siis olevan syntaksivirhe ja voimme myös nähdä,  
että tosiaan kirjoitusvirhe sieltä löytyy.  
Suuntasin seuraavaksi Apachen error logiin komennolla ```sudo less /var/log/apache2/error.log```.  

```error.log``` tiedosto oli tyhjää täynnä.  

![image](https://user-images.githubusercontent.com/90974678/216949536-4e84a9b2-9a54-4a0e-a5f7-0b00a67064e9.png)

Suuntasin siis tiedostoon ```error.log.1``` komennolla ```sudo less /var/log/apache2/error.log.1``` ja sieltä avautui enemmän sisältöä.  

![image](https://user-images.githubusercontent.com/90974678/216949726-1e2fd745-af97-4d3c-878f-dbf095ad96b8.png)  

Rivi  
```[Mon Feb 06 12:17:50.183908 2023] [mpm_event:notice] [pid 704:tid 140426694737216] AH00491: caught SIGTERM, shutting down```  
Ei kerro juurikaan muuta, kuin että apache2 on sulkeutunut.  


Kävin lopuksi korjaamassa kirjoitusvirheen tiedostosta ```frontpage.conf```, jonka jälkeen tarkistin palvelimen statuksen ja ajoin configtest-komennon uudestaan.  

Kaikki OK.  

![image](https://user-images.githubusercontent.com/90974678/216951603-c315f369-ddb4-432c-bf12-13046b6def10.png)  


### Tehtävänantojen lähde  
Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  












