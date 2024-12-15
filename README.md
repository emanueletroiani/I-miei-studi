Consente di **trasferire dati nel WEB**, dove il **Client fa** una **richiesta** e il **WEB server Risponde**. 

L’HTTP e il Web server comunicano in una porta ben definita, L’80.

Negli anni per motivi di sicurezza si è aggiunta una cryptografia al livello HTTP diventando HTTPS (security) che ascolta alla porta 443.

### Esempio di **Richiesta HTT**P (suddivisa in blocchi) dal **lato Client**:

![Untitled](https://github.com/user-attachments/assets/0190eb68-cbb6-4919-a068-188c7c00b614)

1. Metodo: Modalità con il quale il Client interagisce con il Server. 
2. **Url**: Stringa di caratteri ben definita che identifica la risorsa richiesta
3. **Versione**: Versione HTTP in uso dal client
4. **Header**: Info varie (nome WEB Server, formato, applicazione client)
5. **Body:** Contenuto della richiesta (Se stiamo compilando un modulo o caricando un file)

# Tipi di Metodo

![Untitled](https://github.com/user-attachments/assets/22cff6ab-f44f-4471-a531-84628bcdc19b)

**IMPORTANTE**: Ogni volta che il Web Server invia una risposta ad una precisa richiesta del client la connessione viene chiusa, serve per non appesantire il Client. Per far si che le informazioni tra utente e Web Server vengano conservati sono stati inventati i **Cookies.**

**COSA SONO I COOKIES?**

Sono delle **stringhe di testo** che vengono memorizzate nel Client, sono **utili** perchè c**ontengono informazioni sulla nostra navigazione** e la rendono piu intuitiva e rapida. ad esempio possono memorizzare un carrello nei web shop, mantengono compilati i documenti presso un sito web etc etc. Non pone problemi di sicurezza.

# Esempio di Richiesta HTTP (suddivisa in blocchi) dal lato Server:

![Untitled](https://github.com/user-attachments/assets/2b574bbe-6858-43fe-b393-1c744ae72241)

1. **Versione:** Versione dell’http 
2. **Stato:**  un codice numerico che indica lo stato della richiesta.  
3. **Reason:** Indica il motivo della risoluzione dello stato. In questo caso la richiesta del client ha avuto esito positivo (OK)
4. **Header:** Sono forniti i dati, Data,Serve di utilizzo, Tipo di contenuto, connessione
5. **Body:** Sono i dati veri e propri contenuti nell’ html

# Tipi ci codice di stato

![Untitled](https://github.com/user-attachments/assets/8b44c689-0390-405f-b845-0b898b14ded1)

# HTTPs

HTTP+SSL/TLS+TCP= HTTPs

Utilizza protocolli di cifratura come **SSL**(**secure socket layer**)o la sua evoluzione **TLS**(**Trasport layer security**) utilizza sia la chiave asimmetrica che simmetrica.




