# Cos’è un firewall?

Il firewall è uno dei principali strumenti di sicurezza informatica, **progettato** per **monitorare** e controllare il **traffico** in **entrata** e in **uscita da una rete**, sulla base di **regole** di **sicurezza** predefinite. 

Serve a **prevenire accessi non autorizzati** a una rete privata, **proteggendo** risorse critiche da **attacchi esterni**.

Ci sono due tipi di firewall, quello presente nei dispositivi (economico, adatto a reti piccole) e quello installato in un apposito Hardware (si parla di FW perimetrale ed è piu costoso. Vantaggi: Maggiore robustezza, protezione centralizzata e gestione scalabile di reti aziendali.)

# Funzionamento

 Un firewall può bloccare o consentire traffico sulla base di:

- Indirizzi IP
- Numeri di porta
- Tipo di protocollo (TCP, UDP)
- Contenuto del pacchetto
- Stato della connessione

Lo fa tramite le **action,** le piu comuni sono

- **Allow**
- **Drop** il firewall scarta il pacchetto senza inviare nessun messaggio diagnostico alla sorgente
- **Deny**  il firewall non fa passare il pacchetto, ed informa la sorgente

Da qui si evince che funziona al livello 3 e 4 della pila iso osi perchè proteggono il trasferimento dei dati e il traffico di rete. Evitando attacchi DNS,FTP,SMTP,SSH e Telnet.

# NAT

network address Translation

Tramite il NAT il firewall **oscura** **l’indirizzi IP privati**, cambiandolo in IP pubblico quando effettua una richiesta nella WAN

# Protezione da queste minacce

- **Accesso non autorizzato:** gli aggressori accedono a una rete senza autorizzazione. Questo è possibile grazie al furto di credenziali e agli account compromessi dovuti all’uso di password deboli, di ingegneria sociale e di minacce interne.
- **Attacchi MITM:** gli aggressori intercettano il traffico tra la rete e i siti esterni o all’interno della rete stessa. Si tratta spesso del risultato di protocolli di comunicazione non sicuri che consentono agli aggressori di rubare i dati in trasmissione, per poi ottenere le credenziali utente e dirottare gli account utente.
- **Escalation dei privilegi:** gli aggressori ottengono l’accesso a una rete, quindi utilizzano l’escalation dei privilegi per espandere la loro portata nel sistema. Possono farlo orizzontalmente, ottenendo l’accesso ai sistemi adiacenti, o verticalmente, ottenendo privilegi più elevati all’interno dello stesso sistema.

### Come configureresti un firewall per prevenire un attacco DDoS?

- **Rate Limiting**: Configurerei il firewall per limitare il numero di richieste che possono provenire da un singolo indirizzo IP in un certo intervallo di tempo. Questo impedisce che un attacco **DDoS volumetrico** riesca a sovraccaricare la banda.
- **Blocco degli IP sospetti**: Imposterei regole che bloccano automaticamente gli IP che superano una certa soglia di richieste o che mostrano comportamenti sospetti, come un'alta frequenza di pacchetti SYN senza completare la connessione (SYN flood attack).
- **Geoblocking**: Se l'attacco proviene da una regione geografica specifica e non è necessario traffico legittimo da quella zona, potrei bloccare tutte le connessioni in arrivo da quella regione.

![image](https://github.com/user-attachments/assets/8a0aa39e-ff34-4b5e-ad38-a71be0b9b086)


