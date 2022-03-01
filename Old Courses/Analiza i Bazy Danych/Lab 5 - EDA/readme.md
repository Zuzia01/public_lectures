# Ćwiczenie 5 - Exploratory Data Analysis

## Cel ćwiczenia

Celem ćwiczenia jest:

1. Przygotowanie Data Dictionary dla zbioru danych opracowanego w ćwiczeniu 1 zgodnie z protokołem TIER. 

2. Korzystając z narzędzi do wizualizacji i podsumowań ``pandas`` sformułować odpowiedź na przydzielone pytania.

## Informacje dodatkowe


 [TIER Protocol](https://www.projecttier.org/tier-protocol/)

Instalacja pakietów z poziomu jupytera:

``import sys``

``!{sys.executable} -m pip install plotly``


## Dane do zadania 1.
  
Grupa środa 10:00

 1. pew.sav - religia i przychody w USA (UWAGA! plik jest w formacie spss, dane mają formę wyników ankiet, należy je przekształcić do formy zawierającej tylko religię i przychody, następnie policzyć ile osób w danej kategorii finansowej deklaruje daną religię)
 2. weather.txt - dane pogodowe (dataset opisany na wykładzie)
 3. tb.csv - dane o gruźlicy w różnych grupach pacjentów (tabela koduje jednocześnie informacje o wieku i o płci w kolumnach i zawiera dużo pustych miejsc)
 4. billboard.csv - notowania billboardu (w tabeli jest data wejścia na listę i ranking w kolejnych tygodniach, nie da się wprost odczytać rankingu w danym tygodniu kalendarzowym i jest dużo pustych miejsc)

Grupa poniedziałek 11:00

1. drinks.csv Dane i informacje: https://fivethirtyeight.com/features/dear-mona-followup-where-do-people-drink-the-most-beer-wine-and-spirits/
2. dem_score.xlsx  -  contains ratings of the level of democracy in different countries spanning 1952 to 1992. In this dataset, the minimum value of -10 corresponds to a highly autocratic nation whereas a value of 10 corresponds to a highly democratic nation. Note also that backticks surround the different variable names.
3. weather.txt - dane pogodowe (dataset opisany na wykładzie)
4. tb.csv - dane o gruźlicy w różnych grupach pacjentów (tabela koduje jednocześnie informacje o wieku i o płci w kolumnach i zawiera dużo pustych miejsc)

Grupa poniedziałek 14:00

1. weather.txt - dane pogodowe (dataset opisany na wykładzie)
2. drinks.csv Dane i informacje: https://fivethirtyeight.com/features/dear-mona-followup-where-do-people-drink-the-most-beer-wine-and-spirits/
3. billboard.csv - notowania billboardu (w tabeli jest data wejścia na listę i ranking w kolejnych tygodniach, nie da się wprost odczytać rankingu w danym tygodniu kalendarzowym i jest dużo pustych miejsc)
4. earthquake_data.csv https://fivethirtyeight.com/features/the-rock-isnt-alone-lots-of-people-are-worried-about-the-big-one/ (należy zmienić nazwy kolumn i przygotować tabelę łączącą wiek, płeć i odpowiedź na pytanie "Do you think the "Big One" will occur in your lifetime?"

Numer swojego datasetu uzyskujemy ze wzoru **(N mod 4) +1**, gdzie N to liczba liter w nazwisku.


## Dane do zadania 2.
  
Grupa środa 10:00

1. Dataset tips.csv. Czy kobiety dają większe napiwki? Czy grupy palaczy są bardziej czy mniej liczne od niepalących.
2. Dataset InsectSprays.csv. Dane przedstawiają obserwowaną liczbę owadów na polu doświadczalnym zaobserwowaną po dokonaniu oprysku pestycydem A-F. Przygotować analizę skuteczności pestycydów.
3. Dataset mpg.csv. Jakie czynniki wpływają na zużycie paliwa samochodu w trasie (hwy) i w mieście (cty)?

Grupa poniedziałek 11:00

1. Dataset tb.csv. Czy mężczyźni częściej chorują na gruźlice ? Która grupa wiekowa jest najbardziej narażona na zachorowanie.
2. Dataset drinks.csv. Przeanalizować dla wszystkich typów alkoholi w których Państwach spożywa się więcej danego typu alkoholu a w których mniej niż wynosi średnia obliczona z danych. Analizę przeprowadź również dla spożycia czystego alkoholu. Porównaj otrzymane grupy ze sobą.
3. Dataset dem_score.xlsx.  W jakich państwach poziom demokracji w opisywanych latach był stały, ciągle malejący, ciągle rosnący dla pozostałych określ czy poziom demokracji miał tendencję wzrostową czy malejącą?

Grupa poniedziałek 14:00

1. Dataset weather.txt. Która stacja zarejestrował największą różnicę temperatur w ciągu miesiąca? Określ które ze stacji zarejestrowały temperatury najbliższe do średniej wartości temperatury maksymalnej i minimalnej z poszczególnych miesięcy.
2. Dataset billboard.csv. Określ który z gatunków muzyki znajdował się najczęściej w pierwszej 10 notowań? Podziel zbiór ze względu na długość trwania utworu i sprawdź która grupa najczęściej zdobywała miejsce w pierwszej 10 a jaka w ostatniej. 
3. Dataset earthquake_data.csv. Określ który ze stanów obawia się najbardziej a który najmniej trzęsienia ziemi. Czy trzęsienia ziemi obawiają się bardziej mężczyźni czy kobiety? Która grupa zarobkowa ma największe doświadczenie z trzęsieniami ziemi?

Numer swojego tematu uzyskujemy ze wzoru **(N mod 3) +1**, gdzie N to liczba liter w nazwisku.

