# DATABASE
Programmi che permettono la memorizzazione e la gestione (lettura, modifica, eliminazione) di dati

**vantaggi**
- possibilità di memorizzare grandi quantità di dati
- struttura ben organizzata ed ordinata
- veloce recupero dei dati
- sicuro
- backup e ripristino

# DBMS
Database Management System -> interfaccia software per creare, modificare e interrogare i database in modo sicuro ed efficiente

# Database Relazionali
Ad oggi è ancora il database più utilizzato.

**caratteristiche**
- **dati strutturati** -> i dati all'interno di un database sono organizzati in modo strutturato, spesso seguendo uno schema ben preciso
- **tabelle** -> principale rapprensentazione dei dati in un db relazionale. Ogni tabella è composta da righe(instanze di un dato) e colonne(attributi dei dati)
- **chiave primaria** -> attributo che identifica univocamente ogni riga in una tabella
- **chiavi esterne** -> utilizzate per creare relazioni tra tabelle
- **indici** -> strutture dati aggiuntive che facilitano la ricerca e l'accesso veloce ai dati
- **query** -> utilizzate per recuperare e gestire dati specifici da una o più tabelle in base a determinati criteri
- **operazioni CRUD** -> principali attività eseguite su un database: 
    * Create: aggiungere nuovi dati
    * Read: recuperare dati
    * Update: modificare dati
    * Delete: eliminare dati

# Relazioni fra tabelle
tre tipi di relazioni:
- **Uno a Molti**
- **Uno a Uno**
- **Molti a Molti**

# Database NoSQL
Utilizzati quando si ha bisogno di una maggiore flessibilità, per esempio quando i nostri dati non possono essere facilmente strutturati in schemi fissi.
Sono fortemente scalabili, performanti e adatti all'utilizzo in cloud.

# SQL(Structured Query Language)
Linguaggio utilizzato per gestire e manipolare i database relazionali. Le operazioni di base includono la creazione e gestione di tabelle, modifica della struttura dei database, l'inserimento di nuovi dati, l'aggiornamento e l'eliminazione di record, recupero dei dati etc...

il linguaggio si può dividere in:
- **Data Definition Language(DDL)** -> utilizzato per definire e modificare la struttura dei database, tabelle, viste, indici, vincoli etc...
- **Data Manipulation Language(DML)** -> utilizzato per consultare e manipolare i dati all'interno del database (es: SELECT, INSERT, UPDATE, DELETE)
- **Data Control Language(DCL)** -> utilizzato per gestire i diritti di accesso e i privilegi degli utenti (es: GRANT e REVOKE)
- **Transaction Control Language(TCL)** -> utilizzato per gestire le transazioni all'interno del database (es: COMMIT, ROLLBACK, SAVEPOINT)