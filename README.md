[DOWNLOAND](https://fireeye.market/apps/211364)

E’ un tool gratuito di Windows che permette di investigare su di un Host attraverso l’analisi delle memoria e dei file. ai fini di sviluppare un profili di valutazione delle minacce.

In sostanza **forniremo a Redline** un **file** IOC **generato** in **IOC Editor** e lo **useremo** per **verificare** un **sistema**, alla **ricerca** della presenza di uno qualsiasi degli **indicatori** di **compromissione** elencati.

# Installazione

1. Fare clic su "Crea un raccoglitore di ricerca IOC".
2. Fare clic su "Sfoglia" nell'angolo in alto a destra
3. Individuare la cartella denominata "IOCs" e fare clic su "Seleziona cartella".
4. Selezionare il file IOC nella finestra di sinistra, quindi fare clic su "Avanti" nell'angolo in basso a destra.

Dopo aver selezionato il file IOC, dovrebbe apparire la schermata seguente, che chiede di selezionare una posizione per salvare il raccoglitore IOC. Prima di proseguire, è necessario andare in "Modifica lo script" per selezionare l'enumerazione dei file. Andare alla voce "disco" e selezionare le caselle contrassegnate qui sotto. Ora create una cartella vuota, poiché Redline richiede una posizione di base per salvare tutti i file e i risultati della caccia. Navigare in un punto qualsiasi e creare una nuova cartella chiamata "Caccia di prova 1". Una volta fatto questo, possiamo fare clic sul pulsante "Sfoglia" e selezionare la nuova cartella. Successivamente, un popup ci dirà che il pacchetto Collector è stato creato e salvato nella posizione selezionata.

![Untitled](https://github.com/user-attachments/assets/5bd808ba-a972-4e46-b73c-a851901ce6d7)

![Untitled](https://github.com/user-attachments/assets/01b259bf-3145-41f4-8c28-5f2bf8065192)

![Untitled](https://github.com/user-attachments/assets/d3261746-63f9-4481-b200-add12258f0da)

# Pre-Hunt Brief

Riassumiamo quindi ciò che abbiamo fatto finora e ciò che stiamo per fare. Nella sezione del corso precedente, abbiamo creato un file IOC per un'immagine denominata clint-patterson-dYEuFB8KQJk-unsplash.jpg. Abbiamo raccolto l'hash MD5, l'hash SHA-1, il nome e la dimensione del file. Abbiamo quindi importato questo file IOC nello strumento di auditing Redline e creato un pacchetto IOC Collector che consiste in script che analizzeranno il nostro computer di destinazione per identificare i file che corrispondono a uno qualsiasi degli indicatori di compromissione che abbiamo fornito. Cerchiamo i seguenti valori

- **File Size Value = 1057889**
- **File Name Value = clint-patterson-dYEuFB8KQJk-unsplash.jpg**
- **MD5 Hash = 81ef348226632fb1061d22d4e6fd3479**
- **SHA-1 Hash = 173b0434341b25fb17c4b2829f8058b29738faef**

Per questo esempio di valutazione, ho nascosto lo stesso file immagine in 3 posizioni diverse sul mio sistema Windows host. Tuttavia, ho apportato alcune modifiche in modo che non siano tutte uguali:

- **The first file has the exact same values as mentioned above** (we should detect it from all IOCs)
- **The second file has a different MD5/SHA-1 hashes, and file size, as I have added some random characters into the file** (we should detect it from the filename)
- **The last file has an altered file name** (we should detect it from the MD5 and SHA-1 hashes, and the file size)

# Trovare la minaccia

Abbiamo i nostri IOC. Abbiamo la nostra base di collettori di IOC. Siamo pronti a controllare il sistema utilizzando Redline per rilevare la presenza dei nostri indicatori di compromissione. Passare alla cartella di caccia e vedere tutti i file del raccoglitore come mostrato di seguito.

![Untitled](https://github.com/user-attachments/assets/8b1cf4c8-1b4f-4a12-b31f-4c0e73f71224)

Ora è il momento di avviare la verifica. Digitare "CMD" nella barra di ricerca di Windows e fare clic con il pulsante destro del mouse su > esegui come amministratore. Questa operazione è importante perché Redline deve essere eseguito come amministratore per poter condurre tutte le ricerche senza essere interrotto o senza che gli venga negato l'accesso a determinate posizioni. Ora passate alla cartella di caccia usando "cd" per cambiare directory. Partendo da C:/ ho dovuto usare i seguenti comandi: cd Users > cd JBeam > cd Documents > cd "Test Hunt 1". Una volta che ci si trova nella stessa posizione dei file del raccoglitore, utilizzare il comando .\RunRedlineAudit.bat

Quando si esegue questo script, Redline inizia a lavorare. Dovreste vedere apparire una nuova directory nella cartella del Collector denominata "Sessioni", una sottocartella denominata "AnalysisSession1" e una sottocartella denominata "Audit". Continuate ad aggiornare questa posizione (fate clic con il pulsante destro del mouse su un punto qualsiasi > aggiorna) e vedrete che la dimensione del file XML aumenterà e alla fine si fermerà. Il valore della Data di modifica è utile per capire se l'audit è in corso o è terminato.

Una volta terminata la verifica nella directory "AnalysisSession1", si vedranno apparire dei nuovi file, come nella schermata seguente. Utilizzeremo AnalysisSession1.mans per importare in Redline, in modo da generare un rapporto IOC e vedere cosa abbiamo trovato.

![Untitled](https://github.com/user-attachments/assets/e6a7484d-cf8c-4330-8a59-d4fa2881aedf)

Aprire Redline, sotto la voce Analizza dati fare clic su Apri analisi precedente. Selezionare il file AnalysisSession1.mans, che verrà caricato in Redline per l'analisi. Nell'angolo in basso a sinistra sono visibili tre schede. Fate clic su Rapporti IOC e dovreste vedere un rapporto della vostra caccia (in caso contrario, date a Redline un po' di tempo per finire di creare il rapporto: dovreste vedere un popup nella parte inferiore dello strumento che indica che ci sta lavorando). Fare clic sul rapporto IOC, quindi su "Visualizza risultati +" a destra per visualizzare i risultati.

![Untitled](https://github.com/user-attachments/assets/839142a5-ee8a-42ec-941b-891cdfe0937c)

Ce l'abbiamo fatta! Redline ha trovato con successo tutti i nostri file in base ai IOC forniti, comprese le versioni originali e due modificate. Siamo in grado di vedere il percorso del file, le dimensioni, l'hash MD5, l'utente e varie date importanti del file.

![Untitled](https://github.com/user-attachments/assets/92e127fe-35c3-45c6-8d7e-4de9eb225ab3)





