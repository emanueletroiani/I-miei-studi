![image](https://github.com/user-attachments/assets/fc9af464-731e-468d-9592-fbf1a4975963)

**Consiste:** nell'identificazione del bersaglio, nella decisione e nell'ordine di attaccare il bersaglio e infine nella distruzione del bersaglio.

Grazie a **Lockheed Martin**, un'azienda aerospaziale e di sicurezza globale, che ha stabilito il **framework Cyber Kill Chain** per il settore della sicurezza informatica nel 2011 basato sul **concetto militare**. Il framework **definisce** i **passaggi** utilizzati dagli avversari o dagli attori **malintenzionati nel cyberspazio**. Per avere successo, un **avversario** deve **passare** attraverso **tutte le fasi** della **Kill Chain**. Esamineremo le fasi di attacco e ti aiuteremo a comprendere meglio gli avversari e le loro tecniche utilizzate nell'attacco per difenderti.

Affrontiamo il tutto mettendoci dalla parte dell’attacante

# Reconnaissance

**La ricognizione** consiste nello scoprire e raccogliere informazioni sul sistema e sulla vittima.

**Guardiamo la cosa dal punto di vista dell'attaccante, che inizialmente non sa quale azienda vuole attaccare.** 

Si possono sfruttare ad esempio gli **OSINT:** 

- OSINT è il primo passo che un aggressore deve completare per portare a termine le fasi successive di un attacco.  L'aggressore deve **studiare** la **vittima raccogliendo** ogni **informazione** disponibile **sull'azienda** e sui suoi **dipendenti** , come le dimensioni dell'azienda, gli indirizzi e-mail, i numeri di telefono da risorse disponibili al pubblico  per determinare il miglior obiettivo per  l'attacco.

Ecco alcuni strumenti 

- [theHarvester](https://github.com/laramies/theHarvester) oltre a raccogliere e-mail, questo strumento è anche in grado di raccogliere nomi, sottodomini, IP e URL utilizzando più fonti di dati pubblici
- [Hunter.io](https://hunter.io/) questo è uno strumento di ricerca e-mail che ti consentirà di ottenere informazioni di contatto associate al dominio
- [Framework OSINT](https://osintframework.com/) Il framework OSINT
    
    fornisce la raccolta di
    
    strumenti OSINT
    
    basati su varie categorie
    

Un aggressore utilizzerebbe anche siti web di social media come LinkedIn, Facebook, Twitter e Instagram per raccogliere informazioni su una specifica vittima che vorrebbe attaccare o sull'azienda. Le informazioni trovate sui social media possono essere utili per un aggressore per condurre un attacco di phishing.

# Weaponization

In questa fase semplicemente l’attaccante si armamentizza con malware, o un exploit o un payload. Può scriverlo da solo oppure acquistarlo sul dark web.

# Delivery

E’ il mezzo con cui spedisce il payload o il malware.

lo può fare ad esempio tramite:

- email di phishing
- chiavette usb, tipo nei bar, nei muri, nei parcheggi etc

# Exploitation

Se la vittima apre un un malware l’hacker avrà aottenuto l'accesso al sistema e questa è la fase di **sfruttamento.**

l'attore malintenzionato potrebbe sfruttare vulnerabilità basate su software, sistema o server per **aumentare** i **privilegi** o **muoversi lateralmente** attraverso la rete. 

Gli attaccanti **mirano** poi a **mantenere l’accesso** al sistema compromesso più a lungo possibile. Possono stabilire **backdoor**, creare **account utente** o installare malware persistente per garantire un accesso continuo anche se il punto di ingresso iniziale viene scoperto e mitigato.

# Installation

Con il malware consegnato nei sistemi qui l’hacker installerà in modo silenzioso il malware per poi attivarlo quando lo vorrà, ovvero la **persistenza** sui sistemi

Verranno istallati payload o malware che permettono di mantenere gli accessi come:

- Installazione di una web shell sul server
- backdoor

# C2 o Command and control

Qui l’obiettivo è di **controllare** e **manipolare** la vittima **da remoto** attraverso il malware, **stabilendo** una **comunicazione** dove l’endpoint compromesso comunicherebbe con un **server esterno** impostato dall’aggressore per stabilire un canale di comando e controllo. I canali piu utilizzati sono:

- **protocollo HTTP** (porta 80)e HTTPS (porta 443) questo tipo di comunicazione **fonde** il **traffico dannoso con** quello **legittimo** e può aiutare l'aggressore a **eludere** i **firewall**.
- DNS: La **macchina infetta** effettua **richieste DNS** costanti **al server DNS** e al **dominio** che appartiene a un **aggressore**, questo tipo di comunicazione C2 è anche noto come **DNS Tunneling.**

# Action on Objectives

In questa fase gli aggressori mirano a conseguire il loro obiettivo finale, che rappresenta il culmine delle loro attività di attacco, rubare dati sensibili, danneggiare l’operatività dell’organizzazione, estorcere denaro o altre risorse
