# Virtuaalikoneen kopiointi toiseen laitteeseen

Tämä dokumentti kuvaa ohjeena, miten onnistuin kopioimaan Linux-virtuaalikoneeni kannettavalta tietokoneelta pöytäkoneelle.

## Laitteisto

## Prosessi

### Virtuaalikoneen vieminen laitteelta

1. Valitse VirtualBoxissa yläreunasta "File" ja "Export Appliance"  

![Screenshot_20230123_091155](https://user-images.githubusercontent.com/90974678/213991911-64ba9732-4780-4e48-9c0d-4bb6d886fd12.png)

2. Valitse virtuaalikone, jonka haluat viedä. Minun tapauksessani siis "DebianLauriTorma".  

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

### Ratkaisu

1.

![image](https://user-images.githubusercontent.com/90974678/213999878-72dd936f-2b78-4724-ba0b-0a4073937056.png)

