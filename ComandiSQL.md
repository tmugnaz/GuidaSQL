
# APPUNTI SQL  

### COMANDI BASE  *SELECT* E *FROM*

```SQL
SELECT   
```

Serve ad indicare le colonne che ci interessano da tabelle che ci interessano grazie al comando

``` SQL
FROM
```

Indica appunto le tabelle che vogliamo andare ad analizzare, modificare lavorare in generale.

 **Es.**

```SQL
    SELECT 
        <colonna1>
    FROM
        <tabella1>
```

---
**DISTINCT** -> specifica per il SELECT , indica che devono essere visualizzati solo dati provenienti da quella colonna che sono diversi l'uno dall'altro --> devono essere appunto distinti

```SQL
    SELECT DISTINCT 
        <colonna1>
    FROM 
        <tabella1>

```

---

### WHERE

Serve a filtrare dati dalla tabella che il from referenzia
utilizzato con:

- Confronto tra valore -> colonna1 = X (< , > , <> [diverso], <=, >=)

- Operatori logici -> X **AND** Y  (*OR*, *NOT* )

- Funzioni di Confronto -> colonna **BETWEEEN** X **AND** Y;
- Controllo su valori  ->  colonna **IN / NOT IN** ('nome1', 'nome2', etc)
- Filtro su modello di Stringa -> key word **LIKE** operatoti % e _

Il carattere % si riferisce ad un qualsiasi numero di carattere può essere usato sia all'inizio che alla fine di un pezzo di stringa

            WHERE colonna1 LIKE ('Ca%')

darà come true tutti le stringhe che iniziano per **Ca** : cane , casa , cavallo etc

_ si riferisce ad un singolo carattere che deve essere "riempito"

            WHERE colonna1 LIKE ('C__a')                    

in questo caso darà come risultato tutti i valori nel db che rispettano quelle condizioni ovvero che hanno al Primo posto una C e al quarto posto una A ad esempio casa , cava etc tutte da 4 caratteri

viene usato anche per cercare record che hanno nel nome un apostrofo che da noia al programma chiudendo gli apici nella parentesi

        WHERE acqua LIKE ('Sant_Anna')

esiste anche la condizione IS NULL E IS NOT NULL  serve a vedere se un dato campo ha come valore l'assenza del valore ovvero che ancora non è stato inserito (null);

**ES.**

```SQL
 SELECT 
    <colonna1>,
    <colonna2>
 FROM
    <tabella1>
 WHERE 
    <colonna1> = <valore>
    AND 
    <colonna2> >= <valore>

```

---

### ALIAS

A volte le Query iniziano a diventare complesse ed è difficile tenere traccia di quale campo appartiene a quale tabella, oppure per 'utente finale sarà complicato decifrare i titoli dei campi come REF_CP; per queste occasioni possiamo usare gli **ALIAS**

Parola chiave è AS da scrivere dopo la dichiarazione della colonna durante la SELECT

può essere seguita da una stringa singola oppure da una stringa compresa tra due apici "" se è complessa

è possibile concatenare diverse colonne in una sola usando i i simpoli || ' ' || tra i nomi delle colonne ( in questo caso ' ' significa spazio vuoto, avrei potuto mettere anche '-' trattino tra i due)

**ES**

```SQL
SELECT 
        <colonna1> AS "unità di misura",
        <colonna2> || '-' || <colonna3> AS  confronto

```

### ORDER BY

Serve a riordinare il risultato della Query in ordine secondo una colonna specifica

viene usato dopo il filtro della **WHERE**
 
```SQL
WHERE   
    <condizione>
GROUP BY 
    <colonna> DESC;    

```

Puo essere seguito dalle KEyword **DESC** per un ordine Decrescente o **ASC** per un ordine crescente.
Di base però l'ordine sarà crescente;

---

### FETCH FIRST ROWS

Limita il numero di Righe restitutite dalla Query
Vene usato dopo il **Order by**

```SQL
-- Seleziona le prime 10 righe dalla tabella products
SELECT product_id, product_name
FROM products
ORDER BY product_id
FETCH FIRST 10 ROWS ONLY;

```
Può essere usato insieme al comando **OFFSET** per far iniziare la restituzione della Query dalla riga del numero selezionato, può anche essere concatenato in questo modo:
```SQL
-- Seleziona la seconda pagina di 10 prodotti (record da 11 a 20)
SELECT product_id, product_name
FROM products
ORDER BY product_id
OFFSET 10 ROWS
FETCH FIRST 10 ROWS ONLY;

```

---
---



