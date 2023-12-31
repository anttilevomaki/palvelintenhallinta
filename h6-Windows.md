# h6 Windows

Tein harjoituksen 2023-12-02. Työaseman prosessori: 11th Gen Intel(R) Core(TM) i5-11600K @ 3.90GHz 3.91 GHz, RAM: 16.0 GB, järjestelmä: Windows 10 Pro, Oracle VM VirtualBox,

### x) Lue ja tiivistä
  - Vapaavalintainen aiemman vuoden kotitehtäväraportti Saltin käytöstä Windowsilla
    - Windows as Salt-minion – homework 5 (Kunnari)
    - Salt-minionin asennus windowsille
    - pkg.installed
    - state.apply
  - Installing Windows 10 on a virtual machine
    - Lataa windows10-iso-tiedosto
    - Luo VirtualBoxissa uusi virtuaalikone ja asenna siihen äsken ladattu iso-tiedosto
    - Valitse oikeat näppäimistö- kieli- ym. asetukset
  - Filesystem Hierarchy Standard
    - root - juuri
    - /bin - sisältää komentoja, joita sekä sysadmin että käyttäjät voivat käyttää
    - /etc - sisältää asetustiedostoja (configuration files). "Asetustiedosto" on paikallinen tiedosto, jota käytetään ohjaamaan ohjelman toimintaa
    - /home - käyttäjän kotihakemisto
    - /srv - sisältää sivustokohtaisia tietoja, joita tämä järjestelmä palvelee
    - /tmp - hakemiston on oltava käytettävissä ohjelmille, jotka vaativat väliaikaisia tiedostoja
    - /usr - on tiedostojärjestelmän toinen tärkeä osa. /usr on jaettavaa, read-only dataa
    - /var - sisältää muuttuvia datatiedostoja

## a) Asenna Windows virtuaalikoneeseen.

Asensin windowsin uuteen virtuaalikoneeseen VirtualBoxissa tämän ohjeen mukaan. (https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md)
Tämä tehtiin jo tunnilla, joten siitä ei tullut otettua screenshotteja eri vaiheista. Alla kuitenkin kuva käynnissä olevasta virtuaalikoneesta.

![](kuvat/h6-Windows/Capture00.PNG)

## b) Asenna Salt Windowsille.

Latasin ja asensin saltin virtuaalikoneelle osoitteesta https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/windows.html.

![](kuvat/h6-Windows/Capture01.PNG)

Olin ilmeisesti jo tehnyt tämänkin tunnilla, mutta asensin sen silti uudelleen. Asennuksen aikana tuli siihen liittyen myös tällainen ilmoitus.

![](kuvat/h6-Windows/Capture02.PNG)

Asennus tuli valmiiksi ja laitoin saltin käynnistymään heti.

![](kuvat/h6-Windows/Capture03.PNG)

Komennolla "salt-call --local --version" saatiin saltin versio, joten asennuksen pitäisi olla onnistunut.

![](kuvat/h6-Windows/Capture04.PNG)
   
## c) Kerää Windows-koneesta tietoa grains.items -toiminnolla.

Pelkällä "salt-call --local grains.items" -komennolla tuli parin sivun verran tavaraa, ml. paljon varoitus- ja virheilmoituksia.

![](kuvat/h6-Windows/Capture06.PNG)
![](kuvat/h6-Windows/Capture07.PNG)

Nämä virheilmoitukset johtuivat kuitenkin siitä etten aluksi ajanut command promptia administratorina. Sama komento uudestaan niin oikeaa tietoa alkoi tulla sivukaupalla.

![](kuvat/h6-Windows/Capture08.PNG)
![](kuvat/h6-Windows/Capture09.PNG)

Alla sitten muutama grains.item -komento: osfinger kertoo käyttöjärjestelmän, cwd current working directory, systempath ilmeisesti järjetelmäpolku eli listaus hakemistoista, jotka ovat käytössä tai joita tarvitaan.

![](kuvat/h6-Windows/Capture11.PNG)

## d) Kokeile Saltin file -toimintoa Windowsilla.

Tähän katsoin mallia kokeneemman Linux-osaajan raportilta (https://github.com/RenneJ/hh-palvelinten-hallinta/blob/main/h6-windows.md). Loin C:lle tekstitiedoston komennolla "salt-call --local state.single file.managed C:\testfile.txt". Tehtävä myös onnistui.

![](kuvat/h6-Windows/Capture12.PNG)

Uusi testitiedosto myös löytyi tämän jälkeen C:ltä.

![](kuvat/h6-Windows/Capture13.PNG)

## e) Kokeile jotain itsellesi uutta toimintoa Saltista Windowsilla.

Salt Projectin sivuilta (https://docs.saltproject.io/en/latest/topics/windows/windows-package-manager.html#install-a-package) löysin komennon, jolla sain listattua järjestelmään asennetut paketit. Komento oli "salt-call --local pkg.list_pkgs".

![](kuvat/h6-Windows/Capture14.PNG)

Kokeilin myös Teron ohjeiden (https://terokarvinen.com/2018/04/18/control-windows-with-salt/) mukaan asentaa firefoxia, mutta se ei pelkästään tuolla komennolla onnistunut.

![](kuvat/h6-Windows/Capture15.PNG)


## References
- Karvinen 2023: Infra as Code 2023 - Palvelinten Hallinta 2023 syksy https://terokarvinen.com/2023/configuration-management-2023-autumn/
- Kunnari 2019: Windows as Salt-minion – homework 5 https://irenekunnari.wordpress.com/2019/05/01/windows-as-salt-minion/
- Halonen, Rajala, Ollikainen 2023: Installing Windows 10 on a virtual machine https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md
- The Linux Foundation 2015: Filesystem Hierarchy Standard https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html
- Salt Project 2023: Windows - Salt installguide https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/windows.html
- Salt Project 2023: Windows Package manager https://docs.saltproject.io/en/latest/topics/windows/windows-package-manager.html#install-a-package
- Karvinen 2018: Control Windows with Salt https://terokarvinen.com/2018/04/18/control-windows-with-salt/
- RenneJ 2023: H6 Windows https://github.com/RenneJ/hh-palvelinten-hallinta/blob/main/h6-windows.md
