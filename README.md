# Che cos’è

E’ una soluzione di sicurezza che aiuta le organizzazioni a riconoscere e affrontare potenziali minacce e vulnerabilità della sicurezza prima che possano interrompere le operazioni di business.

# Cosa fa

Il SIEM **acquisisce** i dati degli **eventi da** un'ampia gamma di **fonti** nell'intera **infrastruttura IT** di un'organizzazione, compresi gli ambienti on-premises e cloud.

I dati dei **registri eventi** di **utenti**, **endpoint**, **applicazioni, origini dei dati, carichi di lavoro cloud e reti,** nonché i dati provenienti da **hardware** e **software** di **sicurezza** quali firewall o software antivirus, vengono raccolti, **correlati** e **analizzati in tempo reale.** 

Alcune soluzioni SIEM integrano anche feed di [threat intelligence](https://www.ibm.com/it-it/topics/threat-intelligence) di terza parte al fine di correlare i propri dati di sicurezza interna con firme e profili di minaccia precedentemente riconosciuti. L'integrazione in tempo reale con i feed di threat intelligence consente ai team di bloccare o rilevare nuove tipologie di firme utilizzate negli attacchi.

- **Riconoscimento delle minacce in tempo reale**
- **Automazione basata sull'AI**
    - Le soluzioni SIEM di nuova generazione oggi si integrano con potenti sistemi di [orchestrazione della sicurezza, automazione e risposta (SOAR)](https://www.ibm.com/it-it/topics/security-orchestration-automation-response), che apprende automaticamente dal comportamento della rete
- **Migliore efficienza organizzativa**
    - Una dashboard centrale fornisce una visione unificata dei dati, degli avvisi e delle notifiche di sistema, consentendo ai team di comunicare e collaborare in modo efficiente quando rispondono a minacce e incidenti di sicurezza.
- **Valutazioni e reporting di conformità**
- **Monitoraggio di utenti e applicazioni**
    - tracciano le attività di rete di tutti gli utenti, i dispositivi e le applicazioni, migliorando notevolmente la trasparenza dell'intera infrastruttura e rilevando le minacce
- **Rilevamento di minacce avanzate e sconosciute**
    - [*Minacce interne](https://www.ibm.com/it-it/topics/insider-threats):* vulnerabilità della sicurezza o attacchi provenienti da individui con accesso autorizzato alle reti aziendali e agli asset digitali.
    - [*Phishing*](https://www.ibm.com/it-it/topics/phishing)
    - [*Ransomware](https://www.ibm.com/it-it/topics/ransomware):* [malware](https://www.ibm.com/it-it/topics/malware)
    - [*Attacchi DDoS (Distributed Denial of Service)](https://www.ibm.com/it-it/topics/ddos):*
    - [*Esfiltrazione dei dati](https://www.ibm.com/it-it/topics/data-exfiltration):*

# Esempi di log

- **log di Host**
    - Un utente che accede a un file
    - Un utente che tenta di autenticarsi.
    - Un'attività di esecuzione del processo
    - Un processo che aggiunge/modifica/elimina una chiave o un valore del registro.
    - Esecuzione di Powershell
- **log di Rete**
    - Connessione SSH
    - Un file a cui si accede tramite FTP
    - Traffico web
    - Un utente che accede alle risorse aziendali tramite VPN
    - Attività di condivisione file di rete

# Dove sono fisicamente i log

- **Windows**: Se digitiamo **Event Viewer** nella barra di ricerca troviamo i log
- **Linux:**
    - /var/log/httpd: contiene i registri delle richieste/risposte HTTP e degli errori.
    - /var/log/cron: in questa posizione vengono memorizzati gli eventi relativi ai cron job.
    - /var/log/auth.log e /var/log/secure: memorizzano i log relativi all'autenticazione.
    - /var/log/kern: questo file memorizza gli eventi relativi al kernel.
- **Server Web:**
    - /var/log/apache  o  /var/log/httpd.

# Come arrivano i Log nel SIEM?

Ogni soluzione SIEM ha il suo modo di ingerire i log:

- **Agent / Forwarder:** queste soluzioni SIEM forniscono uno strumento leggero chiamato agente (inoltro di Splunk) che viene installato nell'Endpoint. È configurato per catturare tutti i log importanti e inviarli al server SIEM .
- **Syslog**:  Syslog è un protocollo ampiamente utilizzato per raccogliere dati da vari sistemi come server web, database, ecc., e inviarli in tempo reale alla destinazione centralizzata.
- **Caricamento manuale**:  alcune soluzioni SIEM , come Splunk , ELK , ecc., consentono agli utenti di ingerire dati offline per un'analisi rapida. Una volta ingeriti, i dati vengono normalizzati e resi disponibili per l'analisi.
- **Port-Forwarding:** le soluzioni  SIEM possono anche essere configurate per l'ascolto su una determinata porta, dopodiché gli endpoint inoltrano i dati all'istanza SIEM sulla porta di ascolto.

# Regole di Correlazione

Una volta che il SIEM ottiene i Log dovrà esaminarli tramite le condizioni o regole impostate di defoult o dagli analisti.

Le regole di correlazione sono praticamente espressioni logiche impostate per essere attivate. Ecco alcuni esempi di regole di correlazione:

- Se un utente ottiene 5 tentativi di accesso non riusciti in 10 secondi, invia un avviso per**`Multiple Failed Login Attempts`**
- Se l'accesso riesce dopo più tentativi di accesso non riusciti, genera un avviso per**`Successful Login After multiple Login Attempts`**
- Viene impostata una regola per ricevere un avviso ogni volta che un utente collega una **chiavetta USB** (utile se la chiavetta USB è soggetta a restrizioni in base alla politica aziendale)
- **Se il traffico in uscita è > 25 MB** - Genera un avviso per un potenziale tentativo di **esfiltrazione** dei **dati** (solitamente, dipende dalla politica aziendale)
