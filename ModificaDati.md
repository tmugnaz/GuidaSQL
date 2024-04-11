# INSERIMENTO, MODIFICA E ELIMINAZIONE DATI
---
---
## Clonazione tabelle
Possiamo Clonare tabelle per effettuare test oppure per creare dei set di dati piu piccoli.

```sql
CREATE TABLE table2 AS 
SELECT * FROM table1  
WHERE condizione
```
automaticamente la popolerà con i risultati della SubQ ma perderemo tutte le Primary-Key

---

## INSERT

comando per inserire dati nelle tabelle 

ci sono 3 alternative 
* senza specificare colonne 

```sql
INSERT INTO table1 
VALUES ('X','Y','Z');
```
in questo caso i dati verranno assegnati nell'ordine in cui compaiono le colonne nella tabella e nel caso alcune saranno settate a null.

* esplicitiamo le colonne

```sql
INSERT INTO table2 (column1,column2,column3)
VALUES('x','y','z')
```
quei valori verranno inseriti in quelle tabelle in quell'ordine preciso

* inserimento su tabelle multiple

```sql
INSERT ALL
    WHEN condition1 THEN INTO table1 (column1, column2) VALUES (value1, value2)
    WHEN condition2 THEN INTO table2 (column3, column4) VALUES (value3, value4)
    ELSE INTO default_table (column5, column6) VALUES (value5, value6)
SELECT column7, column8
FROM source_table;
```
ha bisogno di una DUMMY QUERY

Dopo l'INSERT è necessario dare la conferma del'inserimento con il comando COMMIT per rendere gli inserimenti permaneni nel DB.

---

## UPDATE 

Serve per modificare i dati già presenti nel DB 

```sql
UPDATE table1
SET
    column1 = MODIFICA
    column2 = MODIFICA
WHERE condizione / (SubQuery)    
```

È possibile modificare più campi contemporaneamente ed è anche possibile utilizzare una SubQuery come filtro della condizione 

---

## DELETE

serve per cancellare in maniera permanente (dopo il COMMIT )i dati dal DB 

```sql
DELETE FROM table1
WHERE condizione (solitamente confronto)
```
Come il caso dell UPDATE è possibile utilizzare una SubQuery come filtro.

---
---