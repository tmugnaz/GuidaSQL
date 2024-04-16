# Comandi
### Funzioni di aggregazione
- **AVG** -> media
- **SUM** -> somma
- **MIN** -> valore minimo
- **MAX** -> valore massimo
- **COUNT([DISTINCT])** -> calcolo il numero degli elementi(con o senza duplicati), es: SELECT COUNT(DISTINCT CODFID) as "Numero clienti" FROM ...
- **COUNT(*)** -> calcolo il numero totale delle righe
---
- **GROUP BY** -> raggruppa i record
- **HAVING** -> utilizzato con GROUP BY per filtrare i risultati
- **ROLLUP** -> estende GROUP BY attraverso la creazione di sub total rows e grand total rows
- **CUBE** -> estende GROUP BY

# Concetti
Con SQL possiamo anche aggregare i dati per ottenere utili informazioni statistiche.

### Link utili
ROLLUP -> https://docs.oracle.com/cd/F49540_01/DOC/server.815/a68003/rollup_c.htm#32084 \
CUBE -> https://docs.oracle.com/cd/F49540_01/DOC/server.815/a68003/rollup_c.htm#32311
