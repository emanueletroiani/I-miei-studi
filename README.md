[IDS-IPS Analisi Comparativa.pdf](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/6b19a153-c6e8-4ec2-b5c5-97338e819fcd/IDS-IPS_Analisi_Comparativa.pdf)

**IDS** (intrusion detection system) è un sistema di rilevamento di minacce che invia **feedback** ad un **operatore** che a suo volta attuerà delle azioni, decidendo se far passare la minaccia o meno.

**IPS** (intrusion Prevenction System) è il sistema che rileva e **prende decisioni** di Drop o allow della minaccia rilevata.

Non è detto che L’IPS sia migliore dei due in quanto bisogna tenere conta anche dei **falsi positivi** e in alcuni **sistemi** che **necessitano** una **continuità** di **servizio** l’IDS risulta la scelta ideale.

# Tipi di IDS

In base alla collocazione del sistema possiamo avere 2 tipi:

- HIDS: IDS basati sugli host
    - Installato nel sistema operativo, monitorerà il traffico di entrata ed uscita dell’host e i processi in esecuzione.
- NIDS: IDS basati sul network
    - è un server dedicato al monitoraggio della rete VLAN attaccandolo allo Switch.

# COME L’IDS FUNZIONA

Bisogna che rilevi il traffico malevolo all’interno della rete, lo fa in 2 modi:

- Con le Firme: ovvero tramite un database sempre aggiornato, sa quali attività sono malevole.
- Con anomalie di traffico, qui bisogna insegnare all’ IDS il regolare traffico e lo possiamo fare tramite apprendimento automatico o con regole manuali
