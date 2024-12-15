I sistemi multi tasking sono es: Windows e linux che permettono di utilizzare piu programmi alla volta. 

1. **Processi Concorrenti:**
    - Nei sistemi multitasking, **più process**i possono essere in esecuzione **contemporaneamente**. Ogni processo è un'istanza indipendente di un programma in esecuzione, e il sistema operativo alloca risorse della CPU a ciascun processo in base a politiche di scheduling specifiche.
2. **Scheduling:**
    - Il sistema operativo utilizza algoritmi di scheduling per determinare quali processi devono essere eseguiti in un determinato momento e per quanto tempo. Ciò consente di bilanciare l'utilizzo della CPU tra i vari processi e di rispondere alle esigenze di priorità dei processi.
3. **Switching del Contesto:**
    - Per passare da un processo all'altro, il sistema operativo esegue uno "switch di contesto". Questo comporta il salvataggio dello stato del processo corrente e il ripristino dello stato del nuovo processo da eseguire. Lo switch di contesto consente ai processi di condividere la CPU senza interferenze.
4. **Multithreading:**
    - I sistemi multitasking possono supportare anche il multithreading, che è la capacità di un programma di suddividere il proprio lavoro in più thread, ciascuno dei quali può essere eseguito in modo indipendente. I thread condividono le risorse dello stesso processo, semplificando lo scambio di informazioni.
5. **Priorità dei Processi:**
    - I processi possono avere diverse priorità assegnate dal sistema operativo. I processi ad alta priorità riceveranno più tempo di CPU rispetto a quelli a bassa priorità. Questo aiuta a garantire che i processi critici siano gestiti in modo tempestivo.
6. **Sistemi Operativi Moderni:**
    - I moderni sistemi operativi, come Windows, macOS e molte distribuzioni di Linux, sono progettati per supportare il multitasking. Gli utenti possono eseguire più applicazioni contemporaneamente, passare tra di esse e gestire le risorse in modo efficiente.
7. **Utente e Background:**
    - Gli utenti possono interagire direttamente con un'applicazione in primo piano, mentre altre applicazioni possono essere in esecuzione in background. Ciò consente l'esecuzione di processi in modo trasparente all'utente.

![Untitled](https://github.com/user-attachments/assets/cc331b4e-edf3-4200-98ac-cb6a40caa35e)

**Seguono sempre L’ordine di priorità A-B-C**

