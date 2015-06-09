-   WstÄ™p
    -   Od autora
    -   Tylko "knitr"
-   Kabela 1.
-   PDF, markdown, HTML, MsWord i dalej
-   Opis argumentĂłw funkcji **kable**
-   PrzykĹ‚adowy zbiĂłr danych
-   DziaĹ‚anie argumentĂłw funkcji na przykĹ‚adzie tabeli w formacie
    "*markdown*"
    -   Ustawienia domyĹ›lne kable
    -   Bez nazwy wierszy
    -   ZaokrÄ…glenie do *2 cyfry* po przecinku
    -   WyrĂłwnanie do lewej
    -   Kombinacja wyrĂłwnaĹ„ i zaokrÄ…gleĹ„
-   Uwagi koĹ„cowe

WstÄ™p
======

Od autora
---------

Znalezienie sposobu na umieszczenie tabel z wynikami z R w raporcie
generowanym przy uĹĽyciu *knitr* zajÄ™Ĺ‚o mi bardzo duĹĽu czasu i sporo
nerwĂłw. Dlatego, ĹĽeby nikt nie musiaĹ‚ powtarzaÄ‡ mojej drogi przez
mÄ™ki, publikujÄ™ niniejszy krĂłtki przewodnik po tabelach w dokumentach
rmarkdown.

Tylko "knitr"
-------------

Klasyczny, tradycyjny sposĂłb wstawiania tabel do dokumentĂłw
generowanych przez *knitr* polega na zastosowaniu funkcji **xtable** z
pakietu *xtable*. Nie bÄ™dÄ™ o tym mĂłwiĹ‚ z kilku powodĂłw, przy czym
wymieniÄ™ tylko jeden wcale nie najwaĹĽniejszy. OtĂłĹĽ nie omĂłwiÄ™
dziaĹ‚ania funkcji **xtable** poniewaĹĽ nie pochodzi ona z pakietu
*knitr*. Jest czymĹ› zewnÄ™trznym, dodatkowym, i jak siÄ™ zaraz okaĹĽe,
niepotrzebnym (chyba, ĹĽe mamy jekieĹ› bardzo specyficzne wymagania
dotyczÄ…ce tabel). Pakiet *knitr* sam bardzo dobrze radzi sobie z
wiÄ™kszoĹ›ciÄ… tabel.

Kabela 1.
=========

W dalszej czÄ™Ĺ›ci tegp dokumentu znajdujÄ… siÄ™ tabele wygenerowane
przy uĹĽyciu funkcji **kable** z pakietu *knitr*. To rozwiÄ…zanie nie
jest, o ile wiem, bardzo popularne. Przez lata wszyscy uczyli siÄ™
korzystania z funkcji **xtable** i do dzisiaj istnieje mnĂłstwo opisĂłw,
jak jej uĹĽywaÄ‡. Na **kable** natknÄ…Ĺ‚em siÄ™ wiÄ™c kiedyĹ›
przypadkiem, w trakcie jednej z moich licznych walk z tabelami. Od razu
przypadĹ‚a mi do gustu prostota tej funkcji, ktĂłra oczywiĹ›cie wiÄ…rze
siÄ™ z pewnymi ograniczeniami.

**kable** dziaĹ‚a trochÄ™ inaczej niĹĽ jej "pierwowzĂłw" **table**. Nie
generuje tabel z danych lecz "drukuje" gotowe dane do tabeli markdown.
Co waĹĽne **kable** wyĹ›wietla jedynie obiekty klasy "*data.frame*" lub
"*matrix*". To oznacza, ĹĽe aby przedstawiÄ‡ wynik naszych obliczeĹ„ w
tabeli musimy go sprowadziÄ‡ do jednej z tych dwĂłch klas.

PDF, markdown, HTML, MsWord i dalej
===================================

Jak wiadomo *knitr* daje moĹĽliwoĹ›Ä‡ tworzenia rĂłĹĽnego rodzaju
dokumentĂłw. Funkcja **kable** bez problemy umie siÄ™ do tego
dostosowaÄ‡. Niniejszy dokument zostaĹ‚ wygeerowany na podstawie jednego
pliku "Tabele\_markdown.Rmd" w czterech wersjach:

-   dokument html - "Tabele\_markdown.html"
-   dokument PDF - "Tabele\_markdown.pdf"
-   dokument md (markdown) - "Tabele\_markdown."
-   domument MSWord - "Tabele\_markdown.Rmd"

Taka sztuczka moĹĽe byÄ‡ przydatna, gdy wysyĹ‚amy nasz dokument w
rĂłĹĽne miejsca.

W "nagĹ‚Ăłwku" pliku "Tabele\_markdown.Rmd" znajduje siÄ™ opis formatĂłw
w jakich moĹĽemy z niego generowaÄ‡ dokumenty. Aby je "odpaliÄ‡"
wpisujemy w **KONSOLI R** (to waĹĽne) komendÄ™:
*rmarkdown::render("Tabele\_rmarkdown.Rmd", "...")*. W miejsce trzech
kropek wpisujemy po kolei odpowiednio (zachowujÄ…c cudzysĹ‚Ăłw):

-   word\_document
-   pdf\_document
-   md\_document
-   html\_document

W ten sposĂłb otrzymujemy 4 rĂłĹĽne dokumenty z 4 rĂłĹĽnymi
formatowaniami tabel. Teoretycznie teĹĽ podaÄ‡ R komendÄ™
*rmarkdown::render("Tabele\_rmarkdown.Rmd", "all")* i w ten sposĂłb
wygenerowaÄ‡ wszystkie dokumenty jednoczĹ›nie, ale niestety u mnie to
nie dziaĹ‚a.

OczywiĹ›cie nie ma koniecznoĹ›ci generowania wszyskiego na raz. Zawsze
moĹĽna sobie wybrac jeden dokument.

Opis argumentĂłw funkcji **kable**
==================================

*kable(x, format, digits = getOption("digits"), row.names = NA, align,
output = TRUE, ...)*

-   **x** - obiekt R (macierz lub ramka danych), ktĂłry chcemy
    wyĹ›wietliÄ‡ jako tabelÄ™ w naszym dokumencie
-   **format** - obiekt typu *charakter*; moĹĽna wybraÄ‡ nastÄ™pujÄ…ce
    wartoĹ›ci
    -   "latex" - dla dokumnetĂłw LaTeX
    -   "html" - dla dokumentĂłw html
    -   "markdown" - dla dokumntu markdown
    -   "pandoc" - dla dokumnetĂłw LaTeX  
    -   "rst" - teĹĽ dla dokumentĂłw word
-   **digits** - jak Ĺ‚atwo siÄ™ domyĹ›liÄ‡ chodzi o zaaokrÄ…glenia
    liczb (przekazywane do funkcji *round()*); moĹĽna wpisaÄ‡ jednÄ…
    cyfrÄ™ dla caĹ‚ej tabeli lub wektor liczb, aby zdefiniowaÄ‡ rĂłĹĽne
    zaokrÄ…glenia dla pposzczegĂłlnych kolumn
-   **row.names** - czy wyĹ›wietlaÄ‡ nazwy wierszy; TRUE / FALSE
-   **align** - wyrĂłwnanie tekstu w kolumanch; domyĹ›lnie liczby do
    prawej, a reszta do lewej
    -   "l" - do lewej;
    -   "c" - do Ĺ›rodka;
    -   "r" - do prawej;
-   **output** - czy wpisywaÄ‡ wynik do konsoli

PrzykĹ‚adowy zbiĂłr danych
==========================

    head(mtcars)

    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1

DziaĹ‚anie argumentĂłw funkcji na przykĹ‚adzie tabeli w formacie "*markdown*"
=============================================================================

uwaga !!! Funkcja wyĹ›wietli tabele tylko jeĹĽeli w ustawieniach bloku
kodu results='asis'

Ustawienia domyĹ›lne kable
--------------------------

    knitr::kable(head(mtcars,50), format = "markdown")

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="right">mpg</th>
<th align="right">cyl</th>
<th align="right">disp</th>
<th align="right">hp</th>
<th align="right">drat</th>
<th align="right">wt</th>
<th align="right">qsec</th>
<th align="right">vs</th>
<th align="right">am</th>
<th align="right">gear</th>
<th align="right">carb</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Mazda RX4</td>
<td align="right">21.0</td>
<td align="right">6</td>
<td align="right">160.0</td>
<td align="right">110</td>
<td align="right">3.90</td>
<td align="right">2.620</td>
<td align="right">16.46</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Mazda RX4 Wag</td>
<td align="right">21.0</td>
<td align="right">6</td>
<td align="right">160.0</td>
<td align="right">110</td>
<td align="right">3.90</td>
<td align="right">2.875</td>
<td align="right">17.02</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Datsun 710</td>
<td align="right">22.8</td>
<td align="right">4</td>
<td align="right">108.0</td>
<td align="right">93</td>
<td align="right">3.85</td>
<td align="right">2.320</td>
<td align="right">18.61</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="even">
<td align="left">Hornet 4 Drive</td>
<td align="right">21.4</td>
<td align="right">6</td>
<td align="right">258.0</td>
<td align="right">110</td>
<td align="right">3.08</td>
<td align="right">3.215</td>
<td align="right">19.44</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Hornet Sportabout</td>
<td align="right">18.7</td>
<td align="right">8</td>
<td align="right">360.0</td>
<td align="right">175</td>
<td align="right">3.15</td>
<td align="right">3.440</td>
<td align="right">17.02</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Valiant</td>
<td align="right">18.1</td>
<td align="right">6</td>
<td align="right">225.0</td>
<td align="right">105</td>
<td align="right">2.76</td>
<td align="right">3.460</td>
<td align="right">20.22</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Duster 360</td>
<td align="right">14.3</td>
<td align="right">8</td>
<td align="right">360.0</td>
<td align="right">245</td>
<td align="right">3.21</td>
<td align="right">3.570</td>
<td align="right">15.84</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Merc 240D</td>
<td align="right">24.4</td>
<td align="right">4</td>
<td align="right">146.7</td>
<td align="right">62</td>
<td align="right">3.69</td>
<td align="right">3.190</td>
<td align="right">20.00</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="left">Merc 230</td>
<td align="right">22.8</td>
<td align="right">4</td>
<td align="right">140.8</td>
<td align="right">95</td>
<td align="right">3.92</td>
<td align="right">3.150</td>
<td align="right">22.90</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Merc 280</td>
<td align="right">19.2</td>
<td align="right">6</td>
<td align="right">167.6</td>
<td align="right">123</td>
<td align="right">3.92</td>
<td align="right">3.440</td>
<td align="right">18.30</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Merc 280C</td>
<td align="right">17.8</td>
<td align="right">6</td>
<td align="right">167.6</td>
<td align="right">123</td>
<td align="right">3.92</td>
<td align="right">3.440</td>
<td align="right">18.90</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Merc 450SE</td>
<td align="right">16.4</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">4.070</td>
<td align="right">17.40</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="odd">
<td align="left">Merc 450SL</td>
<td align="right">17.3</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">3.730</td>
<td align="right">17.60</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="even">
<td align="left">Merc 450SLC</td>
<td align="right">15.2</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">3.780</td>
<td align="right">18.00</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="odd">
<td align="left">Cadillac Fleetwood</td>
<td align="right">10.4</td>
<td align="right">8</td>
<td align="right">472.0</td>
<td align="right">205</td>
<td align="right">2.93</td>
<td align="right">5.250</td>
<td align="right">17.98</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Lincoln Continental</td>
<td align="right">10.4</td>
<td align="right">8</td>
<td align="right">460.0</td>
<td align="right">215</td>
<td align="right">3.00</td>
<td align="right">5.424</td>
<td align="right">17.82</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Chrysler Imperial</td>
<td align="right">14.7</td>
<td align="right">8</td>
<td align="right">440.0</td>
<td align="right">230</td>
<td align="right">3.23</td>
<td align="right">5.345</td>
<td align="right">17.42</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Fiat 128</td>
<td align="right">32.4</td>
<td align="right">4</td>
<td align="right">78.7</td>
<td align="right">66</td>
<td align="right">4.08</td>
<td align="right">2.200</td>
<td align="right">19.47</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Honda Civic</td>
<td align="right">30.4</td>
<td align="right">4</td>
<td align="right">75.7</td>
<td align="right">52</td>
<td align="right">4.93</td>
<td align="right">1.615</td>
<td align="right">18.52</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Toyota Corolla</td>
<td align="right">33.9</td>
<td align="right">4</td>
<td align="right">71.1</td>
<td align="right">65</td>
<td align="right">4.22</td>
<td align="right">1.835</td>
<td align="right">19.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Toyota Corona</td>
<td align="right">21.5</td>
<td align="right">4</td>
<td align="right">120.1</td>
<td align="right">97</td>
<td align="right">3.70</td>
<td align="right">2.465</td>
<td align="right">20.01</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="even">
<td align="left">Dodge Challenger</td>
<td align="right">15.5</td>
<td align="right">8</td>
<td align="right">318.0</td>
<td align="right">150</td>
<td align="right">2.76</td>
<td align="right">3.520</td>
<td align="right">16.87</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="left">AMC Javelin</td>
<td align="right">15.2</td>
<td align="right">8</td>
<td align="right">304.0</td>
<td align="right">150</td>
<td align="right">3.15</td>
<td align="right">3.435</td>
<td align="right">17.30</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Camaro Z28</td>
<td align="right">13.3</td>
<td align="right">8</td>
<td align="right">350.0</td>
<td align="right">245</td>
<td align="right">3.73</td>
<td align="right">3.840</td>
<td align="right">15.41</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Pontiac Firebird</td>
<td align="right">19.2</td>
<td align="right">8</td>
<td align="right">400.0</td>
<td align="right">175</td>
<td align="right">3.08</td>
<td align="right">3.845</td>
<td align="right">17.05</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Fiat X1-9</td>
<td align="right">27.3</td>
<td align="right">4</td>
<td align="right">79.0</td>
<td align="right">66</td>
<td align="right">4.08</td>
<td align="right">1.935</td>
<td align="right">18.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Porsche 914-2</td>
<td align="right">26.0</td>
<td align="right">4</td>
<td align="right">120.3</td>
<td align="right">91</td>
<td align="right">4.43</td>
<td align="right">2.140</td>
<td align="right">16.70</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Lotus Europa</td>
<td align="right">30.4</td>
<td align="right">4</td>
<td align="right">95.1</td>
<td align="right">113</td>
<td align="right">3.77</td>
<td align="right">1.513</td>
<td align="right">16.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="left">Ford Pantera L</td>
<td align="right">15.8</td>
<td align="right">8</td>
<td align="right">351.0</td>
<td align="right">264</td>
<td align="right">4.22</td>
<td align="right">3.170</td>
<td align="right">14.50</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Ferrari Dino</td>
<td align="right">19.7</td>
<td align="right">6</td>
<td align="right">145.0</td>
<td align="right">175</td>
<td align="right">3.62</td>
<td align="right">2.770</td>
<td align="right">15.50</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">6</td>
</tr>
<tr class="odd">
<td align="left">Maserati Bora</td>
<td align="right">15.0</td>
<td align="right">8</td>
<td align="right">301.0</td>
<td align="right">335</td>
<td align="right">3.54</td>
<td align="right">3.570</td>
<td align="right">14.60</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">8</td>
</tr>
<tr class="even">
<td align="left">Volvo 142E</td>
<td align="right">21.4</td>
<td align="right">4</td>
<td align="right">121.0</td>
<td align="right">109</td>
<td align="right">4.11</td>
<td align="right">2.780</td>
<td align="right">18.60</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
</tbody>
</table>

Bez nazwy wierszy
-----------------

    knitr::kable(head(mtcars,50), format = "markdown", row.names = FALSE)

<table>
<thead>
<tr class="header">
<th align="right">mpg</th>
<th align="right">cyl</th>
<th align="right">disp</th>
<th align="right">hp</th>
<th align="right">drat</th>
<th align="right">wt</th>
<th align="right">qsec</th>
<th align="right">vs</th>
<th align="right">am</th>
<th align="right">gear</th>
<th align="right">carb</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="right">21.0</td>
<td align="right">6</td>
<td align="right">160.0</td>
<td align="right">110</td>
<td align="right">3.90</td>
<td align="right">2.620</td>
<td align="right">16.46</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="right">21.0</td>
<td align="right">6</td>
<td align="right">160.0</td>
<td align="right">110</td>
<td align="right">3.90</td>
<td align="right">2.875</td>
<td align="right">17.02</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="right">22.8</td>
<td align="right">4</td>
<td align="right">108.0</td>
<td align="right">93</td>
<td align="right">3.85</td>
<td align="right">2.320</td>
<td align="right">18.61</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="even">
<td align="right">21.4</td>
<td align="right">6</td>
<td align="right">258.0</td>
<td align="right">110</td>
<td align="right">3.08</td>
<td align="right">3.215</td>
<td align="right">19.44</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="right">18.7</td>
<td align="right">8</td>
<td align="right">360.0</td>
<td align="right">175</td>
<td align="right">3.15</td>
<td align="right">3.440</td>
<td align="right">17.02</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="right">18.1</td>
<td align="right">6</td>
<td align="right">225.0</td>
<td align="right">105</td>
<td align="right">2.76</td>
<td align="right">3.460</td>
<td align="right">20.22</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="right">14.3</td>
<td align="right">8</td>
<td align="right">360.0</td>
<td align="right">245</td>
<td align="right">3.21</td>
<td align="right">3.570</td>
<td align="right">15.84</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="right">24.4</td>
<td align="right">4</td>
<td align="right">146.7</td>
<td align="right">62</td>
<td align="right">3.69</td>
<td align="right">3.190</td>
<td align="right">20.00</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="right">22.8</td>
<td align="right">4</td>
<td align="right">140.8</td>
<td align="right">95</td>
<td align="right">3.92</td>
<td align="right">3.150</td>
<td align="right">22.90</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="right">19.2</td>
<td align="right">6</td>
<td align="right">167.6</td>
<td align="right">123</td>
<td align="right">3.92</td>
<td align="right">3.440</td>
<td align="right">18.30</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="right">17.8</td>
<td align="right">6</td>
<td align="right">167.6</td>
<td align="right">123</td>
<td align="right">3.92</td>
<td align="right">3.440</td>
<td align="right">18.90</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="right">16.4</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">4.070</td>
<td align="right">17.40</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="odd">
<td align="right">17.3</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">3.730</td>
<td align="right">17.60</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="even">
<td align="right">15.2</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">3.780</td>
<td align="right">18.00</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="odd">
<td align="right">10.4</td>
<td align="right">8</td>
<td align="right">472.0</td>
<td align="right">205</td>
<td align="right">2.93</td>
<td align="right">5.250</td>
<td align="right">17.98</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="right">10.4</td>
<td align="right">8</td>
<td align="right">460.0</td>
<td align="right">215</td>
<td align="right">3.00</td>
<td align="right">5.424</td>
<td align="right">17.82</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="right">14.7</td>
<td align="right">8</td>
<td align="right">440.0</td>
<td align="right">230</td>
<td align="right">3.23</td>
<td align="right">5.345</td>
<td align="right">17.42</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="right">32.4</td>
<td align="right">4</td>
<td align="right">78.7</td>
<td align="right">66</td>
<td align="right">4.08</td>
<td align="right">2.200</td>
<td align="right">19.47</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="right">30.4</td>
<td align="right">4</td>
<td align="right">75.7</td>
<td align="right">52</td>
<td align="right">4.93</td>
<td align="right">1.615</td>
<td align="right">18.52</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="right">33.9</td>
<td align="right">4</td>
<td align="right">71.1</td>
<td align="right">65</td>
<td align="right">4.22</td>
<td align="right">1.835</td>
<td align="right">19.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="right">21.5</td>
<td align="right">4</td>
<td align="right">120.1</td>
<td align="right">97</td>
<td align="right">3.70</td>
<td align="right">2.465</td>
<td align="right">20.01</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="even">
<td align="right">15.5</td>
<td align="right">8</td>
<td align="right">318.0</td>
<td align="right">150</td>
<td align="right">2.76</td>
<td align="right">3.520</td>
<td align="right">16.87</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="right">15.2</td>
<td align="right">8</td>
<td align="right">304.0</td>
<td align="right">150</td>
<td align="right">3.15</td>
<td align="right">3.435</td>
<td align="right">17.30</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="right">13.3</td>
<td align="right">8</td>
<td align="right">350.0</td>
<td align="right">245</td>
<td align="right">3.73</td>
<td align="right">3.840</td>
<td align="right">15.41</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="right">19.2</td>
<td align="right">8</td>
<td align="right">400.0</td>
<td align="right">175</td>
<td align="right">3.08</td>
<td align="right">3.845</td>
<td align="right">17.05</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="right">27.3</td>
<td align="right">4</td>
<td align="right">79.0</td>
<td align="right">66</td>
<td align="right">4.08</td>
<td align="right">1.935</td>
<td align="right">18.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="right">26.0</td>
<td align="right">4</td>
<td align="right">120.3</td>
<td align="right">91</td>
<td align="right">4.43</td>
<td align="right">2.140</td>
<td align="right">16.70</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="right">30.4</td>
<td align="right">4</td>
<td align="right">95.1</td>
<td align="right">113</td>
<td align="right">3.77</td>
<td align="right">1.513</td>
<td align="right">16.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="right">15.8</td>
<td align="right">8</td>
<td align="right">351.0</td>
<td align="right">264</td>
<td align="right">4.22</td>
<td align="right">3.170</td>
<td align="right">14.50</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="right">19.7</td>
<td align="right">6</td>
<td align="right">145.0</td>
<td align="right">175</td>
<td align="right">3.62</td>
<td align="right">2.770</td>
<td align="right">15.50</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">6</td>
</tr>
<tr class="odd">
<td align="right">15.0</td>
<td align="right">8</td>
<td align="right">301.0</td>
<td align="right">335</td>
<td align="right">3.54</td>
<td align="right">3.570</td>
<td align="right">14.60</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">8</td>
</tr>
<tr class="even">
<td align="right">21.4</td>
<td align="right">4</td>
<td align="right">121.0</td>
<td align="right">109</td>
<td align="right">4.11</td>
<td align="right">2.780</td>
<td align="right">18.60</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
</tbody>
</table>

ZaokrÄ…glenie do *2 cyfry* po przecinku
---------------------------------------

     knitr:: kable( head(mtcars,50) , format ="markdown", digits=2 )

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="right">mpg</th>
<th align="right">cyl</th>
<th align="right">disp</th>
<th align="right">hp</th>
<th align="right">drat</th>
<th align="right">wt</th>
<th align="right">qsec</th>
<th align="right">vs</th>
<th align="right">am</th>
<th align="right">gear</th>
<th align="right">carb</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Mazda RX4</td>
<td align="right">21.0</td>
<td align="right">6</td>
<td align="right">160.0</td>
<td align="right">110</td>
<td align="right">3.90</td>
<td align="right">2.62</td>
<td align="right">16.46</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Mazda RX4 Wag</td>
<td align="right">21.0</td>
<td align="right">6</td>
<td align="right">160.0</td>
<td align="right">110</td>
<td align="right">3.90</td>
<td align="right">2.88</td>
<td align="right">17.02</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Datsun 710</td>
<td align="right">22.8</td>
<td align="right">4</td>
<td align="right">108.0</td>
<td align="right">93</td>
<td align="right">3.85</td>
<td align="right">2.32</td>
<td align="right">18.61</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="even">
<td align="left">Hornet 4 Drive</td>
<td align="right">21.4</td>
<td align="right">6</td>
<td align="right">258.0</td>
<td align="right">110</td>
<td align="right">3.08</td>
<td align="right">3.21</td>
<td align="right">19.44</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Hornet Sportabout</td>
<td align="right">18.7</td>
<td align="right">8</td>
<td align="right">360.0</td>
<td align="right">175</td>
<td align="right">3.15</td>
<td align="right">3.44</td>
<td align="right">17.02</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Valiant</td>
<td align="right">18.1</td>
<td align="right">6</td>
<td align="right">225.0</td>
<td align="right">105</td>
<td align="right">2.76</td>
<td align="right">3.46</td>
<td align="right">20.22</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Duster 360</td>
<td align="right">14.3</td>
<td align="right">8</td>
<td align="right">360.0</td>
<td align="right">245</td>
<td align="right">3.21</td>
<td align="right">3.57</td>
<td align="right">15.84</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Merc 240D</td>
<td align="right">24.4</td>
<td align="right">4</td>
<td align="right">146.7</td>
<td align="right">62</td>
<td align="right">3.69</td>
<td align="right">3.19</td>
<td align="right">20.00</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="left">Merc 230</td>
<td align="right">22.8</td>
<td align="right">4</td>
<td align="right">140.8</td>
<td align="right">95</td>
<td align="right">3.92</td>
<td align="right">3.15</td>
<td align="right">22.90</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Merc 280</td>
<td align="right">19.2</td>
<td align="right">6</td>
<td align="right">167.6</td>
<td align="right">123</td>
<td align="right">3.92</td>
<td align="right">3.44</td>
<td align="right">18.30</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Merc 280C</td>
<td align="right">17.8</td>
<td align="right">6</td>
<td align="right">167.6</td>
<td align="right">123</td>
<td align="right">3.92</td>
<td align="right">3.44</td>
<td align="right">18.90</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">4</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Merc 450SE</td>
<td align="right">16.4</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">4.07</td>
<td align="right">17.40</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="odd">
<td align="left">Merc 450SL</td>
<td align="right">17.3</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">3.73</td>
<td align="right">17.60</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="even">
<td align="left">Merc 450SLC</td>
<td align="right">15.2</td>
<td align="right">8</td>
<td align="right">275.8</td>
<td align="right">180</td>
<td align="right">3.07</td>
<td align="right">3.78</td>
<td align="right">18.00</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">3</td>
</tr>
<tr class="odd">
<td align="left">Cadillac Fleetwood</td>
<td align="right">10.4</td>
<td align="right">8</td>
<td align="right">472.0</td>
<td align="right">205</td>
<td align="right">2.93</td>
<td align="right">5.25</td>
<td align="right">17.98</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Lincoln Continental</td>
<td align="right">10.4</td>
<td align="right">8</td>
<td align="right">460.0</td>
<td align="right">215</td>
<td align="right">3.00</td>
<td align="right">5.42</td>
<td align="right">17.82</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Chrysler Imperial</td>
<td align="right">14.7</td>
<td align="right">8</td>
<td align="right">440.0</td>
<td align="right">230</td>
<td align="right">3.23</td>
<td align="right">5.34</td>
<td align="right">17.42</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Fiat 128</td>
<td align="right">32.4</td>
<td align="right">4</td>
<td align="right">78.7</td>
<td align="right">66</td>
<td align="right">4.08</td>
<td align="right">2.20</td>
<td align="right">19.47</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Honda Civic</td>
<td align="right">30.4</td>
<td align="right">4</td>
<td align="right">75.7</td>
<td align="right">52</td>
<td align="right">4.93</td>
<td align="right">1.62</td>
<td align="right">18.52</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Toyota Corolla</td>
<td align="right">33.9</td>
<td align="right">4</td>
<td align="right">71.1</td>
<td align="right">65</td>
<td align="right">4.22</td>
<td align="right">1.84</td>
<td align="right">19.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Toyota Corona</td>
<td align="right">21.5</td>
<td align="right">4</td>
<td align="right">120.1</td>
<td align="right">97</td>
<td align="right">3.70</td>
<td align="right">2.46</td>
<td align="right">20.01</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">1</td>
</tr>
<tr class="even">
<td align="left">Dodge Challenger</td>
<td align="right">15.5</td>
<td align="right">8</td>
<td align="right">318.0</td>
<td align="right">150</td>
<td align="right">2.76</td>
<td align="right">3.52</td>
<td align="right">16.87</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="left">AMC Javelin</td>
<td align="right">15.2</td>
<td align="right">8</td>
<td align="right">304.0</td>
<td align="right">150</td>
<td align="right">3.15</td>
<td align="right">3.44</td>
<td align="right">17.30</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Camaro Z28</td>
<td align="right">13.3</td>
<td align="right">8</td>
<td align="right">350.0</td>
<td align="right">245</td>
<td align="right">3.73</td>
<td align="right">3.84</td>
<td align="right">15.41</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">4</td>
</tr>
<tr class="odd">
<td align="left">Pontiac Firebird</td>
<td align="right">19.2</td>
<td align="right">8</td>
<td align="right">400.0</td>
<td align="right">175</td>
<td align="right">3.08</td>
<td align="right">3.85</td>
<td align="right">17.05</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Fiat X1-9</td>
<td align="right">27.3</td>
<td align="right">4</td>
<td align="right">79.0</td>
<td align="right">66</td>
<td align="right">4.08</td>
<td align="right">1.94</td>
<td align="right">18.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">1</td>
</tr>
<tr class="odd">
<td align="left">Porsche 914-2</td>
<td align="right">26.0</td>
<td align="right">4</td>
<td align="right">120.3</td>
<td align="right">91</td>
<td align="right">4.43</td>
<td align="right">2.14</td>
<td align="right">16.70</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">2</td>
</tr>
<tr class="even">
<td align="left">Lotus Europa</td>
<td align="right">30.4</td>
<td align="right">4</td>
<td align="right">95.1</td>
<td align="right">113</td>
<td align="right">3.77</td>
<td align="right">1.51</td>
<td align="right">16.90</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">2</td>
</tr>
<tr class="odd">
<td align="left">Ford Pantera L</td>
<td align="right">15.8</td>
<td align="right">8</td>
<td align="right">351.0</td>
<td align="right">264</td>
<td align="right">4.22</td>
<td align="right">3.17</td>
<td align="right">14.50</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">4</td>
</tr>
<tr class="even">
<td align="left">Ferrari Dino</td>
<td align="right">19.7</td>
<td align="right">6</td>
<td align="right">145.0</td>
<td align="right">175</td>
<td align="right">3.62</td>
<td align="right">2.77</td>
<td align="right">15.50</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">6</td>
</tr>
<tr class="odd">
<td align="left">Maserati Bora</td>
<td align="right">15.0</td>
<td align="right">8</td>
<td align="right">301.0</td>
<td align="right">335</td>
<td align="right">3.54</td>
<td align="right">3.57</td>
<td align="right">14.60</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="right">5</td>
<td align="right">8</td>
</tr>
<tr class="even">
<td align="left">Volvo 142E</td>
<td align="right">21.4</td>
<td align="right">4</td>
<td align="right">121.0</td>
<td align="right">109</td>
<td align="right">4.11</td>
<td align="right">2.78</td>
<td align="right">18.60</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="right">4</td>
<td align="right">2</td>
</tr>
</tbody>
</table>

WyrĂłwnanie do lewej
--------------------

    knitr:: kable( head(mtcars,50), format ="markdown", align = "l")

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">mpg</th>
<th align="left">cyl</th>
<th align="left">disp</th>
<th align="left">hp</th>
<th align="left">drat</th>
<th align="left">wt</th>
<th align="left">qsec</th>
<th align="left">vs</th>
<th align="left">am</th>
<th align="left">gear</th>
<th align="left">carb</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Mazda RX4</td>
<td align="left">21.0</td>
<td align="left">6</td>
<td align="left">160.0</td>
<td align="left">110</td>
<td align="left">3.90</td>
<td align="left">2.620</td>
<td align="left">16.46</td>
<td align="left">0</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Mazda RX4 Wag</td>
<td align="left">21.0</td>
<td align="left">6</td>
<td align="left">160.0</td>
<td align="left">110</td>
<td align="left">3.90</td>
<td align="left">2.875</td>
<td align="left">17.02</td>
<td align="left">0</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Datsun 710</td>
<td align="left">22.8</td>
<td align="left">4</td>
<td align="left">108.0</td>
<td align="left">93</td>
<td align="left">3.85</td>
<td align="left">2.320</td>
<td align="left">18.61</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">Hornet 4 Drive</td>
<td align="left">21.4</td>
<td align="left">6</td>
<td align="left">258.0</td>
<td align="left">110</td>
<td align="left">3.08</td>
<td align="left">3.215</td>
<td align="left">19.44</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Hornet Sportabout</td>
<td align="left">18.7</td>
<td align="left">8</td>
<td align="left">360.0</td>
<td align="left">175</td>
<td align="left">3.15</td>
<td align="left">3.440</td>
<td align="left">17.02</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Valiant</td>
<td align="left">18.1</td>
<td align="left">6</td>
<td align="left">225.0</td>
<td align="left">105</td>
<td align="left">2.76</td>
<td align="left">3.460</td>
<td align="left">20.22</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Duster 360</td>
<td align="left">14.3</td>
<td align="left">8</td>
<td align="left">360.0</td>
<td align="left">245</td>
<td align="left">3.21</td>
<td align="left">3.570</td>
<td align="left">15.84</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Merc 240D</td>
<td align="left">24.4</td>
<td align="left">4</td>
<td align="left">146.7</td>
<td align="left">62</td>
<td align="left">3.69</td>
<td align="left">3.190</td>
<td align="left">20.00</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">4</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">Merc 230</td>
<td align="left">22.8</td>
<td align="left">4</td>
<td align="left">140.8</td>
<td align="left">95</td>
<td align="left">3.92</td>
<td align="left">3.150</td>
<td align="left">22.90</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">4</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Merc 280</td>
<td align="left">19.2</td>
<td align="left">6</td>
<td align="left">167.6</td>
<td align="left">123</td>
<td align="left">3.92</td>
<td align="left">3.440</td>
<td align="left">18.30</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">4</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Merc 280C</td>
<td align="left">17.8</td>
<td align="left">6</td>
<td align="left">167.6</td>
<td align="left">123</td>
<td align="left">3.92</td>
<td align="left">3.440</td>
<td align="left">18.90</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">4</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Merc 450SE</td>
<td align="left">16.4</td>
<td align="left">8</td>
<td align="left">275.8</td>
<td align="left">180</td>
<td align="left">3.07</td>
<td align="left">4.070</td>
<td align="left">17.40</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">3</td>
</tr>
<tr class="odd">
<td align="left">Merc 450SL</td>
<td align="left">17.3</td>
<td align="left">8</td>
<td align="left">275.8</td>
<td align="left">180</td>
<td align="left">3.07</td>
<td align="left">3.730</td>
<td align="left">17.60</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">3</td>
</tr>
<tr class="even">
<td align="left">Merc 450SLC</td>
<td align="left">15.2</td>
<td align="left">8</td>
<td align="left">275.8</td>
<td align="left">180</td>
<td align="left">3.07</td>
<td align="left">3.780</td>
<td align="left">18.00</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">3</td>
</tr>
<tr class="odd">
<td align="left">Cadillac Fleetwood</td>
<td align="left">10.4</td>
<td align="left">8</td>
<td align="left">472.0</td>
<td align="left">205</td>
<td align="left">2.93</td>
<td align="left">5.250</td>
<td align="left">17.98</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Lincoln Continental</td>
<td align="left">10.4</td>
<td align="left">8</td>
<td align="left">460.0</td>
<td align="left">215</td>
<td align="left">3.00</td>
<td align="left">5.424</td>
<td align="left">17.82</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Chrysler Imperial</td>
<td align="left">14.7</td>
<td align="left">8</td>
<td align="left">440.0</td>
<td align="left">230</td>
<td align="left">3.23</td>
<td align="left">5.345</td>
<td align="left">17.42</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Fiat 128</td>
<td align="left">32.4</td>
<td align="left">4</td>
<td align="left">78.7</td>
<td align="left">66</td>
<td align="left">4.08</td>
<td align="left">2.200</td>
<td align="left">19.47</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Honda Civic</td>
<td align="left">30.4</td>
<td align="left">4</td>
<td align="left">75.7</td>
<td align="left">52</td>
<td align="left">4.93</td>
<td align="left">1.615</td>
<td align="left">18.52</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Toyota Corolla</td>
<td align="left">33.9</td>
<td align="left">4</td>
<td align="left">71.1</td>
<td align="left">65</td>
<td align="left">4.22</td>
<td align="left">1.835</td>
<td align="left">19.90</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Toyota Corona</td>
<td align="left">21.5</td>
<td align="left">4</td>
<td align="left">120.1</td>
<td align="left">97</td>
<td align="left">3.70</td>
<td align="left">2.465</td>
<td align="left">20.01</td>
<td align="left">1</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">Dodge Challenger</td>
<td align="left">15.5</td>
<td align="left">8</td>
<td align="left">318.0</td>
<td align="left">150</td>
<td align="left">2.76</td>
<td align="left">3.520</td>
<td align="left">16.87</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">AMC Javelin</td>
<td align="left">15.2</td>
<td align="left">8</td>
<td align="left">304.0</td>
<td align="left">150</td>
<td align="left">3.15</td>
<td align="left">3.435</td>
<td align="left">17.30</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Camaro Z28</td>
<td align="left">13.3</td>
<td align="left">8</td>
<td align="left">350.0</td>
<td align="left">245</td>
<td align="left">3.73</td>
<td align="left">3.840</td>
<td align="left">15.41</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Pontiac Firebird</td>
<td align="left">19.2</td>
<td align="left">8</td>
<td align="left">400.0</td>
<td align="left">175</td>
<td align="left">3.08</td>
<td align="left">3.845</td>
<td align="left">17.05</td>
<td align="left">0</td>
<td align="left">0</td>
<td align="left">3</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Fiat X1-9</td>
<td align="left">27.3</td>
<td align="left">4</td>
<td align="left">79.0</td>
<td align="left">66</td>
<td align="left">4.08</td>
<td align="left">1.935</td>
<td align="left">18.90</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Porsche 914-2</td>
<td align="left">26.0</td>
<td align="left">4</td>
<td align="left">120.3</td>
<td align="left">91</td>
<td align="left">4.43</td>
<td align="left">2.140</td>
<td align="left">16.70</td>
<td align="left">0</td>
<td align="left">1</td>
<td align="left">5</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Lotus Europa</td>
<td align="left">30.4</td>
<td align="left">4</td>
<td align="left">95.1</td>
<td align="left">113</td>
<td align="left">3.77</td>
<td align="left">1.513</td>
<td align="left">16.90</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">5</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">Ford Pantera L</td>
<td align="left">15.8</td>
<td align="left">8</td>
<td align="left">351.0</td>
<td align="left">264</td>
<td align="left">4.22</td>
<td align="left">3.170</td>
<td align="left">14.50</td>
<td align="left">0</td>
<td align="left">1</td>
<td align="left">5</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Ferrari Dino</td>
<td align="left">19.7</td>
<td align="left">6</td>
<td align="left">145.0</td>
<td align="left">175</td>
<td align="left">3.62</td>
<td align="left">2.770</td>
<td align="left">15.50</td>
<td align="left">0</td>
<td align="left">1</td>
<td align="left">5</td>
<td align="left">6</td>
</tr>
<tr class="odd">
<td align="left">Maserati Bora</td>
<td align="left">15.0</td>
<td align="left">8</td>
<td align="left">301.0</td>
<td align="left">335</td>
<td align="left">3.54</td>
<td align="left">3.570</td>
<td align="left">14.60</td>
<td align="left">0</td>
<td align="left">1</td>
<td align="left">5</td>
<td align="left">8</td>
</tr>
<tr class="even">
<td align="left">Volvo 142E</td>
<td align="left">21.4</td>
<td align="left">4</td>
<td align="left">121.0</td>
<td align="left">109</td>
<td align="left">4.11</td>
<td align="left">2.780</td>
<td align="left">18.60</td>
<td align="left">1</td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left">2</td>
</tr>
</tbody>
</table>

Kombinacja wyrĂłwnaĹ„ i zaokrÄ…gleĹ„
------------------------------------

    knitr:: kable( head(mtcars,50), format ="markdown", 
                   align = c( "l","r","l","r","l","r","l","r","l","r","l"),
                   , digits=c(2,0,0,0,1,1,2,2,2,2,2) )

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">mpg</th>
<th align="right">cyl</th>
<th align="left">disp</th>
<th align="right">hp</th>
<th align="left">drat</th>
<th align="right">wt</th>
<th align="left">qsec</th>
<th align="right">vs</th>
<th align="left">am</th>
<th align="right">gear</th>
<th align="left">carb</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Mazda RX4</td>
<td align="left">21.0</td>
<td align="right">6</td>
<td align="left">160</td>
<td align="right">110</td>
<td align="left">3.9</td>
<td align="right">2.6</td>
<td align="left">16.46</td>
<td align="right">0</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Mazda RX4 Wag</td>
<td align="left">21.0</td>
<td align="right">6</td>
<td align="left">160</td>
<td align="right">110</td>
<td align="left">3.9</td>
<td align="right">2.9</td>
<td align="left">17.02</td>
<td align="right">0</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Datsun 710</td>
<td align="left">22.8</td>
<td align="right">4</td>
<td align="left">108</td>
<td align="right">93</td>
<td align="left">3.8</td>
<td align="right">2.3</td>
<td align="left">18.61</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">Hornet 4 Drive</td>
<td align="left">21.4</td>
<td align="right">6</td>
<td align="left">258</td>
<td align="right">110</td>
<td align="left">3.1</td>
<td align="right">3.2</td>
<td align="left">19.44</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Hornet Sportabout</td>
<td align="left">18.7</td>
<td align="right">8</td>
<td align="left">360</td>
<td align="right">175</td>
<td align="left">3.1</td>
<td align="right">3.4</td>
<td align="left">17.02</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Valiant</td>
<td align="left">18.1</td>
<td align="right">6</td>
<td align="left">225</td>
<td align="right">105</td>
<td align="left">2.8</td>
<td align="right">3.5</td>
<td align="left">20.22</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Duster 360</td>
<td align="left">14.3</td>
<td align="right">8</td>
<td align="left">360</td>
<td align="right">245</td>
<td align="left">3.2</td>
<td align="right">3.6</td>
<td align="left">15.84</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Merc 240D</td>
<td align="left">24.4</td>
<td align="right">4</td>
<td align="left">147</td>
<td align="right">62</td>
<td align="left">3.7</td>
<td align="right">3.2</td>
<td align="left">20.00</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">4</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">Merc 230</td>
<td align="left">22.8</td>
<td align="right">4</td>
<td align="left">141</td>
<td align="right">95</td>
<td align="left">3.9</td>
<td align="right">3.1</td>
<td align="left">22.90</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">4</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Merc 280</td>
<td align="left">19.2</td>
<td align="right">6</td>
<td align="left">168</td>
<td align="right">123</td>
<td align="left">3.9</td>
<td align="right">3.4</td>
<td align="left">18.30</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">4</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Merc 280C</td>
<td align="left">17.8</td>
<td align="right">6</td>
<td align="left">168</td>
<td align="right">123</td>
<td align="left">3.9</td>
<td align="right">3.4</td>
<td align="left">18.90</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">4</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Merc 450SE</td>
<td align="left">16.4</td>
<td align="right">8</td>
<td align="left">276</td>
<td align="right">180</td>
<td align="left">3.1</td>
<td align="right">4.1</td>
<td align="left">17.40</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">3</td>
</tr>
<tr class="odd">
<td align="left">Merc 450SL</td>
<td align="left">17.3</td>
<td align="right">8</td>
<td align="left">276</td>
<td align="right">180</td>
<td align="left">3.1</td>
<td align="right">3.7</td>
<td align="left">17.60</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">3</td>
</tr>
<tr class="even">
<td align="left">Merc 450SLC</td>
<td align="left">15.2</td>
<td align="right">8</td>
<td align="left">276</td>
<td align="right">180</td>
<td align="left">3.1</td>
<td align="right">3.8</td>
<td align="left">18.00</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">3</td>
</tr>
<tr class="odd">
<td align="left">Cadillac Fleetwood</td>
<td align="left">10.4</td>
<td align="right">8</td>
<td align="left">472</td>
<td align="right">205</td>
<td align="left">2.9</td>
<td align="right">5.2</td>
<td align="left">17.98</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Lincoln Continental</td>
<td align="left">10.4</td>
<td align="right">8</td>
<td align="left">460</td>
<td align="right">215</td>
<td align="left">3.0</td>
<td align="right">5.4</td>
<td align="left">17.82</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Chrysler Imperial</td>
<td align="left">14.7</td>
<td align="right">8</td>
<td align="left">440</td>
<td align="right">230</td>
<td align="left">3.2</td>
<td align="right">5.3</td>
<td align="left">17.42</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Fiat 128</td>
<td align="left">32.4</td>
<td align="right">4</td>
<td align="left">79</td>
<td align="right">66</td>
<td align="left">4.1</td>
<td align="right">2.2</td>
<td align="left">19.47</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Honda Civic</td>
<td align="left">30.4</td>
<td align="right">4</td>
<td align="left">76</td>
<td align="right">52</td>
<td align="left">4.9</td>
<td align="right">1.6</td>
<td align="left">18.52</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Toyota Corolla</td>
<td align="left">33.9</td>
<td align="right">4</td>
<td align="left">71</td>
<td align="right">65</td>
<td align="left">4.2</td>
<td align="right">1.8</td>
<td align="left">19.90</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Toyota Corona</td>
<td align="left">21.5</td>
<td align="right">4</td>
<td align="left">120</td>
<td align="right">97</td>
<td align="left">3.7</td>
<td align="right">2.5</td>
<td align="left">20.01</td>
<td align="right">1</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">Dodge Challenger</td>
<td align="left">15.5</td>
<td align="right">8</td>
<td align="left">318</td>
<td align="right">150</td>
<td align="left">2.8</td>
<td align="right">3.5</td>
<td align="left">16.87</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">AMC Javelin</td>
<td align="left">15.2</td>
<td align="right">8</td>
<td align="left">304</td>
<td align="right">150</td>
<td align="left">3.1</td>
<td align="right">3.4</td>
<td align="left">17.30</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Camaro Z28</td>
<td align="left">13.3</td>
<td align="right">8</td>
<td align="left">350</td>
<td align="right">245</td>
<td align="left">3.7</td>
<td align="right">3.8</td>
<td align="left">15.41</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Pontiac Firebird</td>
<td align="left">19.2</td>
<td align="right">8</td>
<td align="left">400</td>
<td align="right">175</td>
<td align="left">3.1</td>
<td align="right">3.8</td>
<td align="left">17.05</td>
<td align="right">0</td>
<td align="left">0</td>
<td align="right">3</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Fiat X1-9</td>
<td align="left">27.3</td>
<td align="right">4</td>
<td align="left">79</td>
<td align="right">66</td>
<td align="left">4.1</td>
<td align="right">1.9</td>
<td align="left">18.90</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">1</td>
</tr>
<tr class="odd">
<td align="left">Porsche 914-2</td>
<td align="left">26.0</td>
<td align="right">4</td>
<td align="left">120</td>
<td align="right">91</td>
<td align="left">4.4</td>
<td align="right">2.1</td>
<td align="left">16.70</td>
<td align="right">0</td>
<td align="left">1</td>
<td align="right">5</td>
<td align="left">2</td>
</tr>
<tr class="even">
<td align="left">Lotus Europa</td>
<td align="left">30.4</td>
<td align="right">4</td>
<td align="left">95</td>
<td align="right">113</td>
<td align="left">3.8</td>
<td align="right">1.5</td>
<td align="left">16.90</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">5</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">Ford Pantera L</td>
<td align="left">15.8</td>
<td align="right">8</td>
<td align="left">351</td>
<td align="right">264</td>
<td align="left">4.2</td>
<td align="right">3.2</td>
<td align="left">14.50</td>
<td align="right">0</td>
<td align="left">1</td>
<td align="right">5</td>
<td align="left">4</td>
</tr>
<tr class="even">
<td align="left">Ferrari Dino</td>
<td align="left">19.7</td>
<td align="right">6</td>
<td align="left">145</td>
<td align="right">175</td>
<td align="left">3.6</td>
<td align="right">2.8</td>
<td align="left">15.50</td>
<td align="right">0</td>
<td align="left">1</td>
<td align="right">5</td>
<td align="left">6</td>
</tr>
<tr class="odd">
<td align="left">Maserati Bora</td>
<td align="left">15.0</td>
<td align="right">8</td>
<td align="left">301</td>
<td align="right">335</td>
<td align="left">3.5</td>
<td align="right">3.6</td>
<td align="left">14.60</td>
<td align="right">0</td>
<td align="left">1</td>
<td align="right">5</td>
<td align="left">8</td>
</tr>
<tr class="even">
<td align="left">Volvo 142E</td>
<td align="left">21.4</td>
<td align="right">4</td>
<td align="left">121</td>
<td align="right">109</td>
<td align="left">4.1</td>
<td align="right">2.8</td>
<td align="left">18.60</td>
<td align="right">1</td>
<td align="left">1</td>
<td align="right">4</td>
<td align="left">2</td>
</tr>
</tbody>
</table>

Uwagi koĹ„cowe
==============

W powyĹĽszych przykĹ‚adach nie dodano tutuĹ‚Ăłw do tabel. Jest to
sposodowane zastosowaniem formatu *markdown*. Ĺ»eby zosbaczyÄ‡, jak
dziaĹ‚a dodawania tytuĹ‚u na przykĹ‚adzie dokumentu PDF przejdĹş do
przykĹ‚adu

Aby zobaczyÄ‡, jak tworzyÄ‡ tabele w dokumnetach PDF generowanych
bezpoĹ›rednio z LaTeX bez udziaĹ‚u Rmarkdowna przejdĹş do pliku
[Tabela\_LaTeX/Tabela\_LaTeX.pdf](Tabela_LaTeX/Tabela_LaTeX.pdf)
