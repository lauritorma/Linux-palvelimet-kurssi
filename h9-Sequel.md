# h9 Sequel

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


## b) CRUD  

Aloitin CRUD-operaatiot komennolla ```psql```.  

Loin tietokantaan uuden taulun "items" komennolla ```CREATE TABLE items (id SERIAL PRIMARY KEY, name VARCHAR(200));```. items taulun on columnit "id" ja "name". id on pöydän pääavain.  

Tarkastin komennolla ```\d```, että taulu on luotu ja löytyy.  

![image](https://user-images.githubusercontent.com/90974678/219359203-b6a8af91-868d-4d90-a379-e9ce7461664a.png)

Lisäsin items tauluun uusia arvoja komennolla ```INSERT INTO students(name) VALUES ('esimerkki');```.  

![image](https://user-images.githubusercontent.com/90974678/219360145-a3435d94-4a42-4d9a-b096-e468d2e6f3cf.png) 

Seuraavaksi halusin selata items taulua, joten annoin komennon ```SELECT * FROM items;```, joka tulosti koko taulun sisällön.  

![image](https://user-images.githubusercontent.com/90974678/219360499-cf4295d2-4e5a-4409-b6b7-62ae11cc0b3a.png)  

Päivitin items taulun tietoja komennolla ```UPDATE items SET name='Laptop' WHERE name='Computer';```.  

![image](https://user-images.githubusercontent.com/90974678/219360761-c792bf7c-e5fe-47a8-a8c7-1b045f00663a.png)

Lopuksi poistin yhden rivin taulusta komennolla ```DELETE FROM items  WHERE name='Keyboard';```.  

![image](https://user-images.githubusercontent.com/90974678/219361121-109528aa-727e-49dd-b6be-867a2d936359.png)


### Lähteet

Install PostgreSQL on Ubuntu – New user and database in 3 commands. Karvinen 2016. Luettavissa: https://terokarvinen.com/2016/03/03/install-postgresql-on-ubuntu-new-user-and-database-in-3-commands/  

PostgreSQL Install and One Table Database – SQL CRUD tutorial for Ubuntu. Karvinen 2016. Luettavissa: https://terokarvinen.com/2016/03/05/postgresql-install-and-one-table-database-sql-crud-tutorial-for-ubuntu/

Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  



