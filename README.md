# Pila Iso/Osi
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/24f8c8f2-610e-4dcd-a7ef-d63fc2237a52/Untitled.png)

Perchè è stato creato e come funziona teoricamente:

E' nato dalla necessità dei costruttori di trovare un **mezzo** che **permette**sse ai diversi
**dispositivi di comunicare tra di loro tramite protocolli.** Le informazioni che il dispositivo sorgente e quello destinatario  si scambiano vengono chiamati **pacchetti**, sono **flussi di Bit** scambiati tramite segnali elettrici. I pacchetti sono composti da Header e Payload.

**HEADER**: contiene tutto il necessario affinche l’informazione contenuta nel pacchetto arrivi e venga compresa dal destinatario.

**Payload:** E’ l’informazione vera e propria.

Entrambi vengono **inglobati e diventano il Payload del livello successivo**, **sino** ad arrivare al **livello 1** **del ricevente che in maniera inversa procederà al decapsulamento**.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/660206fc-7be1-4ce7-bc86-d3b829ce3b4b/Untitled.png)

Si sviluppa in **7 livelli** dove **ogni livello** ha un preciso compito e **può comunicare** solo ad un **dispositivo dello stello livello** **o al livello successivo affinchè il pacchetto dati dal dispositivo 1 arrivi al dispositivo 2.** Questo avviene tramite l'**incapsulamento** di ogni livello. 

**N.B.** il modello ISO/OSI è un modello teorico da utilizzare come referenza. In pratica le applicazioni utilizzano il modello TCP/IP che varia leggermente dal modello teorico ISO/OSI.

**Differenza ISO/OSI con Tcp/ip**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/640417d1-d122-4c1e-b573-bc22f2cc705e/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/b7449c9f-12d9-4337-b092-2d679776cad9/Untitled.png)

**Dal livello 1 al 3 siamo fuori il sistema operativo. Dal layer 4 al 7 siamo dentro al sistema operativo**

**Livello 1: Fisico**
Permette la trasmissione dei dati tramite segnali elettrici, occupandosi della forma e dei livelli di tensione del segnale tramite fibra ottica o cavi in rame, frammentando l'informazione del computer sorgente in Bit. 

I **BIT** sono comporti da due soli **numeri** lo **0** e **1.**

**Livello 2: DataLink**
Si occupa di spacchettare in **Frame** i bit del livello 1 per inviarli al livello3. **Fa da ponte.**

Inoltre **verifica** e **gestisce** gli **errori di sua competenza**, se ad esempio un pacchetto è danneggiato lo elimina o lo farà rispedire. Quindi **è responsabile della comunicazione degli Host** **della stessa rete** (Lan) tramite l'indirizzo MAC (indirizzo fisico della scheda di rete, ad esempio io ho 2 MAC, una scheda di rete Ethernet e una wifi).

A questo livello lavorano gli **switch (legge gli indirizzi MAC)**: un **dispositivo** di rete **che** serve per **connette**re **piu** dispositivi facendoli scambiare dati tramite L’ **indirizzo MAC** della loro scheda di rete, dispone di porte ethernet alle quali è possibile connettersi con il classico cavo. Unendo **troppi dispositivi** **allo stesso switch** si può incorrere a **latenza**. **Per evitare** questo si possono **frammentare le reti Lan con reti vistuali (Vlan)**, in questo modo s**i può decide** quali **gruppi** di **pc** possono c**omuncare tra di loro**.
I diversi Protocolli del livello 2 sono:

- **Ethernet IEEE 802.3**: **Ethernet** si riferisce a una **tecnologia** che **consente** ai **dispositivi all’interno** di **reti cablate** di **comunicare** tra loro. I dispositivi collegati in Ethernet possono quindi formare una rete e scambiare pacchetti di dati. Ciò crea una rete locale (LAN) su connessioni
Ethernet. Ha ampiamente sostituito le tecnologie LAN cablate concorrenti come Token ring, FDDIe ARCnet. E’ considerata una delle tecnologie chiave che compongono internet.
- **Token Ring**: IEEE 802.5: al suo posto è entrato il protocollo ethernet. Token ring è una rete locale dove i PC comunicano ad anello, ovvero a DX e SX, nel caso un pc smette di riceve pacchetti o di funzionare si blocca l’intera rete.
- **MAC**: media access control identifica universalmente la scheda di rete di un Host, è un codice a 48 bit esadecimale univoco che viene fisicamente assegnato dal produttore in fase di fabbricazione
- **LLC 802.2**: Logical link control è a **diretto contatto con il Livello 3** e si preoccupa di fare due cose 1 **Regola il controllo del Flusso dei dati** e si occupano della **gestione degli ACK**. Il ruolo di LLC, infatti, è di nascondere al livello di rete le differenze che esistono tra i vari protocolli [802.In](http://802.in/) questo modo, il livello di rete viene completamente isolato dal mezzo trasmissivo
attraverso il quale avviene la trasmissione dei dati. I dati provenienti dal livello superiore vengono incapsulati in una unità di trasmissione del livello LLC e opportunamente trasferiti al livello MAC, che ne cura la trasmissione sul mezzo fisico prescelto; viceversa, le unità di trasmissione provenienti dal livello MAC vengono elaborate secondo i criteri definiti dal protocollo e quindi inoltrate al livello superiore.
- **ARP**: Address resolution protocol **serve per mappare l’indirizzo IP con l’indirizzo fisico MAC.**
Nel caso in cui un **Host debba comunicare ad un pc solo conoscendo l’indirizzo IP,** il protocollo **ARP invia** una **ARP request** **contenente** il proprio **indirizzo MAC** **e l’indirizzo IP del destinatario a tutti i pc collegati dallo switch**. Ogni Host verifica se l’indirizzo IP della ARP request combacia con il suo, solo **l’Host che possiede quell’indirizzo IP risponde tramite una
ARP replay contenente il proprio indirizzo MAC** in modalità unica. Ogni host conserva nella cache una tabella di indirizzo MAC, prima di inviare una ARP request verifica se è già presente nella cache. La Tabella ARP si rigenera ogni 5 minuti e può essere verificata tramite il comando ARP -a

Il livello 3 **Network**

Il livello di rete **determina il percorso** dei pacchetti (**datagrammi**) **attraverso** il **Router** che permette il collegamento tra due dispositivi appartenenti a reti differenti. Ci riesce tramite  gli Indirizzi IP dell’host sorgente e dell’host destinatario. 

### IP: Internet Protocol

[ReS1.08 INDIRIZZI IP.pdf](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/c68432d9-ace5-4707-ad51-0df2eb9264d8/ReS1.08_INDIRIZZI_IP.pdf)

Serve per identificare in maniera univoca un Host all’interno della rete. Ci sono due tipo: **pubblico e privato**.

**Pubblico**: è ’IP che ci identifica all’interno della rete Internet Globale, è fornito dal **ModemRouter del nostro ISP** (internet service provider). E’ unico al Mondo.

**Privato**: Identifica ogni singolo dispositivo connesso alla rete domestica/aziendale che ha accesso al ModemRouter. Di conseguenza possono esserci millioni di 192.168.1.1

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/aa840704-88bf-4ca0-98f3-9b37b6d7ef2d/Untitled.png)

Quando usi Internet, i dati che invii e ricevi vengono inviati tramite il tuo indirizzo IP pubblico, quindi il tuo router passa quel traffico al tuo dispositivo utilizzando il suo indirizzo IP privato. Questo processo di scambio tra indirizzi IP pubblici e privati è chiamato **Network Address Translation (NAT)**.

Attualmente gli IP che si utilizzano sono gli **IPV4,** formati da 32Bit o 8 Byte. vanno da 0 a 255 ma hanno dei valori specifici per ogni categoria. Di IP ce ne sono circa 4 miliardi e sono in esaurimento, presto si passera agli IPV6.

# [CLASSI DI INDIRIZZI IP](https://www.youtube.com/watch?v=Wcn958GFBeA&list=PL3itjooulgzP0YTfCTsjndtuRJ7o3qPEF&index=11&ab_channel=RobertoManfrin)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/34b4ff0c-fb90-4773-a24d-2be723c9ea63/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/a925bdbf-032d-45de-9d80-bb8a171e8354/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/d436df2a-14c3-430a-9454-6c3c88e40e0d/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/0864eb37-3250-4af8-a4f7-7cd9f166244f/Untitled.png)

**da notare le subnetmask che di valore impostato partono da:**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/7ed8d232-5db1-4818-8b45-683373b1aa1f/Untitled.png)

In questo layer bisogna capire se il destinatario fa parte della stessa rete o u di una rete diversa. Lo fa attraverso la **Subnetmask.** 

ES: Host 1 IP: 192.168.1.100

Netmask: 255.255.255.0

Host 2 IP: 192.168.1.101

      Host 3 IP: 194.132.5.2

Possiamo notare che tramite la variabile booleana AND che restituirà 1 se entrambi sono 1, i valori 255 se restituiscono lo stesso indirizzo IP per le prime 3 terzine 192.168.1 (in questo caso l’ ultima terzina identifica l’host)  vorrà dire che farà parte della stessa rete. se al contrario restituirà un indirizzo di rete diverso vorrà dire ce farà parte di una rete differente e il pacchetto verrà inviata al Gateway.

In conclusione  Host 1 e Host 2 sono nella stessa rete, Host 3 ha una rete differente.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/69df3a67-b2e3-4d8b-a41a-0719bb97a043/Untitled.png)

# [COME SI CALCOLA IL CODICE BINARIO DI UN INDIRIZZO IP](https://www.youtube.com/watch?v=Pc9t35vrUXo&list=PL3itjooulgzP0YTfCTsjndtuRJ7o3qPEF&index=9&ab_channel=RobertoManfrin)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/3e8378e8-3d14-46ad-b0ae-bc72784f4982/Untitled.png)

**dividiamo ogni terzina per 2, se è divisibile per 2 ci darà valore 0 se no è divisibile ci darà valore 1.**

# [COME SI RISALE ALL’INDIRIZZO IP TRAMITE IL CODICE BINARIO](https://www.youtube.com/watch?v=Pc9t35vrUXo&list=PL3itjooulgzP0YTfCTsjndtuRJ7o3qPEF&index=9&ab_channel=RobertoManfrin)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/414966d4-ea60-4942-9ca8-766624909be2/Untitled.png)

**eleviamo alla potenza da DX vs SX e poi sommiamo la cifra che esce.** C’è una scorciatoia per calcolare l’IP numerico attraverso una tabellina da imparare a memoria se dovesse servire.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/28922e90-9414-4733-81a0-7eee15312e8e/Untitled.png)

### Capire la subnetmask e la sua divisione di reti, chiamata Subnetting.

Se un’azienda ha bisogno di dividere in piu reti invece di acquistare nuovi indirizzi IP può utilizzare la tecnica del subnetting. Ovvero dividere gli indirizzi IP in piu reti grazie alla subnetmask.

ES. classica Subnetmask= 255.255.255.0 dove i valori 255 identificano la classe della rete e lo 0 gli indirizzi a disposizione. **tenendo conto che 255 è uguale a 11111111 in valore binario, restituirà una rete /24. ovvero sono gli 1 precedenti allo zero.** infatti 255.255.255.0 è uguale a 11111111.11111111.11111111.00000000

Qualora volessimo dividere la rete e diminuirne gli Indirizzi IP perchè non ne abbiamo bisogno. basterà restituire un valore 1 al primo 0 partendo da SX, così: 11111111.11111111.11111111.10000000 in questo caso il numero di 1 è 25 e gli indirizzi a disposizione sono 128 percè avremo dedicato alla rete un valore in piu diminuendo i valori dedicati agli HOST

**Quindi possiamo dire che piu valori attribuiamo alla netmask e meno indirizzi IP possiamo dedicare a quella rete.**

### [Come determinare a quale rete frazionata un indirizzo IP appartiene](https://www.youtube.com/watch?v=3HRX9dMcI6Q&list=PL3itjooulgzOMzrQwsI5kRxn9WD_7Z6WZ&index=2&ab_channel=RobertoManfrin)

Tenendo in considerazione l’esempio sopra citato, ovvero Subnet 255.255.255.0 e una 255.255.255.128 con indirizzi IP che vanno da **192.168.1.0/25 a 192.168.1.128/25** e da 1**92.168.1.129/25 a 192.168.1.255/25** avremo due reti (prendiamo in considerazione le ultime 3 ottine):

Rete 1: (0)0000000 

Rete 2: (1)0000000

Ogni rete ha un indirizzo broadcast con tutti 1 e un indirizzo di rete con tutti 0 

Rete 1, IP Rete: (0)0000000 

Rete 1, IP braodcast (0)1111111

Rete 2, IP Rete: (1)0000000 

Rete 2, IP braodcast (1)1111111

### Come fa una sorgente a capire se il destinatario di un pacchetto fa parte della sua stessa rete?

Utilizzeremo la Netmask. Calcolando l’indirizzo di rete dell’IP

ES:             

      IP 192.168.1.100

netmask: 255.255.255.0

indirizzo rete= 192.168.1.0

ES: 

IP 192.168.1.250

netmask: 255.255.255.128

Indirizzo di rete: ?

**ECCO COME CALCOLARLO CON LA VARIABILE BOOLANA AND**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/28922e90-9414-4733-81a0-7eee15312e8e/Untitled.png)

Le ultime ottine in binario sono

IP .250:          (1)1111010

NM .128:       (1)0000000

Indirizzo rete: **128**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/b5b4e4cb-d9c9-4232-b20c-8ce2fe9e14c2/Untitled.png)

# Es: a /27

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/c4329a34-677f-4bc8-b42e-2177489a43eb/Untitled.png)

La regola dice che per calcolare bisogna prendere i bit piu a destra ed intervallare l’1 e lo 0 ogni 1 volta. a mano a mano che le rate si restringe (in questo caso una/27) gli 1 e gli 0 si intervallano raddoppiandosi. 

ogni 1 volta per la /25

ogni 2 volte per la /26 

ogni 4 volte per la /27

ogni 8 volte per la /28

ogni 16 volte per la /29

ETC..

**PARTENDO SEMPRE DALLO 0 DI DX**

# Chi fornisce gli indirizzi IP?

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/ac1b8b22-d6b4-49fd-993e-b77a16cf7da6/Untitled.png)

Il livello 4 **Trasporto**

In questo layer si parla di **Segmenti in TCP o Datagrammi in UDP e** si garantisce una **connessione end to end.**

Il Protocollo di Controllo di Trasmissione (**TCP**) e il Protocollo Datagramma Utente (**UDP**) **sono** due **protocolli di comunicazione** fondamentali all'interno della suite di protocolli di Internet (TCP/IP), ma **differiscono in** diversi aspetti, tra cui **affidabilità, orientamento alla connessione, gestione degli errori e altre caratteristiche.** Ecco una panoramica delle differenze principali tra TCP e UDP:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/1483f7d8-7d24-49c7-bfff-7006303ec741/Untitled.png)

**Utilizzo tipico:**

- **TCP:** È spesso **utilizzato** in applicazioni che richiedono una comunicazione **affidabile** e in **ordine**, che **controlli** gli **errori** dei pacchetti affinchè arrivi tutto perfetto e in **ordine** con un **flusso di scambio regolare,** in caso di errore si fa rispedire il segmento. come il **trasferimento di file, la navigazione web e l'invio di e-mail.** Header è composto da 20 Byte
- **UDP:** Non ha una connessione, manda i **Datagram** in broadcast, **non è affidabile** perchè non gli interessa che riceva una conferma della ricezione da parte di un client o di un host. Il **controllo degli errori** è **obbligatorio** solo negli **IPv6**. È più **adatto** a situazioni in cui la **latenza** è più c**ritica** e la **perdita di** alcuni **datagrammi** e **non vengono messi in ordine** . Usato in trasmissioni in tempo reale (**streaming multimediale, videochiamate, giochi online**). Header di 8 byte

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/4f659198-071a-4123-bfaf-27f75aed10ab/Untitled.png)

**COME ARRIVA  A DESTINAZIONE**?

I **Segmenti** **viaggiano** attraverso i protocolli **conoscendo l’IP** di **destinazione** e la **porta da utilizzare**, sono **contenuti** nell’ **Header**.

**COME INSTAURA UNA CONNESSOINE IL PROTOCOLLO TCP?**

Tramite la **three-way-handshake**, con il processo Syn-syn/ack-ack

Syn=Syncronisation

ack= acknowlegement

Header:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/d117571f-a254-4e08-94c3-5c0c34911db4/Untitled.png)

Il **Client** **invierà** una richiesta **SYN** positiva (con **flag a valore 1**) con un numero SEQ (sequens number) casuale.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/49ca0d4d-9d2f-4791-b6c2-621bcff74ee1/Untitled.png)

il **Server** risponderà con un **segmento di SYN/ACK** con valore impostato a +1 del SEQ inviato in precedenza. Invierà anche un SEQ con valore impostato dal Server. Infine sarà presente un **SYN** impostato con **flag ad 1** per la richiesta di connessione.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/3fb85b12-3c94-46b7-b7a8-6a81cbed722f/Untitled.png)

Il **Client** completa la configurazione inviando **segmento** contenente **ACK** con valore impostato a **+1** d**el SEQ del Server** e un **SEQ** con **valore impostato del SEQ del client +1.** Infine conterrà una **flag** **SYN** impostata a 0 per chiudere la connessione.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/2570dc22-47da-43d8-ba7c-5bc150963d4d/Untitled.png)

**COME TERMINA LA CONNESSIONE TCP?**

Con la **Four ways end connection.**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/fb95a7c7-15ac-4a28-985f-650ac479b869/Untitled.png)

1.  Il **client invia** un **Segmento** con Flag **FIN** impostato ad **1** e un numero di **SEQ random**
2. Il **server** risponde con un **ACK** con **valore SEQ+1**. **FIN** è impostato a **0** e A**CK a 1**, **la connessione ancora non è interrotta e il server può ancora spedire dati.**
3. Una volta finito il **server manderà** un **segmento FIN** con Flag impostata ad **1** e una **SEQ random.**
4. Il **Client Risponderà** con un **Fin** con Flag **0**, un **ACK con valore SEQ+1 del server.**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/e9198636-d4a3-4db2-abbe-331726ddc591/Untitled.png)


**LAYER 5**

Si occupa di stabilire una sessione tra host e host o tra client e server. Il suo compito principale è quello di **gestire la connessione** creando e mantenendo la connessione. Crea dei checkpoint in modo che ad esempio in un trasferimento di file non bisogna reinviare tutti i pacchetti da capo. 

Qui lavora anche il protocollo **SSH (secure shell)**  che instaura una connessione privata e cifrata all’interno della stessa rete dei dispositivi tramite server remoti.

**LAYER 6**

In questo layer i pacchetti vengono **presentati** in maniera tale che siano comprensibili al destinatario. **Per evitare che i pacchetti vengano aperti o intercettati** da non autorizzati, vengono utilizzati 2 elementi, L’**algoritmo di cifratura** e le **chiavi di cifratura**

**Algoritmo di cifratura: (Noto a tutti)** insieme di regole che determinano il funzionamento della cifratura

**Chiave di cifratura:** insieme di numeri e lettere generati in maniera casuale seguendo l’algoritmo di cifratura.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/71305810-3e64-42e2-9a78-9fcb8d87690a/Untitled.png)

**TIPOLOGIE DI CHIAVI**

- **Chiave simmetrica: (tipo la chiave del wifi)**  è la piu semplice e consiste nella creazione di **2 chiavi uguali.** Una chiave serve per criptare il messaggio dalla sorgente e una chiave serve al destinatario per decriptare il messaggio. Si chiama anche conversazione in chiaro
- **Chiave asimmetrica:** qui ci sono 2 chiavi diverse, **una pubblica e una privata.**  Il pc **sorgente** e il pc **destinatario** possiedono **entrambi** una **chiave privata** e una **pubblica**. Le chiavi pubbliche sono conosciute da tutti. **Una chiave privata di un host può essere aperta solo dalla chiave pubblica di dello stesso host.** Il **mittente cripta** il messaggio con la **sua chiave privata con la chiave pubblica del destinatario** che riuscirà ad aprire con la sua chiave privata. Perchè ricordiamo che queste chiavi possono aprirsi a vicenda, ovvero la chiave pubblica di un individuo può aprire la sua stessa chiave privata e viceversa.

- Livello 7 **Applicativo**

E’ il livello che fornisce l’interfaccia all’utente e supporto alla rete per le applicazioni.

Come funziona.

- **DNS** Quando digitiamo un nome di un sito nel nostro Browser il **DNS risolve il nome del sito con un l’indirizzo IP**.
- L**’HTTP** fa una **richiesta** al **Web Server**
- **SMTP/IMAP/POP3**: per l'invio e la ricezione di email.
- **DNS**: per la risoluzione dei nomi di dominio (convertendo nomi di dominio in indirizzi IP).
- **Telnet/SSH**: per l'accesso remoto ai sistemi.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/258c49ba-0ffa-40c5-98d1-546cc0cd518d/Untitled.png)

# DNS: domain name sistem

Ha la funzione di **tenere traccia dei nomi e degli indirizzi IP degli host di una rete.** 

Nel World Wide Web il DNS permette a noi umani di non memorizzare tutti i nomi e gli indirizzi ip dei siti. 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/2ae07041-48f5-482e-b3e2-fc6504dfcded/Untitled.png)

1. L’**utente digita l’url** sul proprio browser
2. Il **serve DNS** risolve quel nome restituendo l’**indirizzo IP del sito**
3. Ottenuto l’indirizzo il nostro **PC  può raggiungere** e collegarsi via IP all’url

Il Server **DNS** è una parte **integrata** nel nostro **router** ed è **fornito** dal nostro **provider internet** (fastweb, poste mobile etc etc).

# HTTP: HiperText Transfer Protocol

Consente di **trasferire dati nel WEB**, dove il **Client fa** una **richiesta** e il **WEB server Risponde**. 

L’HTTP e il Web server comunicano in una porta ben definita, L’80.

Negli anni per motivi di sicurezza si è aggiunta una cryptografia al livello HTTP diventando HTTPS (security) che ascolta alla porta 443.

### Esempio di **Richiesta HTT**P (suddivisa in blocchi) dal **lato Client**:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/5c43b221-9fe9-459f-b291-6ee334d5fe59/Untitled.png)

1. **Metodo**: Modalità con il quale il Client interagisce con il Server. 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/aed69fac-3bcb-4e42-adea-2c94cceb67c4/Untitled.png)

1. **Url**: Stringa di caratteri ben definita che identifica la risorsa richiesta
2. **Versione**: Versione HTTP in uso dal client
3. **Header**: Info varie (nome WEB Server, formato, applicazione client)
4. **Body:** Contenuto della richiesta (Se stiamo compilando un modulo o caricando un file)

IMPORTANTE: Ogni volta che il WS invia una risposta ad una precisa richiesta del client la connessione viene chiusa, serve per non appesantire il Client. Per far si che le informazioni tra utente e WS vengano conservati sono stati inventati i **Cookies.**

**COSA SONO I COOKIES?**

Sono delle **stringhe di testo** che vengono memorizzate nel Client, sono **utili** perchè c**ontengono informazioni sulla nostra navigazione** e la rendono piu intuitica e rapida. ad esempio possono memorizzare un carrello nei web shop, mantengono compilati i documenti presso un sito web etc etc. Non pone problemi di sicurezza.

### Esempio di **Richiesta HTT**P (suddivisa in blocchi) dal **lato Server**:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/828066ab-7e88-4cc5-a56e-ada2637ac342/Untitled.png)

1. **Versione:** Versione dell’http 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/61bab657-ed9f-454c-9055-046876dd2d50/Untitled.png)

1. **Stato:**  un codice numerico che indica lo stato della richiesta. 
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/fa46fddb-2e1a-4556-bb50-2a85f2f95bc4/Untitled.png)
    
2. **Reason:** Indica il motivo della risoluzione dello stato. In questo caso la richiesta del client ha avuto esito positivo (OK)
3. **Header:** Sono forniti i dati, Data,Serve di utilizzo, Tipo di contenuto, connessione
4. **Body:** Sono i dati veri e propri contenuti nell’ html

# HTTPs

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/94e41fda-6016-4b2b-bb36-330b5308a87b/Untitled.png)

Utilizza protocolli di cifratura come **SSL**(**secure socket layer**)o la sua evoluzione **TLS**(**Trasport layer security**) utilizza sia la chiave asimmetrica che simmentrica.

# FTP**: (file transfert protocol)**

E’ utilizzato per il trasferimento di File, ovviamente **utilizza** il protocollo **TCP** per garantire l’arrivo di tutti i dati. Apre **2 connessioni** in parallelo: 

- Connessione **di controllo**: Usata per **spedire informazion**i come **username/password,** comandi per navigare nella directory e per inviare/ricevere file. Utilizza la **porta 21**
- Connessione **di dat**i: Nella quale **transitano fisicamente i dati**. Utilizza la **porta 20**

Il protocollo è stato sostituito con il **FTPs** che è supportato da un protocollo di criptazione **SSL.**

# DHCP: **Dynamic Host Configuration Protocol**

Permette l’assegnazione dell’indirizzo IP statica, dinamica o automatica ad un Client senza che noi dobbiamo andare ad impostarlo ogni volta. Le reti vengono riconosciute tramite il MAC Address.  

Dinamica: Il server **DHCP** assegna un **IP** e alla **scadenza** del **periodo di lease** l’IP viene **assegnato ad altri host** che ne fanno richiesta.

Automatica: All’**host** verrà assegnato sempre lo **stesso IP**, quando ne farà nuovamente richiesta, anche quando il **periodo di lease è scaduto**.

Statica: **IP** è assegnano all’host in modo **permanete** e **non esiste il periodo di lease**. es stampati.

Il Protocollo DHCP è composto da 4 Step:

1. **DHCP Discovery**: Il nostro Pc (host) invia una **richiesta Broadcast** di tipo DHCP Discovery, nell’intento di **trovare** un server che fornisca una **configurazione** dell’ **IP**
2. **DHCP Offer**: I server **DHCP** presenti nella rete **ricevano la richiesta** e **rispondono inviano una configurazione IP** al solo client (**unicast**), piu client (**Multicast**), A tutti i client (**Broadcast**)
3. **DHCP Request:** L’**host** **riceve** le proposte di **configurazione** **e** ne seleziona una. successivamente **invia** un messaggio Broadcast chiamato **DHCP Request** che indica il nome del server DHCP selezionato.
4. **DHCP ACK**: Il **server** selezionato riceve la DHCP Request **invia all’ host** un messaggio chiamato **DHCP ACK** in cui conferma la configurazione IP.
