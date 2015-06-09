# Krótki przewodnik po tabelach generowanych w markdown przy pomocy funkcji _kable_ z pakietu _knitr_ na podstawie danych z R
Zbyszek Marczewski  
Wtorek, 9 czerwca 2015 r.  

# Wstęp

## Od autora

Znalezienie sposobu na umieszczenie tabel z wynikami z R w raporcie generowanym przy użyciu _knitr_ zajęło mi bardzo dużu czasu i kosztowało mnie sporo nerwów. Dlatego, żeby nikt nie musiał powtarzać mojej drogi przez męki, publikuję niniejszy krótki przewodnik po tabelach generowanych w rmarkdown. 

## Tylko "knitr"

Klasyczny, tradycyjny sposób wstawiania tabel do dokumentów generowanych przez _knitr_ polega na zastosowaniu funkcji __xtable__ z pakietu _xtable_. Nie będę o tym mówił z kilku powodów, przy czym wymienię tylko jeden wcale nie najważniejszy. Otóż nie omówię działania funkcji  __xtable__ ponieważ nie pochodzi ona z pakietu _knitr_. Jest czymś zewnętrznym, dodatkowym, i jak się zaraz okaże, niepotrzebnym (chyba, że mamy jekieś bardzo specyficzne wymagania dotyczące tabel). Pakiet _knitr_ sam bardzo dobrze radzi sobie z większością tabel.

## Tabele "kable""

W dalszej części tego dokumentu znajdują się tabele wygenerowane przy użyciu funkcji __kable__ z pakietu _knitr_. To rozwiązanie nie jest, o ile wiem, bardzo popularne. Przez lata wszyscy uczyli się korzystania z funkcji __xtable__ i do dzisiaj istnieje mnóstwo opisów, jak jej używać. Na __kable__ natknąłem się więc kiedyś przypadkiem, w trakcie jednej z moich licznych walk z tabelami. Od razu przypadła mi do gustu prostota tej funkcji, która oczywiście wiąrze się z pewnymi ograniczeniami. 

Funkcja __kable__ działa trochę inaczej niż jej "pierwowzów" __table__. Nie generuje tabel z danych lecz "drukuje" gotowe dane do tabeli markdown. Co ważne __kable__ wyświetla jedynie obiekty klasy "_data.frame_" lub "_matrix_". To oznacza, że aby przedstawić wynik naszych obliczeń w tabeli, musimy go sprowadzić do jednej z tych dwóch klas. 

## PDF, HTML, MsWord i dalej

Jak wiadomo _knitr_ daje możliwość tworzenia dokumentów w różnychformatach. Funkcja __kable__ bez problemy umie się do tego dostosować. Aby to zademonstwować __ten dokument__ został wygenerowany w czterech wersjach na podstawie jednego pliku "Tabele\_markdown.Rmd":

* dokument html - "Tabele\_markdown.html"
* dokument PDF - "Tabele\_markdown.pdf"
* dokument md (markdown) - "Tabele\_markdown.md"
* domument MSWord - "Tabele\_markdown.docx"

Taka sztuczka może być przydatna, gdy wysyłamy nasz dokument w różne miejsca.

W "nagłówku" pliku "Tabele\_markdown.Rmd" znajduje się opis formatów w jakich możemy z niego generować dokumenty. Aby to zrobić używamy przycisku "knitr" w RStudio (odpowiednio: "PDF", "Word" lub "HTML"), albo w __KONSOLI__ R wpisujemy komendę: _rmarkdown::render("Tabele\_rmarkdown.Rmd", "...")_. W miejsce trzech kropek wstawiamy po kolei odpowiednio (zachowując cudzysłów):

* word_document
* pdf_document
* md_document
* html_document

W ten sposób możemy otrzymać 4 różne dokumenty z 4 różnymi formatowaniami tabel. Teoretycznie można też podać R komendę _rmarkdown::render("Tabele\_rmarkdown.Rmd", "all")_  i w ten sposób wygenerować wszystkie dokumenty jednoczśnie, ale niestety u mnie to nie działa. W przypadku generowania dokumentów przy pomocy poleceń w konsoli może pojawić się problem z kodowaniem. Jeżeli plik źródłowy .Rmd jest kodowany w UTF-8, a systemowe kodowanie to WINDOWS 1253 (tak jest w moim przypadku) to dokumentach generowanych przy pomocy polecenia z konsoli zamiast polskich znaków pojawią się krzaki.  

Oczywiście nie ma konieczności generowania wszystkich dokumentów na raz. Zawsze można sobie wybrac jeden. 

# Opis argumentów funkcji __kable__

_kable(x, format, digits = getOption("digits"), row.names = NA, align, output = TRUE, ...)_

  * __x__ - obiekt R (macierz lub ramka danych), który chcemy wyświetlić jako tabelę w naszym dokumencie
  * __format__	- obiekt typu _charakter_; można wybrać następujące wartości
      + "latex" - dla dokumnetów LaTeX
      + "html" - dla dokumentów html
      + "markdown" - dla dokumntu markdown
      + "pandoc" - dla dokumnetów LaTeX
      + "rst" - też dla dokumentów word
  * __digits__	- jak łatwo się domyślić chodzi o zaaokrąglenia liczb (przekazywane do funkcji _round()_); można wpisać jedną liczbę dla całej tabeli lub wektor liczb, aby zdefiniować różne zaokrąglenia dla poszczególnych kolumn
  * __row.names__ - czy wyświetlać nazwy wierszy; TRUE / FALSE 
  * __align__	- wyrównanie tekstu w kolumanch; domyślnie liczby do prawej,  a reszta do lewej
    + "l" - do lewej;
    + "c" - do środka;
    + "r" - do prawej;
  * __output__	- czy wpisywać wynik do konsoli 


# Działanie argumentów funkcji na przykładzie tabeli w formacie _markdown_

UWAGA !!! Funkcja __kable__ wyświetli tabele tylko jeżeli w ustawieniach bloku kodu (_chunk options_) __results='asis'__

## Przykładowy zbiór danych: mtcars


```r
mtcars
```

```
##                      mpg cyl  disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
## Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
## Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
## Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
## Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
## Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
## Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
## Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
## Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
## Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
## Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
## Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
## Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
## Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
## Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
## Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
## Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
## Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
## AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
## Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
## Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
## Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
## Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
## Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
## Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
## Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
## Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
## Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
```

## Ustawienia domyślne funkcji kable


```text
knitr::kable(head(mtcars,20), format = "markdown")
```



|                    |  mpg| cyl|  disp|  hp| drat|    wt|  qsec| vs| am| gear| carb|
|:-------------------|----:|---:|-----:|---:|----:|-----:|-----:|--:|--:|----:|----:|
|Mazda RX4           | 21.0|   6| 160.0| 110| 3.90| 2.620| 16.46|  0|  1|    4|    4|
|Mazda RX4 Wag       | 21.0|   6| 160.0| 110| 3.90| 2.875| 17.02|  0|  1|    4|    4|
|Datsun 710          | 22.8|   4| 108.0|  93| 3.85| 2.320| 18.61|  1|  1|    4|    1|
|Hornet 4 Drive      | 21.4|   6| 258.0| 110| 3.08| 3.215| 19.44|  1|  0|    3|    1|
|Hornet Sportabout   | 18.7|   8| 360.0| 175| 3.15| 3.440| 17.02|  0|  0|    3|    2|
|Valiant             | 18.1|   6| 225.0| 105| 2.76| 3.460| 20.22|  1|  0|    3|    1|
|Duster 360          | 14.3|   8| 360.0| 245| 3.21| 3.570| 15.84|  0|  0|    3|    4|
|Merc 240D           | 24.4|   4| 146.7|  62| 3.69| 3.190| 20.00|  1|  0|    4|    2|
|Merc 230            | 22.8|   4| 140.8|  95| 3.92| 3.150| 22.90|  1|  0|    4|    2|
|Merc 280            | 19.2|   6| 167.6| 123| 3.92| 3.440| 18.30|  1|  0|    4|    4|
|Merc 280C           | 17.8|   6| 167.6| 123| 3.92| 3.440| 18.90|  1|  0|    4|    4|
|Merc 450SE          | 16.4|   8| 275.8| 180| 3.07| 4.070| 17.40|  0|  0|    3|    3|
|Merc 450SL          | 17.3|   8| 275.8| 180| 3.07| 3.730| 17.60|  0|  0|    3|    3|
|Merc 450SLC         | 15.2|   8| 275.8| 180| 3.07| 3.780| 18.00|  0|  0|    3|    3|
|Cadillac Fleetwood  | 10.4|   8| 472.0| 205| 2.93| 5.250| 17.98|  0|  0|    3|    4|
|Lincoln Continental | 10.4|   8| 460.0| 215| 3.00| 5.424| 17.82|  0|  0|    3|    4|
|Chrysler Imperial   | 14.7|   8| 440.0| 230| 3.23| 5.345| 17.42|  0|  0|    3|    4|
|Fiat 128            | 32.4|   4|  78.7|  66| 4.08| 2.200| 19.47|  1|  1|    4|    1|
|Honda Civic         | 30.4|   4|  75.7|  52| 4.93| 1.615| 18.52|  1|  1|    4|    2|
|Toyota Corolla      | 33.9|   4|  71.1|  65| 4.22| 1.835| 19.90|  1|  1|    4|    1|

## Tabela bez nazwy wierszy 


```r
knitr::kable(head(mtcars,20), format = "markdown", row.names = FALSE)
```



|  mpg| cyl|  disp|  hp| drat|    wt|  qsec| vs| am| gear| carb|
|----:|---:|-----:|---:|----:|-----:|-----:|--:|--:|----:|----:|
| 21.0|   6| 160.0| 110| 3.90| 2.620| 16.46|  0|  1|    4|    4|
| 21.0|   6| 160.0| 110| 3.90| 2.875| 17.02|  0|  1|    4|    4|
| 22.8|   4| 108.0|  93| 3.85| 2.320| 18.61|  1|  1|    4|    1|
| 21.4|   6| 258.0| 110| 3.08| 3.215| 19.44|  1|  0|    3|    1|
| 18.7|   8| 360.0| 175| 3.15| 3.440| 17.02|  0|  0|    3|    2|
| 18.1|   6| 225.0| 105| 2.76| 3.460| 20.22|  1|  0|    3|    1|
| 14.3|   8| 360.0| 245| 3.21| 3.570| 15.84|  0|  0|    3|    4|
| 24.4|   4| 146.7|  62| 3.69| 3.190| 20.00|  1|  0|    4|    2|
| 22.8|   4| 140.8|  95| 3.92| 3.150| 22.90|  1|  0|    4|    2|
| 19.2|   6| 167.6| 123| 3.92| 3.440| 18.30|  1|  0|    4|    4|
| 17.8|   6| 167.6| 123| 3.92| 3.440| 18.90|  1|  0|    4|    4|
| 16.4|   8| 275.8| 180| 3.07| 4.070| 17.40|  0|  0|    3|    3|
| 17.3|   8| 275.8| 180| 3.07| 3.730| 17.60|  0|  0|    3|    3|
| 15.2|   8| 275.8| 180| 3.07| 3.780| 18.00|  0|  0|    3|    3|
| 10.4|   8| 472.0| 205| 2.93| 5.250| 17.98|  0|  0|    3|    4|
| 10.4|   8| 460.0| 215| 3.00| 5.424| 17.82|  0|  0|    3|    4|
| 14.7|   8| 440.0| 230| 3.23| 5.345| 17.42|  0|  0|    3|    4|
| 32.4|   4|  78.7|  66| 4.08| 2.200| 19.47|  1|  1|    4|    1|
| 30.4|   4|  75.7|  52| 4.93| 1.615| 18.52|  1|  1|    4|    2|
| 33.9|   4|  71.1|  65| 4.22| 1.835| 19.90|  1|  1|    4|    1|

## Tabela z zaokrągleniem liczb do 2 cyfr po przecinku


```r
 knitr:: kable( head(mtcars,20) , format ="markdown", digits=2 )
```



|                    |  mpg| cyl|  disp|  hp| drat|   wt|  qsec| vs| am| gear| carb|
|:-------------------|----:|---:|-----:|---:|----:|----:|-----:|--:|--:|----:|----:|
|Mazda RX4           | 21.0|   6| 160.0| 110| 3.90| 2.62| 16.46|  0|  1|    4|    4|
|Mazda RX4 Wag       | 21.0|   6| 160.0| 110| 3.90| 2.88| 17.02|  0|  1|    4|    4|
|Datsun 710          | 22.8|   4| 108.0|  93| 3.85| 2.32| 18.61|  1|  1|    4|    1|
|Hornet 4 Drive      | 21.4|   6| 258.0| 110| 3.08| 3.21| 19.44|  1|  0|    3|    1|
|Hornet Sportabout   | 18.7|   8| 360.0| 175| 3.15| 3.44| 17.02|  0|  0|    3|    2|
|Valiant             | 18.1|   6| 225.0| 105| 2.76| 3.46| 20.22|  1|  0|    3|    1|
|Duster 360          | 14.3|   8| 360.0| 245| 3.21| 3.57| 15.84|  0|  0|    3|    4|
|Merc 240D           | 24.4|   4| 146.7|  62| 3.69| 3.19| 20.00|  1|  0|    4|    2|
|Merc 230            | 22.8|   4| 140.8|  95| 3.92| 3.15| 22.90|  1|  0|    4|    2|
|Merc 280            | 19.2|   6| 167.6| 123| 3.92| 3.44| 18.30|  1|  0|    4|    4|
|Merc 280C           | 17.8|   6| 167.6| 123| 3.92| 3.44| 18.90|  1|  0|    4|    4|
|Merc 450SE          | 16.4|   8| 275.8| 180| 3.07| 4.07| 17.40|  0|  0|    3|    3|
|Merc 450SL          | 17.3|   8| 275.8| 180| 3.07| 3.73| 17.60|  0|  0|    3|    3|
|Merc 450SLC         | 15.2|   8| 275.8| 180| 3.07| 3.78| 18.00|  0|  0|    3|    3|
|Cadillac Fleetwood  | 10.4|   8| 472.0| 205| 2.93| 5.25| 17.98|  0|  0|    3|    4|
|Lincoln Continental | 10.4|   8| 460.0| 215| 3.00| 5.42| 17.82|  0|  0|    3|    4|
|Chrysler Imperial   | 14.7|   8| 440.0| 230| 3.23| 5.34| 17.42|  0|  0|    3|    4|
|Fiat 128            | 32.4|   4|  78.7|  66| 4.08| 2.20| 19.47|  1|  1|    4|    1|
|Honda Civic         | 30.4|   4|  75.7|  52| 4.93| 1.62| 18.52|  1|  1|    4|    2|
|Toyota Corolla      | 33.9|   4|  71.1|  65| 4.22| 1.84| 19.90|  1|  1|    4|    1|

## Tabela z wyrównaniem do lewej


```r
knitr:: kable( head(mtcars,20), format ="markdown", align = "l")
```



|                    |mpg  |cyl |disp  |hp  |drat |wt    |qsec  |vs |am |gear |carb |
|:-------------------|:----|:---|:-----|:---|:----|:-----|:-----|:--|:--|:----|:----|
|Mazda RX4           |21.0 |6   |160.0 |110 |3.90 |2.620 |16.46 |0  |1  |4    |4    |
|Mazda RX4 Wag       |21.0 |6   |160.0 |110 |3.90 |2.875 |17.02 |0  |1  |4    |4    |
|Datsun 710          |22.8 |4   |108.0 |93  |3.85 |2.320 |18.61 |1  |1  |4    |1    |
|Hornet 4 Drive      |21.4 |6   |258.0 |110 |3.08 |3.215 |19.44 |1  |0  |3    |1    |
|Hornet Sportabout   |18.7 |8   |360.0 |175 |3.15 |3.440 |17.02 |0  |0  |3    |2    |
|Valiant             |18.1 |6   |225.0 |105 |2.76 |3.460 |20.22 |1  |0  |3    |1    |
|Duster 360          |14.3 |8   |360.0 |245 |3.21 |3.570 |15.84 |0  |0  |3    |4    |
|Merc 240D           |24.4 |4   |146.7 |62  |3.69 |3.190 |20.00 |1  |0  |4    |2    |
|Merc 230            |22.8 |4   |140.8 |95  |3.92 |3.150 |22.90 |1  |0  |4    |2    |
|Merc 280            |19.2 |6   |167.6 |123 |3.92 |3.440 |18.30 |1  |0  |4    |4    |
|Merc 280C           |17.8 |6   |167.6 |123 |3.92 |3.440 |18.90 |1  |0  |4    |4    |
|Merc 450SE          |16.4 |8   |275.8 |180 |3.07 |4.070 |17.40 |0  |0  |3    |3    |
|Merc 450SL          |17.3 |8   |275.8 |180 |3.07 |3.730 |17.60 |0  |0  |3    |3    |
|Merc 450SLC         |15.2 |8   |275.8 |180 |3.07 |3.780 |18.00 |0  |0  |3    |3    |
|Cadillac Fleetwood  |10.4 |8   |472.0 |205 |2.93 |5.250 |17.98 |0  |0  |3    |4    |
|Lincoln Continental |10.4 |8   |460.0 |215 |3.00 |5.424 |17.82 |0  |0  |3    |4    |
|Chrysler Imperial   |14.7 |8   |440.0 |230 |3.23 |5.345 |17.42 |0  |0  |3    |4    |
|Fiat 128            |32.4 |4   |78.7  |66  |4.08 |2.200 |19.47 |1  |1  |4    |1    |
|Honda Civic         |30.4 |4   |75.7  |52  |4.93 |1.615 |18.52 |1  |1  |4    |2    |
|Toyota Corolla      |33.9 |4   |71.1  |65  |4.22 |1.835 |19.90 |1  |1  |4    |1    |

## Tabela z kombinacją różnych wyrównań i zaokrągleń w kolumnach


```r
knitr:: kable( head(mtcars,20), format ="markdown", 
               align = c( "l","r","l","r","l","r","l","r","l","r","l"),
               , digits=c(2,0,0,0,1,1,2,2,2,2,2) )
```



|                    |mpg  | cyl|disp |  hp|drat |  wt|qsec  | vs|am | gear|carb |
|:-------------------|:----|---:|:----|---:|:----|---:|:-----|--:|:--|----:|:----|
|Mazda RX4           |21.0 |   6|160  | 110|3.9  | 2.6|16.46 |  0|1  |    4|4    |
|Mazda RX4 Wag       |21.0 |   6|160  | 110|3.9  | 2.9|17.02 |  0|1  |    4|4    |
|Datsun 710          |22.8 |   4|108  |  93|3.8  | 2.3|18.61 |  1|1  |    4|1    |
|Hornet 4 Drive      |21.4 |   6|258  | 110|3.1  | 3.2|19.44 |  1|0  |    3|1    |
|Hornet Sportabout   |18.7 |   8|360  | 175|3.1  | 3.4|17.02 |  0|0  |    3|2    |
|Valiant             |18.1 |   6|225  | 105|2.8  | 3.5|20.22 |  1|0  |    3|1    |
|Duster 360          |14.3 |   8|360  | 245|3.2  | 3.6|15.84 |  0|0  |    3|4    |
|Merc 240D           |24.4 |   4|147  |  62|3.7  | 3.2|20.00 |  1|0  |    4|2    |
|Merc 230            |22.8 |   4|141  |  95|3.9  | 3.1|22.90 |  1|0  |    4|2    |
|Merc 280            |19.2 |   6|168  | 123|3.9  | 3.4|18.30 |  1|0  |    4|4    |
|Merc 280C           |17.8 |   6|168  | 123|3.9  | 3.4|18.90 |  1|0  |    4|4    |
|Merc 450SE          |16.4 |   8|276  | 180|3.1  | 4.1|17.40 |  0|0  |    3|3    |
|Merc 450SL          |17.3 |   8|276  | 180|3.1  | 3.7|17.60 |  0|0  |    3|3    |
|Merc 450SLC         |15.2 |   8|276  | 180|3.1  | 3.8|18.00 |  0|0  |    3|3    |
|Cadillac Fleetwood  |10.4 |   8|472  | 205|2.9  | 5.2|17.98 |  0|0  |    3|4    |
|Lincoln Continental |10.4 |   8|460  | 215|3.0  | 5.4|17.82 |  0|0  |    3|4    |
|Chrysler Imperial   |14.7 |   8|440  | 230|3.2  | 5.3|17.42 |  0|0  |    3|4    |
|Fiat 128            |32.4 |   4|79   |  66|4.1  | 2.2|19.47 |  1|1  |    4|1    |
|Honda Civic         |30.4 |   4|76   |  52|4.9  | 1.6|18.52 |  1|1  |    4|2    |
|Toyota Corolla      |33.9 |   4|71   |  65|4.2  | 1.8|19.90 |  1|1  |    4|1    |

# Uwagi końcowe

W powyższych przykładach nie dodano tutułów do tabel. Jest to sposodowane zastosowaniem w funkcji __kable__ dla argumentu _format_ wartości _markdown_, który nie daje takiej możliwości. Żeby zobaczyć, jak działa dodawania tytułu na przykładzie dokumentu PDF lub HTML przejdź do przykładów: [Tabela_rmarkdown_tytuly/Tabela_rmarkdown_tytuly_PDF.pdf](Tabele_rmarkdown_tytuly/Tabele_rmarkdown_tytuly_PDF.pdf) lub [Tabela_rmarkdown_tytuly/Tabela_rmarkdown_tytuly_HTML.html](Tabele_rmarkdown_tytuly/Tabele_rmarkdown_tytuly_HTML.html)


Aby zobaczyć, jak tworzyć tabele w dokumnetach PDF generowanych bezpośrednio z LaTeX bez udziału rmarkdown (narzędzie __Sweave__) przejdź do pliku  [Tabela_LaTeX/Tabela_LaTeX.pdf](Tabele_LaTeX\Tabele_LaTeX.pdf)
