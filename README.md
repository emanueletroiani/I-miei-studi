# [Che cos’è?](https://www.ictsecuritymagazine.com/articoli/aspetti-di-sicurezza-di-bgp-e-routing-in-internet-parte-i/) (articolo perfetto)

Il border Gateway Protocol sono un insieme di **regole** che servono per **instradare** i **dati** nel **percorso** piu **veloce** nella rete internet, in quanto è composta da piccole **società** che **dispongono** di **aeree**, chiamate sistemi autonomi **AS**, composte da **tanti router** che **comunicano** tra di loro. **ogni AS** ha un **Path piu veloce** per **raggiungere** un determinato **IP**, salvato nella **tabella** di **routing**. Se la mia navigazione web dovesse attraversare 2 nodi di AS senza il BGP non troverei nessuna connessione o risposta dal serve IP. E’ fondamentale perchè mette in comunicazione e condivisione tutti gli AS.

# Cosa sono gli AS

I sistemi autonomi sono **gruppi** di **router controllati** da una **società** all’interno della rete internet. Ci sono 2 tipi

- **Sistema autonomo interno (IAS)**: comprende tutti i router e tabelle di routing posseduti da una società
- **Sistema autonomo esterno (EAS**): comprende tutti i router esterni che comunica tra di loro

Ad ogni AS viene assegnato un **numero univoco** **(ASN)** che lo rappresenta all’interno della rete. Quando un pacchetto di rete viene instradato su Internet, può seguire una varietà di percorsi, sfruttando i diversi collegamenti tra gli ASN.

Gli AS sono anche detentori di molti in indirizzi IP pubblici, quando si parla di AS questi blocchi di IP vengono chiamati **Prefix**

# Come i pacchetti trovano la via piu veloce

lo fanno con gli **annunci** tramite il protocollo BGP, e **pubblicizzano** il **Path** **piu** **veloce** per arrivare ai vari indirizzi IP o intervalli.

In sostanza riceve e manda i percorsi piu veloci dai diversi AS condividendo tabelle di routing

# Mettiamo caso che

Per capire meglio come l’instradamento dei pacchetti e la condivisione delle tabelle di routing possiamo fare il seguente esempio:

Voglio visitare un sito web, TIM conosce il Path per arrivare a questo sito internet, se TIM va giu io non posso accedere a questo sito. 

Se TIM condivide il suo Path per raggiungere questo sito con la Vodafone e TIM va giu io potrò visualizzare il sito in quanto la Vodafone conosce la strada per raggiungere l’IP del sito.

# [Tipi di attacchi](https://www.ictsecuritymagazine.com/articoli/aspetti-di-sicurezza-di-bgp-e-routing-in-internet-parte-ii/)

- **Dirottamento**: Questo può anche essere fatto intenzionalmente, una pratica chiamata BGP hijacking. Un dirottatore BGP può instradare il traffico Internet attraverso se stesso per eseguire vari attacchi. Ad esempio, un dirottatore BGP potrebbe eseguire un attacco [denial of service](https://www.checkpoint.com/it/cyber-hub/cyber-security/what-is-denial-of-service/) (DoS) instradando il traffico attraverso i propri sistemi e interrompendo le connessioni. In alternativa, il BGP hijacking è stato utilizzato anche negli attacchi di [DNS](https://www.checkpoint.com/it/cyber-hub/network-security/what-is-dns-security/) hijacking, in cui l'attaccante ha reindirizzato le query DNS e inviato risposte false indirizzando gli utenti verso siti di phishing
- **DDoS**: Il BGP funziona in modo che gli AS pubblichino informazioni di routing ai loro peer. Questi AS elaborano le informazioni, aggiornano le loro tabelle interne e passano le informazioni ai loro pari. Questo crea l'opportunità di un attacco Distributed DoS (DDoS). Gli aggressori creano un falso annuncio secondo cui un AS sta cercando di aggiornare le informazioni di routing, causando un'ondata di traffico e di dati che può sommergere il sistema.
