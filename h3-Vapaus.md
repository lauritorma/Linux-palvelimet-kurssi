# h3 Vapaus!

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

## x) Tiivistelmä

### Tiivistelmä artikkelista "What is Free Software?"  

* *Vapaa ohjelmisto* tarkoittaa ohjelmistoa, jota käyttäjällä on vapaus muun muassa ajaa, jakaa ja kehittää    
* *Avoin lähdekoodi* tarkoittaa eri asiaa kuin vapaa ohjelmisto, mutta lähes kaikki avoimen lähdekoodin ohjelmistot ovat vapaita ohjelmistoja  
* Vapaata ohjelmistoa saa käyttää myös kaupallisessa käytössä  
* Jos ohjelmisto ei täytä neljää keskeistä vapaan ohjelmiston kriteeriä, se ei ole *vapaa*  

Lähde: 

What is Free Software?. FSF 2022-06-25. Luettavissa: https://www.gnu.org/philosophy/free-sw.html  


### Tiivistelmä artikkelin "The Rise of Open Source Licensing" kappaleesta 5: "Open Source Licenses as Alternative Governance Mechanisms": 5.1.1 - 5.1.4 (sivu 113 - 121)  

* OSI hyväksyy avoimen lähdekoodin lisensseiksi sellaiset lisenssit, jotka täyttävät tarvittavat vapaan käytön vaatimukset    
* Tullakseen hyväksytyksi, lisenssin täytyy sallia muun muassa vapaa käyttö, kopiointi, levitys, muokkaaminen  
* Lisenssit voidaan kategorioida eri tavalla, tämän kirjan tapauksessa käytetään funktionaalista ja historiallista luokittelujärjestelmää  

## a) Kolmen ohjelman lisenssit

Asensin edellisessä harjoituksessa kolme ohjelmaa:  
* googler  
* cowsay  
* fortune  

### googler

googler käyttää GPL-3.0 lisenssiä. Tämä selviää googlerin repositorysta.  

![image](https://user-images.githubusercontent.com/90974678/214613518-b36b7801-1520-45f3-baa2-5a7662469ec6.png)  
##### Lähde: https://github.com/jarun/googler  


Kyseessä on vapaa lisenssi. Tärkein lisenssin oikeusvaikutus on, että käyttäjän on hyväksyttävä GPL:n ehdot, jotta hän tekijänoikeuslain mukaan saa jakaa ohjelmaa jonka lisenssinä on GPL.  

### cowsay

cowsay käyttää GPL-3.0 lisenssiä. Tämä selviää cowsayn repositorysta.

![image](https://user-images.githubusercontent.com/90974678/214615252-7fb0d451-4af7-4023-b8c0-1129b7d43ad7.png)  
##### Lähde: https://github.com/cowsay-org/cowsay  


Kyseessä on vapaa lisenssi. Tärkein lisenssin oikeusvaikutus on, että käyttäjän on hyväksyttävä GPL:n ehdot, jotta hän tekijänoikeuslain mukaan saa jakaa ohjelmaa jonka lisenssinä on GPL.  

### fortune

fortune käyttää MIT-lisenssiä. Tämä selviää fortunen wikipedia-artikkelista. Wikipedia tietysti voi olla kyseenalainen lähde, mutta lisenssistä oli vaikeaa löytää tietoa muualta.

![image](https://user-images.githubusercontent.com/90974678/214616852-82156dea-2a22-4cbb-811b-a03d47534349.png)  
##### Lähde: https://en.wikipedia.org/wiki/Fortune_(Unix)  


Kyseessä on vapaa lisenssi. Tärkein lisenssin oikeusvaikutus on, että MIT-lisenssin omaavaa ohjelmaa käyttävän on säilytettävä ohjelman alkuperäiset tekijänoikeustiedot.


#### Lähteet

* GNU General Public License. FSF 2022-01-20. Luettavissa: https://www.gnu.org/licenses/gpl-3.0.html
* MIT-lisenssi. Linux.fi 2020-11-05. Luettavissa: https://www.linux.fi/wiki/MIT-lisenssi  

## b) Säännöllistä  

Loin Documents-kansioon uuden tiedoston *contacts.txt* ja lisäsin sinne muutaman rivin tekstiä. Seuraavaksi poimin tiedostosta tietoa komennolla  
```
grep 'Ma' contacts.txt 
```   
sekä  
```
grep 'Lauri' contacts.txt  
```  

![image](https://user-images.githubusercontent.com/90974678/214622194-3cbd5f0c-ac87-4f2d-a110-f7127e0fd10f.png)  

## c) Pipe  

Suoritin kaksi esimerkkiä putkituksesta.  
Ensin putkitin komennot  
```
fortune | cowsay  
```  

![image](https://user-images.githubusercontent.com/90974678/214625948-142c9cf3-75b5-4c71-b005-631d1902cb43.png)  

![image](https://user-images.githubusercontent.com/90974678/214626069-43ebff85-cf3d-4256-8977-1b854ee7ddb9.png)  

Jonka jälkeen putkitin komennot  
```
cat contacts.txt | sort  
```  

## d) Regex Crossword, tutorial




