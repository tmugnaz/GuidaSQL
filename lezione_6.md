# Comandi
### Parametri per le subquery
- **ALL** -> Viene utilizzata insieme agli operatori di confronto all'interno delle subquery per specificare che una condizione deve essere vera per tutti i valori restituiti dalla subquery. Confronta un singolo valore con ciascun valore nel set di risultati della subquery e restituisce vero se la condizione è vera per tutti i valori, altrimenti falso.
- **ANY** -> Viene utilizzata insieme agli operatori di confronto all'interno delle subquery per specificare che una condizione deve essere vera per almeno un valore restituito dalla subquery. Confronta un singolo valore con ciascun valore nel set di risultati della subquery e restituisce vero se la condizione è vera per uno qualsiasi dei valori, altrimenti falso.

# Concetti
- **SUB QUERY** -> ci consente di utilizzare il risultato di una query come input per un'altra query. Le subquery sono messe tra parentesi
 * **SEARCH con IN** -> subquery eseguite come argomento di filtri
 * **FROM** -> subquery eseguite come sostituti di una o più tabelle
- **QUERY COMPLESSE** -> combinazione di più query e subquery
- **SUBQUERY FACTORING(CTE) con WITH** -> La fattorizzazione delle subquery, nota anche come Common Table Expressions (CTE), è una funzionalità di SQL che consente di definire set di risultati denominati temporanei (subquery) all'interno di una query, semplificando la scrittura e la lettura di istruzioni SQL complesse. È particolarmente utile quando è necessario fare riferimento alla stessa subquery più volte all'interno di una singola query.