# SUBQUERY 

---
---
## SUBQUERY semplici

Sono delle Query più semplici che vengono usate come filtro dalla Query principale.

Possono essere nel filtro **WHERE** con la clausola **IN**
e nel filtro **HAVING** come check di una funzione di aggregazione.

Vengono scritte come normali Query ma tra parentesi.


```sql
SELECT employee_name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

oppure

```sql
SELECT customer_id, SUM(order_amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING SUM(order_amount) > (
    SELECT AVG(total_amount)
    FROM (
        SELECT customer_id, SUM(order_amount) AS total_amount
        FROM orders
        GROUP BY customer_id
    ) AS avg_amount
);
```
In questo caso la Subquery è un record di dati dove il filtro HAVING controlla il confronto.

---

## Parametro ALL e ANY

Il parametro **ALL** nelle subquery in SQL viene utilizzato per confrontare un valore con tutti i valori restituiti dalla subquery. Questa parola chiave è utilizzata con operatori di confronto come =, >, <, >=, <=, <> per confrontare il valore con ogni singolo valore risultante dalla subquery.

```sql
SELECT column1
FROM table1
WHERE column1 > ALL (SELECT column2 FROM table2 WHERE condition);
```
In questo esempio, la subquery restituisce un insieme di valori e il filtro **WHERE** confronta column1 con ogni valore restituito dalla subquery utilizzando il parametro  **ALL**. 
La condizione column1 > **ALL** sarà vera se e solo se column1 è maggiore di tutti i valori restituiti dalla subquer

Il parametro **ANY** ha la stessa sintassi di ALL ma sarà vero 
se ALMENO UNO dei valori soddifla la condizione dello WHERE

```sql
SELECT column1
FROM table1
WHERE column1 >= ANY (10, 20, 30);
```
Entrambi come si puo vedere sopra possono essere anche usati al di fuori delle SUBQUERY.

---

### SUBQUERY come Sostituti di Tabelle

Possiamo usare una SubQ come una tabella dalla quale la nostra QUery prncipale andrà a prendere i dati.
In questo caso solitamente diamo degli alias a queste SubQ per rendere più leggibile il codice (solitamwnte doppia lettera 'AA' etc)

Le usiamo quindi nella FROM della Query principale 

```sql
SELECT AA.customer_id, AA.total_amount
FROM (SELECT customer_id, SUM(order_amount) AS total_amount
      FROM orders
      GROUP BY customer_id) AS AA
WHERE total_amount > 1000;
```
---

### CTE (Common TAble Expression)

Un altro modo per usare le SubQuery è quello di dichiararle prima della SELECT tramite la parola chiave WITH  e usarle direttamente come se fossero tabelle del nostro DB 

```sql
WITH nome_cte (colonna1, colonna2, ...)
AS (
    SELECT colonna1, colonna2, ...
    FROM nome_tabella
    WHERE condizione
)
SELECT A.colonna1
FROM nome_cte A
WHERE condizione2;
```
---

---