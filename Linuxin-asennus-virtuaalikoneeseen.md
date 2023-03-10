
# Linuxin asennus virtuaalikoneeseen.

Tämä raportti on kuvaus Linuxin asennuksesta virtuaalikoneeseen. suoritin asennuksen torstaina 19.01.2023. Koneena oli Asus ZenBook UX433FA-kannettava tietokone.
Käyttöjärjestelmänä oli Microsoft Windows 11 Home.

Tätä dokumenttia saa kopioida ja muokata GNU General Public License (versio 2 tai uudempi) mukaisesti. http://www.gnu.org/licenses/gpl.html

Pohjana Tero Karvinen 2012: Linux kurssi, http://terokarvinen.com

## Asennus

Aloitin asennuksen klo 11:10. Virtualisointiohjelmistona Oracle VM VirtualBox, versio 7.0.6, jonka olin aiemmin asentanut.
Avasin VirtualBoxin ja valitsin valikosta ”Machine” ja ”New”. Seuraavaksi valitsin ”Create Virtual Machine”.
Tässä VirtualBoxin versiossa ei ollut valittavissa Expert modea. Annoin virtuaalikoneelle nimeksi ”DebianLauriTorma”, valitsin tyypiksi Linux,
versioksi Debian (64-bit) ja muistin määräksi 4000 MB. Valitsin ”Create a virtual hard disk now” ja klikkasin ”Create”.

Kun virtuaalikone oli luotu, valitsin sen valikosta ja siirryin sen asetuksiin. Etenin ”Storage” välilehdelle ja valitsin ”Controller: IDE” alta ”CDROM Empty”.
Oikealla ”Attributes” kohdan alla valitsin pienen levykuvakkeen kohdalta ”Choose a disk file”. Etsin ISO-kuvan (debian-live-11.6.0-amd64-xfce+nonfree.iso) ja valitsin sen.
Tallensin asetukset.

Seuraavaksi tuplaklikkasin virtuaalikonetta ja boottasin sen. Suoritin boottauksen valinnalla ”Debian GNU/Linux Live”. Debian latautui hetken ja työpöytä avautui näytölle. Valitsin työpöydän vasemmasta alareunasta ”Install Debian”. 
Installerissa valitsin ensimmäisenä kieleksi ”American English” ja aikavyöhykkeeksi Helsinki. Näppäimistön kieleksi valitsin Suomi.
Seuraavassa kohdassa valitsin ”Erase Disk”. Tämän jälkeen täytin käyttäjätietoihin oman nimeni, valitsin käyttäjänimen ja salasanan.
Seuraavana aukesi ”Summary” välilehti. Valitsin ”Install”. 
Asennus onnistui ja virtuaalikone käynnistyi uudestaan. Debian avautui kirjautumisnäkymään, johon syötin aiemmin luodut käyttäjänimen ja salasanan.
Kirjautuminen onnistui ja asennettu Debian avautui työpöydälle.

VirtualBox ei antanut ottaa kuvakaappauksia virtuaalikoneesta, joten raporttiin ei niitä saanut mukaan.
