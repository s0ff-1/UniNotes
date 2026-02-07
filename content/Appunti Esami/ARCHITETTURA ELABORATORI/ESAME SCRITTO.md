
## ESERCIZIO 1 
#esercizio1 #cache

#### FORMULE PUNTO 1

| ADDRESS   |         1000         |
| --------- | :------------------: |
| **BLOCK** | $\frac{ADDRESS}{DB}$ |
| **INDEX** |    $BLOCKmodSET$     |
| **TAG**   | $\frac{BLOCK}{SET}$  |

#### FORMULE PUNTO 2


| DIM.BLOCCO | $$ Nword \times 4 word = x \times 8 bit = x bit $$   |
| ---------- | ---------------------------------------------------- |
| **OFFSET** | $$ \log_2(Nword\times4) $$                           |
| **INDEX**  | $$ \log_2(SET)$$                                     |
| **TAG**    | $$(32-INDEX- OFFSET)$$                               |
| **L-TOT**  | $$Nvie \times SET \times (TAG + V + U +DIM.BLOCCO)$$ |
 - *L-TOT VARIA IN BASE AL TIPO DI CACHE*

#### FORMULE PUNTO 3


| TEMPO (TT)     | $$(L1HIT \times ns) + (L2HIT \times ns) + (Nmiss \times ns) $$ |
| -------------- | -------------------------------------------------------------- |
| **TEMPO (TM)** | $$\frac {TT}{Naddress}$$                                       |
| **NUM-IST**    | $$\frac {TM}{CPI} \times \frac {1}{f}$$                        |


-----

## ESERCIZIO 2
#esercizio2 #RISC

#### TIPO DI ISTRUZIONE:

![[Pasted image 20260206104712.png|500]]

#### REGISTRI:


![[Pasted image 20260206105014.png|200]]


---

## ESERCIZIO 3
 #esercizio3 #no-forwarding #forwarding 

#### NO-FORWARDING 

>[!example] **CASO 1:**
	istruzione x, bla , bla
	bla bla bla 
	istruzione bla, x ,bla 
	
>[!warning] 1 STALLI

<br>

>[!example] **CASO 2:**
	istruzione x, bla , bla
	istruzione bla,  x  , bla
	
>[!warning] 2 STALLI

----

#### FORWARDING

**CASO 1/2 PRECEDENTI DA IGNORARE**

>[!success] **SEMPRE VALIDO:**
	se beq/s salta
	beq ... FDXMW
	slli F
	addi FDXMW

>[!warning] 1 STALLO

<br>

>[!example] **CASO 1F:**
	la , li
	istruzione  ≠ beq, bqe...
	
>[!warning] NO STALLI
<br>

>[!example] **CASO 2F:**
	b,lw,lh
	istrzione ≠ beq,bqe...
    
>[!warning] 1 STALLO
<br>

>[!example] **CASO 3F:**
	la,li, R-Type
	istruzione beq,bge... 
	
>[!warning] 1 STALLO
<br>

>[!example] **CASO 4F:**
	lw,lh,lb
	istruzione beq,bge...
	
>[!warning] 2 STALLI
<br>

>[!example] **CASO 5F:**
	lw,lb,lh x
	bla, bla, bla
	istruzione beq,bge...
	
>[!warning] 1 STALLO
