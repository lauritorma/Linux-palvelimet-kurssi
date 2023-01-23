# Virtuaalikoneen kopiointi toiseen laitteeseen

*Lauri Törmä 2023-01-23*

Tämä dokumentti kuvaa ohjeena, miten onnistuin kopioimaan Linux-virtuaalikoneeni toiselle laitteelle.

## Laitteisto

Tämän ohjeen prosessit on toteutettu alla listatulla laitteistolla.  

### Laite jolta virtuaalikone viedään

-Asus ZenBook UX433FA  
-OS: Microsoft Windows 11 Home  
-Prosessori: Intel Core i5-8265U CPU @ 1.60GHz 1.80 GHz  
-RAM: 8GB  
-Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6 
 

### Laite jolle virtuaalikone tuodaan

-HP EliteDesk 800 G2 TWR  
-OS: Microsoft Windows 10 Pro  
-Prosessori: Intel Core i7-6700 CPU @ 3.40GHz  
-RAM: 2x 8GB  
-Virtualisointiympäristö: VM Oracle VirtualBox 7.0.6  

## Prosessi

### Virtuaalikoneen vieminen laitteelta

1. Valitse VirtualBoxissa yläreunasta "File" ja "Export Appliance"  

![Screenshot_20230123_091155](https://user-images.githubusercontent.com/90974678/213991911-64ba9732-4780-4e48-9c0d-4bb6d886fd12.png)

2. Valitse virtuaalikone, jonka haluat viedä. Minun tapauksessani siis "DebianLauriTorma", jonka OS on Debian (64-bit).  

3. Valitse "Next"   

![Screenshot (79)](https://user-images.githubusercontent.com/90974678/213992361-1403edc1-e43f-4362-a1d3-3f469b533873.png)

4. Format settings valikossa valitse valikosta aktiiviseksi "Write Manifest file" sekä "Include ISO image files"  

5. Valitse "Next"  

![Screenshot (81)](https://user-images.githubusercontent.com/90974678/213991967-cd0690a1-e68a-4d4e-8345-0eafb569a6c3.png)

6. Appliance settings valikossa tarkista tiedot ja valitse "Finish"

![Screenshot (82)](https://user-images.githubusercontent.com/90974678/213991984-4d026af3-2c08-4549-b929-36a06cee5996.png)

7. Virtuaalikone viedään johonkin hakemistoon. Minun tapauksessani tiedosto *DebianLauriTorma.ova* vietiin hakemistoon "Documents". Tässä kestää jonkin aikaa   

![image](https://user-images.githubusercontent.com/90974678/213997710-812659a3-7a42-4f6d-b1b9-7a83c1ef967f.png)


8. Kopioi viety *xxx.ova* tiedosto esim. ulkoiselle kovalevylle tai Google Driveen, josta voit siirtää sen toiselle laitteelle  

### Virtuaalikoneen tuominen laitteelle

9. Siirrä *xxx.ova* tiedosto laitteelle, jossa haluat käyttää virtuaalikonetta  
10. Valitse VirtualBoxissa yläreunasta "File ja "Import Appliance"  

![Näyttökuva 2023-01-23 095435](https://user-images.githubusercontent.com/90974678/213995626-e9e6b086-046e-4156-b1b0-3616422f205e.png)

11. "Appliance to import" ikkunassa katso, että lähteenä on "Local File System"

12. Etsi ja valitse *xxx.ova* tiedosto hakemistosta  

13. Valitse "Next"

![image](https://user-images.githubusercontent.com/90974678/213996312-22d1633b-0b5c-4146-9f44-95c5de402960.png)

14. "Appliance settings" ikkunassa pidä oletusasetukset ja valitse "Finish"  

![image](https://user-images.githubusercontent.com/90974678/213996677-db012cf3-d4ab-4d38-bda9-86c6372c0c0d.png)

15. Oikeaan yläreunaan ilmestyy latauspalkki ja valittu virtuaalikone tuodaan VirtualBoxiin. Tässä kestää jonkin aikaa

![image](https://user-images.githubusercontent.com/90974678/213996899-afaa0c5d-3c31-4821-b376-ce258ec82460.png)

Virtuaalikoneen pitäisi nyt ilmestyä VirtualBoxiin ja olla valmis käyttöä varten.

![image](https://user-images.githubusercontent.com/90974678/213997097-43fec6d6-331b-46d4-9751-ee3b8571f7cc.png)

## Not in a hypervisor partition | VT-x is disabled in the BIOS for all CPU modes

### Ongelma 
Yrittäessäni käynnistää tuodun virtuaalikoneen, törmäsin virheviestiin *Not in a hypervisor partition (HVP=0) (VERR_NEM_NOT_AVAILABLE)*, eikä kone tämän johdosta toiminut.  
Apuna ongelman korjaamiseen käytin artikkelia "How to Fix Not in a Hypervisor Partition Error [Partition Manager]" (partitionwizard.com, 2023-01-03, Luettavissa: https://www.partitionwizard.com/partitionmanager/not-in-a-hypervisor-partition.html).  
Ongelman ratkaisu oli avata koneen BIOS ja käydä sallimassa virtualisointi. Avaan vielä tämän prosessin ohjeena.  
Ohje ei välttämättä toimi samalla tavalla kaikilla tietokoneilla tai käyttöjärjestelmillä.  

### Ratkaisu

1.Käynnistä tietokone uudestaan BIOS-modessa. Itse painoin shift-näppäimen pohjaan ja valitsin käynnistysvalikosta samalla käynnistä uudelleen.

![image](https://user-images.githubusercontent.com/90974678/213999878-72dd936f-2b78-4724-ba0b-0a4073937056.png)

2. Windows käynnistyy kuvan kaltaiseen valikkoon. Valitse "vianmääritys"  

![IMG_20230123_110214](https://user-images.githubusercontent.com/90974678/214002038-ec2a9a34-1bab-4d9d-99f1-adf1a7a7e3db.jpg)

3. Valitse "lisäasetukset"

![IMG_20230123_110203](https://user-images.githubusercontent.com/90974678/214002322-2ff52b8a-0155-426b-81a7-058c1e8500ae.jpg)

4. Valitse "UEFI-laiteohjelmiston asetukset"  

![IMG_20230123_110150](https://user-images.githubusercontent.com/90974678/214002421-80acdd1b-bc82-4cf6-bed0-6dd759a5158f.jpg)

5. Valitse "BIOS-setup"


![IMG_20230123_110138](https://user-images.githubusercontent.com/90974678/214002676-ece1b54b-83b2-47bf-a24c-2e53144a4f29.jpg)

6. Siirry nuolinäppäimillä valikossa kohtaan "Advanced"  

![IMG_20230123_110117](https://user-images.githubusercontent.com/90974678/214002760-02c5c9bf-ba18-4b91-a1c2-b79682aa3f4b.jpg)

7. Valitse "System options"

![IMG_20230123_110100](https://user-images.githubusercontent.com/90974678/214002872-bb918f39-f5e4-4e1c-9f3d-9af98ed2d156.jpg)

8. Klikkaa "Virtualization Technology"-valinnat aktiivisiksi  


![IMG_20230123_110050](https://user-images.githubusercontent.com/90974678/214002925-ed0c8e38-95d7-4c12-b7ad-54be09c62674.jpg)

9. Tallenna asetukset ja käynnistä tietokone uudestaan  



Virtuaalikoneen pitäisi nyt käynnistyä ja toimia moitteetta!
