Una web app di distingue da un’applicazione perchè non necessita di un’istallazione da parte del cliente ma utilizza il browser per accedere all’app. La sua architettura si divide in 3 livelli ed ognuno ha una specifica funzione:

- **Presentazione (Front end):** è l’interfaccia grafica con cui interagisce l’utente. Realizzata utilizzando linguaggi HTML, CSS e script javascript
- **Logico**: E’ il motore elabora le richieste dell’ utente inviando a suo volta richieste al Back end per poi inviare la risposta all’utente. Questo livello è ciò che distingue un sito web dalla web app. Utilizza linguaggi come PHP e Java.
- **Dati (Back end)**: è il database che contiene i dati della web app. scritto in Mysql, oracle etc.

# ES:

il client invia una richiesta HTTP tramite il front end ma arriva al livello 2 logico che da una parte interpreta e gestisce le interrogazioni del back end e dall'altra genera il risultato in un *output* diretto allo stesso *browser*,

![image](https://github.com/user-attachments/assets/acd43b18-bb37-41ad-a021-125a43ade566)
