# h5 Hello Web

## Laitteisto  

### Host  

-HP EliteDesk 800 G2 TWR  
-OS: Microsoft Windows 10 Pro  
-Prosessori: Intel Core i7-6700 CPU @ 3.40GHz  
-RAM: 2x 8GB  
-Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6  

### Guest
-Virtualisointiympäristönä Oracle VM VirtualBox 7.0.6  
-Virtuaalikoneena Debian GNU/Linux 11 (Bullseye)  
-Keskusmuisti: 4000 MB   
-Selain: Mozilla Firefox 102.7.0esr (64-bit)  

## x)

## a) Apachen esimerkkisivun vaihto

Aloitin käynnistämällä Apachen komennolla ```sudo systemctl start apache2```.  
Yritin vaihtaa esimerkkisivun komennolla  ```sudo echo "This is text" > /var/www/html/index.html```, mutta sain vastauksena  
```bash: /var/www/html/index.html: Permission denied```.  

![image](https://user-images.githubusercontent.com/90974678/216301833-dc3a849f-b52e-4561-9f07-07f300a37858.png)  

Korjasin ongelman kirjautumalla root-ympäristöön komennolla ```sudo su```, jonka jälkeen sain syötettyä aiemman echo-komennnon onnistuneesti.  
Lopuksi kirjauduin ulos root-ympäristöstä näppäinyhdistelmällä ```Ctrl+D```.  

![image](https://user-images.githubusercontent.com/90974678/216302551-b3095d1a-f683-483d-b37b-138e1b5fcf6d.png)  

Apachen esimerkkisivu vaihdettiin onnistuneesti.  

![image](https://user-images.githubusercontent.com/90974678/216303137-fa39cce1-3b9b-4b1a-8a07-6cb7a24978c0.png)  

## b) Käyttäjän kotisivu  

Otin käyttäjähakemiston käyttöön komennolla ```sudo a2enmod userdir``` ja käynnistin apachen uudestaan komennolla ```systemctl restart apache2```.  


![image](https://user-images.githubusercontent.com/90974678/216304920-21f0be01-8e8a-44f4-b1b9-9cba4cb3f566.png)  

Siirryin lauritorma-käyttäjän kotihakemistoon ja loin uuden hakemiston komennolla ```mkdir public_html```. Tarkistin käyttäjän nimen komennolla ```whoami```

![image](https://user-images.githubusercontent.com/90974678/216305657-5aaa3f23-6145-4b9b-b545-7d1d815aca70.png)  

Siirryin selaimessa osoitteeseen ```http://localhost/~lauritorma/```. Selaimeen avautui listaus tyhjästä hakemistosta.  

![image](https://user-images.githubusercontent.com/90974678/216306122-cfff2138-d06c-453a-8703-c8604fa7c884.png)  

## c) Uusi käyttäjä  

Loin uuden "vierailija" käyttäjän komennolla ```sudo useradd vierailija```. Loin käyttäjälle salasanan komennolla ```sudo passwd vierailija```.  

![image](https://user-images.githubusercontent.com/90974678/216307814-3a29848c-2574-4fc5-8270-776c42792929.png)

Kirjauduin ulos "lauritorma"-käyttäjältä ja käynnistin virtuaalikoneen uudestaan.  

![image](https://user-images.githubusercontent.com/90974678/216308213-2371f956-c450-4fee-8d72-35f63e8d2c20.png)  

Yritin kirjautua "vierailija"-käyttäjälle sisään, mutta en onnistunut. Varmistin, että käytän oikeaa käyttäjänimeä ja salasanaa, mutta kirjautumisnäkymä luuppasi aina takaisin, kun klikkasin kirjautumisnappia.  

En voinut täten jatkaa tätä tehtävää loppuun asti.  

## d) HTML5-sivu  

Siirryin ```public_html``` kansioon ja avasin luomani tiedoston ```index.html``` Microssa komennolla ```micro index.html```.  

![image](https://user-images.githubusercontent.com/90974678/216310661-a0aaad7d-845d-4355-aa96-92d89398cc37.png)

Lisäsin Microssa index.html tiedostoon sisältöä.  

![image](https://user-images.githubusercontent.com/90974678/216310316-a3e6e749-26c2-48be-9e82-499c497c918e.png)

Siirryin selaimessa osoitteeseen ```http://localhost/~lauritorma/```. Muokatun ```index.html``` tiedoston sisältö tuli näkyviin.  

### Tehtävänantojen lähde  
Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  






