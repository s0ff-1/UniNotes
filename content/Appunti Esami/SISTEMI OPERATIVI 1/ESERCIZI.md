
#### UNITÀ DI MISURA E CONVERSIONI:


|         |         Base binaria         |
| :-----: | :--------------------------: |
| **GiB** | $$ 1 \times 2^{30} \ bits $$ |
| **KiB** |  $$1\times 2^{10} \ bits$$   |
|         |      **Base decimale**       |
| **Gb**  |   $$1 \times 10^9 \ bits$$   |
| **Kb**  |   $$1\times 10^3 \ bits$$    |

---

#### ESERCIZIO 1
#VPN #OFFSET 

>[!question] **OBBIETTIVO:** TROVA VPN E OFFSET

>[!info] **DATI:**

	 INDIRIZZO LOGICO = 9876
	 DIMENSIONE PAGINA = 1024 byte

>[!success] **SOLUZIONE:**
> VPN: $$\frac {9874}{1024} = 9$$ <br>
>OFFSET : $$9876 \ mod \ 1024 = 660$$ 

#### ESERCIZIO 2
#PAGE-TABLE

>[!question] **OBBIETTIVO:** TROVA DIM. DELLA SINGOLA PAGE TABLE

>[!info] **DATI:**

	MEMORIA LOGICA = 1GiB (IN PAGINE DI 4KiB)
	PTE = 8 byte (DIM. PAGE TABLE ENTRY)

>[!success] **SOLUZIONE:**
>N. PTEs: $$\frac {2^{30}B}{2^{12}B} = 2^{18}B$$ <br>
>DIM: $$(2^{18} \ \times  ( 8 = 2^{3}))\ B = 2^{21}B = 2\ MiB $$

#### ESERCIZIO 3
#VPN #OFFSET

>[!question] **OBBIETTIVO:** TROVA I BIT NECESSARI PER IDENTIFICARE IL VPN

>[!info] **DATI:**

	BIT INDIRIZZO LOGICO = 36 bit
	DIMENSIONE PAGINA = 4 KiB

>[!success] **SOLUZIONE:**
>OFFSET: $4\ KiB = 2^{12} \rightarrow  12\ bit$ <br>
>VPN: $36 -12 = 24\ bit$

#### ESERCIZIO 4
#VPN #PAGE-TABLE #OFFSET 

>[!question] **OBBIETTIVO:** TROVA I LIVELLI NECESSARI PER MEMORIZZARE LA PAGE TABLE

>[!info] **DATI:**

	BIT INDIRIZZO LOGICO = 48 bit
	DIMENSIONE PAGINA = 4 KiB
	PTE = 8 byte

>[!success] **SOLUZIONE:**
>OFFSET: $4\ KiB = 2^{12} \rightarrow  12\ bit$ <br>
>VPN: $36 -12 = 24\ bit$ <br>
>N. PTE PER PAGINA: $$\frac {2^{12}}{2^{3}} = 2^9 = 521\ PTE$$ <br>
>N. LIVELLI $36/9\  bit = 4$

#### ESERCIZIO 5
#PAGE-TABLE #PAGE-FAULT #ACCESSO-MEM

>[!question] **OBBIETTIVO:** TROVA IL TEMPO DI ACCESSO EFFETTIVO MEDIO ALLA MEMORIA

>[!info] **DATI:**

	TEMPO ACCESSO ALLA MEM. = 200 ns (T_M)
	TEMPO PER OGNI PAGE FAULT = 10 ms (T_FAULT) = 10 ^-2
	FREQUENZA = 1/4000 ACCESSI (P_FAULT)

>[!success] **SOLUZIONE:**
>SOL: $$Pfault \times Tfault\ +\ (1\ -\ Pfault)\times Tm  = x \ µs$$

#### ESERCIZIO 6
#ROUND-ROBIN #I/O

>[!question] OBBIETTIVO: CALCOLA IL TEMPO D'ATTESA

>[!info] DATI:

	P1: CPU 6, I/O 4, CPU 4
	P2: CPU 5, I/O 2, CPU 3
	P3: CPU 4, I/O 3, CPU 2

>[!success] SOLUZIONE: 
>

| INTERVALLO |       PROCESSO        | ESECUZIONE |         RIM         |
| :--------: | :-------------------: | :--------: | :-----------------: |
|    0-4     |          P1           |     4      | CPU 2, I/O 4, CPU 4 |
|    4-8     |          P2           |     4      | CPU 1, I/O 2, CPU 3 |
|    8-12    | P3 (I/O DA T12 A T15) |     4      |    I/O 3, CPU 2     |
|   12-14    | P1 (I/O DA T12 A T15) |     2      |    I/O 4, CPU 4     |
|   14-15    |          P2           |     1      |    I/O 2, CPU 3     |
|   15-17    |          P3           |     2      |      ESAURITO       |
|   17-20    |          P2           |     3      |      ESAURITO       |
|   20-24    |          P1           |     4      |      ESAURITO       |

- AL TERMINE **P1** VA DOPO **P2** PERCHÉ ATTENDE I/O, AVENDOLO MAGGIORE RISPETTO A **P2**