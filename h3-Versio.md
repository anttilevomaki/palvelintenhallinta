# h3 Versio

Tein harjoituksen 2023-11-11. Työaseman prosessori: 11th Gen Intel(R) Core(TM) i5-11600K @ 3.90GHz 3.91 GHz, RAM: 16.0 GB, järjestelmä: Windows 10 Pro

### a) Online
Aluksi tein uuden varaston Githubiin Tero Karvisen ohjeilla. (https://terokarvinen.com/2023/create-a-web-page-using-github/) Annoin varastolle nimen winter. Lisäsin samalla myös readme-tiedoston sekä GNU General Public License 3 -lisenssin.
![](kuvat/h3-Versio/Capture2.PNG)

### b) Dolly
Avasin omalla koneella GitBashin ja loin uuden kansion nimellä github, jonne kloonaan winter-varaston Githubista. (Github 2023)
![](kuvat/h3-Versio/Capture3.PNG)

Varmistin Githubin ohjeiden mukaan, että omalla koneella ei ole ennenstään ssh-avainta. (Github 2023)

![](kuvat/h3-Versio/Capture4.PNG)

Tämän jälkeen loin ssh-avaimen Githubin ohjeiden mukaan. (https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

![](kuvat/h3-Versio/Capture6.PNG)

Sitten kopioin ssh-avaimen leikepöydälle...
![](kuvat/h3-Versio/Capture9.PNG)

...ja loin Githubissa uuden ssh-avainparin...
![](kuvat/h3-Versio/Capture10.PNG)

sekä authentication-, että signing-avaimeksi. (https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
![](kuvat/h3-Versio/Capture12.png)

Kloonausta varten kävin kopioimassa Githubista winter-varaston osoitteen.
![](kuvat/h3-Versio/Capture13.PNG)

Gitbashilla kloonasin varaston omalle koneelle.
![](kuvat/h3-Versio/Capture17.png)

Tein nanolla muutoksia readme-tiedostoon.

![](kuvat/h3-Versio/Capture24.PNG)

Komennolla git add . tallensin muutokset seuraavaa commitia varten. git commit -komennolla tallensin muutokset omalle koneelle. Commit messageksi laitoin "Add reverse thurst estimation to main view". Git pushilla työnsin muutokset Githubiin.
![](kuvat/h3-Versio/Capture22.PNG)

Kuten alla olevasta kuvasta näkyy, muutokset menivät läpi.
![](kuvat/h3-Versio/Capture23.PNG)

### (c Doh!
Tarkistin aluksi gitin statuksen. Up to date, nothing to commit. (https://www.atlassian.com/git/tutorials/undoing-changes/git-reset)
![](kuvat/h3-Versio/Capture25.PNG)

Tein tyhmän muutoksen readme-tiedostoon.
![](kuvat/h3-Versio/Capture26.PNG)

Uusi git status, muutoksia tehty readme-tiedostoon.
![](kuvat/h3-Versio/Capture27.PNG)

Annoin vielä git add . -komennon, jonka jälkeen uusi git status. Readme-tiedoston muutos odottaa committia. Git reset --hard -komennolla tuhosin muutokset, edellinen päivitys palasi voimaan ja uusi git status -tarkistus näytti, että ei ole enää päivittämistä odottavia muutoksia.
![](kuvat/h3-Versio/Capture30.PNG)

### (d Tukki
Pelkkä git commit -komento näytti kaikki kolme committia, mitkä varastoon on tehty.
![](kuvat/h3-Versio/Capture31.PNG)

Git commit --patch -komennolla tuli enemmän dataa, mm. muutosten sisällöstä ja tiedostoista, sekä koko GNU lisenssi.
![](kuvat/h3-Versio/Capture33.PNG)


## References
- Karvinen 2023: Infra as Code 2023 - Palvelinten Hallinta 2023 syksy https://terokarvinen.com/2023/configuration-management-2023-autumn/
- Karvinen 2023: Create a Web Page Using Github https://terokarvinen.com/2023/create-a-web-page-using-github/
- Github 2023: Cloning a repository  https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository
- Github 2023: Checking for existing SSH keys https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
- Github 2023: Generating a new SSH key and adding it to the ssh-agent https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- Github 2023: Adding a new SSH key to your GitHub account https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
- Atlassian 2023: Git reset https://www.atlassian.com/git/tutorials/undoing-changes/git-reset
