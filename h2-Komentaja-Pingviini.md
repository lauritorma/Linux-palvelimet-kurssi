
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

#### Quest
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

Avasin Debianissa komentorivin ja syötin komennon *sudo apt install micro*.  
Komentoriville tuli ilmoitus, joka kertoi tämän operaation käyttävän 14,4 MB lisätilaa. Valitsin vaihtoehdon kyllä.  
Micron asennus onnistui.  







