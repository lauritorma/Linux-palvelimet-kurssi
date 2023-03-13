# h14 Uusi komento

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

### Tehtävänantojen lähde  

Linux Palvelimet 2023 alkukevät. Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  

## a) Linuxiin uusi komento Bashilla  

#### Aloitin työskentelyn 13.3.2023 klo 11.48  

Aloitin uuden komennon tekemisen luomalla uuden tiedoston ```~/.custom_aliases```, johon tallennan luomani aliakset. Voisin tallentaa aliakset myös ```~/.bashrc``` tiedostoon, mutta haluan niille erillisen oman tiedoston, jossa leikkiä niillä.  
  
Kirjoitin ```custom_aliases``` tiedostoon microlla aliaksen, joka kutsuttaessa tervehtii käyttäjää käyttäjänimellä.  
  
```touch ~/.custom_aliases```    
  
```micro ~/.custom_aliases```    
  
```alias welcome='echo "Welcome $USER."'```  
  
```source ~/.custom_aliases```  
  
```welcome```  
  
```Welcome lauritorma.```

![image](https://user-images.githubusercontent.com/90974678/224666488-a14230d3-c6d8-459f-a081-399432ef5694.png) 


## b) Linuxiin uusi komento Pythonilla  

#### ⏰ 9.3.2023 klo 15.25.

Loin uuden tiedoston ```telldaytime.py``` ja kirjoitin siihen microlla koodin, joka ottaa komentoriviparametrina joko "date", "time" tai jonkin muun sanan ja tulostaa sen mukaan joko päivämäärän, ajan tai molemmat.  
  
Asetin tiedoston käyttöoikeudet niin, että se voidaan suorittaa. Muutin tiedoston nimeä niin, että .py pääte jäi pois. 


![image](https://user-images.githubusercontent.com/90974678/224721225-c297e789-b325-4e83-ad02-db320d9317f3.png)
  

## c) Linuxiin komento, joka tekee jotain usealle tiedostolle.  

  
   
  
  
  
  
#### Lopetin työskentelyn 9.3.2023 klo 13.54.

### Lähteet



Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  

