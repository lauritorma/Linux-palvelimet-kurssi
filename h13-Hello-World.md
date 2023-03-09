# h13 Hello World

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

## a) Käännä "Hello World!" kolmella kielellä  

#### Aloitin työskentelyn 9.3.2023 klo 12.32  

### Python  

Loin ```helloworld_python.py``` tiedoston. Kirjoitin tiedostoon yhden rivin: ```print("Hello World)``` ja lopuksi suoritin sen.  
  
```touch helloworld_python.py```  
  
```micro helloworld_python.py```  
  
```print("Hello World)```  
  
```python3 helloworld_python.py```  
  
```Hello World!```  
  
  
![image](https://user-images.githubusercontent.com/90974678/223998820-fedc0693-67bf-45ff-b0ab-fd31a98a7156.png)
  
### Bash  

Loin ```helloworld_bash.sh``` skriptitiedoston. Kirjoitin tiedostoon rivit:  
```
#!/bin/bash
echo "Hello World"
```  
Asetin oikeudet skriptin suorittamiseksi ja lopulta suoritin sen.  

```touch helloworld_bash.sh```  
  
```micro helloworld_bash.sh```  
  
```
#!/bin/bash
echo "Hello World"
```  
  
```chmod +x helloworld_bash.sh```  
  
```bash helloworld_bash.sh```  
  
```Hello World!```  

![image](https://user-images.githubusercontent.com/90974678/224000510-04ac126d-64a9-4ce7-8865-931dde1a1891.png)  

### Java  

Asensin ensin Java Runtime Environmentin (JRE), sekä Java Development Kitin (JDK), joita minulla ei vielä ollut asennettuna. Tarkistin asennettujen ohjelmistojen versiot.  
  
```sudo apt-get install default-jre```  
  
```sudo apt-get install default-jdk```  
  
```java -version```  
  
```openjdk version "11.0.18" 2023-01-17```  
  
```javac -version```  
  
```javac 11.0.8```  

![image](https://user-images.githubusercontent.com/90974678/224003739-ca87f2e1-262d-4610-846a-446d15bc5ca1.png)

Loin uuden tiedoston ```HelloWorld.java```, johon kirjoitin luokan joka tulostaa "Hello World!". Käänsin ```HelloWorld.java``` tiedoston, jolloin luotiin ```HelloWorld.class``` tiedosto. 
Lopuksi suoritin tiedoston.  

```touch HelloWorld.java```  
  
```micro HelloWorld.java```  
  
```
public class HelloWorld {
   public static void main(String[] args) {
      System.out.println("Hello World!");
   }
}
```  
  
```javac HelloWorld.java```  
  
```java HelloWorld```  
  
```Hello World!```  
  


![image](https://user-images.githubusercontent.com/90974678/224004684-147ef163-1995-46f5-9193-014ca3f8be4a.png)  

## b) greetme Pythonilla  

#### ⏰ 9.3.2023 klo 13.08.  
  
```"Tee ohjelma, joka ottaa käyttäjän nimen komentoriviparametrina ja tervehtii 'greetme Tero' vastaa "Hello, Tero" ja 'greetme foo' vastaa "Hello, foo"."```  

Halusin tehdä ohjelman pythonilla, joten loin uuden tiedoston ```greetme.py```. Kirjoitin microlla tiedostoon skriptin, joka ottaa käyttäjältä ```sys.argv()``` avulla komentoriviparametrina syötteen,  
ja tulostaa tervehdyksen.  
Lopuksi suoritin skriptin.  

```touch greetme.py```  
  
```micro greetme.py```  
  
```
import sys

name = sys.argv[1]

print ("Hello", name)
```  
  
```python3 greetme.py Lauri```  
  
```Hello Lauri```  
  

![image](https://user-images.githubusercontent.com/90974678/224009840-307c13db-1707-4756-874b-ceab1eb21abd.png)  

  
#### Lopetin työskentelyn 9.3.2023 klo 13.30.

### Lähteet

Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04. Karvinen 2018. Luettavissa: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/

Linux Palvelimet 2023 alkukevät. Tero Karvinen 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/  

Java Hello World example on Linux. Rendek 2020. Luettavissa: https://linuxconfig.org/java-hello-world-example-on-linux

How to use sys.argv in Python. GeeksForGeeks 2019. Luettavissa: https://www.geeksforgeeks.org/how-to-use-sys-argv-in-python/  
  
How To Install Java with Apt on Ubuntu 18.04. Vlaswinkel 2018. Luettavissa: https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04  




