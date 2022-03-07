# Ćwiczenie 2 - Połaczenie z bazą danych i  select

Celem ćwiczenia jest połaczenie się z bazą danych przypomocy pgAdmin i wykonanie zapytań select. Dodatkowo zostanie pokazana metoda łączenia się z bazą danych z poziomu skryptu pythona przy użyciu sqlAlchemy oraz pandasa.

## Baza ćwiczeniowa

W części poświęconej bazom danych na zajęciach będziemy używać bazy z oficjalnego tutoriala PostgeSQL dostępnej (tutaj)[http://www.postgresqltutorial.com/wp-content/uploads/2019/05/dvdrental.zip].

## Polecenie SELECT

Jednym z najczęstszych zadań podczas pracy z bazami danych jest wyszukiwanie danych  za pomocą instrukcji SELECT. Instrukcja SELECT jest jedną z najbardziej złożonych instrukcji w PostgreSQL. Zawiera wiele klauzul umożliwiających utworzenie elastycznych zapytań.

Instrukcja SELECT zawiera następujące klauzule:

 - DISTINCT - wypisz .
 - ORDER BY - sortuj po wybranej kolumnie.
 - WHERE.- filtorwanie według wartości logicznych
 - LIMIT lub FETCH -wybieranie podzbiór wierszy z tabeli wynikowej
 - GROUP BY - grupowanie wiersze według zadanej kolumny
 - HAVING - filtrowanie ze zbioru .
 - Łączenie z innymi tabelami za pomocą złączeń: INNER JOIN, LEFT JOIN, FULL OUTER JOIN, CROSS JOIN.
 
### Podstawowa składnia SELECT 

SELECT
   column_1,
   column_2,
   ...
FROM
   table_name;
   
#### Przykład użycia

Wypisz wybrane kolumny z zadanej tabeli:
SELECT
   first_name,
   last_name,
   email
FROM
   customer;
   
Wypisz wszystkie kolumny z zadanej tabeli:
SELECT
   *
FROM
   customer;
   
### Klauzula ORDER BY
Klauzula ORDER BY pozwala sortować wiersze zwrócone z instrukcji SELECT w kolejność rosnąca lub malejąca na podstawie określonych kryteriów i kolumny. 

#### Składnia ogólna:

SELECT
   column_1,
   column_2
FROM
   tbl_name
ORDER BY
   column_1 ASC,
   column_2 DESC;
   
### Klauzula DISTINCT
Klauzula DISTINCT jest używana w instrukcji SELECT do usuwania zduplikowanych wierszy z wyniku zapytania. Klauzula DISTINCT zachowuje jeden wiersz dla każdej grupy duplikatów. Klauzula DISTINCT może być używane dla jednej lub więcej kolumn tabeli.

#### Składnia ogólna:

SELECT
 DISTINCT column_1
FROM
 table_name;
 
#### Przykłady użycia:

Dla więcej niż jednej kolumny:

SELECT
 DISTINCT column_1,
 column_2
FROM
 tbl_name;

Dla dokładnie jendej kolumny i pokazanie pozostałych:

SELECT
 DISTINCT ON
 (column_1) column_1_alias,
 column_2
FROM
 tbl_name
 
### Klauzula WHERE

Klauzula WHERE pojawia się zaraz po klauzuli FROM instrukcji SELECT. Klauzula WHERE wykorzystuje warunek do filtrowania wierszy zwróconych z instrukcji SELECT.

Warunek musi mieć wartość prawda, fałsz lub nieznany. Może to być wyrażenie boolowskie lub kombinacja wyrażeń boolowskich przy użyciu operatorów AND i OR.

Zapytanie zwraca wiersze spełniające warunek w klauzuli WHERE. Innymi słowy, tylko wiersze, które powodują spełnienie warunku, zostaną uwzględnione w zestawie wyników.

Oprócz instrukcji SELECT można użyć klauzuli WHERE w instrukcji UPDATE i DELETE, aby określić wiersze do aktualizacji lub usunięcia.

#### Składnia ogólna:

SELECT select_list
FROM table_name
WHERE condition;

|Operator|Opis|
|-|-|
|=|Równy|
|>|większy niż|
|<|mnijeszy niż|
|>=| większy bądź równy|
|<=| mniejszy bądź równy|
|<> lub !=| różny|
|AND| operator AND|
|OR|operator OR|

### Klauzula OFFSET
LIMIT jest opcjonalną klauzulą instrukcji SELECT, która pomija n pierwszych wierszy.

####  Składnia ogólna:
SELECT
   *
FROM
   table
OFFSET n;

### Klauzula LIMIT

LIMIT jest opcjonalną klauzulą instrukcji SELECT, która zwraca n pierwszych wierszy z zapytania.

####  Składnia ogólna:

SELECT
   *
FROM
   table_name
LIMIT n;

Jeśli chcemy poominąć liczbę wierszy przed zwróceniem n wierszy, użyj klauzuli OFFSET umieszczonej po klauzuli LIMIT jako następującej instrukcji:

SELECT
   *
FROM
   table
LIMIT n OFFSET m;


### Klauzula FETCH 

Klauzula FETCH umożliwia pobrania części wierszy zwróconych przez zapytanie. 

OFFSET start { ROW | ROWS }
FETCH { FIRST | NEXT } [ row_count ] { ROW | ROWS } ONLY


#### Przykłady użycia:

SELECT
    film_id,
    title
FROM
    film
ORDER BY
    title 
FETCH FIRST ROW ONLY;


SELECT
    film_id,
    title
FROM
    film
ORDER BY
    title 
FETCH FIRST 5 ROW ONLY;


### Klauzula IN

Umożliwia sprawdzenie czy dana kolumna zawiera wartość ze zbioru: value IN (value1,value2,...), lub w wersji przeciwnej czy nie należy do zbioru: value NOT IN (value1,value2,...),

#### Przykłady użycia:

SELECT
 customer_id,
   rental_id,
   return_date
FROM
   rental
WHERE
   customer_id IN (1, 2)
ORDER BY
   return_date DESC;


### Klauzula BETWEEN

Sprawdza czy wartość znajduje się w zadanym przedziale: value BETWEEN low AND high; lub przeciwnie value NOT BETWEEN low AND high

#### Przykłady użycia:

SELECT
   customer_id,
   payment_id,
   amount
FROM
   payment
WHERE
   amount BETWEEN 8
AND 9;

## Łączenie z bazą danych przy pomocy skryptu Python

Istnieje wiele bibliotek do obsługi połączeń Pythona z bazami danych. Na tych zajęciach będziemy korzystać z biblioteki sqlAlchemy oraz psycopg2. 

### Łączenie się za pomocą sqlAlchemy

from sqlalchemy import create_engine

db_string = "postgres://postgres:admin@localhost:5432/test"

db = create_engine(db_string)

print(db)

Gdzie *db_string* ma składnie nazwa_silnika://użytkownik:hasło@adres_serwera:port/nazwa_bazy

Wykonanie zapytania:

result_set = db.execute("SELECT * FROM city")  
for r in result_set:  
    print(r)

### Łączenie się za pomocą psycopg2 i pandas

import psycopg2 as pg
import pandas.io.sql as psql
import pandas as pd

connection = pg.connect(host='localhost', port=5432, dbname='test', user='postgres', password='admin')

Wykonanie zapytania:

df = pd.read_sql_query('select * from city',con=connection)
print(df)


## Ćwiczenie:
1. Ile kategorii filmów mamy w wypożyczalni?
2. Wyświetl listę kategorii w kolejności alfabetycznej.
3. Znajdź najstarszy i najmłodszy film do wypożyczenia.
4. Ile wyporzyczeń odbyło się między 2005-07-01 a 2005-08-01?
5. Ile wyporzyczeń odbyło się między 2010-01-01 a 2011-02-01?
6. Znajdź największą płatność wyporzyczenia.
7. Znajdź wszystkich klientów z Polski, Nigerii lub Bangladeszu.
8. Gdzie mieszkają członkowie personelu?
9. Ilu pracowników mieszka w Argentynie lub Hiszpanii?
10. Jakie kategorie filmów zostały wypożyczone przez klientów?
11. Znajdź wszystkie kategorie filmów wypożyczonych w Ameryce.
12. Znajdź wszystkie tytuły filmów, w których grał: Olympia Pfeiffer lub Julia Zellweger lub Ellen Presley
13*. Powtórz powyższe zapytania użyciu Pythona 


















