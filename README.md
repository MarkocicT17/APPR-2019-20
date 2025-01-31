# Analiza podatkov s programom R, 2019/20

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2019/20
test
* [![Shiny](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=shiny/APPR-2019-20/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=rstudio) RStudio

## Tematika
V tej projektni nalogi bom analizirala gradbeništvo v Sloveniji s pomočjo podatkov pridobljenih na spletni strani Statističnega urada Republike Slovenije(SURS). 

Pokazati želim, kako se ocena stanovanj in stavb različnih velikosti razlikujejo po občinah, statističnih regijah med leti 2008 do 2018 za določen tip investitorja(pravna ali fizična oseba). Podatke bom razvrstila glede na:

-vrednost gradnje glede na tip investitorja, tip stavbe, statistične regije, občine

-izdana gradbena dovoljenja za statistično regijo in občino glede na površino in prostornino, število stanovanj v stavbah)

-število dokončanih stanovanj na 1000 prebivalca

-število dokončanih stanovanj na kvadratni meter

-število dokončanih stanovanj glede na tip stavbe(ena ali več stanovanjska stavba in nestanovanjeske stavbe npr. poslovna, gostinska, kulturna)

### Tabele
1. TABELA Ocena stanovanj v gradnji in dokončanih stanovanj, Slovenija, letno (glede na površino, štveilo sob, investitor, na 1000 preb.)

2. TABELA Ocena dokončanih stanovanj - izbrani kazalniki, po statističnih regijah Slovenije, letno 

3. TABELA Ocena dokončanih stanovanj - izbrani kazalniki, po občinah Slovenije, letno

4. TABELA Ocena dokončanih stavb in stavb v gradnji ob koncu leta, Slovenija, letno (tip stavbe, tip gradbene aktivnosti-novogradnja, povečava, sprememba namembnosti, investitor)

5. TABELA Vrednost opravljenih gradbenih del [v EUR] po tipu gradbene aktivnosti in vrsti objektov, Slovenija, letno

6. TABELA Dovoljenja za gradnjo stavb: število stavb, njihova gradbena velikost in stanovanja v njih, glede na vrsto stavbe in vrsto investitorja, po statističnih regijah Slovenije, letno

7. TABELA Dovoljenja za gradnjo stavb: število stavb, njihova gradbena velikost in stanovanja v njih, glede na vrsto stavbe, po občinah Slovenije, letno    

Za nadgradnjo bi lahko svoje podatke primerjala s kakšno drugo tematiko npr. z izobrazbo ljudi, povprečnimi mesečnimi plačami v posamezni občini in statistični regiji.

### Povezave do tabel
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__05_19069_graditev_stan/1906901S.px/)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__05_19069_graditev_stan/1906910S.px/)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__05_19069_graditev_stan/1906911S.px/)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__05_19238_graditev_stavb/1923801S.px/)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__07_19198_vrednost_del/1919801S.px/)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__06_19707_dovoljenja/1970716S.px/)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__19_gradbenistvo__06_19707_dovoljenja/1970717S.px/)


## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `rgeos` - za podporo zemljevidom
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `tidyr` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-201819)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).
