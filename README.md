# Pila Iso/Osi

![Pila](https://github.com/user-attachments/assets/4faf5c62-364f-4de5-a213-907feaeae97c)


# Perchè è stata creata

E' nato dalla necessità dei costruttori di trovare un **mezzo** che **permette**sse ai diversi
**dispositivi di comunicare tra di loro tramite protocolli.** Le informazioni che il dispositivo sorgente e quello destinatario  si scambiano vengono chiamati **pacchetti**, sono **flussi di Bit** scambiati tramite segnali elettrici. I pacchetti sono composti da Header e Payload.

**HEADER**: contiene tutto il necessario affinche l’informazione contenuta nel pacchetto arrivi e venga compresa dal destinatario.

**Payload:** E’ l’informazione vera e propria.

Entrambi vengono **inglobati e diventano il Payload del livello successivo**, **sino** ad arrivare al **livello 1** **del ricevente che in maniera inversa procederà al decapsulamento**.

![decaplulamento](https://github.com/user-attachments/assets/2d745762-0001-4002-b63a-70885719bf54)

Si sviluppa in **7 livelli** dove **ogni livello** ha un preciso compito e **può comunicare** solo ad un **dispositivo dello stello livello** **o al livello successivo affinchè il pacchetto dati dal dispositivo 1 arrivi al dispositivo 2.** Questo avviene tramite l'**incapsulamento** di ogni livello. 

**N.B.** il modello ISO/OSI è un modello teorico da utilizzare come referenza. In pratica le applicazioni utilizzano il modello TCP/IP che varia leggermente dal modello teorico ISO/OSI. Dal livello 1 al 3 siamo fuori il sistema operativo. Dal layer 4 al 7 siamo dentro al sistema operativo

# **Differenza ISO/OSI con Tcp/ip**

![Untitled](https://github.com/user-attachments/assets/92871e3e-1081-4a6b-a71d-7c6b514ab57b)
![Untitled](https://github.com/user-attachments/assets/733ad97a-1bfd-4b3e-ba30-c7de989a012d)


