#I/O 

#### DEFINIZIONE:

Entità composte da due componenti:
1. **Dispositivo fisico**.
2. **Device controller**.

##### DEVICE CONTROLLER:

Per gestire la comunicazione ogni controller dispone di registri dedicati (un interfaccia):
1. **Registri di stato**.
2. **Registri di controllo**.
3. **Registri dati.**

----

#### ESECUZIONE DELLE TASK:

Le task possono essere eseguite in 4 modi diversi:
1. **Polling**.
2. **Interrupt-driven**.
3. **Programmed I/O**.
4. **Direct Memory Access.**

##### POLLING: 
#POLLING

La **CPU** controlla periodicamente lo status delle task.

##### INTERRUPT-DRIVEN:
#INTERRUPT-DRIVEN

La **CPU** riceve un interruzione dal controller al fine della task.

##### PROGRAMMED I/O
#PROGRAMMED-I/O

La **CPU** si occupa direttamente di spostare i dati.

##### DIRECT MEMORY ACCESS (DMA):
#DMA

La **CPU** delega il lavoro ad un controller **DMA** dedicato.

----

#### TIPI DI MAPPING:
La **CPU** comunica con il device controller in 2 modi:
1. **Port-Mapped**.
2. **Memory-Mapped**.

##### PORT-MAPPED:
#PORT-MAPPED

1. Si riferisce ai registri del controller utilizzando un **address space** separato.
2. Utilizza delle istruzioni speciali (e.g., IN/OUT).
3. Ogni controller è mappato su una porta specifica a **boot-up time**.
##### MEMORY-MAPPED:
#MEMORY-MAPPED

1. Mappa i registri del controller nello stesso **address space** usato per la memoria principale.
2. **Spreca** degli **address space**.
3. **Non** ha bisogno di istruzioni speciali.
4. Mappati come normali memory address nella RAM a **boot-up time**.

