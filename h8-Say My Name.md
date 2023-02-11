# h8 Say My Name

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

## a) Domain  

Vuokrasin namecheap-palvelusta domainnimen *lauritorma.com*.  

Siirryin namecheap-palvelussa *dashboard -> domain list -> lauritorma.com -> manage -> advanced DNS*  

Lisäsin *Add new record* nappulasta kaksi uutta Host recordia, molemmat tyypiltään *A Record*.  
Asetin molemmat osoittamaan virtuaalipalvelimeni IP-osoitteeseen *143.42.57.227*.  

![image](https://user-images.githubusercontent.com/90974678/218251822-3e5b9bd9-f465-4091-80aa-dbfc9ff92733.png)  

Siirryin selaimessa osoitteeseen *lauritorma.com* ja *www.lauritorma.com*. Molemmat toimivat.  

![image](https://user-images.githubusercontent.com/90974678/218252134-0e38f500-21f5-436a-b9e2-4db62cf7f46f.png)


## b) Domainnimen tiedot  

Tässä alakohdassa käytin apuna artikkeleita "How to Install Dig in Linux with Command Line Examples", sekä "How to Use Linux dig Command (DNS Lookup)".  

Tutkin vuokraamani domainnimen tietoja kahdella komennolla.  

Ensimmäisenä annoin komentorivillä komennon ```host lauritorma.com```.  

![image](https://user-images.githubusercontent.com/90974678/218252248-ead630f4-86d9-4475-a106-d1c3c9a003d6.png)

Ensimmäinen rivi
```lauritorma.com has address 143.42.57.227```  
kertoo vain, että lauritorma.com osoittaa kyseiseen IP-osoitteeseen.  

Loppujen *mail is handled by* rivien tarkoitusta en tiedä, enkä oikein löytänyt googlettamalla siihen hyvää vastausta.  

Seuraavaksi tutkin domainnimeä komennolla ```dig lauritorma.com```.  

En kuitenkaan onnistunut heti, vaan minun oli ensin asennettava Dig komennolla ```apt-get install dnsutils```. Asennuksen jälkeen vielä päivitin kaikki ohjelmistot ja tarkistin sitten Dig-version komennolla ```dig -v```.  

![image](https://user-images.githubusercontent.com/90974678/218252606-4f619da4-c858-43fa-a8ed-333484b7088d.png)

![image](https://user-images.githubusercontent.com/90974678/218252718-707898a4-0c40-498c-81ca-64d6ad841c4e.png)

Nyt pystyin käyttämään dig-komentoa.  

![image](https://user-images.githubusercontent.com/90974678/218252738-93bf5f72-4c4d-4499-b268-d1353176c8b5.png)  

Vastauksen *ANSWER SECTION* kohdassa nähdään ensinnäkin palvelin, jolle kysely tehtiin eli tässä tapauksessa *lauritorma.com.*, jonka IP-osoite on 143.42.57.227. Lisäksi nähdään numero 300, joka kuvastaa *Time to Live* aikaa, jonka kuluttua data päivittyy. *IN* tarkoittaa Internetiä ja *A* A recordia.  

*Query time* kertoo, että vastauksen saamisessa kesti 12 msec.  
*SERVER* kohdassa nähdään vastanneen DNS palvelimen IP-osoite ja portti, eli tässä tapauksessa IP-osoite 62.241.198.245 ja portti 53.  
*WHEN* kohta näyttää, että komento on ajettu Helmikuun 11. päivänä kello 12:18:12 EET aikavyöhykkellä vuonna 2023.  
*MSG SIZE rcvd* kohta kertoo DNS palvelimelta saadun vastauksen koon olevan 59.  

Loppuja kohtia en osaa analysoida tarpeeksi hyvin ilman, että vastaus menee apuna käyttämäni artikkelin puhtaaksi lainaamiseksi.  



### Lähteet

How to Install Dig in Linux with Command Line Examples. Unixcop.com. Luettavissa: https://unixcop.com/how-to-install-dig-in-linux-with-command-line-examples/  

How to Use Linux dig Command (DNS Lookup). Jevtic 2020. Luettavissa: https://phoenixnap.com/kb/linux-dig-command-examples  

Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  




