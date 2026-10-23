# Importazione della versione attuale

Questa procedura serve a portare nel repository il gestionale già in uso senza interrompere il servizio né sovrascrivere la copia funzionante.

## Prima dell'importazione

1. Identificare il server e la cartella che contengono la versione effettivamente usata al banco. Non usare come fonte una copia di sviluppo o un archivio precedente senza confrontarla.
2. Annotare data, percorso, versione PHP, configurazione e dipendenze. Non copiare credenziali nel repository.
3. Creare una copia completa e datata del codice fuori dal repository, per esempio `gestionale-pre-git-AAAA-MM-GG/`. Fare anche un backup separato del database e conservarlo in un luogo protetto, non nel repository pubblico.
4. Verificare che il backup si apra e che i file principali siano presenti. Calcolare e conservare un checksum dell'archivio, ad esempio con `sha256sum nome-archivio.zip`.
5. Lavorare su una copia locale del backup, mai direttamente sulla cartella in produzione.

## Primo caricamento

1. Clonare il repository e controllare che `main` contenga solo i file iniziali di documentazione.
2. Estrarre il codice in una cartella di lavoro separata e confrontarlo con la copia funzionante: cercare file mancanti, versioni alternative e modifiche locali.
3. Prima di aggiungere i file, rimuovere dalla copia di lavoro credenziali, configurazioni locali, database, log, cache, file temporanei e dati personali. Conservare invece un esempio di configurazione senza segreti, se utile.
4. Aggiungere il codice rispettando inizialmente la struttura esistente. Non rinominare o spostare file e non correggere bug nello stesso commit dell'importazione.
5. Controllare l'elenco dei file in staging con `git status --short` e `git diff --cached --stat`; esaminare in particolare file ignorati e configurazioni.
6. Salvare una fotografia iniziale con un messaggio chiaro, ad esempio `Importa versione funzionante verificata YYYY-MM-DD`.
7. Eseguire i controlli PHP disponibili e una prova su ambiente di test con una copia del database anonimizzata. Verificare accesso, ricerca cliente, accettazione ordine, lavorazioni, consegna e pagamento.
8. Solo dopo il superamento delle verifiche, pubblicare il commit su `main` e creare un tag annotato, per esempio `baseline-2026-10-24`.

## Dopo il caricamento

La versione in produzione non va aggiornata automaticamente dal push. Ogni rilascio deve avere una copia di sicurezza, una prova in ambiente di test, una nota delle modifiche e una procedura di ritorno alla versione precedente.
