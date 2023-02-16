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
