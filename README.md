Il sistema monotasking, o monoprogrammazione, si riferisce a un ambiente in cui solo un singolo processo può essere eseguito alla volta sulla CPU. In un sistema monotasking, la CPU è dedicata completamente all'esecuzione di un'unica attività o processo per un determinato periodo. **in pratica avvia una sola applicazione alla volta**

Quando si tratta di leggere i processi nella CPU in un sistema monotasking, il flusso di esecuzione è abbastanza semplice. Ecco come funziona:

1. **Caricamento del Programma:**
    - Quando il sistema operativo viene avviato, viene caricato un programma principale o un processo iniziale nella memoria principale (RAM). Questo processo rappresenta l'attività primaria del sistema.
2. **Esecuzione del Processo:**
    - La CPU inizia ad eseguire le istruzioni del processo caricato in memoria. Il sistema operativo assegna l'intera potenza di elaborazione della CPU a questo unico processo.
3. **Completamento o Interruzione:**
    - Il processo continua ad essere eseguito fino a quando non è completato o viene interrotto da un'azione specifica, come la terminazione del programma o l'attivazione di un altro processo.
4. **Pianificazione del Processo Successivo:**
    - Se è previsto l'avvio di un altro processo, il sistema operativo può pianificare il caricamento del nuovo processo in memoria e l'avvio dell'esecuzione. Tuttavia, in un sistema monotasking, ciò avviene solo dopo che il processo corrente è stato completato o interrotto.
5. **Ripetizione del Ciclo:**
    - Il ciclo di caricamento, esecuzione e completamento o interruzione si ripete ogni volta che un nuovo processo deve essere eseguito. In un sistema monotasking, solo un processo è attivo alla volta.

La monoprogrammazione ha la sua utilità in sistemi operativi dedicati a compiti specifici, come i microcontrollori incorporati, ma è meno comune nei moderni sistemi operativi per computer personali, che generalmente utilizzano sistemi multitasking per consentire l'esecuzione simultanea di più processi sulla CPU.

![Untitled](https://github.com/user-attachments/assets/642e0879-34b5-413e-8567-16fdcfe421f5)
