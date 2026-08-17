# 1 — Trasforma la chat AI in una base per un Email Manager Gmail

Parti dall'applicazione di chat AI già esistente e trasformala progressivamente in un **AI Email Manager per Gmail**, mantenendo l'interfaccia di chat come elemento principale.

In questo primo passaggio prepara l'architettura e l'interfaccia di base senza implementare ancora tutte le funzioni avanzate.

L'applicazione deve:

- mantenere la chat AI esistente;
- aggiungere una modalità/sezione dedicata a Gmail;
- avere una schermata iniziale chiara per utenti non autenticati;
- mostrare un pulsante **"Sign in with Google"**;
- usare esclusivamente il normale flusso OAuth di Google;
- NON chiedere all'utente API key, token, password Gmail o altre credenziali;
- non utilizzare password applicative;
- gestire autenticazione e autorizzazioni tramite Google OAuth;
- richiedere solamente permessi compatibili con un'applicazione **read-only**;
- non richiedere mai permessi per inviare, modificare o cancellare email;
- predisporre il backend per conservare in modo sicuro la sessione OAuth;
- prevedere il logout.

Per Gmail usa il principio del minimo privilegio, preferendo lo scope:

`https://www.googleapis.com/auth/gmail.readonly`

insieme agli scope strettamente necessari per identificare l'utente.

L'utente non deve vedere o inserire chiavi API. Eventuali configurazioni OAuth necessarie all'applicazione, come Client ID e redirect URI, devono essere considerate configurazione dell'applicazione e non credenziali richieste all'utente finale.

Crea inoltre una struttura dell'interfaccia composta da:

- header;
- area principale della chat;
- area Gmail;
- stato di autenticazione;
- avatar/account Google quando autenticato;
- comando Logout.

Mantieni il codice semplice e modulare perché nei prossimi passaggi aggiungeremo accesso alla mailbox, ricerca e AI.

L'interfaccia deve essere progettata fin dall'inizio come responsive, senza larghezze rigide che possano impedire l'utilizzo su schermi piccoli.

Alla fine implementa realmente questo primo passaggio nel progetto esistente, senza limitarti a descrivere cosa fare.

---

# 2 — Collega Gmail e costruisci la mailbox read-only

Partendo esattamente dal risultato del passaggio precedente, completa l'integrazione Gmail usando l'utente autenticato tramite Google OAuth.

Non introdurre API key da inserire manualmente.

Dopo il login, l'applicazione deve poter accedere alla mailbox Gmail autorizzata dall'utente esclusivamente in lettura.

Implementa una vera sezione email che permetta di:

- caricare la lista dei messaggi;
- mostrare mittente;
- mostrare destinatari quando disponibili;
- mostrare subject;
- mostrare data e ora;
- mostrare una breve preview/snippet;
- distinguere messaggi letti e non letti se l'informazione è disponibile;
- aprire un messaggio;
- visualizzare il contenuto completo;
- visualizzare correttamente email plain text;
- visualizzare in modo sicuro email HTML;
- mostrare thread/conversazioni quando opportuno;
- gestire paginazione o caricamento progressivo;
- gestire loading state;
- gestire mailbox vuota;
- gestire errori e sessione scaduta.

Aggiungi filtri utilizzabili dall'interfaccia per:

- mittente;
- destinatario;
- parole nel subject;
- testo;
- data;
- email non lette;
- email con allegati;
- label Gmail.

Non implementare nessuna possibilità di:

- inviare email;
- rispondere;
- inoltrare;
- creare bozze;
- cancellare messaggi;
- archiviare messaggi;
- modificare label;
- segnare come letto/non letto.

L'applicazione è un **AI Email Manager strettamente read-only**.

Mantieni la chat AI esistente e prepara un livello applicativo pulito che permetta alla chat, nel prossimo passaggio, di interrogare i dati Gmail senza mettere la logica Gmail direttamente nei componenti UI.

Alla fine implementa e prova il flusso:

Login Google → apertura mailbox → lista email → filtro → apertura email → logout.

---

# 3 — Permetti di interrogare Gmail attraverso la chat AI

Partendo dall'applicazione funzionante del passaggio precedente, collega la chat AI alla mailbox Gmail.

L'obiettivo è permettere all'utente di fare domande naturali sulle proprie email, per esempio:

- "Quali email importanti ho ricevuto oggi?"
- "Mostrami le email ricevute da Mario questa settimana."
- "Cosa mi ha scritto Luca riguardo al contratto?"
- "Ci sono email di Google negli ultimi 30 giorni?"
- "Trova le email che parlano della fattura di luglio."
- "Riassumi la conversazione con Paolo sul progetto."
- "Quali email non lette parlano di pagamenti?"
- "Quando mi hanno mandato l'ultima email relativa a Nuvolaris?"
- "Fammi un riepilogo delle email ricevute ieri."
- "Cerca tutte le email relative alla riunione di venerdì."

Implementa un sistema nel quale il modello AI NON riceva indiscriminatamente l'intera mailbox.

Il flusso deve essere:

1. interpretazione della richiesta dell'utente;
2. conversione della richiesta in criteri di ricerca Gmail;
3. recupero solamente delle email necessarie;
4. estrazione del contenuto rilevante;
5. passaggio del minimo contesto necessario al modello;
6. risposta nella chat.

Crea strumenti/funzioni interne che il livello AI possa usare, ad esempio:

- searchEmails
- getEmail
- getThread
- getRecentEmails
- getUnreadEmails
- searchBySender
- searchByDateRange

Il modello deve poter scegliere quali strumenti usare in funzione della domanda.

Quando la risposta deriva dalle email, mostra anche riferimenti alle email utilizzate, per esempio:

- mittente;
- subject;
- data;
- collegamento/apertura del messaggio nell'interfaccia.

Quando possibile, rendi cliccabili i riferimenti nella risposta della chat così che selezionandoli venga aperta l'email corrispondente nell'Email Manager.

La chat non deve mai avere strumenti che permettano di modificare Gmail.

Mantieni quindi completamente assenti azioni come send, delete, archive, modify, draft o reply.

Gestisci anche domande alle quali non è possibile rispondere: in quel caso l'AI deve dichiarare che non ha trovato informazioni sufficienti invece di inventarle.

Alla fine implementa realmente queste funzionalità e verifica il funzionamento con diversi tipi di ricerca.

---

# 4 — Trasforma l'app in un vero Email Manager AI responsive

Partendo dal risultato precedente, migliora completamente l'esperienza utente rendendo l'applicazione utilizzabile come prodotto reale su smartphone, tablet, notebook e desktop.

L'interfaccia deve adattarsi fluidamente almeno a:

- smartphone molto piccoli;
- smartphone Android comuni;
- iPhone;
- dispositivi presenti nelle dimensioni tipiche della Device Toolbar/DevTools;
- tablet portrait;
- tablet landscape;
- notebook;
- desktop 1080p;
- monitor larghi.

Non progettare solamente per breakpoint specifici: usa un layout realmente fluido.

Su desktop utilizza preferibilmente una struttura tipo:

sidebar / mailbox | contenuto email | chat AI

oppure una variante equivalente che massimizzi lo spazio disponibile.

Su tablet riduci automaticamente il numero di pannelli simultanei.

Su smartphone:

- mostra un pannello principale alla volta;
- evita scroll orizzontale;
- usa navigation appropriata;
- permetti di passare facilmente tra Chat, Email e ricerca;
- usa controlli sufficientemente grandi per il touch;
- mantieni sempre accessibile il campo della chat senza coprire contenuti;
- considera la tastiera virtuale;
- considera safe areas e viewport mobile;
- evita elementi che escano dallo schermo.

Implementa inoltre:

- sidebar responsive;
- ricerca email;
- pannello filtri;
- lista risultati;
- visualizzazione email;
- riferimenti alle email nelle risposte AI;
- indicatori di caricamento;
- empty states;
- error states;
- menu account;
- logout.

Il design deve essere semplice, moderno e orientato alla produttività.

Verifica esplicitamente che nessuna parte dell'applicazione permetta di scrivere, rispondere, inoltrare, cancellare o modificare email.

Fai una revisione responsive completa usando varie dimensioni di viewport e correggi overflow, layout spezzati, elementi troppo piccoli, testi non leggibili e problemi con la tastiera mobile.

Alla fine lascia l'applicazione completamente funzionante e non limitarti a produrre mockup.

---

# 5 — Completa, testa e rendi production-ready l'AI Gmail Manager read-only

Partendo da tutto ciò che è stato costruito nei quattro passaggi precedenti, esegui una revisione completa e porta l'applicazione a uno stato production-ready.

Il prodotto finale deve permettere questo flusso:

1. utente non autenticato;
2. click su "Sign in with Google";
3. autenticazione e consenso Google;
4. ritorno automatico nell'app;
5. accesso read-only alla propria casella Gmail;
6. navigazione delle email;
7. ricerca e filtraggio;
8. apertura dei messaggi;
9. utilizzo della chat AI;
10. domande in linguaggio naturale sulle email;
11. ricerca automatica delle email necessarie;
12. risposta AI basata esclusivamente sulle informazioni recuperate;
13. apertura delle email citate dalla risposta;
14. logout;
15. invalidazione/pulizia corretta della sessione locale.

Controlla in particolare sicurezza e privacy.

Assicurati che:

- non vengano richieste API key all'utente;
- non vengano richieste password Gmail;
- OAuth sia l'unico metodo di autorizzazione Gmail;
- venga richiesto esclusivamente accesso read-only;
- i token non vengano esposti nel frontend, nei log o nella UI;
- i token siano trattati e conservati in modo sicuro;
- il frontend non possa richiedere arbitrariamente token OAuth;
- logout e scadenza sessione siano gestiti correttamente;
- gli errori OAuth siano gestiti;
- le risposte AI non inventino email inesistenti;
- venga recuperata solamente la quantità di contenuto Gmail necessaria alla domanda;
- contenuti HTML delle email vengano visualizzati in sicurezza;
- nessun contenuto proveniente da una email venga interpretato come istruzione privilegiata per il sistema AI;
- eventuali prompt injection contenute nelle email siano trattate come semplice contenuto non affidabile.

Aggiungi test per:

- login;
- callback OAuth;
- sessione;
- logout;
- caricamento Gmail;
- ricerca;
- filtri;
- apertura email;
- thread;
- chat;
- ricerca AI;
- email inesistente;
- nessun risultato;
- token scaduto;
- errore Gmail;
- comportamento su mobile;
- comportamento su tablet;
- comportamento su desktop.

Verifica inoltre tutti i breakpoint e diverse dimensioni della Device Toolbar dei browser.

Non aggiungere funzionalità di scrittura.

Il prodotto finale deve restare deliberatamente limitato a:

**READ → SEARCH → FILTER → ASK AI → SUMMARIZE → FIND → NAVIGATE**

e non deve implementare:

**SEND → REPLY → FORWARD → DRAFT → DELETE → ARCHIVE → MODIFY**

Alla fine esegui una revisione dell'intero progetto, elimina codice morto o duplicato, correggi errori, assicurati che login Google, Gmail, AI chat, responsive layout e logout funzionino insieme e restituisci l'applicazione completa e funzionante.
