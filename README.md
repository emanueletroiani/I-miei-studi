# DHCP: Dynamic Host Configuration Protocol

Permette l’assegnazione dell’indirizzo IP statica, dinamica o automatica ad un Client senza che noi dobbiamo andare ad impostarlo ogni volta. Le reti vengono riconosciute tramite il MAC Address.  

Dinamica: Il server **DHCP** assegna un **IP** e alla **scadenza** del **periodo di lease** l’IP viene **assegnato ad altri host** che ne fanno richiesta.

Automatica: All’**host** verrà assegnato sempre lo **stesso IP**, quando ne farà nuovamente richiesta, anche quando il **periodo di lease è scaduto**.

Statica: **IP** è assegnano all’host in modo **permanete** e **non esiste il periodo di lease**. es stampati.

Il Protocollo DHCP è composto da 4 Step:

1. **DHCP Discovery**: Il nostro Pc (host) invia una **richiesta Broadcast** di tipo DHCP Discovery, nell’intento di **trovare** un server che fornisca una **configurazione** dell’ **IP**
2. **DHCP Offer**: I server **DHCP** presenti nella rete **ricevano la richiesta** e **rispondono inviano una configurazione IP** al solo client (**unicast**), piu client (**Multicast**), A tutti i client (**Broadcast**)
3. **DHCP Request:** L’**host** **riceve** le proposte di **configurazione** **e** ne seleziona una. successivamente **invia** un messaggio Broadcast chiamato **DHCP Request** che indica il nome del server DHCP selezionato.
4. **DHCP ACK**: Il **server** selezionato riceve la DHCP Request **invia all’ host** un messaggio chiamato **DHCP ACK** in cui conferma la configurazione IP.
