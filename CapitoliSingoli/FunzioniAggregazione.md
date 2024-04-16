# FUNZIONI DI AGGREGAZIONE

---
---
Sono funzioni utilizzate per calcolare un singolo valore risultante da un insieme di valori all'interno di un gruppo di righe. Queste funzioni sono ampiamente utilizzate nelle query per eseguire calcoli sui dati e ottenere risultati aggregati come somme, conteggi, medie, massimi e minimi.

SOno inserite nella Query nella **SELECT** come se fossero attributi di una tabella , infatti non sono altro che il risultato di una funzione su uno di questi campi .

In particolare sono:

* SUM()-> SOMMA
 La funzione SUM() restituisce la somma totale dei valori in una colonna numerica.

```sql
SELECT SUM(amount) AS total_sales
FROM orders;
```

* AVG()-> Media
La funzione AVG() calcola la media dei valori in una colonna numerica.

```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```

* MIN()->Minimo
La funzione MIN() restituisce il valore minimo in una colonna.

```sql
SELECT MIN(salary) AS min_salary
FROM employees;
```

* MAX()-> Massimo
La funzione MAX() restituisce il valore massimo in una colonna.

```sql
SELECT MAX(amount) AS max_order_amount
FROM orders;
```

* COUNT (DISTINCT)->Conteggio
La funzione COUNT() restituisce il numero di righe o valori non nulli in una colonna.
Conta i valori unici non duplicati in una colonna specificata.

```sql
SELECT COUNT(customer_id) AS total_customers
FROM customers;
```

* COUNT (*)-> Conteggio
Conta il numero totale di righe nella tabella. Questa funzione viene spesso utilizzata per ottenere il conteggio complessivo delle righe, indipendentemente dalla presenza di valori NULL o duplicati.

```sql
SELECT COUNT(*) AS total_students
FROM students;
```

Solitamente seguiti da un alias come **AS** "Nome risultato" per rendere piu chiaro il risultato

---

## GROUP BY

Utilizzato per raggruppare le righe di una tabella in base ai valori di una o più colonne specifiche.

Raggruppa tutti i campi non Calcolati , ovvero quelli non derivati da una funzione di aggregazione è infatti necessario se abbiamo campi non calcolati.

```sql
SELECT 
    column1,colum2,
    aggregate_function(column3)
FROM table_name
GROUP BY column1, column2;
```
---

## HAVING

Operatore che applica un filtro ai campi calcolati soggetti a funzioni di aggregazione .

Il check sul filtro **Having** avviene dopo che tuti i campi sono stati calcolati a differenza del filtro **Where** che invece filtra quali dati devono essere poi calcolati.
Nella sintassi della Query è dichiarato dopo il **Group By**.

Puo essere usate anche dalle colonne senza funzioni di aggregazione.

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

---

## ROLLUP e CUBE 


### ROLLUP 

Con la clausola ROLLUP nel group by vengono generati i totali tra le combinazioni delle colonne specificate.
Viene usato con funzioni di aggregazione per otterene risultati piu complessi. 

I totali sono seguono un ordine specifico e vengono creati basandosi sulla sequenza di colonne specificata nella clausola

```sql
SELECT year, month, SUM(revenue) AS total_revenue
FROM sales
GROUP BY ROLLUP(year, month)
ORDER BY year, month;
```
Risultato:

 |year|month|total_revenue|
 |---|---|---| 
 |2022|Jan|5000|
 |2022|Feb|6000|
 |2022|NULL|11000| 
 |2023|Jan|7000|
 |2023|Feb|8000|
 |2023|NULL|15000|
 |NULL|NULL|26000|

Possiamo vedere nella 3 riga abbiamo il vaolre totale dell'anno 2022 , nella 5 riga quello del 2023 e nell'ultima il valore combinato dei 2 anni.

È quindi la combinazione dei totali dei campi selezionati nella Query

### CUBE

La clausola **CUBE** è utile quando si desidera ottenere una visione completa dei dati aggregati in quanto riporta tutte le possibili combinazioni dei dati specificati.
Si andranno solitamente a generare più righe rispetto al **ROLLUP** in quanto **CUBE** non segue un ordine specifico ma sono tutte le possibili proiezioni sui ragruppament di colonne.

```sql
SELECT year, month, SUM(revenue) AS total_revenue
FROM sales
GROUP BY CUBE(year, month)
ORDER BY year, month;
```
Risultato:

|year|month|total_revenue|
|---|---|---|
|2022|Jan| 5000|
|2022|Feb|6000|
|2022|NULL|11000|
|2023|Jan|7000|
|2023|Feb|8000|
|2023|NULL|15000|
|NULL|Jan|12000|
|NULL|Feb|14000|
|NULL|NULL|26000|

possiamo quindi notare i totali riportati che sono 
* totale anno 2022
* totale anno 2023 
* totale mesi Gennaio
* totale mesi Febraio
* totale di entrambe 

È quindi la combinazione delle righe specificate nella Query.

---
---
