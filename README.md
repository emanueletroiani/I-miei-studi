Serve per identificare in maniera univoca un Host all’interno della rete. Ci sono due tipo: **pubblico e privato**.

- **Pubblico**: è ’IP che ci identifica all’interno della rete Internet Globale, è fornito dal **ModemRouter del nostro ISP** (internet service provider). E’ unico al Mondo.
- **Privato**: Identifica ogni singolo dispositivo connesso alla rete domestica/aziendale che ha accesso al Modem Router. Di conseguenza possono esserci milioni di 192.168.1.1
  
[Approfondimento.pdf](https://prod-files-secure.s3.us-west-2.amazonaws.com/6f46adb7-7950-4f75-92a1-803289993db5/c68432d9-ace5-4707-ad51-0df2eb9264d8/ReS1.08_INDIRIZZI_IP.pdf)

![Untitled](https://github.com/user-attachments/assets/76aed820-0223-43e7-a91f-8e6c62ca9e4d)

Quando usi Internet, i dati che invii e ricevi vengono inviati tramite il tuo indirizzo IP pubblico, quindi il tuo router passa quel traffico al tuo dispositivo utilizzando il suo indirizzo IP privato. Questo processo di scambio tra indirizzi IP pubblici e privati è chiamato **Network Address Translation (NAT)**.

Attualmente gli IP che si utilizzano sono gli **IPV4,** formati da 32Bit o 8 Byte. vanno da 0 a 255 ma hanno dei valori specifici per ogni categoria. Di IP ce ne sono circa 4 miliardi e sono in esaurimento, presto si passera agli IPV6.

# CLASSI DI INDIRIZZI IP

![Untitled](https://github.com/user-attachments/assets/eb225a46-3fb0-4632-aef4-41d9bd279c8f)

![Untitled](https://github.com/user-attachments/assets/2407ea2e-27e6-4bd1-9b1e-e18324655564)

![Untitled](https://github.com/user-attachments/assets/8faae0b1-7d7c-44a6-aea3-7e20b4030022)

Nel livello 3 bisogna capire se il destinatario fa parte della stessa rete o u di una rete diversa. Lo fa attraverso la **Subnetmask.** 

**Esempio**

    Host 1 IP:192.168.1.100

    Netmask: 255.255.255.0

    Host 2 IP: 192.168.1.101

    Host 3 IP: 194.132.5.2

Possiamo notare che tramite la variabile booleana **AND** che **restituirà 1 se entrambi sono 1**, i valori 255 se restituiscono lo stesso indirizzo IP per le prime 3 terzine 192.168.1 (in questo caso l’ ultima terzina identifica l’host)  vorrà dire che farà parte della stessa rete. se al contrario restituirà un indirizzo di rete diverso vorrà dire ce farà parte di una rete differente e il pacchetto verrà inviata al Gateway.

In conclusione  Host 1 e Host 2 sono nella stessa rete, Host 3 ha una rete differente.

![Untitled](https://github.com/user-attachments/assets/ccbeeec0-aec8-474f-9fcc-64a9cca7c3f4)

# COME SI CALCOLA IL CODICE BINARIO DI UN INDIRIZZO IP

![Untitled](https://github.com/user-attachments/assets/0b6919d9-7014-46cf-8adb-68c51109ed9e)

**Dividiamo ogni terzina per 2, se è divisibile per 2 ci darà valore 0 se no è divisibile ci darà valore 1.**

# COME SI RISALE ALL’INDIRIZZO IP TRAMITE IL CODICE BINARIO

![Untitled](https://github.com/user-attachments/assets/dfaca443-725f-47e1-9c75-530c5f90e200)

Eleviamo alla potenza da DX vs SX e poi sommiamo la cifra che esce. C’è una scorciatoia per calcolare l’IP numerico attraverso una tabellina da imparare a memoria se dovesse servire.

![Untitled](https://github.com/user-attachments/assets/ae4e3b53-f290-427a-bc9e-d51451b0cc9a)

### Capire la subnetmask e la sua divisione di reti, chiamata Subnetting.

Se un’azienda ha bisogno di dividere in piu reti invece di acquistare nuovi indirizzi IP può utilizzare la tecnica del subnetting. Ovvero dividere gli indirizzi IP in piu reti grazie alla subnetmask.

ES. classica Subnetmask= 255.255.255.0 dove i valori 255 identificano la classe della rete e lo 0 gli indirizzi a disposizione. **tenendo conto che 255 è uguale a 11111111 in valore binario, restituirà una rete /24. ovvero sono gli 1 precedenti allo zero.** infatti 255.255.255.0 è uguale a 11111111.11111111.11111111.00000000

Qualora volessimo dividere la rete e diminuirne gli Indirizzi IP perchè non ne abbiamo bisogno. basterà restituire un valore 1 al primo 0 partendo da SX, così: 11111111.11111111.11111111.10000000 in questo caso il numero di 1 è 25 e gli indirizzi a disposizione sono 128 percè avremo dedicato alla rete un valore in piu diminuendo i valori dedicati agli HOST

**Quindi possiamo dire che piu valori attribuiamo alla netmask e meno indirizzi IP possiamo dedicare a quella rete.**

### [Come determinare a quale rete frazionata un indirizzo IP appartiene](https://www.youtube.com/watch?v=3HRX9dMcI6Q&list=PL3itjooulgzOMzrQwsI5kRxn9WD_7Z6WZ&index=2&ab_channel=RobertoManfrin)

Tenendo in considerazione l’esempio sopra citato, ovvero Subnet 255.255.255.0 e una 255.255.255.128 con indirizzi IP che vanno da **192.168.1.0/25 a 192.168.1.128/25** e da 1**92.168.1.129/25 a 192.168.1.255/25** avremo due reti (prendiamo in considerazione gli ultimi 3 ottetti):

    Rete 1: (0)0000000 

    Rete 2: (1)0000000

Ogni rete ha un indirizzo broadcast con tutti 1 e un indirizzo di rete con tutti 0 

    Rete 1, IP Rete: (0)0000000 

    Rete 1, IP braodcast (0)1111111

    Rete 2, IP Rete: (1)0000000 

    Rete 2, IP braodcast (1)1111111

### Come fa una sorgente a capire se il destinatario di un pacchetto fa parte della sua stessa rete?

Utilizzeremo la Netmask. Calcolando l’indirizzo di rete dell’IP

ES:             

    IP 192.168.1.100

    netmask: 255.255.255.0

    indirizzo rete= 192.168.1.0

ES: 

    IP 192.168.1.250

    netmask: 255.255.255.128

Indirizzo di rete: ?

**ECCO COME CALCOLARLO CON LA VARIABILE BOOLANA AND**

![Untitled](https://github.com/user-attachments/assets/6d42a1e0-7c75-4240-b91c-f8ee57f934b0)

Le ultime ottine in binario sono

IP .250:       (1)1111010

NM .128:       (1)0000000

Indirizzo rete: **128**

![Untitled](https://github.com/user-attachments/assets/d70ddb30-4100-4c1a-9fc5-afbbb313aeff)

# Es: a /27

![Untitled](https://github.com/user-attachments/assets/ff8f3240-950f-4d5f-bcf3-889a89bf367e)

La regola dice che per calcolare bisogna prendere i bit piu a destra ed intervallare l’1 e lo 0 ogni 1 volta. a mano a mano che le rate si restringe (in questo caso una/27) gli 1 e gli 0 si intervallano raddoppiandosi. 

ogni 1 volta per la /25

ogni 2 volte per la /26 

ogni 4 volte per la /27

ogni 8 volte per la /28

ogni 16 volte per la /29

ETC..

**PARTENDO SEMPRE DALLO 0 DI DX**

# Chi fornisce gli indirizzi IP?

![Untitled](https://github.com/user-attachments/assets/ac7ba5fd-db07-4c24-adaa-5da6e2c5fd57)









