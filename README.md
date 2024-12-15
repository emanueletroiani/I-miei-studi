La piramide del dolore indica quanto dolore un difensore causa ad un attaccante quando gli nega uno di questi IoC, cioè quanto poi sarà difficile per l’attante modificare il suo IoC per un attacco

![image](https://github.com/user-attachments/assets/77123dea-3370-453a-adf4-63a9e02157d3)


Gli indicatori di compromissione (**IOC**, Indicator of Compromise) sono **eventi** o **attività anomale** che **indicano** la **presenza** di una **minaccia** informatica **all'interno** di un **sistema** o di una rete. Gli **IOC** possono essere **utilizzati** per **identificare**, tracciare e rispondere alle **minacce** informatiche, al fine di prevenire o mitigare i danni causati.

Divini in:

- **Indicatori di compromissione(IoC):** questi indicano una **violazione** del **sistema** o della rete, **come** ad esempio l'attività di un **malware**, un **accesso non autorizzato** o un **tentativo** di **furto** di **dati** sensibili.
- **Indicatori di attacco (IoA):** questi **indicano** una potenziale **minaccia informatica** o un tentativo di attacco, come ad esempio **tramite** l'utilizzo di indirizzi **IP sospetti**, **URL malevoli**, **hash** di **file** noti per essere dannosi, ecc.
- **Indicatori di comportamento**: questi indicano **comportamenti anomali** o sospetti **all'interno** del **sistema** o della rete, come ad esempio un **aumento** del **traffico di rete**, un **elevato utilizzo della CPU, Artefatti di rete** o la modifica di file di sistema. DDOS volumetrico e l’altro

La raccolta e l'analisi degli IOC sono spesso utilizzate come parte di un sistema di rilevamento delle minacce informatiche (TDS, Threat Detection System) o di un sistema di informazione sulla sicurezza (SIEM, Security Information and Event Management). L'identificazione tempestiva degli IOC può consentire alle organizzazioni di mitigare i rischi di sicurezza e di prevenire il verificarsi di attacchi informatici.

# Hash Values

Alla base della piramide ci sono i valori hash. I **valori hash** come ad esempio **firme sh1 sh2 md5**. Sono gli **ioc** più comunemente **utilizzati** da **sistemi** di **difesa** tipo **IDS** e **IPS**, sistemi antimalware. Però questi questi valori **Hash** sono un qualcosa di estremamente **semplice** da **modificare**, oggi come oggi poi i **malware** metamorfici o polimorfici quindi **continuano** a **modificare** le **proprie** firme **Hash** e quindi andare a studiare un attaccante, andando a rilevare le firme Hash, abbiamo fatto veramente poco danno all'attaccante. Perché oramai gli attaccanti continuano a variare continuamente le firme hash sugli artefatti che poi vengono rilasciati all'interno dei sistemi infettati.

## Come facciamo a sapere se un email è infetta da un malware?

Ad esempio possiamo verificare se c’è una **corrispondenza** della **grandezza** in **byte** dell’allegato con una **lista** di **malware** già individuati.

## Generazione di indicatori di hash dei file

Il codice **Hash** è generato da algoritmi ed è **univoco per** ogni **file** e un **solo carattere** aggiunti ne può **modificare** l’intera **stringa**, su kali possiamo utilizzare i tools **md5sum(**meno utilizzato) ****e **sha256sum** per **generare Hash** di un **file**

ES:
![Untitled](https://github.com/user-attachments/assets/5d11453d-8b9a-4b2c-95fd-acdbaefa9525)

## Generare Hash da Windows

Aprite un **terminale** PowerShell, **spostatevi** nella stessa **posizione** del **file** di cui volete recuperare l'hash e utilizzate il **comando Get-FileHash <nomefile>**. Per **impostazione predefinita**, l'algoritmo di hashing sarà **SHA256**. Ma è possibile utilizzare il flag -algoritmo per specificare l'algoritmo da utilizzare, ad esempio MD5 o SHA1

![Untitled](https://github.com/user-attachments/assets/7946941c-8514-41d1-a193-066d621ea3ab)

## Modificare file per bipassare il controllo dell’hash

Basta modificare il file aggiungendo una stringa echo per cambiare l’ hashing

![Untitled](https://github.com/user-attachments/assets/a44d1021-1d6e-44d3-98d9-b1c0cdc13fb8)

# IP Address

Nella Piramide del dolore sono collocati in Verde. In caso di tentativi di accesso da parte di indirizzi **IP** potenzialmente **malevoli possiamo bloccarli** MA per un **hacker esperto** sarà facile utilizzare un **altro IP pubblico** e tentare di nuovo l’accesso. 

## Come Fanno gli Hacker a cambiare IP?

Utilizzano un Tool chiamato **Fast Flux** spiegato [**qui](https://unit42.paloaltonetworks.com/fast-flux-101/).**

**l’attaccante ha un server con un indirizzo IP, il dns cambia sempre perchè le richieste HTTP vengono spedite dalla botnet e non dal server madre.** di conseguenza è difficile trovare il vero IP associato al DNS

**IN BREVE:** è una **tecnica** **DNS** utilizzata dalle **botnet** per nascondere attività di phishing, proxy web, distribuzione di malware e comunicazione di malware dietro host compromessi che agiscono come proxy. Lo scopo dell'utilizzo della rete Fast Flux è rendere la comunicazione tra malware e il suo server di comando e controllo (C&C) difficile da scoprire per i professionisti della sicurezza.

Quindi, il concetto principale di una rete Fast Flux è avere più indirizzi IP associati a un nome di dominio, che cambia costantemente.

Vengono utilizzate anche reti **Tor, VPN**

# Domain Names

Un hacker può sfruttare i caratteri di un dominio sicuro per ingannare una vittima. Lo da acquistando un dominio con caratteri simili all’originale ES:

![image](https://github.com/user-attachments/assets/c9ff9098-eb04-41f3-a33a-e57a3d5436bf)

Questo attacco si chiama **Punycode** è un modo per converitire parole che non possono essere scritte in ASCII in una codifica ASCII Unicode.

## Per rilevare i domini dannosi è possibile utilizzare i log dei proxy o dei server web.

Gli aggressori solitamente nascondono i domini dannosi sotto **URL Shorteners.** AU RL Shortener  è uno strumento che crea un URL breve e univoco che reindirizzerà al sito Web specifico specificato durante la fase iniziale di impostazione del collegamento URL Shortener. Secondo [Cofense](https://cofense.com/url-shorteners-fraudsters-friend/) , gli aggressori utilizzano i seguenti servizi di URL Shortening per generare collegamenti dannosi:

- bit.ly
- goo.gl
- ow.ly
- s.id
- smarturl.it
- tiny.pl
- tinyurl.com
- x.co

## Come scoprire il vero reindirizzamento

- mettiamo caso che abbiamo questo link https://tinyurl.com/bw7t8p4u se aggiungessimo un segno + alla fine otterremo il reale link
    - https://tinyurl.com/bw7t8p4u+

# Host Artifacts

A questo livello, **l'attaccante** si sentirà un po' più **infastidito** e frustrato **se si riesce a rilevare l'attacco.**  L'attaccante dovrà tornare indietro a questo livello di rilevamento e cambiare i suoi strumenti e metodologie di attacco.  Ciò richiede molto tempo all'attaccante e, probabilmente, dovrà spendere più risorse sui suoi strumenti di attacco.

**Gli artefatti sono le tracce o gli elementi osservabili che gli aggressori lasciano sul sistema,** come valori di registro, esecuzioni di processi sospetti, pattern url, modelli di attacco o IOC, file rilasciati da applicazioni dannose o qualsiasi cosa esclusiva della minaccia attuale.

Gli artefatti di rete e di host rappresentano un’importante fonte di informazioni per gli investigatori di sicurezza informatica, consentendo loro di raccogliere prove e identificare attività sospette o malevole all’interno di una rete o su un dispositivo specifico.

*Importanza degli Artefatti di Rete e di Host*

1.**Indizi di Attività Malevole**: Gli artefatti di rete e di host possono fornire indizi cruciali sull’attività dei criminali informatici, inclusi file di log, registri di sistema e altre tracce digitali lasciate durante un attacco.

2.**Analisi Forense Digitale**: Gli investigatori di sicurezza utilizzano gli artefatti di rete e di host per condurre analisi forensi digitali, ricostruendo la sequenza degli eventi e identificando le vulnerabilità utilizzate dagli aggressori.

3.**Rilevamento delle Minacce**: I sistemi di rilevamento delle minacce possono utilizzare gli artefatti di rete e di host per identificare comportamenti sospetti o modelli anomali che potrebbero indicare la presenza di un attacco informatico.

*Tipi di Artefatti di Rete e di Host*

- **File di Log**: I file di log contengono registrazioni dettagliate delle attività di rete e di sistema, tra cui connessioni in ingresso e in uscita, accessi agli account e modifiche alle impostazioni del sistema.
- **Registri di Sistema**: I registri di sistema registrano eventi critici e informazioni diagnosticate relative al funzionamento del sistema operativo, come avvio e spegnimento del sistema, installazione di software e errori di sistema.
- **Cache DNS**: La cache DNS contiene informazioni sui nomi di dominio recentemente risolti in indirizzi IP, che possono essere utili per identificare tentativi di accesso a siti web malevoli o compromessi.

*Utilizzo degli Artefatti nella Pratica*

- **Analisi Forense**: Gli artefatti di rete e di host vengono analizzati durante le indagini di incidenti per identificare l’origine e l’entità di un attacco informatico e prendere misure correttive appropriate.
- **Monitoraggio Continuo**: Le organizzazioni devono implementare soluzioni di monitoraggio continuo per rilevare e rispondere tempestivamente alle attività sospette o dannose all’interno della loro rete e sui loro dispositivi.
- **Integrazione con Strumenti di Sicurezza**: Gli artefatti di rete e di host possono essere integrati con strumenti di sicurezza avanzati, come sistemi di rilevamento delle minacce e piattaforme di gestione degli eventi e delle informazioni di sicurezza (SIEM), per una maggiore visibilità e controllo.

Gli artefatti di rete e di host rappresentano una risorsa preziosa per gli investigatori di sicurezza informatica, consentendo loro di comprendere meglio le minacce e proteggere le reti e i dispositivi da attacchi informatici dannosi.

# Network Artifacts

Un artefatto di rete **può essere** una stringa user-agent, informazioni C2 o modelli URI seguiti dalle richieste HTTP POST. Un aggressore potrebbe **usare** una **stringa** User-Agent che non è mai stata osservata prima nel tuo ambiente o che sembra fuori dall'ordinario. User-Agent è definito da [RFC2616](https://datatracker.ietf.org/doc/html/rfc2616#page-145) come il campo request-header che contiene le informazioni sullo user agent che ha originato la richiesta.

**USER-AGENT:**

Il campo request-header User-Agent contiene informazioni sull'agente utente che ha originato la richiesta. Ciò serve a fini statistici, per tracciare le violazioni del protocollo e per il riconoscimento automatico degli User-Agent al fine di adattare le risposte per evitare particolari limitazioni del User-Agent

## Possono essere rilevati?

Gli artefatti di rete possono essere rilevati nei PCAP di Wireshark (file che contiene i dati dei pacchetti di una rete) utilizzando un analizzatore di protocollo di rete come [TShark](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html) o esplorando la registrazione IDS (Intrusion Detection System) da una fonte come [Snort](https://www.snort.org/) .

Richieste HTTP POST contenenti stringhe sospette:

![image](https://github.com/user-attachments/assets/080f3f36-a3dd-4d25-87bd-6dbbdfd7cd3d)

Andiamo in console e utilizziamo il seguente comando per filtrare le Stringhe User-Agent ****

- **tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap**
  
  ![image](https://github.com/user-attachments/assets/541a4011-3de6-4792-b3d3-5f2dbf415350)

Queste sono le stringhe User-Agent più comuni trovate per il [Trojan Emotet Downloader](https://www.mcafee.com/blogs/other-blogs/mcafee-labs/emotet-downloader-trojan-returns-in-force/)

Se riesci a rilevare le stringhe User-Agent personalizzate utilizzate dall'aggressore, potresti riuscire a bloccarlo, creando ulteriori ostacoli e rendendo più fastidioso il suo tentativo di compromettere la rete.

# Tools

A questo punto, abbiamo potenziato ﻿le nostre capacità di rilevamento contro gli artefatti. **L'attaccante** rinuncerebbe molto **probabilmente** a provare a entrare nella tua rete o **tornerebbe indietro** e proverebbe a creare un nuovo strumento che serva allo stesso scopo. **Sarà** la **fine** dei **giochi** per gli aggressori, **poiché dovrebbero investire** del **denaro** nella creazione di un **nuovo strument**o (se sono in grado di farlo), trovare lo strumento che ha lo stesso potenziale o persino ricevere un po' di formazione per imparare a essere competenti in un determinato strumento.

 

Gli aggressori utilizzerebbero le utility per creare documenti macro dannosi (maldoc) per tentativi di spear phishing, una backdoor che può essere utilizzata per stabilire [C2 (Command and Control Infrastructure) , file .EXE e](https://www.varonis.com/blog/what-is-c2/) .DLL personalizzati , payload o password cracker.

**Un trojan ha rilasciato il file sospetto "Stealer.exe" nella cartella Temp:**

![image](https://github.com/user-attachments/assets/06bf5421-df98-4028-82f8-d5f7265ffc64)

L'esecuzione del binario sospetto:

![image](https://github.com/user-attachments/assets/0c8f143b-576a-45d4-9705-7337f1515502)

In questa fase, le firme antivirus, le regole di rilevamento e le regole YARA possono rivelarsi ottime armi da utilizzare contro gli aggressori.

[MalwareBazaar](https://bazaar.abuse.ch/)  e  [Malshare](https://malshare.com/)  sono ottime risorse per accedere a campioni, feed dannosi e risultati YARA: possono rivelarsi molto utili quando si tratta di ricerca delle minacce e risposta agli incidenti.

Per le regole di rilevamento, [SOC Prime Threat Detection Marketplace](https://tdm.socprime.com/) è un'ottima piattaforma in cui i professionisti della sicurezza condividono le proprie regole di rilevamento per diversi tipi di minacce, tra cui le più recenti CVE sfruttate in natura dagli avversari.

L'hashing fuzzy è anche un'arma potente contro gli strumenti dell'attaccante. L'hashing fuzzy ti aiuta a  eseguire analisi di similarità: fai corrispondere due file con piccole differenze in base ai valori di hash fuzzy. Uno degli esempi di hashing fuzzy è l'utilizzo di [SSDeep](https://ssdeep-project.github.io/ssdeep/index.html) ; sul  sito Web ufficiale di SSDeep, puoi anche trovare la spiegazione completa dell'hashing fuzzy. 

Esempio di SSDeep da VirusTotal:

![image](https://github.com/user-attachments/assets/7c8851e8-d8aa-40aa-b758-008c3e367f5b)

# TTP

Ovvero capire come si muove l’attaccante.

TTP sta per Tactics, Techniques & Procedures (Tattiche, Tecniche e Procedure). Ciò i**nclude l'intera [MITRE  ATT&CK Matrix](https://attack.mitre.org/) ,** ([qui spiegata](https://www.ibm.com/it-it/topics/mitre-attack))ovvero tutti i **passaggi intrapresi** da un **avversario** per **raggiungere** il suo **obiettivo**, a partire dai **tentativi di phishing fino alla persistenza e all'esfiltrazione dei dati.** 

**Studiando** le **tattiche tecniche procedure utilizzate** **dagli attaccanti**, sicuramente **siamo** in **grado** di **creare** nell'attaccante il **maggior** **danno** possibile. Gli attaccanti per poter modificare il loro tts, dovranno studiare, imparare nuove tattiche e dovranno utilizzare nuovi tool.

In definitiva la **piramide** del **dolore** è la **strada** da seguire **per ottenere il massimo valore per gli investimenti in difesa ed intelligence delle minacce** da parte appunto del difensore **l'utilizzo** del framework **mitre Attack** insieme alla Piramide del dolore permetteranno ai team di sicurezza di concentrarsi sulle formazioni più preziose e sulle misure di protezione che causeranno il massimo dolore agli attaccanti rendendo più difficile per loro condurre attacchi di successo.

Se riesci a rilevare e rispondere rapidamente ai TTP, non lasci agli avversari quasi nessuna possibilità di reagire.  Ad esempio, se potessi rilevare un attacco [Pass-the-Hash](https://www.beyondtrust.com/resources/glossary/pass-the-hash-pth-attack) utilizzando Windows Event Log Monitoring e porvi rimedio, saresti in grado di trovare l'host compromesso molto rapidamente e fermare il movimento laterale all'interno della tua rete . A questo punto, l'attaccante avrebbe due opzioni:

1. Torna indietro, fai più ricerca e formazione, riconfigura i tuoi strumenti personalizzati
2. Arrendersi e trovare un altro obiettivo





