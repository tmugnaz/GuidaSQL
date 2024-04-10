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

---

## HAVING

---
 <!--TODO GROUPBY E HAVING-->
