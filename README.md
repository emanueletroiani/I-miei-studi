le iniezioni SQL si verificano quando il codice SQL e i dati dell'utente vengono mescolati insieme ciò consente agli aggressori di iniettare codice per modificare la struttura dell'istruzione SQL per rubare dati modificare dati e persino inserire comandi di sistema. 

SQL è essenzialmente un linguaggio di programmazione quindi le tue query SQL sono essenzialmente un programma e quando una query SQL arriva al server SQL, il server analizzerà la compilazione, la eseguirà e restituirà i risultati dell'esecuzione.  

Sfrutta vulnerabilità del linguaggio SQL utilizzando delle query per ottenere **dati** dal **database** di **back**-**end**. Come:

- Le credenziali di tutti gli utenti
- I dati dell’applicazione
- Le informazioni sulle carte di credito degli utenti
- Le transazioni degli ordini di acquisto degli utenti

# Cosa si intende per Database?

Un database è una **collezione** di **oggetti** che viene **gestita** ed **organizzata da** un **software** chiamato **DBMS**, DataBase Management System, ovvero sistema di gestione di database. Vediamo il relazionale che è quello piu utilizzato.

# **Database relazionali**

I database relazionali sono un tipo di database che **organizzano** i **dati in tabelle** con **righe** e **colonne**.  **I database relazionali utilizzano il linguaggio SQL (Structured Query Language)** per interrogare e manipolare i dati.

- **Tabelle**: I **dati** sono **organizzati in tabelle**, che sono strutture bidimensionali **composte** da **righe** e **colonne**. **Ogni tabella rappresenta un'entità** o un **concetto**, come ad esempio un cliente, un ordine, un prodotto, ecc.
- **Righe e Colonne**: Le **righe** delle tabelle **rappresentano** istanze o **record** specifici **di quell'entità**, mentre le **colonne rappresentano** gli **attributi** o le **caratteristiche** di **quell'entità**. Ad esempio, in una tabella "Cliente", ogni riga potrebbe rappresentare un cliente specifico e ogni colonna potrebbe rappresentare informazioni come il nome, l'indirizzo, il numero di telefono, ecc.
- **Chiavi Primarie**: Ogni **tabella** ha una **chiave primaria**, che è un attributo univoco **utilizzato** per **identificare** in modo univoco **ogni riga** nella tabella. La chiave primaria è **fondamentale** per garantire **l'integrità** dei **dati** e per **consentire relazioni tra** le **tabelle**.
- **Relazioni tra Tabelle**: I database relazionali consentono di stabilire relazioni tra le tabelle. Ad **esempio**, una tabella "**Ordine**" potrebbe essere **collegata** a una tabella "**Cliente**" **attraverso** una **chiave esterna** che identifica il cliente associato a ciascun ordine.
- **Integrità Referenziale**: Le relazioni tra le tabelle possono essere vincolate per mantenere l'integrità referenziale dei dati. Ciò significa che non è possibile eliminare o modificare un record in una tabella padre se ci sono record correlati nelle tabelle figlio.
- **Linguaggio SQL**: Il linguaggio SQL è **utilizzato** per **interrogare** e **manipolare** i **dati** nei database relazionali. SQL fornisce **comandi** per **selezionare**, **inserire**, **aggiornare** e **eliminare dati**, nonché per **definire** la **struttura** del **database**, le **relazioni** e le **regole** di **integrità**.

![Untitled](https://github.com/user-attachments/assets/ef8bf97b-5764-467d-90c9-9d491ba14538)

- La tabella "**Cliente**" ha una **chiave primaria** "**ID**" univoca per identificare ogni cliente. (numeri in tabella sono la chiave)
- La tabella "**Ordine**" ha una **chiave primaria** "**ID**" univoca per identificare ogni ordine e una **chiave esterna** "**Cliente_ID**" che fa **riferimento all'ID** del **cliente associato** a **quell'ordine**.
- La relazione tra le tabelle è stabilita dalla chiave esterna "Cliente_ID" nella tabella "Ordine", che si riferisce all'ID del cliente nella tabella "Cliente".

Ogni **cliente** può avere **molti ordini**, ma **ogni ordine** è **associato** solo **a** un **cliente specifico**.

# Come si forma una query

Utilizzando una **query** potremo **richiamare** dei **dati** all’interno dei **database** delle **web app**. Per fare ciò dovremo prima **collegarci** al **database**, **inviare** la **query** e poi **otterremo** i **dati** nella nostra **Shell.**

Ci sono 2 tipologie di comandi:

- **SELECT** Si utilizza per recuperare informazioni.
- **UNION** Unisce piu query in un unico comando

## I commenti in SQL

Ci sono diversi modi di scrivere i commenti in SQL. Si può utilizzare:

- **#** il carattere cancelletto
- **--**  due trattini continui, **seguiti** da uno **spazio**

## Esempio

### **TABELLA N1**

![Untitled](https://github.com/user-attachments/assets/6ce266d3-4b8b-430c-8b80-9f0c39910243)

### **TABELLA N2**

![Untitled](https://github.com/user-attachments/assets/8a20a768-e57f-49b2-a70a-075e5632608c)

Esempio di **SELECT** 

- **SELECT** Nome, Descrizione **FROM** Prodotti **WHERE** id=1

![Untitled](https://github.com/user-attachments/assets/3f444464-2a40-4dae-b5a9-c95d3bd8c0fa)

- **SELECT** Nome, Descrizione **FROM** Prodotti **WHERE** id=1  **UNION SELECT** Username, Password **FROM** Utenti

![Untitled](https://github.com/user-attachments/assets/3f8f4c82-08fe-4889-bd99-e3bf82e25320)

# Ottenere tutti i dati di di una colonna o di un campo di ricerca.

Utilizzando un **query** che **composta** da un operatore logico **OR** che dia un **comando sempre vero**. ES 1=1 oppure ciao=ciao etc 

- **SELECT** Nome, Descrizione **FROM** Prodotti **WHERE** ID=’ ’ OR ‘1’=1’;
    - Il campo **ID** deve essere **vuoto ID= ‘ ‘** Oppure (OR)
    - Una condizione sempre vera **a = a**

la query sopra chiede al database di **selezionare tutte** le **entry** della **tabella Products**!

# Sfruttare le query per gli attacchi

1. **Commento -- -** la punteggiatura è fondamentale. si commenta con -- -  e tutto ciò che viene messo dopo vorrà dire che non interessa al database. ES: se conosciamo l’username di un utente possiamo accede con questa query
- **NOME_UTENTE’-- -**
    - se richiede anche la password per loggare possiamo mettere qualsiasi cosa tanto non la conta perchè è commentata.
1. **' OR 1=1-- -**

Supponiamo di avere un'applicazione web con una pagina di login che prende un username e una password. La query SQL utilizzata per verificare le credenziali dell'utente potrebbe sembrare simile a questa:

```sql
SELECT * FROM users WHERE username = 'input_username' AND password = 'input_password';

```

### Attacco

Un malintenzionato potrebbe inserire il seguente input nel campo dell'username:

```sql
' OR 1=1-- -

```

E lasciare il campo della password vuoto. La query risultante sarebbe:

```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';

```

### Spiegazione

La condizione `'1=1'` è sempre vera, quindi la query selezionerà tutte le righe nella tabella `users`, permettendo all'attaccante di accedere senza una password valida.

1. **‘ order by NUMERO**

Qui andiamo a capire, tramite tentativi (errori), quante colonne ha il database. Ricordiamoci che il database a volte non utilizza numeri ma NULL session, ogni NULL sostituisce un numero progressivo. (1,2,3=NULL,NULL,NULL)

- Scriviamo nell’URL
    - **‘ order by 1**
    - **‘ order by 2**
    - **‘ order by 3**
    - **‘ order by 4**

sino a quando non ci darà la conferma che ci sono le suddette colonne.

# Protezione contro SQL Injection

Per proteggere l'applicazione da SQL Injection, si dovrebbero adottare le seguenti misure:

**Parametrizzazione delle Query**:

- **Sanificazione degli Input**: Assicurarsi che gli input degli utenti contengano solo dati validi e sicuri. La sanificazione degli input può includere la **rimozione di caratteri speciali,** l'escape di s**tringhe potenzialmente pericolose** e la **validazione del tipo e della lunghezza dei dati.** Implementare rigidi controlli sugli input non solo protegge dal SQL Injection, ma migliora anche la qualità complessiva dei dati nel sistema.
- **Parametrizzazione delle Query (prepared statement):** il codice sql verrà scritto in modo che il server interpreterà la query in modo diverso ovvero: In un prepared statement la query viene divisa in 2, una parte logica e una parte dai dati immessi dall’utente che verrà sostituita con dei segnaposto (nel codice sql è il ?) che vengono poi sostituiti con i valori reali in modo sicuro dal sistema di gestione del database.  Questo significa che invece di passare una query SQL completa al server, tutto ciò che non era nella istruzione di origine verrà trattato come dati di stringa e non come codice SQL eseguibile. ES: se un aggressore dovesse immettere l'ID utente di `tom' or '1'='1`, la query parametrizzata cercherebbe un nome utente che corrispondesse letteralmente all'intera stringa `tom' or '1'='1`

