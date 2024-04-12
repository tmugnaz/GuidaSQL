# FUNZIONI ANALITICHE 
---
---

## Funzioni Analitiche 

Le funzioni analitiche in SQL sono un insieme di funzioni avanzate che consentono di eseguire calcoli complessi su dati raggruppati senza dover utilizzare sottoquery o operazioni di join complesse. 

| Funzione       | Descrizione                                                                              | Sintassi                                                                                                                             |
|----------------|------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| SUM() OVER()   | Calcola la somma di una colonna su una partizione di righe.                               | ``` SELECT colonna1, colonna2, SUM(colonna3) OVER (PARTITION BY colonna1) AS total FROM tabella; ```                            |
| ROW_NUMBER()   | Assegna un numero di riga unico a ciascuna riga in una partizione, in base all'ordine.   | ``` SELECT colonna1, colonna2, ROW_NUMBER() OVER (ORDER BY colonna1) AS row_num FROM tabella; ```                               |
| RANK()         | Assegna un rango alle righe in base al valore ordinato.                                    | ``` SELECT colonna1, colonna2, RANK() OVER (ORDER BY colonna3 DESC) AS rank FROM tabella; ```                                    |
| LEAD()         | Restituisce il valore di una colonna dalla riga successiva all'interno di una partizione. | ``` SELECT colonna1, colonna2, LEAD(colonna3) OVER (ORDER BY colonna1) AS next_value FROM tabella; ```                         |
| LAG()          | Restituisce il valore di una colonna dalla riga precedente all'interno di una partizione. | ``` SELECT colonna1, colonna2, LAG(colonna3) OVER (ORDER BY colonna1) AS prev_value FROM tabella; ```                         |
| FIRST_VALUE()  | Restituisce il primo valore in base all'ordine specificato all'interno di una partizione. | ``` SELECT colonna1, colonna2, FIRST_VALUE(colonna3) OVER (PARTITION BY colonna1 ORDER BY colonna3) AS first_value FROM tabella; ``` |
| LAST_VALUE()   | Restituisce l'ultimo valore in base all'ordine specificato all'interno di una partizione. | ``` SELECT colonna1, colonna2, LAST_VALUE(colonna3) OVER (PARTITION BY colonna1 ORDER BY colonna3) AS last_value FROM tabella; ```  |
| LISTAGG()        | Concatena i valori di una colonna in una stringa, separati da un delimitatore specificato.     | ```sql SELECT colonna1, LISTAGG(colonna2, ', ') WITHIN GROUP (ORDER BY colonna2) AS concatenated_values FROM tabella GROUP BY colonna1; ``` |
| RATIO_TO_REPORT()| Calcola la percentuale di una riga rispetto alla somma totale in una partizione di righe.    | ```sql SELECT colonna1, colonna2, RATIO_TO_REPORT(colonna2) OVER (PARTITION BY colonna1) AS ratio FROM tabella; ```                           |
| CUME_DIST()      | Calcola la distribuzione cumulativa dei valori in un insieme di dati ordinato.                  | ```sql SELECT colonna1, colonna2, CUME_DIST() OVER (ORDER BY colonna2) AS cumulative_distribution FROM tabella; ``` |
| PERCENT_RANK()   | Calcola il rango percentuale di ciascun valore in un insieme di dati ordinato.                   | ```sql SELECT colonna1, colonna2, PERCENT_RANK() OVER (ORDER BY colonna2 DESC) AS percent_rank FROM tabella; ```   |


* **La WINDOW clause**
Chiamato così il blocco di codice all'interno delle parentesi dopo OVER che permette di alle funzioni analitiche di operare sui date che vogliamo, può essere configurata con una clausola PARTITION BY per dividere il set di dati in gruppi o con una clausola ORDER BY ( anche insieme al PARTITION) per irordinare i idati all'interno di una Partition.

---

## PIVOT E UNPIVOT 

* **PIVOT**: La clausola PIVOT consente di trasformare i dati da righe a colonne, aggregando i valori di una colonna specifica in nuove colonne corrispondenti a valori univoci di un'altra colonna.
Esempio :
da questa tabella 

| Seller    | Month | Sales  |
|--------|--------|--------|
| Alice     | Jan   | 1000   |
| Bob       | Jan   | 1500   |
| Alice     | Feb   | 1200   |
| Bob       | Feb   | 1800   |


grazie a PIVOT 

```sql
SELECT *
FROM (
    SELECT Seller, Month, Sales
    FROM Sales
)
PIVOT (
    SUM(Sales) FOR Month IN ('Jan', 'Feb')
) AS PivotTable;

```
abbiamo come risultato una tabella con le vendite di ogni vendirore per i mesi di gennaio e febbraio come colonne separate


| Seller | Jan    | Feb    |
|--------|--------|--------|
| Alice  | 1000   | 1200   |
| Bob    | 1500   | 1800   |



È come se fosse una rotazione (PIVOT) della tabella.

* **UNPIVOT**: L'operazione UNPIVOT consente di trasformare i dati da colonne a righe, convertendo valori di diverse colonne in una singola colonna con valori corrispondenti.
Esempio:
Dalla tabella di prima lanciando il comando UNPIVOT: 
```sql
SELECT Seller, Month, Sales
FROM (
    SELECT Seller, Jan, Feb
    FROM SalesSummary
) AS SalesSummaryUnpivot
UNPIVOT (
    Sales FOR Month IN (Jan, Feb)
) AS UnpivotTable;

```
torniamo piu o meno alla situazione di partenza :

| Seller | Month | Sales  |
|--------|--------|--------|
| Alice  | Jan   | 1000   |
| Alice  | Feb   | 1200   |
| Bob    | Jan   | 1500   |
| Bob    | Feb   | 1800   |

----
----




