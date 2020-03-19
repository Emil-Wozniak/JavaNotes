1.Tworzenie baz danych:

```sql
CREATE DATABASE <nazwa>
CHARACTER SET utf8mb4 //ustawia kodowanie na utf8mb4
COLLATE utf8mb4_unicode_ci //ustawia reguły sortowania, 
//ci - case insensitive
```


2. Zmiana akrywnej bazy danych:
```sql
USE <nazwa_bazy_danych>
```


3. Pokazanie baz danych na serwerze:

```sql
SHOW DATABASES;
```

4. Pokazanie tabel w bazie:

```sql
SHOW TABLES;
```


5. Wydruk struktury tabeli:

```sql
DESCRIBE <nazwa_tabeli>;
```

6. Tworzenie nowej tabli:
```sql
CREATE TABLE <nazwa> (
kolumna_1 typ_danych CONSTRAIN
....
);
/*
Jako CONSTRAIN  może być np NOT NULL, UNIQUE, PIMARY KEY, DEFAULT
dokładniej precyzuje to tabeli jakie dane przyjmować w daną kolumnę
*/
```


7. Dodawanie do tabeli:
```sql
INSERT INTO <nazwa_tabeli> 
(col1, col2,..) 
VALUES (var1, var2,....);
```

8. Pobieranie z tabelI:
```sql
SELECT column FROM table;
//zwaraca całą zawartość danej kolumny z tabeli.
SELECT * FROM table;
//zwraca całą tabelę - wszystkei kolumny


SELECT column AS 'nazwa'
FROM table;
//zwraca kolumnę ale pod nazwą podaną w '..' 
//nie zmienia nazwy kolumny, tylko zwraca pod inną nazwą

/* Można kilka kolumn naraz: */
SELECT column1 AS 'nazwa1', column2 AS 'nazwa2'
FROM table;

SELECT DISTINCT column
FROM table;
```
9. zwraca wartości ale bez powtórzen

```sql
SELECT column 
FROM table
WHERE column condition;
//WHERE rating > 8;
//WHERE job = 'junior developer';
//WHERE name IS NOT NULL;


SELECT column
FROM table
WHERE column LIKE condition;
//LIKE nie zwraca uwagi na wielkośc liter

WHERE name LIKE _ob;
//zwróci Bob, Rob, Sob, 
WHERE count LIKE 20_;
//zwróci tam gdzie 201,202,203...
* "%"
WHERE name LIKE A%;
//zwróci Adam, Ania, Aneta, ....
WHERE surname LIKE %ski;
//zwróci Cegłowski, Kowalski,...
WHERE cośtam LIKE %abc%;
//zwróci tylko tam gdzie wystepuje 'abc'


SELECT column
FROM table
WHERE value BETWEEN val1 AND val2;
/*

//np. WHERE name BETWEEN 'A' AND 'J'
//dla liter uwzględni A, ale nie uwzględni J
//WHERE year BETWEEN 1990 AND 1999;
//dla cyfr uwzględni 1990 i 1999

```
10. Można łączyć warunki:
```sql
SELECT column
FROM table
WHERE birth_year BETWEEN 1990 AND 1999
AND name = 'Jon'; 
```

```sql
SELECT column
FROM table
WHERE year > 2014
OR genre = 'action';

/* ================ */
SELECT column
FROM table
WHERE ....
ORDER BY name;
//poszegreguje rosnąco po 'name'
    ORDER BY name DESC;
//poszegreguje malejąco po 'name'
ORDER BY name ASC, year DESC;
//jednocześnie rosnąco po name i malejąco po year
```
11. If - else tylko SQL:SELECT column,
```sql
CASE
WHEN rating > 8 THEN 'Very Good'
WHEN rating > 5 THEN 'OK'
//zamiast rating to kolumna po której ifujemy
ELSE 'Avoid'
END AS review
//bez tego kolumna miałaby strasznie długa nazwę
FROM table;
```
12. Ograniczenie ilości wyników:SELECT column
```sql
FROM table
LIMIT 10;
//wyświetli 10 wyników query
OFFSET 2;
//zaczyna od rzędu nr 2
//skrócona forma:
LIMIT 2,10;
```

13. Zmiana tabeli:
```sql
ALTER TABLE <tabela>
ADD COLUMN column TYP_DANYCH;
//po dodaniu nowej kolumny wszystkie rzędy mają tam NULL
MODIFY COLUMN column typ_danych CONSTRAIN;
//zmienia typ danych i constrain danej columny
```
14. Zmiana zawartości rowów:
```sql
UPDATE tabela
SET column = valueToSet
WHERE col = value;
// (np. WHERE id = 4)
```
15. Usuwanie rowów:
```sql
DELETE FROM tabela
WHERE col IS value;
//(np. WHERE name IS NULL)
```

16. Funckje agregujące:
```sql
SELECT COUNT(column)
FROM table;
//zwraca ilość niepustych wierszy danej kolumny

SELECT SUM(column)
FROM table;
//zwraca sumę z kolumny

SELECT MIN/MAX(column)
FROM table;
//zwraca MIN/MAX z kolumny

SELECT AVG(column)
FROM table;
//zwraca średnią z kolumny

SELECT ROUND(column,<ilość_zer>
//np
SELECT ROUND(price,2)
FROM table;
//zwraca kolumnę zaokrągloną do dwóch miejsc po przecinku

SELECT column
FROM table
GROUP BY columnToGroupBy;
//grupuje wpisy w tabeli 

SELECT year, COUNT(name)
FROM table
GROUP BY 1,2
HAVING COUNT(name) > 10;
//zwróci tylko to którego ilość jest >10
//HAVING jest umieszczane ZA GROUP BY, PRZED ORDER BY i LIMIT
// GROUP BY 1,2 oznacza grupowanie po 1 i 2 podanej kolumnie przy SELECT
// When we want to limit the results of a query based on values of the individual rows, 
//use WHERE.
//When we want to limit the results of a query based on an aggregate property,
// use HAVING.
```

17. Łączenie tabel
```sql
/*
JOIN:==== INNER JOIN ====
*/
//zwaraca tylko rzędy spełniające warunek
SELECT *
FROM table
JOIN tableToCombine
ON table.columnToCompare = tableToCombine.columnToCompare;
//Zwróci tabelę będącą połączeniem table i tableToCompare
//przy użyciu warunków podanych po ON
   SELECT column1.table1
columnt2.table2
//w ten sposób możemy wybrac które kolumny zwrócić

==== LEFT JOIN ====
//zwraca wszystkie rzędy lewej tabeli 
//i z prawej tylko te spełniające warunki
SELECT *
FROM table
LEFT JOIN tableToCombine
ON table.columnToCombine = tableToCombine.columnToCompare
```
18. Tworzenie baz danych:
```sql
CREATE DATABASE <nazwa>
```