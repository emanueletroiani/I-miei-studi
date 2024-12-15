[Mediant IOC Editor
](https://fireeye.market/apps/S7cWpi9W)

Girà esclusivamente su Windows e permette di gestire i dati e manipolare le strutture logiche degli IOC (Indicatori di compromissione)

[Download](https://fireeye.market/apps/S7cWpi9W)

Per confrontare il file bisogna compilare il tools con:

1. Creiamo una cartella per esportare i file IOC
2. Creiamo un nuovo File IOC
3. Ora dobbiamo compilare il nostro IOC con Nome, Autore, Dimensione file, codice Hash
4. La **dimensione** del **file** la prendiamo cliccando con il tasto destro sul file e su proprietà, **deve essere precisa sul bit**
5. Generiamo il codice **Hash** con **sha1sum**
6. Tasto destro su Mediant, Add File, File Item, File MD5. Questo creerà **una** nuova **voce** nella nostra **struttura OR**. Tutto ciò che si trova in questo riquadro verrà ricercato quando in seguito si utilizzeranno i file IOC per la caccia.
7. aggiungere anche:
- SHA-1 Hash: **Add Item > FileItem > Sha1sum**
- File Name: **Add Item > FileItem > File Name**
- File Size: **Add Item > FileItem > File Size**
8. Compilare i campi con i valori raccolti in precedenza facendo doppio clic su di essi. Una volta terminato, salvate il file utilizzando il pulsante in basso a destra e il gioco è fatto: avete creato il vostro primo semplice file IOC!

  # Differenza tra

- Se ci sono tre IOC in questo albero, tutti e tre devono corrispondere a un file per ottenere un riscontro positivo. Se sono presenti solo 2 IOC, il sistema non lo comunicherà.
- **OR -** Se abbiamo tre IOC in questo albero, se uno qualsiasi di essi è presente in un file, riceveremo una notifica in seguito quando utilizzeremo Redline.
