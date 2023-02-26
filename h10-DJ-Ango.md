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

Aloitin uuden Django-projektin nimeltä "lauribase" komennolla ```django-admin startproject lauribase```. Siirryin lauribase-projektiin ja käynnistin sen komennolla ```/manage.py runserver```.  
  
Ajoin kuitenkin vielä komennon ```python manage.py migrate```, sillä ilmeisesti projektiin voisi tulla muutoin ongelmia.  


![image](https://user-images.githubusercontent.com/90974678/221435782-29319159-459a-4ee2-9a53-58f617ccf8a0.png)

Siirryin selaimessa osoitteeseen ```http://127.0.0.1:8000/```. Oletussivu aukesi normaalisti. 

![image](https://user-images.githubusercontent.com/90974678/221436052-29168829-d8c7-4796-bc97-2894b532fec4.png)  





