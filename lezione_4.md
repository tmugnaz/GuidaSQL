# Comandi
- **UNION** -> combina i dati provenienti da due o più query in un unico recordset
    * ALL -> determina se veranno inclusi o meno i duplicati
- **MINUS(EXCEPT)** -> si ottengono i dati provenienti dalla prima query ma che non sono presenti nella seconda query. Minus è la sintassi utilizzato da Oracle
    * ALL
- **INTERSECT** -> restituisce solo i record distinti comuni a tutte le SELECT, rimuovendo automaticamente i record duplicati dal result set

### NOTA
Quando si fa UNION, MINUS o INTERSECT dobbiamo avere dei SELECT che abbiano lo stesso numero di colonne