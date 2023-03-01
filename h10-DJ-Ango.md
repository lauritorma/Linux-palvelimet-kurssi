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

## a) Kannattavaa  

### Virtuaaliympäristön asennus  

Aloitin tietokantasovelluksen tekemisen kehitysympäristön asennuksella. Ensimmäisenä asensin virtualenvin komennolla ```sudo apt-get -y install virtualenv```.  

![image](https://user-images.githubusercontent.com/90974678/221434892-dbf08aeb-d6a3-4ae0-9578-bdadd386c6c7.png)  

Seuraavaksi loin uuden virtuaaliympäristön komennolla ```virtualenv --system-site-packages -p python3 env/```.  

![image](https://user-images.githubusercontent.com/90974678/221434973-c0641d5e-6455-4f2d-9985-fa486506b245.png)  

Siirryin käyttämään luomaani virtuaaliympäristöä komennolla ``` source env/bin/activate``` ja tarkistin komennolla ```which pip```, että ollaan asentamassa pip:illä varmasti virtuaaliympäristöön.  

![image](https://user-images.githubusercontent.com/90974678/221435082-b5a1ee30-9085-4157-a784-c23cf55d859d.png) 

### Virtuaaliympäristössä

Muokkasin microlla ```requirements.txt``` tiedostoon yhden rivin: "django". Annoin komennon ```pip install -r requirements.txt``` ja lopuksi tarkistin asennetun Djangon version komennolla ```django-admin --version```.  
  
Asennetun Djangon versio oli 4.1.7.    

![image](https://user-images.githubusercontent.com/90974678/221435438-fc14df75-615e-4ca7-8a51-5ae0815960dd.png)  

### Django  

Aloitin uuden Django-projektin nimeltä "lauribase" komennolla ```django-admin startproject lauribase```. Siirryin lauribase-projektiin ja käynnistin sen komennolla ```./manage.py runserver```.  
  
Ajoin kuitenkin vielä komennon ```python manage.py migrate```, sillä ilmeisesti projektiin voisi tulla muutoin ongelmia.  


![image](https://user-images.githubusercontent.com/90974678/221435782-29319159-459a-4ee2-9a53-58f617ccf8a0.png)

Siirryin selaimessa osoitteeseen ```http://127.0.0.1:8000/```. Oletussivu aukesi normaalisti. 

![image](https://user-images.githubusercontent.com/90974678/221436052-29168829-d8c7-4796-bc97-2894b532fec4.png)  


### Käyttäjien lisääminen  

Seuraavaksi halusin luoda käyttäjän, jotta pääsisin käsiksi ylläpitäjien sivuun.  

Aloitin päivittämällä tietokannat.  

![image](https://user-images.githubusercontent.com/90974678/221436299-f79e8df8-289b-4369-b5be-b2e9663143ad.png)  

Seuraavaksi asensin pwgen-ohjelman komennolla ```sudo apt-get install pwgen``` ja loin komennolla ```pwgen -s 20 1``` uuden salasanan. Loin uuden superuserin komennolla ```./manage.py createsuperuser```, annoin sen nimeksi ```admin1``` ja salasanaksi juuri generoimani salasanan. Sähköpostin jätin tyhjäksi.  


![Näyttökuva 2023-02-26 225017](https://user-images.githubusercontent.com/90974678/221436470-8a0a6b4f-c077-4b51-b3ee-0391a315b225.png)

Siirryin ```/admin``` sivulle ja pääsin kirjautumaan sisään.  

![image](https://user-images.githubusercontent.com/90974678/221436670-a1da4512-920c-4918-94fb-002ed3f379d4.png)

Loin vielä käyttöliittymän kautta toisen "lauritorma" käyttäjän, jolle annoin sekä staff, että superuser oikeudet.  

![image](https://user-images.githubusercontent.com/90974678/221436844-987213c5-ef76-4981-bc83-733676d6a739.png)


### Tietokannan luonti  

Päätin luoda tietokannan verkkokaupan tuotteita varten. Loin uuden kansion ```prm``` (Product Relationship Manafement) komennolla ```./manage.py startapp rrm```.

![image](https://user-images.githubusercontent.com/90974678/221437040-bbee2edf-0b41-4e78-841c-03879a592ff4.png)

Seuraavaksi lisäsin prm-sovelluksen ```lauribase/settings.py``` tiedoston INSTALLED_APPS kohtaan microlla.  

![image](https://user-images.githubusercontent.com/90974678/221437030-5e50b3df-4765-49ca-9c44-0ef75c545b5f.png)  

Muokkasin microlla ```prm/models.py``` tiedostoa ja lisäsin sinne luokan "Product", joka sisältää "productname" sekä "description" pylväät.  

![image](https://user-images.githubusercontent.com/90974678/221437182-a9347b4a-0983-4706-8fce-49c92e71c7ac.png)  

Päivitin tietokannat.  

![image](https://user-images.githubusercontent.com/90974678/221437212-d9ef747b-e310-4166-a2b6-614e58ece689.png)  

Rekisteröin tietokannan muokkaamalla ```crm/admin.py``` tiedostoa microlla.  

![image](https://user-images.githubusercontent.com/90974678/221437380-2bcab27b-5b25-41ff-9a8c-6b0bdc0fb474.png)  

```/admin``` sivulle ilmestyi uusi PRM-appi ja sinne Products-taulu.  

![image](https://user-images.githubusercontent.com/90974678/221437409-d376a862-4d44-4658-8099-6f70ac30f725.png)  

Halusin vielä muokata ```crm/models.py``` tiedostoa niin, saisin lisättyjen tuotteiden nimet näkymään myös käyttöliittymän listauksessa. 

![image](https://user-images.githubusercontent.com/90974678/221437763-414f7428-5df6-4106-a8d6-d4aeafd407a6.png)  

Pystyin nyt lisäämään Product-tauluun uusia tuotteita.  

![image](https://user-images.githubusercontent.com/90974678/221437809-482bc2f8-705d-4ae8-9cde-9c6e27a3e8b0.png)  

Tuotteita pystyi myös muokkaamaan, sekä poistamaan.  

![image](https://user-images.githubusercontent.com/90974678/221437824-a3c94239-9b78-4036-ab6b-596ecc114bec.png)


### Lähteet

Django 4 Instant Customer Database Tutorial. Karvinen 2022. Luettavissa: https://terokarvinen.com/2022/django-instant-crm-tutorial/  

Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  

