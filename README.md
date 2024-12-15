**COME INSTAURA UNA CONNESSOINE IL PROTOCOLLO TCP?**

Tramite la **three-way-handshake**, con il processo Syn-syn/ack-ack

Syn= Syncronisation

Ack= acknowlegement

Header:

![Untitled](https://github.com/user-attachments/assets/7757fd48-197e-479e-b4e4-8d9b8412d6bf)

Il Client invierà una richiesta SYN positiva (con flag a valore 1) con un numero SEQ (sequens number) casuale.

![Untitled](https://github.com/user-attachments/assets/3fdbc77d-212e-47ad-ad63-55f4a6dc3820)

il Server risponderà con un segmento di SYN/ACK con valore impostato a +1 del SEQ inviato in precedenza. Invierà anche un SEQ con valore impostato dal Server. Infine sarà presente un SYN impostato con flag ad 1 per la richiesta di connessione.

![Untitled](https://github.com/user-attachments/assets/47f19535-14e1-4f9e-9bae-5b0f9550ebba)

Il Client completa la configurazione inviando segmento contenente ACK con valore impostato a +1 del SEQ del Server e un SEQ con valore impostato del SEQ del client +1. Infine conterrà una flag SYN impostata a 0 per chiudere la connessione.

![Untitled](https://github.com/user-attachments/assets/d7be2d7d-b16c-4c22-8d3a-c034546f014c)

# **COME TERMINA LA CONNESSIONE TCP?**

Con la **Four ways end connection.**

![Untitled](https://github.com/user-attachments/assets/e59f47e5-cd7d-4e64-921a-d7cf7a043dec)

1.  Il **client invia** un **Segmento** con Flag **FIN** impostato ad **1** e un numero di **SEQ random**
2. Il **server** risponde con un **ACK** con **valore SEQ+1**. **FIN** è impostato a **0** e A**CK a 1**, **la connessione ancora non è interrotta e il server può ancora spedire dati.**
3. Una volta finito il **server manderà** un **segmento FIN** con Flag impostata ad **1** e una **SEQ random.**
4. Il **Client Risponderà** con un **Fin** con Flag **0**, un **ACK con valore SEQ+1 del server.**

![Untitled](https://github.com/user-attachments/assets/459434fe-972b-459e-aeeb-eae9e7eff296)








