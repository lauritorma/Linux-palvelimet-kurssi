# h7 Real Internet(tm)

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

## x) Tiivistelmä artikkelista "First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS"  

* Virtuaalipalvelimista on paljon tarjontaa. 
* Opiskelijat voivat halutessaan käyttää GitHub Education-pakettia.  
* Virtuaalipalvelimelle kirjaudutaan root-käyttäjänä vain ensimmäisellä kerralla. 
* Tulimuuriin täytyy tehdä reikä esimerkiksi SSH:ta ja Apachea varten.  
* Valitse aina hyvä salasana.  
* Muista pitää paketit päivitettyinä  
* Palvelimelle pääsee IP-osoitteella, tai vuokratulla nimellä.  

#### Lähde  

First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Karvinen 2017. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/


## a) Virtuaalipalvelimen vuokraus

Vuokrasin virtuaalipalvelimen *Linodelta*.  
Valitsin Distroksi Debian 11 ja alueeksi eu-central. Valitsin halvimman Nanode 1 GB-paketin, jossa on RAMia 1 GB. Lopuksi asetin Root-salasanan ja loin palvelimen.

![image](https://user-images.githubusercontent.com/90974678/217782379-1aa4814a-1883-4423-90e0-e12eebe3a858.png)  

## b) Alkutoimet  

Otin komentoriviltä ssh-yhteyden virtuaalipalvelimeen komennolla ```ssh root@143.42.57.227```.  
Aloitin palvelimen konfiguroinnin asentamalla tulimuurin ja tekemällä siihen kaksi reikää komennoilla  
```sudo ufw allow 22/tcp```  
```sudo ufw allow 80/tcp```  

Seuraavaksi laitoin tulimuurin päälle komennolla ```sudo ufw enable```.  

![image](https://user-images.githubusercontent.com/90974678/217800768-ad6d6102-bfa0-4235-ab99-bafc9b14d4d8.png)  

Lukitsin root-tunnuksen komennolla ```sudo usermod --lock root```.  
Otin root-kirjautumisen pois käytöstä muokkaamalla tiedostoa ```/etc/ssh/sshd_config``` niin, että kohdassa PermiRootLogin lukee *no*.  

![image](https://user-images.githubusercontent.com/90974678/217801752-fad0c1a7-85fd-430d-bde5-df48b29b0987.png)

![image](https://user-images.githubusercontent.com/90974678/217801600-1929994d-259c-476f-88eb-6bf9f170ce06.png)  

Päivitin myös kaikki paketit.  

## c) Weppipalvelimen asennus virtuaalipalvelimelle

Asensin virtuaalipalvelimelle apachen.  
![image](https://user-images.githubusercontent.com/90974678/217802042-86429f91-d187-4700-9dcb-da3e1a210da1.png)

Muokkasin ```echo```-komennolla  ```/var/www/html/index.html``` tiedostoon oman tekstin.  

![image](https://user-images.githubusercontent.com/90974678/217802460-b15a8565-1aa8-4753-959b-4b63ffcd5407.png)  

Tarkistin apachen ja virtuaalipalvelimen toimivuuden menemällä selaimessa virtuaalipalvelimen IP-osoitteeseen.  

![image](https://user-images.githubusercontent.com/90974678/217802533-4231c561-fbce-467e-a4c3-d7d83ae16272.png)  

Kaikki ok.  


### Tehtävänantojen lähde  
Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  


