# h11 Prod

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

## a) Djangon tuotantoasennus  

#### Aloitin työskentelyn 1.3.2023 klo 18.35

### Alkutoimet  

#### ⏰ 1.3.2023 klo 18.39.

Aloitin Djangon tuotantoasennuksen päivittämällä ohjelmistot.  
```$ sudo apt-get update```  

Tekstieditorina halusin käyttää microa, joka oli jo aiemmin asennettu. En ollut kuitenkaan aiemmin asentanut microon bash-completion pakettia, joten asensin sen nyt.  
```$ sudo apt-get -y install micro bash-completion```  
  
Asetin vielä micron oletus-tekstieditoriksi.  
```$ export EDITOR=micro```  
   
![image](https://user-images.githubusercontent.com/90974678/222205941-240282c6-792d-43e5-b46c-f91cc02ed1c5.png)  

### Apache 2 ja /static/ hakemisto  

#### ⏰ 1.3.2023 klo 18.45.  
  
Olin jo aiemmin asentanut apachen, joten vaihdoin seuraavaksi sen oletussivun.  
```$ echo "This is Lauri Torma website" | sudo tee /var/www/html/index.html```  
  
![image](https://user-images.githubusercontent.com/90974678/222207528-7470d859-088f-4835-90a8-41794f971ace.png)  
  
Siirryin kotihakemistoon, loin hakemiston ```publicwsgi/lauribase/static``` ja loin ```index.html``` tiedostoon sisältöä, joka tulee näkymään sivulla staattisesti.  
```$ cd ```  
```$ mkdir -p publicwsgi/lauribase/static```  
```$ echo "This is static content" | tee publicwsgi/lauribase/static/index.html```  
  
![image](https://user-images.githubusercontent.com/90974678/222209657-8b96e57e-0c86-41f9-8add-7c5748b8d5cd.png)  
  
Lisäsin uuden VirtualHostin muokkaamalla ```lauribase.conf``` tiedostoa sudoeditillä.  
```$ sudoedit /etc/apache2/sites-available/lauribase.conf```  
  
```
<VirtualHost *:80>
	Alias /static/ /home/lauritorma/publicwsgi/lauribase/static/
	<Directory /home/lauritorma/publicwsgi/lauribase/static/>
		Require all granted
	</Directory>
</VirtualHost>
```  
 
![image](https://user-images.githubusercontent.com/90974678/222211176-19cb711e-e048-4952-9a21-3222c4c6fedd.png)  
  
Seuraavaksi kytkin uuden lauribase-nettisivun päälle ja kaikki muut sivut pois päältä.  
```$ sudo a2ensite lauribase.conf```  
```$ sudo a2dissite 000-default.conf```  
  
Testasin, että conffaus on onnistunut ja koska vastauksena tuli "Syntax OK", käynnistin apachen uusiksi.  
```$ /sbin/apache2ctl configtest```  
```$ sudo systemctl restart apache2```  
  
![image](https://user-images.githubusercontent.com/90974678/222212273-d7f10493-4554-4437-8d38-091a970577ca.png)  

Siirryin selaimessa osoitteeseen ```http://localhost/static/``` ja haluttu sisältö tuli näkyviin.  

![image](https://user-images.githubusercontent.com/90974678/222218472-2f77c3d4-e9fa-4147-b643-cbf7748c7d9d.png)  
  
### Djangon asennus virtuaaliympäristöön  

#### ⏰ 1.3.2023 klo 19.40.  

Olin jo aiemmin asentanut virtualenvin, joten siirryin seuraavaksi ```publicwsgi/``` hakemistoon ja loin sinne uuden virtuaaliympäristön.  
```$ cd```  
```$ cd publicwsgi```  
```$ virtualenv -p python3 --system-site-packages env```  
  
![image](https://user-images.githubusercontent.com/90974678/222219700-3165dcc6-aa55-4fb7-b848-3e48ca6a85d2.png)  
  
Siirryin käyttämään uutta virtuaaliympäristöä ja asensin siihen pipillä Djangon.   
```$ source env/bin/activate```  
```$ which pip```  
```$ micro requirements.txt```  
```django```  
```pip install -r requirements.txt```  
```django-admin --version```  
  
Asennetun Djangon versio: 4.1.7.  

![image](https://user-images.githubusercontent.com/90974678/222221158-28b924bb-097e-4a3a-b214-1468b5af0385.png)  

#### Lopetin työskentelyn 1.3.2023 klo 19.58.

#### Jatkoin työskentelyä 2.3.2023 klo xx.xx.
### mod_wsgi  
  




  














### Lähteet

Deploy Django 4 - Production Install. Karvinen 2022. Luettavissa: https://terokarvinen.com/2022/deploy-django/

Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  
