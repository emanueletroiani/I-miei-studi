[BL01_20220520.pdf](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/584e35d9-3c9f-472c-805d-53914f7c2838/BL01_20220520.pdf)


# Che cos’è

Un attacco DdoS ha come **obiettivo disattivare** o eliminare un **sito** o **un'applicazione Web**, un servizio **cloud** o altre risorse online **mediante** il **sovraccarico** di **richieste** di **connessione inutili**, **pacchetti falsi** o altro **traffico dannoso.** Il **sistema** colpito **subisce** un **rallentamento** o un **crash totale** e non risulta più disponibile per gli utenti legittimi. Può colpire 3 diverse memorie che portate ad esaurimento causano il crash:

- CPU (applicativo e protocol attack)
- RAM (applicativo e protocol attack)
- Larghezza banda di rete (volumetrico)

# Come funzionano

Utilizzano protocolli di rete come HTTP e TCP per inondare di richieste server WEB, router o altre infrastrutture di rete che possono elaborare solo un numero limitato di richieste. L’attacco Ddos si divide in 3 fasi:

- **Selezione bersaglio:**  Gli hacker utilizzano attacchi DdoS per estorcere denaro alle organizzazioni e chiedere un riscatto per porre fine all'attacco o per attivismo o per attività concorrenti o per guerre informatiche.
- **Botnet**: Vengono acquistate o create dagli hacker.
- **Lancio dell’attacco:** Gli hacker spesso **oscurano** la fonte dei loro **attacchi** **tramite** lo **spoofing IP**, una tecnica con cui i criminali informatici **forgiano** indirizzi **IP fasulli** **per** i **pacchetti inviati** dalla **botnet**. In un tipo di **spoofing IP**, chiamato "**reflection**", gli hacker fanno **sembrare** che il **traffico** dannoso sia stato **inviato** **dall'indirizzo IP della vittima.**

# Tipi di attacco Ddos

In base al livello, della pila ISO OSI che colpisce, prende un nome

- **Ddos applicativo:** Livello 7 (applicativo). Uno degli attacchi piu utilizzato è l HTTP Flood, dove il malintenzionato manda un gran numero di HTTP request da una botnet al Web server che riuscendo e gestire tutte le richieste rallenta o crash.
- **Ddos Protocol attack:** Livello 3 e 4. Attacchi ai Firewall e server web.
    - **SYN flood:** sfrutta l**'handshake TCP**, il processo con cui due dispositivi stabiliscono una connessione l'uno con l'altro. L’ **attaccante invia** al **server** di **destinazione** un numero elevato di **pacchetti SYN con** indirizzi **IP** di origine **contraffatta**. Il server invia la risposta all'indirizzo IP contraffatto e attende l'ultimo pacchetto ACK. Poiché l'indirizzo IP di origine è stato falsificato, questi **pacchetti non arrivano** mai. Il server è impegnato in un gran numero di connessioni non completate, che lo rendono non disponibile per gli handshake TCP legittimi.
    - **UDP flood:** L’attaccante invia **pacchetti UDP fasulli** a **porte randomiche** di un **host target** con la **richiesta** di un **applicazione** che però **non esiste**, nel protocollo UDP il server comunica con l’host tramite il ping e infatti  **l’host invierà** messaggi **ICMP** “destinazione non raggiungibile” al mittente.
    - **ICMP flood**: L’attaccante **invierà**, **tramite botnet**, richieste **ICMP** provenienti **da** indirizzi **IP falsi** sovraccaricando la rete. (la differenza con lo Smurf è che qui si utilizza una botnet per inviare le richieste ICMP mentre lo smurf utilizza i dispositivi appartenenti alla propria rete)
    - **Attacchi Smurf:** **L’attaccante** utilizza **l’IP spoofing**, ovvero falsifica il **proprio** indirizzo **IP** rendendolo **uguale** a quello della **vittima per** poi **lanciare** richieste di **ICMP** in **broadcast**, tutti i **pc collegati** nella rete di conseguenza **invieranno** una **response** e si **creerà** questo **loop** che sovraccaricherà la memoria del bersaglio. **MITIGAZIONE**: Disabilitazione broadcasting IP o Configurazione di host e router che ignorano le richieste ping
- **Attacchi Volumetrici:** L’ attaccante ha come obiettivo di saturare tutta la larghezza della banda internet. Può farlo in diversi modi
    - **DNS Amplification reflection:** amplificazione perchè ****sfrutta la velocità del protocollo **UDP** che può contenere una **query** (richiesta) di **8byte** e un **answer** di **massimo 512byte**, quindi **l’attaccante invia query leggere** che però **richiedono informazioni** per una risposta 64 volte **piu pesante** obbligando il server DNS a occupare una larghezza di banda di **64 volte superiore a quella dell’attaccante**. La **riflessione** avviene quando un aggressore **falsifica l'indirizzo sorgente** dei pacchetti di richiesta, **fingendo** di essere la **vittima**. I server non sono in grado di distinguere le richieste legittime da quelle falsificate quando viene utilizzato UDP. Pertanto, rispondono direttamente alla vittima. Questa tecnica nasconde il vero indirizzo IP dell'aggressore sia al sistema della vittima che al server abusato. L**e informazioni sono i record memorizzati delle risoluzioni degli indirizzi IP.**
    - [**DDos NTP Amplification**](https://www.youtube.com/watch?v=RuAOGJIkBys&list=PLod5uVuFMqhYKLnkI6t3lhq1zklUWF-fi&index=10&ab_channel=SimoneModiga): Network Time Protocol (**porta 123**) serve per la **sincronizzazione temporale** ovvero regolarizza l’ora  di tutti i dispositivi che fanno parte in una rete. Anche qui si creano **query** (domande) **leggere** con **response pesanti**. L’hacker sfrutta ,se è abilitato, il comando **GET MONLIST,** funzione di **NTP** che **invia** una **risposta** che contiene con la **lista** degli ultimi **600** **IP** che hanno fatto richieste nel server NTP. Con questo attacco si raggiunge **un’amplificazione** di **206 volte.**
    - [DDoS memcached server](https://www.youtube.com/watch?v=e_VZ1xRNxLE&list=PLod5uVuFMqhYKLnkI6t3lhq1zklUWF-fi&index=11&ab_channel=SimoneModiga): E’ un **server** su cui gira un software di caching, che ha la funzione di **velocizzare** le **risposte** delle **web app** dinamiche **basate sul database** (backend). in pratica va a cashare le risposte del database server (che sono molto pesanti). Ecco la struttura network
        
       ![Screenshot 2024-10-05 175048](https://github.com/user-attachments/assets/77b331b7-bfe8-4184-97d6-a9c9e7734407)

**L’attaccante invia** una **richiesta al** **memcached** server vulnerabile **chiedendogli** una risorsa o **chiave** (Memcached funziona con informazioni Chiave:Valore), il **server risponderà** con un risorsa o **Valore**, questo pacchetto UDP può arrivare fino **51.000 volte** piu **grande** della domanda. Ovviamente del server memcached sarà inviata al target. Il tutto avviene sulla **porta 11211.**
        

# Soluzioni Attacchi Ddos

- **CDN**: Content Delivery Network, ovvero una società che possiede **molti server** e offrono il servizio ai clienti di sfruttare questi server. In questo modo le **richieste dei client passeranno tra i diversi server distribuendo l’attacco DDoS.**
- **Load balancer**: è il sistema che **distribuisce** le **richieste** dei **client sui server** (in questo caso si parla di ridondanza dei server, ovvero avere piu server) . Se non ci fosse potrebbe accadere che 1 server si sovraccarica e 2 sono vuoti.
- **Rate limiting:** limitare le richieste che può fare un IP in un determinato lasso di tempo
- **Scrubbing center**: Filtra **il traffico dannoso** da una rete o da una connessione Internet. Questi centri sono specializzati nel monitoraggio e nel filtraggio del traffico per attività dannose, come **attacchi Distributed Denial of Service (DDoS), attività botnet, propagazione di malware** e altre minacce informatiche.

![image](https://github.com/user-attachments/assets/366ab897-1de1-4103-95d8-3738a3ca9e3e)

