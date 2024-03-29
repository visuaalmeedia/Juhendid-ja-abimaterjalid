# Juhendid ja abimaterjalid

## Sisukord

-   [Juhendid ja abimaterjalid](#juhendid-ja-abimaterjalid)
    -   [Sisukord](#sisukord)
    -   [Tundide korraldus](#tundide-korraldus)
        -   [Tunni alguse sissekanne](#tunni-alguse-sissekanne)
        -   [Tunni lõpus](#tunni-lõpus)
    -   [Git'i ja Githubi abi](#giti-ja-githubi-abi)
        -   [Peamised git'i käsud](#peamised-giti-käsud)
        -   [Githubi repo sisu muutmine VSC veebiversioonis](#githubi-repo-sisu-muutmine-vsc-veebiversioonis)
        -   [Võimalikud probleemid](#võimalikud-probleemid)
            -   [Git'cache kustutamine, kui tarvis midagi jälgimisest maha võtma](#gitcache-kustutamine-kui-tarvis-midagi-jälgimisest-maha-võtma)
            -   [.gitignore fail](#gitignore-fail)

## Tundide korraldus

Seda repositoorumi võiks pidada nagu tunni konspekti, ka muu oluline tasuks siia kirja panna, kas tundide kireldustesse või võib teha ka ühe README.md faili selle jaoks. Iga tunni kohta tuleb luua aga md-fail, millesse kirjuta tunni alguses alguse ja tunni lõpus lõpu meelestatus. Lisa tunni lõpus ka pikem kommentaar kogu tunni kohta.

**Sellised võiks olla tundide md-failid:**

### Tunni alguse sissekanne

Hinda 10-balli skaalal:

-   Tänane tuju
-   Huvi tunni vastu
-   Arusaamine aine eesmärkidest

### Tunni lõpus

Hinda 10-balli skaalal:

-   Tuju tunni lõpus
-   Huvi teema vastu tunni lõpus
-   Arusaamine tunni teemast tunni lõpuks
    Lisaks kirjuta vabas vormis, mis meeldis, mis ei meeldinud, millele võiks rohkem tähelepanu pöörata.

**Markdown failid nimetage alati nõnda – "tunni number-kuupäev-kuu.md"
**
Näide: [01-26-jaanuar.md](01-26-jaanuar.md)

## Git'i ja Githubi abi

Sageli juhtub kooli arvutites, et eelmine kasutaja ei ole oma Githubi kasutajat välja loginud. Sel juhul ei saa te oma githubi kontole terminali kaudu sisse. Esmalt logige ennast Visual Studio Code vasakul all nurgas oleva kasutaja ikkoni all oleva nupu kaudu välja, seejärel tehke terminalile igaks juhuks taaskäivitus ja seejärel logige sealt samast uuesti sisse.
![Gthub log out](img/vscodeuser.jpg)

Kui endiselt tekib probleeme proovige terminalis git'i kasutajanime muuta.

Kasutaja määramine kohalikult:  
`git config user.name "SinuNimi"`  
`git config user.email "SinuEpost@example.com"`

Vahel vaja kontrollida, kas masinas on seadistatud globaalne git'i kasutaja

Globaalse git'i kasutaja kontroll:  
`git config --global user.name`

Globaalse git'i kasutaja mahavõtmine:  
`git config --global --unset user.email`

Klobaalset kasutaja määramist arvutites, kus ka teised tööd teevad, pole vast mõistlik, kui just pärast kindlalt maha võtad.

Võid end autentida ka käsuga `gh auth login`, sel juhul peab olema installitud Github CLI

#### Kui ikka ei saa autenditud

Siin üks võimalik probleem: https://github.com/orgs/community/discussions/39141

### Peamised git'i käsud

Peamised git'käsud, mis tasub meie kursusel meelde jätta, on järgmised:  
Giti kloonimine oma masinasse:  
`git clone [sinurepositooriumi aadress]`  
Uuenduste allatõmbamine juba kloonitud reposse:  
`git pull`  
Tehtud muudatuste lisamine töökorraldusse:  
`git add .`  
Hetkeseisu salvestamine ja kommentaar tehtu kohta:  
`git commit -m "Kommentaar tehtud muudatuse kohta"`  
Muudatuste saatmine keskreposse:  
`git push`

### Githubi repo sisu muutmine VSC veebiversioonis

Githubi sisu on võimalik toimetada ka veebis. Eriti hea on seda teha Visual Studio Code veebiredigeerija kaudu. Selleks tuleb lihtsalt on repositooriumi aadressi ette lisada `https://vscode.dev/` nt siinse repositoorumi VSC veebiversioonis redigeerimiseks oleks: `https://vscode.dev/github.com/visuaalmeedia/Juhendid-ja-abimaterjalid`

### Võimalikud probleemid

Giti luues, kasutades käsklust `git init`luuakse suure tõenäosusega `master`"oks". Samas nt Github kasutab tänapäeval `main`nimelist oksa. Seega võiks selle muuta samuti `mainiks`. Võimalik on seadistada globaalselt kohalik git looma `main` oksa, või lihtsalt nimetada ümber.

Esimesel juhul on käsklus `git config --global init.defaultBranch <siia soovitav nimi>`  
Teisel juhul `git branch -m <siia soovitav nimi>`

Seejärel:

```bash
git init
git add .
git commit -m "Add existing project files to Git"
git remote add origin https://github.com/sinurepoaadress
git push -u -f origin main
```

#### Git'cache kustutamine, kui tarvis midagi jälgimisest maha võtma

git rm -r --cached .

#### .gitignore fail

Kui tahad kõik alamakataloogides sisalduvad teatud nimega folderid lisada gitignore faili: `**/node_modules/`
