## TIPI DI DATI 

---
---

| Tipo di Dato     | Descrizione                                               |
|------------------|-----------------------------------------------------------|
| `CHAR(size)`     | Stringa di caratteri di lunghezza fissa                    |
| `VARCHAR2(size)` | Stringa di caratteri di lunghezza variabile               |
| `NCHAR(size)`    | Stringa di caratteri Unicode di lunghezza fissa            |
| `NVARCHAR2(size)`| Stringa di caratteri Unicode di lunghezza variabile        |
| `NUMBER(p, s)`   | Numero a virgola mobile con precisione fissa               |
| `FLOAT`          | Numero a virgola mobile con precisione doppia              |
| `BINARY_FLOAT`   | Numero a virgola mobile binario (precisione singola)       |
| `BINARY_DOUBLE`  | Numero a virgola mobile binario (precisione doppia)        |
| `DATE`           | Data e ora                                                 |
| `TIMESTAMP`      | Data e ora con precisione subsecondi                       |
| `CLOB`           | Oggetto di grandi dimensioni per testo carattere           |
| `BLOB`           | Oggetto di grandi dimensioni per dati binari               |
| `BFILE`          | File binario esterno                                        |
---
## FUNZIONI 

### FUNZIONI DI CONVERSIONE


| Funzione                    | Descrizione                                                            |
|-----------------------------|------------------------------------------------------------------------|
| `TO_CHAR(date, format)`     | Converte una data in una stringa di caratteri secondo il formato specificato |
| `TO_DATE(string, format)`   | Converte una stringa di caratteri in una data secondo il formato specificato |
| `TO_NUMBER(string)`         | Converte una stringa di caratteri in un numero                           |
| `TO_TIMESTAMP(string, format)` | Converte una stringa di caratteri in un timestamp secondo il formato specificato |
| `CAST(expression AS type)`  | Esegue il cast di un'espressione in un tipo di dato specificato          |

### FUNZIONI DI MANIPOLAZIONE STRINGHE

| Funzione                    | Descrizione                                                            |
|-----------------------------|------------------------------------------------------------------------|
| `SUBSTR(string, start, length)`   | Estrae una sottostringa da una stringa in base a una posizione di partenza e lunghezza specificata |
| `INSTR(string, substring)`       | Restituisce la posizione della prima occorrenza di una sottostringa all'interno di una stringa |
| `CONCAT(string1, string2)`       | Concatena due stringhe                                                 |
| `LOWER(string)`                  | Converte una stringa in caratteri minuscoli                             |
| `UPPER(string)`                  | Converte una stringa in caratteri maiuscoli                             |
| `INITCAP(string)`                | Converte la prima lettera di ogni parola in maiuscolo e le altre in minuscolo |
| `LENGTH(string)`                 | Restituisce la lunghezza di una stringa                                 |
| `TRIM(string)`                   | Rimuove gli spazi vuoti in eccesso da una stringa                       |
| `LTRIM(string)`                  | Rimuove gli spazi vuoti in eccesso dall'inizio di una stringa           |
| `RTRIM(string)`                  | Rimuove gli spazi vuoti in eccesso dalla fine di una stringa            |
| `REPLACE(string, search, replace)`| Sostituisce tutte le occorrenze di una sottostringa con un'altra in una stringa |
| `LPAD(string, length, pad_string)`| Aggiunge caratteri di riempimento alla sinistra di una stringa fino a raggiungere una determinata lunghezza |
| `RPAD(string, length, pad_string)`| Aggiunge caratteri di riempimento alla destra di una stringa fino a raggiungere una determinata lunghezza |


### FUNZIONE MANIPOLAZIONE DEI NUMERI

| Funzione                    | Descrizione                                                            |
|-----------------------------|------------------------------------------------------------------------|
| `ROUND(n, p)`  | Arrotonda un numero alla precisione specificata                        |
| `TRUNC(n,p)`  | Tronca un numero alla precisione specificata (rimuove le cifre decimali) |
| `CEIL(n)`              | Arrotonda un numero verso l'alto al valore intero più vicino           |
| `FLOOR(n)`             | Arrotonda un numero verso il basso al valore intero più vicino         |
| `ABS(n)`               | Restituisce il valore assoluto di un numero                             |
| `MOD(dividendo, divisore)`    | Restituisce il resto di una divisione (modulo) tra due numeri          |
| `POWER(base, esponente)`      | Calcola la potenza di un numero (base) elevato a un esponente           |
| `SQRT(n)`              | Calcola la radice quadrata di un numero                                |
| `SIGN(n)`              | Restituisce il segno di un numero (-1 se negativo, 0 se zero, +1 se positivo) |
| `GREATEST(n1, n2)` | Restituisce il numero più grande tra due numeri                        |
| `LEAST(n1, n2)`    | Restituisce il numero più piccolo tra due numeri                       |


### FUNZIONI MANIPOLAZIONE DATA E ORA 

| Funzione                           | Descrizione                                                            |
|------------------------------------|------------------------------------------------------------------------|
| `SYSDATE`                          | Restituisce la data e l'ora correnti nel formato di data e ora del database |
| `CURRENT_DATE`                     | Restituisce la data corrente nel formato di data del database         |
| `CURRENT_TIMESTAMP`                | Restituisce la data e l'ora correnti nel formato di timestamp del database |
| `TO_CHAR(date, format)`             | Converte una data in una stringa di caratteri secondo il formato specificato |
| `TO_DATE(string, format)`           | Converte una stringa di caratteri in una data secondo il formato specificato |
| `ADD_MONTHS(date, n)`               | Aggiunge un numero di mesi a una data                                  |
| `MONTHS_BETWEEN(date1, date2)`      | Calcola il numero di mesi tra due date                                 |
| `EXTRACT(unit FROM date)`           | Estrae una parte specifica (anno, mese, giorno, ora, minuto, secondo, etc.) da una data |
| `LAST_DAY(date)`                    | Restituisce l'ultimo giorno del mese di una data                       |
| `NEXT_DAY(date, day_of_week)`       | Restituisce la prossima data di una determinata settimana (es. 'MONDAY') dopo una data specificata |
| `ROUND(date [, format])`            | Arrotonda una data alla precisione specificata                         |
| `TRUNC(date [, format])`            | Tronca una data alla precisione specificata (rimuove ore, minuti, secondi) |

### FUNZIONI CASE NVL E NVL2 

* La funzione **CASE** è utilizzata per valutazioni su condizioni e restituire un valore al posto di un altro 

È eseguito nella sintassi seguente

```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ...
    ELSE default_result
END
```
e come vediamo è seguito da THEN e alla fine END per chiudere la clausola.

* NVL e NVL2

servono per fare un check sui valori di una colonna e gestire i valori *(null)*
sostituendoli con valori alternativi in base alla presenza o meno di esso.

```sql
NVL(column, default_value)

```

```sql
NVL2(column, valore1, valore2)
```
NVL2 viene usato per sostituire il valore1 se  trova *non-null* e valore2 se invece trova *null* nei check sulla colonna.

### FUNZIONE COALESCE 

Serve per restituire il primo valore non nulla da una lista di valori (come può essere una colonna)

```sql
COALESCE (v1,v2,v3,...vN)
```
 oppure può essere usato per cambiare il valore null all'interno di una colonna con un valore che specifichiamo noi
 può essere utile per effettuar eoperazioni matematiche nel casoa vessimo valori che null.able

 ```sql
COALESCE(column,0)
```
### GROUPING 

Viene usato insieme al CASE WHEN THEN END 
è spesso utilizzato quando abbiamo a che fare con l'operatore **ROLLUP** e permette di cambiare i valori nulli risultati dal group by con quello che vogliamo per "pienare" quel campo.

```sql
CASE GROUPING (column) =1 THEN 'Valore Totale' ELSE etc etc 
```
___
___