# Backup e versioni

## Copie di sicurezza

Mantenere almeno:

- una copia del codice funzionante prima di ogni rilascio;
- un backup del database, creato con strumenti compatibili con il database in uso;
- una copia in un luogo diverso dal server applicativo, protetta e con accesso limitato.

Usare nomi datati e non ambigui, ad esempio `codice-AAAA-MM-GG.zip` e `database-AAAA-MM-GG.sql.gz`. Cifrare i backup che contengono dati personali. Verificare periodicamente che sia possibile ripristinarli su un ambiente di prova.

GitHub conserva la storia del codice, ma non sostituisce il backup del database o una copia indipendente. Non caricare backup, database reali o dati dei clienti nel repository pubblico.

## Versioni del codice

- `main`: versione controllata e pronta per il rilascio.
- `feature/nome-breve` o `fix/nome-breve`: branch temporaneo per singole modifiche.
- Tag annotati: punti di riferimento per la versione funzionante e per ogni rilascio, ad esempio `baseline-2026-10-24` e `v1.0.0`.

Dopo ogni rilascio, conservare il tag e il backup esterno corrispondente. Non riscrivere la storia di `main` con force push.

## Rilascio e ritorno indietro

1. Fare backup separati di codice e database.
2. Provare la modifica su ambiente di test con dati non reali.
3. Annotare commit, data e modifiche incluse.
4. Rilasciare il codice con una procedura controllata.
5. Verificare le funzioni essenziali e registrare l'esito.
6. Se la verifica fallisce, ripristinare il codice dal tag precedente. Ripristinare il database solo se la modifica ne ha cambiato lo schema e il piano di rollback lo richiede.
