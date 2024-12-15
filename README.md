# Il proxy

E’ un software che si frappone tra Client e server. con questa struttura: 

![image](https://github.com/user-attachments/assets/dbfb41b8-c55e-426f-83d2-f5d1d78f2f36)

Permette:

- di rendere piu rapido l’accesso alle pagine web tramite il salvataggio sulla memoria cache
    - se un client cerca una pagine questa viene salvata nella **cache**, se la stessa pagina viene cercata da un altro dispositivo nella stessa rete il proxy server utilizzerà la sua cache per velocizzare la navigazione in piu’ **salva i log** delle **pagine web** visitare.
- Bloccare alcuni indirizzi ip per non permettere la navigazione all’interno di una rete locale lan. Tipo socialnetwork all’interno di una scuola.
- garantisce l’anonimato nascondendo l’indirizzo IP del computer che ha effettuato la richiesta. **Se l’ IP della rete locale viene scambiato in IP pubblico dal NAT e il server proxy Criptografa l’IP pubblico,** mostra solo l’ IP del proxy
    
   ![image](https://github.com/user-attachments/assets/edc2a987-c281-4748-89c2-5c81c318e187)

    - tecnologia in incognito superata dalla VPN in quanto garantisce anche una sicurezza crittografando i dati

# Il reverse proxy

E’ posto tra internet e i server, intercettando le richieste dei client per conto dei server.

![image](https://github.com/user-attachments/assets/c2ea4382-e31d-4d7b-9205-07f1299a3767)

- permette il bilanciamento dl traffico delle richieste ai server.
- Nasconde l’IP del sito web ai client, (utile contro attacchi DDoS)
- Ha una cache che memorizza le richieste ai server velocizzando la navigazione.
- comprime le richieste che vengono dal web aiutando a diminuire la larghezza di banda
- Gestisce la crittografia per conto dei server permettendo agli stessi di utilizzare meno memoria.
