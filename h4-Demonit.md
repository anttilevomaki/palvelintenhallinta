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

## References
- Karvinen 2023: Infra as Code 2023 - Palvelinten Hallinta 2023 syksy https://terokarvinen.com/2023/configuration-management-2023-autumn/
- Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file
- VMware, Inc. 2023: Salt overview https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml
- VMware, Inc. 2023: Salt states https://docs.saltproject.io/salt/user-guide/en/latest/topics/states.html#state-modules
- Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh
- 
