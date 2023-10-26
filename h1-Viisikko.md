# h1 Viisikko

x) Lue ja tiivistä
- ohjeet siihen, miten luodaan oma sivu Githubiin
- ohjeet siihen, miten Githubissa luodaan ja julkaistaan tiedostoja
- ylestietoa mikä salt on
- ohjeet saltin asentamiseen

a) Asenna Salt
- sudo apt-get -y install salt-minion
    - Unable to locate package salt-minion
- sudo salt-call --version
    - salt-call: command not found
- Pythonin asennus koneelle ja koko VirtualBoxin uudelleenasennus
- Debianin/uuden virtuaalikoneen asennus
- Black screen - xforcevesa ei auta
- Xubuntun lataus ja asennus
- Kokeilin vielä Debiania ja sain työpöydän näkymään, mutta Saltin asennus ei edelleenkään onnistunut
- Xubuntulla Saltin asennus meni läpi, versio 3004.1
  - Asensin myös Guest Additions Xubuntuun

b) Viisi tärkeintä
pkg.installed
  $ sudo salt-call --local -l info state.single pkg.installed tree
  - Result: True
  - Comment: All specified packages are already installed
  - Succeeded: 1, Failed: 0, Total states run: 1
    - Paketit asennettu
  $ sudo salt-call --local -l info state.single pkg.removed tree
  - Result: True
  - Comment: All targeted packages were removed
  - Succeeded: 1 (Changed=1), Failed: 0
    - Paketit poistettu, muutos tapahtunut

file.managed
  $ sudo salt-call --local -l info state.single file.managed /tmp/hellotero
  - Comment: Empty file
  - new file created
  - Succeeded: 1 (Changed=1), Failed: 0
    - Uusi tyhjä tiedosto luotu, yksi muutos tapahtunut
  $ sudo salt-call --local -l info state.single file.managed /tmp/moitero contents="foo"
  - Comment: File /tmp/moitero updated
  - diff: New file
  - Succeeded: 1 (Changed=1), Failed: 0
    - Uusi tiedosto luotu, minkä sisältöä myös muokattu, yksi muutos tapahtunut
  $ sudo salt-call --local -l info state.single file.absent /tmp/hellotero
  - Comment: Removed file /tmp/hellotero
  - removed: /tmp/hellotero
  - Succeeded: 1 (Changed=1), Failed: 0
    - poistettu tiedosto /tmp/hellotero, yksi muutos tapahtunut

service.running
  $ sudo salt-call --local -l info state.single service.running apache2 enable=True
  - Result: False
  - Comment: The named service apache2 is not available
  - Succeeded: 0, Failed: 1
    - Olisi käynnistänyt apachen, mutta sitä ei ollut
  $ sudo salt-call --local -l info state.single service.dead apache2 enable=False
  - Result: True
  - Comment: The named service apache2 is not available
  - Succeeded: 1, Failed: 0
    - Olisi sammuttanut apachen, mutta sitä ei ollut, eli failed succesfully? :) 

user.present
  $ sudo salt-call --local -l info state.single user.present terote08
  - Comment: New user terote08 created
  - Succeeded: 1 (Changed=1), Failed: 0
    - Luotiin uusi käyttäjä terote08, yksi muutos tapahtunut
  $ sudo salt-call --local -l info state.single user.absent terote08
  - Comment: Removed user terote08
  - Succeeded: 1 (Changed=1), Failed: 0
    - Poistettiin käyttäjä terote08, yksi muutos tapahtunut

cmd.run
  $ sudo salt-call --local -l info state.single cmd.run 'touch /tmp/foo' creates="/tmp/foo"
  - Comment: Command "touch /tmp/foo" run
  - Succeeded: 1 (Changed=1), Failed: 0
    - Komento suoritettiin, yksi muutos tapahtunut

c) Idempotenssi
Jokin menetelmä on idempotentti, jos sen tulokset ovat aina samat riippumatta siitä, toteutetaanko se kerran, vai monta kertaa.
Esim. tietokantahaku on idempotentti, sillä se ei muuta tietokannan tilaa.
Ensimmäinen pkg.installed komento oli idempotentti, sillä se ei muuttanut mitään, koska kyseiset paketit oli jo asennettu.
Tavallaan myös molemmat service.running ja service.dead komennot olivat tässä tapauksessa idempotentteja, koska mitään muutoksia ei tapahtunut, vaikka niitä yritettiinkin.

d) Tietoa koneesta
- cpu_flags-kohdassa kymmeniä rivejä
- kernelversion: #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Oct  6 10:23:26 UTC 2
- swap_total: 3897
osfinger virtual tulokset:
- osfinger: Ubuntu-22.04
- virtual: VirtualBox
  - Ei näissä tuloksissa ole mitään analysoitavaa

## References

Karvinen 2023: Infra as Code 2023 - Palvelinten Hallinta 2023 syksy https://terokarvinen.com/2023/configuration-management-2023-autumn/
Karvinen 2023: Install Debian on Virtualbox - Updated 2023 https://terokarvinen.com/2021/install-debian-on-virtualbox/
Karvinen 2023: Create a Web Page Using Github https://terokarvinen.com/2023/create-a-web-page-using-github/
Karvinen 2023: Run Salt Command Locally https://terokarvinen.com/2021/salt-run-command-locally/
KodeKloud: Missing Dependencies Python Core / win32api https://kodekloud.com/community/t/missing-dependencies-python-core-win32api/215281
Xubuntu: Download Xubuntu https://xubuntu.org/download/
Index of /ubuntu-dvd/xubuntu/releases/22.04/release/ http://ftp.lysator.liu.se/ubuntu-dvd/xubuntu/releases/22.04/release/
Kumar 2023: How to Install VirtualBox Guest Additions on Ubuntu 22.04 https://www.linuxtechi.com/install-virtualbox-guest-additions-on-ubuntu/?utm_content=cmp-true
Wikipedia: Idempotenssi https://fi.wikipedia.org/wiki/Idempotenssi
