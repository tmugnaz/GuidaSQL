# Comandi
- **SELECT**
    * \*
- **DISTINCT** -> elimina i duplicati
- **FROM**
- **WHERE**
- **AS**
    * possiamo concatenare più colonne in un alias con **||**, es: SELECT codart || desc AS "descrizione lunga" FROM tabella
### Operatori logici
- **AND**
- **OR**
- **NOT** -> es: SELECT * FROM articoli WHERE NOT idiva = 22
---
- **BETWEEN...AND** -> seleziona un intervallo di valori(inclusi i limiti) in una tabella in base ad un criterio di confronto
- **LIKE** -> filtra i dati in base a un modello di stringa specifico
    * % -> es: ca% trova tutte le stringhe che iniziano con ca, per esempio cane, casa, etc...
    * _ -> es t_st trova tutte le stringhe che hanno "t" come primo e quarto char e "s" come terzo, per esempio test, tasti, etc...
- **IS NULL**
- **IS NOT NULL**
- **IN** -> si utilizza quando abbiamo molte opzioni, es: SELECT * FROM clienti WHERE comune in ('NORDELLO', 'SODDI', 'NULVI', 'BIDONI')
- **NOT IN**
- **ORDER BY**
  * **DESC**
  * **ASC** -> default
- **FETCH FIRST...ROWS ONLY** -> limita il numero di righe restituite da una query, es: SELECT * FROM movimenti ORDER BY venduto DESC FETCH FIRST 10 ROWS ONLY
- **OFFSET...ROWS...FETCH NEXT...ROWS ONLY** -> ci permette di partire da un determinata row, es: partire dalla 20° riga e selezionare le successive 50 righe SELECT * FROM movimenti OFFSET 19 ROWS FETCH NEXT 50 ROWS ONLY

 # Concetti
 - **ALIAS** -> etichette che possiamo dare alle colonne per renderli più leggibili
 - **<>** -> è equivalente a !=
 - **NULL** -> quando un campo è NULL vuol dire che non è stato inserito alcun valore
 - **single-quotes vs double-quotes** -> Single-quotes are used to enclose string literals (and, in recent versions, DATE literals). Double-quotes are used to enclose identifiers (like table and column names)