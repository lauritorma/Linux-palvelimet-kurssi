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

Loin uuden käyttäjän "guest" komennolla ```sudo adduser guest```. Loin käyttäjälle salasanan ja täytin muut vaaditut tiedot.  


![image](https://user-images.githubusercontent.com/90974678/216318196-c11eaa16-73d6-45a1-a39b-6809c2d06f4a.png)


Kirjauduin ulos "lauritorma"-käyttäjältä ja käynnistin virtuaalikoneen uudestaan.  

Kirjauduin "guest"-käyttäjälle sisään.  

![image](https://user-images.githubusercontent.com/90974678/216318487-6e216af4-410d-4b35-be73-3414605248b0.png)  

Yritin käynnistää apachen, mutta en onnistunut, sillä "guest"-käyttäjää ei löytynyt ```sudoers``` tiedostosta.  

![image](https://user-images.githubusercontent.com/90974678/216319354-94aca530-b926-40a4-b793-3815520b95e3.png)

Kirjauduin "lauritorma"-käyttäjälle ja lisäsin "guest"-käyttäjän sudo-grouppiin komennolla ```sudo usermod -a -G sudo guest```  

![image](https://user-images.githubusercontent.com/90974678/216320156-11040168-28ef-4823-a169-791d5eaf0d78.png)

Kirjauduin takaisin "guest"-käyttäjälle. Käynnistin apachen ja siirryin selaimessa osoitteeseen ```http://localhost/~guest/```

![image](https://user-images.githubusercontent.com/90974678/216321786-6147a8d9-ee41-40df-b9f1-d1e7fdea9e92.png)

Uuden käyttäjän kotisivun luonti onnistui.  

## d) HTML5-sivu  

Siirryin ```public_html``` kansioon ja avasin luomani tiedoston ```index.html``` Microssa komennolla ```micro index.html```.  

![image](https://user-images.githubusercontent.com/90974678/216310661-a0aaad7d-845d-4355-aa96-92d89398cc37.png)

Lisäsin Microssa index.html tiedostoon sisältöä.  

![image](https://user-images.githubusercontent.com/90974678/216310316-a3e6e749-26c2-48be-9e82-499c497c918e.png)

Siirryin selaimessa osoitteeseen ```http://localhost/~lauritorma/```. Muokatun ```index.html``` tiedoston sisältö tuli näkyviin.  

![image](https://user-images.githubusercontent.com/90974678/216320988-847a819c-9537-45d8-b47a-ffc4ebf6d453.png)

Kirjauduin seuraavaksi "guest"-käyttäjälle ja suoritin samat toimenpiteet. 

![image](https://user-images.githubusercontent.com/90974678/216321254-440d86a4-110d-4bbe-8c78-a6da639c921c.png)


![image](https://user-images.githubusercontent.com/90974678/216321198-8e94ad8d-9cb4-428b-a6f7-3a7ed33ccc42.png)

![image](https://user-images.githubusercontent.com/90974678/216321350-bc89535a-a76e-487d-9d1f-18b9c8a0d08c.png)


### Tehtävänantojen lähde  
Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  






