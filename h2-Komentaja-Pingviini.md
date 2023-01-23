
# h2 Komentaja Pingviini

Tämä tehtävä koostuu tiivistelmästä, sekä muista tehtävistä jotka suoritetaan Linux-ympäristössä.

Aloitin Linux-ympäristössä suoritettavat tehtävät perjantaina 2023-01-20 klo 17:05.  

### Laitteisto

#### Host
-Asus ZenBook UX433FA kannettava tietokone    
-OS: Microsoft Windows 11 Home  
-Prosessori: Intel Core i5-8265U CPU @ 1.60GHz 1.80 GHz  
-RAM: 8GB
-Näytönohjain: Intel UHD Graphics 620  

#### Guest
-Virtualisointiympäristönä Oracle VM VirtualBox 7.0.6  
-Virtuaalikoneena Debian GNU/Linux 11 (Bullseye)  
-Muisti: 4000 MB  

## x)

Tiivistelmä artikkelista *Command Line Basics Revisited* (Karvinen, Tero 2020-02-03, https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited).  

-Linuxin ja BSD:n käyttämä komentorivi on ollut olemassa pitkään  
-pwd tulostaa nykyisen työhakemiston  
-ls listaa tiedostot työhakemistossa  
-cd komennolla voidaan siirtyä eri hakemistoihin  
-Helpoimmat tekstieditorit ovat pico ja nano  
-Uuden hakemiston voi luoda komennolla mkdir  
-On mahdollista ottaa yhteys etäkomentoriviin  
-Tärkeitä hakemistoja ovat esimerkiksi "/" (juurihakemisto), "/home/", "/etc/", "/media/", ja "/var/log/"  
-sudolla ajetaan vain operaatiot jotka vaativat korkeita käyttöoikeuksia, sillä sudo antaa rajattomat käyttöoikeudet  
-Paketinhallinta on hyvä tapa asentaa ohjelmia

## a) Micro

Avasin Debianissa komentorivin ja syötin komennon *curl https://getmic.ro | bash*.  
Micron asennus onnistui.  

![Screenshot (77)](https://user-images.githubusercontent.com/90974678/213872831-9538674b-8a5d-430b-a4d0-e4eabec1f40b.png)  

## b) Rauta  

Asensin komentorivillä lshw:n komennolla *sudo apt-get install lshw*.  
Seuraavaksi syötin komennon *sudo lshw -short -sanitize* ja sain listauksen virtuaalikoneen raudasta.  

<img width="613" alt="image" src="https://user-images.githubusercontent.com/90974678/213873108-017687f9-9c69-49c2-a828-3f9a9075a987.png">

Listauksen alussa näkyy tietoja virtuaalikoneesta, sille annetun muistin määrästä sekä raudasta jonka päällä se pyörii. Alemmista kohdista en tässä kohtaa osaa sanoa vielä juuri mitään.

## Käytettävän laitteen vaihto

Keskeytin tässä vaiheessa työskentelyn.  

Jatkoin työskentelyä 2023-01-23 klo 12:50, siirrettyäni käytettävän virtuaalikoneen kaikkine asetuksineen ja asennuksineen toiselle laitteelle. Alla uudet laitteistotiedot.  

### Host
-HP EliteDesk 800 G2 TWR  
-OS: Microsoft Windows 10 Pro  
-Prosessori: Intel Core i7-6700 CPU @ 3.40GHz  
-RAM: 2x 8GB  
-Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6  

### Guest
-Virtualisointiympäristönä Oracle VM VirtualBox 7.0.6  
-Virtuaalikoneena Debian GNU/Linux 11 (Bullseye)  
-Muisti: 4000 MB  

## c) Apt

Ensimmäisenä asensin googlerin, ja kokeilin käyttää sitä google-haun tekemiseen komentoriviltä  

![image](https://user-images.githubusercontent.com/90974678/214023952-0653d831-adf4-4553-ada9-ffadd45941d5.png)

![image](https://user-images.githubusercontent.com/90974678/214024720-779b66a2-e1db-40ca-8f9a-af9588aab152.png)

Googler toimi jostain syystä melko huonosti, eikä löytänyt hakutuloksia juuri millään hakusanoilla.  

Seuraavana asensin ohjelman nimeltä "cowsay".  

![image](https://user-images.githubusercontent.com/90974678/214025802-bd7f49e2-e130-444d-8711-1356a5139d31.png)

![image](https://user-images.githubusercontent.com/90974678/214025995-e2fb76d2-ca45-4afb-8b4b-3f4a280ef1ed.png)

Ehkä paras ohjelma.  

Viimeisenä asensin fortunen, joka antaa motivoivia lauseita komennolla "fortune"

![image](https://user-images.githubusercontent.com/90974678/214026299-26a02d77-dd2c-458c-884b-20fb3b602f1b.png)

![image](https://user-images.githubusercontent.com/90974678/214026599-388cf01d-6c89-4145-97ca-79c289f788ba.png)


## d) FHS

### "/"

kansio on järjestelmän juurikansio. Juurikansio on kaikkein ylimpänä ja sisältää siis kaiken.  

![image](https://user-images.githubusercontent.com/90974678/214026991-73da7f48-39da-4afe-af11-5c286445421d.png)

### "/home"

on kansio, joka säilyttää käyttäjien kotikansiot. Minun tapauksessani home sisältää vain kansion "lauritorma"

![image](https://user-images.githubusercontent.com/90974678/214027520-1761d907-4890-4852-9c16-85dfc42ee012.png)

### "/home/lauritorma"

on kotikansio, jonka omistaja on käyttäjä "lauritorma". Kyseisen käyttäjän tallentamat tiedot löytyvät tästä kansiosta.

![image](https://user-images.githubusercontent.com/90974678/214027840-4cb9ccfa-f3a7-4d47-ab6b-f4e0604c7f7e.png)

"lauritorma" kansiosta löytyy esimerkiksi Downloads kansio, joka sisältää käyttäjän lataamat tiedostot

![image](https://user-images.githubusercontent.com/90974678/214028027-21b2c561-3d81-44d5-9058-40ab780cdcb9.png)  

### "/etc/"

on kansio, josta löytyvät järjestelmän asetukset sisältävät kansiot ja tiedostot.

![image](https://user-images.githubusercontent.com/90974678/214028500-1554945b-b873-40b0-b350-2191a435afc8.png)

![image](https://user-images.githubusercontent.com/90974678/214028723-46b0a29e-c26b-4650-ab5e-10a31dd8ca78.png)

![image](https://user-images.githubusercontent.com/90974678/214029258-0b4f2573-deda-418a-b431-9784c1abfa40.png)


### "/media/"

on kansio, josta löytyy esimerkiksi usb-laitteet. Valitsin virtuaalikoneen "Devices" valikosta "USB" alta muistitikkuni käytettäväksi virtuaalikoneessa, joten sain sen näkymään tässä kansiossa esimerkkinä.

![image](https://user-images.githubusercontent.com/90974678/214029609-859ade1e-1334-49d9-96a3-a081d2278446.png)

![image](https://user-images.githubusercontent.com/90974678/214029992-8fd88da6-6ca5-4bf0-8e76-47fa96c7a79c.png)

![image](https://user-images.githubusercontent.com/90974678/214030675-e87c5bf0-5c30-4f32-93a1-642a3df107be.png)

### "/var/log/"

on kansio, josta löytyy järjestelmän lokitiedostot. 

![image](https://user-images.githubusercontent.com/90974678/214030947-bcbb1e07-1885-4043-ade5-9a427d8611ea.png)

Tässä halusin tulostaa näytölle boot.log tiedoston sisällön, mutta jouduinkin suorittamaan komennon sudolla.

![image](https://user-images.githubusercontent.com/90974678/214031181-98e03e0c-a1e5-457b-baa5-15e7f796e8ff.png)


## e) The Friendly M

### 1) Etsin polusta /etc/passwd käyttäjää lauritorma

![image](https://user-images.githubusercontent.com/90974678/214032065-871d043f-c6cb-4f15-aed1-1d9da3e0c89a.png)

### 2) Etsin tiedostosta "esimerkki.txt" sanaa "hakusana"

![image](https://user-images.githubusercontent.com/90974678/214032864-159e6401-1d08-4fd2-bc73-a82031e98b75.png)




