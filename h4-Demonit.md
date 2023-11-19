# h4 Demonit

Tein harjoituksen 2023-19-11. Työaseman prosessori: 11th Gen Intel(R) Core(TM) i5-11600K @ 3.90GHz 3.91 GHz, RAM: 16.0 GB, järjestelmä: Windows 10 Pro

### x) Lue ja tiivistä
  - Salt Vagrant
    - YAML:ssa sisennyksellä on merkitystä, ja se on kaksi välilyöntiä
    - top-tiedosto määrittää, mitä tiloja ajetaan millekin orjalle
   
  - Salt overview
    - YAML on merkintäkieli, jonka tehtävänä on ottaa YAML-tietorakenne ja kääntää se Python-tietorakenteeksi Saltille
    - YAML:n kolme perustyyppiä ovat scalar, list ja dictionary
    - YAML on järjestetty lohkorakenteiksi
   
  - Salt states
    - Salt state ei vaadi tarkistusta, koska install state tarkistaa implisiittisesti paketin järjestelmän paketinhallinnasta
    - Tilatiedoston tilan määritelmässä on seuraavat osat: identifier, state, function, name, arguments
    - State treen salt states tulee kirjoittaa niin, että toinen kehittäjä voi nopeasti todeta salt states tarkoituksen
    - Koska joissakin ympäristöissä on satoja tilatiedostoja, jotka on kohdistettu tuhansiin orjiin, ei ole käytännöllistä ajaa jokaista tilaa erikseen ja kohdistaa sitten soveltuviin orjiin joka kerta
    - Itse asia tilan id:ksi, name arvoksi tulee automaattisesti sama

