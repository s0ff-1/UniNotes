
| **RITARDO TRASMISSIONE PACCHETTO**                     | $\frac{L \ bit}{R \ bit/s }$                                               |
| ------------------------------------------------------ | -------------------------------------------------------------------------- |
| **PROBABILITÀ CONNESSIONI CONTEMPORANEE PER X UTENTI** | $Pr(X \ge K)= \Sigma_{i=K}^n (\frac {n}{i}) \times p^i \times (1-p)^{n-1}$ |
| **RITARDO LATENZA PACCHETTO**                          | $d_{nodo} = d_{proc} + d_{coda} + d_{trans} + d_{prop}$                    |
| **d_trans**                                            | $\frac{L \ bit}{R \ bit/s }$                                               |
| **d_prop**                                             | $\frac{K}{V}$                                                              |
| **BITcanale**                                          | $R \times d_{prop}$                                                        |
| **PACCHETTI/s**                                        | $\frac{R}{L}$                                                              |


## 1 Ritardi Fondamentali (Nodali)


- **Ritardo di Trasmissione ($d_{\text{trans}}$):** È il tempo necessario per immettere tutti i bit di un pacchetto sul link.
    
    $$d_{\text{trans}} = \frac{L}{R}$$
    
    - $L$ = Lunghezza del pacchetto in bit.
        
    - $R$ = Velocità di trasmissione (o Rate/Capacità) del link in bit/s (bps).
        
- **Ritardo di Propagazione ($d_{\text{prop}}$ o $\tau$):** È il tempo necessario affinché un singolo bit viaggi fisicamente dall'inizio alla fine del link.
    
    $$d_{\text{prop}} = \frac{d}{s}$$
    - $d$ = Distanza fisica del link (es. in metri o km).
        
    - $s$ = Velocità di propagazione nel mezzo (spesso vicina alla velocità della luce, $c \approx 3 \cdot 10^8$ m/s). Negli esercizi spesso viene già fornito come $\tau$.
        
- **Ritardo Nodale Totale:**
    
    $$d_{\text{nodo}} = d_{\text{proc}} + d_{\text{queue}} + d_{\text{trans}} + d_{\text{prop}}$$
    
    (Nota: il ritardo di processamento e di accodamento spesso vengono assunti pari a zero se non specificato diversamente ).


---

## 2 Prestazioni e Capacità del Canale

- **Tempo di trasmissione di un singolo bit:**
    
    $$t_{\text{bit}} = \frac{1}{R}$$
    
- **Massimo numero di pacchetti al secondo:**
    
    $$\text{Pacchetti/s} = \frac{R}{L}$$
    
- **Quantità massima di bit "in volo" sul canale (Prodotto Banda-Ritardo):** Definisce quanti bit possono essere fisicamente presenti sul mezzo trasmissivo in un dato istante.
    
    $$BDP = R \cdot d_{\text{prop}}$$
    
- **Throughput (Collo di bottiglia):** In un percorso composto da più link in serie, la velocità di trasferimento effettiva è dettata dal link più lento.
    
    $$Th = \min(R_1, R_2, \dots, R_n)$$

---

## 3 Trasferimenti Complessi e Architetture

- **Commutazione di Circuito:** Prima di inviare i dati, è necessario stabilire una connessione dedicata (setup). Il tempo totale è:
    
    $$T_{\text{totale}} = t_{\text{setup}} + \frac{L}{R_{\text{allocato}}}$$
    
    - _Nota per il TDM (Time Division Multiplexing):_ La porzione di banda allocata dipende dagli slot.
        
- **Round-Trip Time (RTT / Ping):** È il tempo necessario affinché un pacchetto arrivi a destinazione e la risposta (eco) torni indietro.
    
    $$RTT = 2 \cdot \sum d_{\text{totali\_di\_andata}}$$

---

## 4 ### Code e Store-and-Forward 

Nei router a commutazione di pacchetto con approccio _store-and-forward_, il router deve ricevere l'intero pacchetto prima di poterlo ritrasmettere sul link successivo.

- **Tempo di arrivo per 1 singolo pacchetto su $K$ link in serie:**
    
    $$T_{\text{arrivo}} = \sum_{i=1}^{K} \left( \frac{L}{R_i} + \tau_i \right)$$
    
- **Formula per $n$ pacchetti (invio back-to-back):** Se invii $n$ pacchetti, il primo pacchetto subisce tutti i ritardi di store-and-forward. I pacchetti successivi arrivano distanziati in base al "collo di bottiglia" del percorso ($R_{\text{min}}$).
    
    $$T_{\text{ultimo}} = T_{\text{arrivo\_primo\_pacchetto}} + (n - 1) \cdot \frac{L}{R_{\text{min}}}$$
    
    _(Attenzione: questa formula semplificata vale se le code non si svuotano mai lungo il percorso. Negli esercizi a cascata specifici, conviene calcolare passo-passo i tempi di uscita dai singoli router per tracciare accuratamente le code)._
