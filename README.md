# Gestionale lavanderia

Repository del gestionale della lavanderia.

## Stato iniziale

Il repository parte con la documentazione e le regole per importare in sicurezza il codice esistente. Il codice applicativo va aggiunto solo dopo aver identificato la copia effettivamente in uso e averne creato una copia di sicurezza verificabile.

## Struttura prevista

```text
app/                 codice applicativo PHP, organizzato per funzionalità
config/
  config.example.php esempio senza credenziali
database/
  migrations/        modifiche versionate allo schema
  seeds/             dati dimostrativi e non personali
public/              punto di ingresso e risorse pubbliche
  assets/
docs/                installazione, backup, rilascio e note operative
tests/               verifiche automatizzabili, quando presenti
```

La disposizione definitiva va adattata ai percorsi reali dell'applicazione durante l'importazione: non spostare file o cambiare configurazioni nello stesso passaggio del primo salvataggio.

## Regole essenziali

- Non versionare credenziali, file `.env`, database di produzione, esportazioni clienti, ricevute o backup contenenti dati reali.
- Mantenere una copia esterna e datata della versione funzionante prima di ogni importazione o modifica.
- Il primo commit del codice deve rappresentare una fotografia della versione verificata, senza modifiche funzionali.
- Le modifiche successive vanno fatte su branch dedicati e integrate in `main` solo dopo il controllo.

Consulta [Importazione della versione attuale](docs/importazione-versione-attuale.md) e [Backup e rilasci](docs/backup-e-rilascio.md).
