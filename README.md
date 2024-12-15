# Layer 1 Fisico

Permette la **trasmissione** dei dati tramite **segnali elettrici**, occupandosi della forma e dei livelli di tensione del segnale tramite **fibra ottica** o **cavi** in rame, frammentando l'informazione del computer sorgente in Bit.

# **Livello 2: DataLink**

Qui si parla di **Frame**
Si occupa di spacchettare in **Frame** i bit del livello 1 per inviarli al livello3. **Fa da ponte.**

Inoltre **verifica** e **gestisce** gli **errori di sua competenza**, se ad esempio un pacchetto è danneggiato lo elimina o lo farà rispedire. Quindi **è responsabile della comunicazione degli Host** **della stessa rete** (Lan) tramite l'indirizzo MAC (indirizzo fisico della scheda di rete, ad esempio io ho 2 MAC, una scheda di rete Ethernet e una wifi).

A questo livello lavorano gli **switch (legge gli indirizzi MAC)**: un **dispositivo** di rete **che** serve per **connette**re **piu** dispositivi facendoli scambiare dati tramite L’ **indirizzo MAC** della loro scheda di rete, dispone di porte ethernet alle quali è possibile connettersi con il classico cavo. Unendo **troppi dispositivi** **allo stesso switch** si può incorrere a **latenza**. **Per evitare** questo si possono **frammentare le reti Lan con reti vistuali (Vlan)**, in questo modo s**i può decide** quali **gruppi** di **pc** possono c**omuncare tra di loro**.
Alcuni Protocolli del livello 2 sono:

- **Ethernet IEEE 802.3**: **Ethernet** si riferisce a una **tecnologia** che **consente** ai **dispositivi all’interno** di **reti cablate** di **comunicare** tra loro. I dispositivi collegati in Ethernet possono quindi formare una rete e scambiare pacchetti di dati. Ciò crea una rete locale (LAN) su connessioni
Ethernet. Ha ampiamente sostituito le tecnologie LAN cablate concorrenti come Token ring, FDDIe ARCnet. E’ considerata una delle tecnologie chiave che compongono internet.
- **Token Ring**: IEEE 802.5: al suo posto è entrato il protocollo ethernet. Token ring è una rete locale dove i PC comunicano ad anello, ovvero a DX e SX, nel caso un pc smette di riceve pacchetti o di funzionare si blocca l’intera rete.
- **MAC**: media access control identifica universalmente la scheda di rete di un Host, è un codice a 48 bit esadecimale univoco che viene fisicamente assegnato dal produttore in fase di fabbricazione
- **LLC 802.2**: Logical link control è a **diretto contatto con il Livello 3** e si preoccupa di fare due cose 1 **Regola il controllo del Flusso dei dati** e si occupano della **gestione degli ACK**. Il ruolo di LLC, infatti, è di nascondere al livello di rete le differenze che esistono tra i vari protocolli [802.In](http://802.in/) questo modo, il livello di rete viene completamente isolato dal mezzo trasmissivo
attraverso il quale avviene la trasmissione dei dati. I dati provenienti dal livello superiore vengono incapsulati in una unità di trasmissione del livello LLC e opportunamente trasferiti al livello MAC, che ne cura la trasmissione sul mezzo fisico prescelto; viceversa, le unità di trasmissione provenienti dal livello MAC vengono elaborate secondo i criteri definiti dal protocollo e quindi inoltrate al livello superiore.
- **ARP**: Address resolution protocol **serve per mappare l’indirizzo IP con l’indirizzo fisico MAC.**
Nel caso in cui un **Host debba comunicare ad un pc solo conoscendo l’indirizzo IP,** il protocollo **ARP invia** una **ARP request** **contenente** il proprio **indirizzo MAC** **e l’indirizzo IP del destinatario a tutti i pc collegati dallo switch**. Ogni Host verifica se l’indirizzo IP della ARP request combacia con il suo, solo **l’Host che possiede quell’indirizzo IP risponde tramite una
ARP replay contenente il proprio indirizzo MAC** in modalità unica. Ogni host conserva nella cache una tabella di indirizzo MAC, prima di inviare una ARP request verifica se è già presente nella cache. La Tabella ARP si rigenera ogni 5 minuti e può essere verificata tramite il comando ARP -a

# Il livello 3 **Rete**

Qui si parla di **Pacchetti o Datagrammi**

Il livello di rete **determina il percorso** dei pacchetti (**datagrammi**) **attraverso** il **Router** che permette il collegamento tra due dispositivi appartenenti a reti differenti. Ci riesce tramite  gli Indirizzi IP dell’host sorgente e dell’host destinatario.

[Approfondimento IP: Internet Protocol](https://github.com/emanueletroiani/Network/blob/IP-Internet-Protocol/README.md)

# Il livello 4 **Trasporto**

Qui si parla di **Segmenti**

In questo layer si parla di **Segmenti in TCP o Datagrammi in UDP e** si garantisce una **connessione end to end.**

Il Protocollo di Controllo di Trasmissione (**TCP**) e il Protocollo Datagramma Utente (**UDP**) **sono** due **protocolli di comunicazione** fondamentali all'interno della suite di protocolli di Internet (TCP/IP), ma **differiscono in** diversi aspetti, tra cui **affidabilità, orientamento alla connessione, gestione degli errori e altre caratteristiche.** Ecco una panoramica delle differenze principali tra TCP e UDP:

![Untitled](https://github.com/user-attachments/assets/d326716d-6a72-48bc-83c2-ef5e5b2466c8)

**Utilizzo tipico:**

- **TCP:** È spesso **utilizzato** in applicazioni che richiedono una comunicazione **affidabile** e in **ordine**, che **controlli** gli **errori** dei pacchetti affinchè arrivi tutto perfetto e in **ordine** con un **flusso di scambio regolare,** in caso di errore si fa rispedire il segmento. come il **trasferimento di file, la navigazione web e l'invio di e-mail.** Header è composto da 20 Byte
- **UDP:** Non ha una connessione, manda i **Datagram** in broadcast, **non è affidabile** perchè non gli interessa che riceva una conferma della ricezione da parte di un client o di un host. Il **controllo degli errori** è **obbligatorio** solo negli **IPv6**. È più **adatto** a situazioni in cui la **latenza** è più c**ritica** e la **perdita di** alcuni **datagrammi** e **non vengono messi in ordine** . Usato in trasmissioni in tempo reale (**streaming multimediale, videochiamate, giochi online**). Header di 8 byte

**COME ARRIVA  A DESTINAZIONE ?**

I **Segmenti** **viaggiano** attraverso i protocolli **conoscendo l’IP** di **destinazione** e la **porta da utilizzare**, sono **contenuti** nell’ **Header**.

# COME INSTAURA UNA CONNESSOINE IL PROTOCOLLO TCP?  [three-way-handshake](https://github.com/emanueletroiani/Network/blob/three-way-handshake/README.md)

# **LAYER 5**

Si occupa di stabilire una sessione tra host e host o tra client e server. Il suo compito principale è quello di **gestire la connessione** creando e mantenendo la connessione. Crea dei checkpoint in modo che ad esempio in un trasferimento di file non bisogna re-inviare tutti i pacchetti da capo. 

Qui lavora anche il protocollo **SSH (secure shell)**  che instaura una connessione privata e cifrata all’interno della stessa rete dei dispositivi tramite server remoti.

# **LAYER 6**

In questo layer i pacchetti vengono **presentati** in maniera tale che siano comprensibili al destinatario. **Per evitare che i pacchetti vengano aperti o intercettati** da non autorizzati, vengono utilizzati 2 elementi, L’**algoritmo di cifratura** e le **chiavi di cifratura**

**Algoritmo di cifratura: (Noto a tutti)** insieme di regole che determinano il funzionamento della cifratura

**Chiave di cifratura:** insieme di numeri e lettere generati in maniera casuale seguendo l’algoritmo di cifratura.

![Untitled](https://github.com/user-attachments/assets/70c100a3-21f0-46dc-87a0-3e722f6e94da)

**TIPOLOGIE DI CHIAVI**

- **Chiave simmetrica: (tipo la chiave del wifi)**  è la piu semplice e consiste nella creazione di **2 chiavi uguali.** Una chiave serve per criptare il messaggio dalla sorgente e una chiave serve al destinatario per decriptare il messaggio. Si chiama anche conversazione in chiaro
- **Chiave asimmetrica:** qui ci sono 2 chiavi diverse, **una pubblica e una privata.**  Il pc **sorgente** e il pc **destinatario** possiedono **entrambi** una **chiave privata** e una **pubblica**. Le chiavi pubbliche sono conosciute da tutti. **Una chiave privata di un host può essere aperta solo dalla chiave pubblica di dello stesso host.** Il **mittente cripta** il messaggio con la **sua chiave privata con la chiave pubblica del destinatario** che riuscirà ad aprire con la sua chiave privata. Perchè ricordiamo che queste chiavi possono aprirsi a vicenda, ovvero la chiave pubblica di un individuo può aprire la sua stessa chiave privata e viceversa.

# Livello 7 **Applicativo**

E’ il livello che fornisce l’interfaccia all’utente e supporto alla rete per le applicazioni.
