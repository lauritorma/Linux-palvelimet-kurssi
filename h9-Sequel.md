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

## x) Yrityssoftaa  

### Esimerkki  
Esimerkki palvelusta, jota käytetään selaimella, jonka koodi ajetaan palvelimella ja jonka taustalla on tietokanta, voisi olla esimerkiksi jonkinlainen nettimarkkinapaikka.  
Käyttäjä voi visuaalisen käyttöliittymän kautta luoda, muokata ja poistaa omia ilmoituksia, sekä selata muiden jättämiä ilmoituksia. Ohjelman koodi ajetaan palvelimella, kuten Apache ja taustalla on tietokanta kuten MariaDB, jonka kanssa koodi kommunikoi ja mahdollistaa CRUD-operaatiot käyttöliittymän kautta. Tietokantaan varastoidaan esimerkiksi tietoa käyttäjistä, sekä käyttäjien jättämistä ilmoituksista.  

### Toteutustavan edut  

Etuja tällaisessa toteutustavassa on ainakin se, että jakamalla resurssit eri palvelimille kuormitus ei kohdistu vain yhteen paikkaan. Toiminta on siis paljon tehokkaampaa, kun ohjelman koodia ajetaan yhdellä palvelimella ja tietokanta sijaitsee toisella.  

## a) Postgre  

Aloitin PostgreSQL-asennuksen päivittämällä kaikki ohjelmat komennolla ```sudo apt-get update```.  

Asensin PostgrenSQL:n komennolla ```sudo apt-get -y install postgresql```.  

![image](https://user-images.githubusercontent.com/90974678/219356895-0dcab9f6-b7bb-48a5-aa63-a5f24b0ef8d9.png)  

Käynnistin PostgrenSQL:n komennolla ```sudo systemctl start postgresql```.  

![image](https://user-images.githubusercontent.com/90974678/219357254-19ccac97-ab30-4bbc-a723-a4493f951a9f.png)  

Loin uuden PostgreSQL tietokannan komennolla ```sudo -u postgres createdb lauritorma``` ja uuden käyttäjän komennolla ```sudo -u postgres createuser```.  

![image](https://user-images.githubusercontent.com/90974678/219357477-04105c55-ada9-44f2-8360-d98464f97148.png) 

![image](https://user-images.githubusercontent.com/90974678/219358328-2d8bb4a6-7576-4186-82e4-79e1a52f19a4.png)



