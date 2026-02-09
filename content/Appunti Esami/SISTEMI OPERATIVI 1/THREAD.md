#### DEFINIZIONE:
#THREAD 

Un **thread** è un **utility unit** di base della **CPU**, composta da:
1. **Program Counter**.
2. **Stack**.
3. **Thread ID**.
4. **Insieme di registri**.

##### BENEFIT:
I thread garantiscono 4 benefici:
1. **Responsiveness**.
2. **Resource sharing**.
3. **Economy**.
4. **Scalability**.

##### TIPOLOGIE:
Sono presenti 2 distinzioni di thread per provvedere al supporto:
1. **Kernel Threads**.
2. **User Threads**.

##### KERNEL THREAD:
#KERNEL-THREAD

Un kernel thread è l’unità di esecuzione più piccola schedulabile dall’OS, il quale è responsabile per il supporto e la gestione.

1. Il Kernel conosce tutti i Kernel attivi.
2. L'OS fornisce syscall per il supporto e la gestione.
3. È dotato di **Thread Control Block** (TCB)

##### USER THREAD:
#USER-THREAD

Gli user thread sono gestiti interamente dal sistema di run-time tramite librerie specifiche per thread, i quali vengono gestiti come se fossero dei processi single-threaded.

1. Molto efficienti e presentano politiche di scheduling flessibili.
2. Non necessitano di **syscall** o **context switch**.
3. Può essere implementato da OS che non supportano il threading.
4. Presentano mancanza di coordinazione tra kernel e thread.
5. Necessita che le **syscall** dell'OS non siano bloccanti.


----

#### PROCESS VS THREAD:
#PROCESS #THREAD

1. Un **processo** definisce address space, text, data, risorse.
2. Un **thread** definisce un singolo flusso sequenziale di esecuzione.
3. Ogni processo può avere diversi thread di controllo all'interno.
4. **L'  address space** è condiviso tra i suoi thread.
5. **Non** sono necessarie chiamate di sistema per la cooperazione dei thread.

##### SINGLE- VS MULTI-THREADED PROCESS:
Nei processi  Multi-Threaded:
1. Condividendo lo stesso address space la comunicazione è più efficiente.
2. Permette l'overlap di [[DISPOSITIVI I-O]] con altre task dello stesso programma.
3. Utile quando è necessario eseguire multiple task indipendentemente.

##### MULTIPLE PROCESSES VS MULTIPLE THREADS:
1. La comunicazione **inter-thread** è significativamente più efficiente rispetto ad una **inter-process**.
2. I **Context-switch** tra thread è molto più veloce rispetto ai processi. 

----
#### MODELLI DI MULTI-THREADING:
#MULTI-THREADING

Per gestire il multithreading si presentano vari modelli:
1. **Many-to-One**.
2. **One-to-One**.
3. **Many-to-Many**.
4. **Two-Level**.
