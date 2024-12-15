E’ utilizzato per il trasferimento di File, ovviamente **utilizza** il protocollo **TCP** per garantire l’arrivo di tutti i dati. Apre **2 connessioni** in parallelo: 

- Connessione **di controllo**: Usata per **spedire informazion**i come **username/password,** comandi per navigare nella directory e per inviare/ricevere file. Utilizza la **porta 21**
- Connessione **di dat**i: Nella quale **transitano fisicamente i dati**. Utilizza la **porta 20**

Il protocollo è stato sostituito con il **FTPs** che è supportato da un protocollo di criptazione **SSL.**
