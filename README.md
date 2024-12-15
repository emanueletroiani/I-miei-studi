I sistemi operativi usano il linguaggio binario. Per distinguere le diverse informazioni divide numeri e serie di carattere con il concetto di “tipo di stato”

![Untitled](https://github.com/user-attachments/assets/0fefb4c1-9fb1-4fc7-a581-eac0ba47c9e8)

- **Bool**: ovvero variabile booleana è molto utilizzata in programmazione per esprimere condizione logiche e decisioni. Sono supportate da Operatori logici, ovvero eseguono espressioni logiche tra espressioni booleane o Bit. I piu comuni sono: AND (**`and`**), OR (**`or`**) e NOT (**`not`**).  In breve, il tipo di dato bool rappresenta una variabile che può essere vera o falsa, mentre gli operatori logici eseguono operazioni logiche su espressioni booleane per determinare il risultato in base alle regole della logica booleana.
1. L'operatore logico **`and`** è un operatore booleano che restituisce **`True`** solo se entrambe le espressioni booleane che collega sono vere, è spesso utilizzato in costrutti condizionali per verificare più condizioni contemporaneamente, richiedendo che tutte siano vere affinché l'intera espressione sia valutata come vera. Ecco una tabella di verità per l'operatore logico AND:

| **A** | **B** | **A and B** |
| --- | --- | --- |
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |
1. OR: è utilizzato per combinare due espressioni booleane e restituisce **`True` (1)** se almeno una delle espressioni è vera (**1**). La tabella di verità per l'operatore OR è la seguente:

| **A** | **B** | **A or B** |
| --- | --- | --- |
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |
1. NOT:  è utilizzato per invertire il valore di un'espressione booleana. Se l'espressione è vera, NOT restituirà **`False` (0)**, e se l'espressione è falsa, NOT restituirà **`True`(1)**. La tabella di verità per l'operatore NOT è la seguente:

| **A** | **not A** |
| --- | --- |
| True | False |
| False | True |

ci sono altri operatori logici disponibili:

XOR, OR esclusivo

XNOR,NOT(XOR)

NAND(NAT(AND))

NOR (NOT(OR)
