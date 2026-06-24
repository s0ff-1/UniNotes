
## CAPITOLO 1
#### Calcolo Combinatorio e Assiomi di Base

1. FORMULE DEL CALCOLO COMBINATORIO
	Permutazioni Semplici (ordinare $n$ elementi distinti): $n!$
	Permutazioni Con Ripetizione (es. anagrammi con lettere doppie): 
	$$\frac{n!}{k_1! \times k_2!...}$$
	Combinazioni Semplici (scelta di $k$ elementi su $n$ senza ordine): $$$$$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$
2. ASSIOMI E OPERAZIONI SUGLI EVENTI
	Unione di due eventi: $\mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B) - \mathbb{P}(A \cap B)$
	Unione di tre eventi: $\mathbb{P}(A \cup B \cup C) = \mathbb{P}(A) + \mathbb{P}(B) + \mathbb{P}(C) - \mathbb{P}(A \cap B) - \mathbb{P}(A \cap C) - \mathbb{P}(B \cap C) + \mathbb{P}(A \cap B \cap C)$
	Eventi Incompatibili (Disj): $\mathbb{P}(A \cap B) = 0$
	Famiglia di £ Eventi Completamente Indipendenti: $$\mathbb{P}(A \cap B \cap C) = \mathbb{P}(A)\mathbb{P}(B)\mathbb{P}(C)$$


---

## CAPITOLO 2
#### Condizionamento e Teorema di Bayes

1. PROBABILITÀ CONDIZIONATA: $$\mathbb{P}(A|B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}$$
2. REGOLA DEL PRODOTTO: $\mathbb{P}(A \cap B) = \mathbb{P}(B)\mathbb{P}(A|B)$
3. FORMULA DELLE PROBABILITÀ TOTALI (CON PARTIZIONE $H_i$): $$\mathbb{P}(E) = \sum_{i} \mathbb{P}(H_i)\mathbb{P}(E|H_i)$$
4. TEOREMA DI BAYES (PROBABILITÀ DELLE CAUSE): $$\mathbb{P}(H_i|E) = \frac{\mathbb{P}(H_i)\mathbb{P}(E|H_i)}{\mathbb{P}(E)}$$
5. RELAZIONI TRA DUE EVENTI:
	Indipendenti: $\mathbb{P}(A|B) = \mathbb{P}(A)$
	Correlati Positivamente: $\mathbb{P}(A|B) > \mathbb{P}(A)$
	Correlati Negativamente: $\mathbb{P}(A|B) < \mathbb{P}(A)$


---

## CAPITOLO 3
#### Variabili Aleatorie Discrete Singole

1. Formule Generali:
	Valore Atteso: $\mathbb{E}(X) = \sum x \cdot \mathbb{P}(X=x)$
	Varianza: $Var(X) = \mathbb{E}(X^2) - (\mathbb{E}(X))^2$

Tabella delle Distribuzioni Notevoli:


| Modello                            | Uso Tipico                                    | **Densità P(X=k)**                                    | **Valore Atteso E(X)** | *Varianza $Var(X)$*                                       |
| ---------------------------------- | --------------------------------------------- | ----------------------------------------------------- | ---------------------- | --------------------------------------------------------- |
| **Binomiale** $Bin(n, p)$          | Estrazioni **con** reinserimento ($n$ prove)  | $$\binom{n}{k} p^k (1-p)^{n-k}$$                      | $$np$$                 | $$np(1-p)$$                                               |
| **Ipergeometrica** $H(N, K, n)$    | Estrazioni **senza** reinserimento            | $$\frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}$$ | $$n\frac{K}{N}$$       | $$n\frac{K}{N}\left(1-\frac{K}{N}\right)\frac{N-n}{N-1}$$ |
| **Geometrica** $Geom(p)$           | Prove fino al **primo successo** (parte da 1) | $$(1-p)^{k-1}p$$                                      | $$\frac{1}{p}$$        | $$\frac{1-p}{p^2}$$                                       |
| **Poisson** $\mathcal{P}(\lambda)$ | Eventi rari in un intervallo continuo         | $$\frac{\lambda^k}{k!} e^{-\lambda}$$                 | $$\lambda$$            | $$\lambda$$                                               |
_Proprietà fondamentale di Poisson nei compiti:_ Se $X$ e $Y$ sono due variabili di Poisson **indipendenti** con parametri $\lambda_X$ e $\lambda_Y$, allora la loro somma $Z = X + Y$ è ancora una variabile di Poisson con parametro $\lambda_Z = \lambda_X + \lambda_Y$.


**LOTUS** (caso val.atteso senza densità): $$\mathbb{E}[g(X_A)] = \sum_{k} g(k) \cdot \mathbb{P}(X_A = k)$$


---


## CAPITOLO 4
#### Variabili Aleatorie Congiunte

1. VERIFICA DELLA SOMMA (COSTANTE INCOGNITA): La somma di tutte le celle della tabella deve fare 1.
2. CALCOLO MARGINALI:  $p_U(i) = \sum_j \mathbb{P}(U=i, V=j)$ (somma di riga o colonna).
3. TEOREMA DI BAYES APPLICATO: $$\mathbb{P}(U = 2 | W = 1) = \frac{\mathbb{P}(U = 2, W = 1)}{\mathbb{P}(W = 1)}$$
4. VERIFICA INDIPENDENZA: $U$ e $V$ sono indipendenti se e solo se **per ogni** cella vale:

$$\mathbb{P}(U=i, V=j) = \mathbb{P}(U=i) \cdot \mathbb{P}(V=j)$$
5. VALORE ATTESO DEL PRODOTTO: $\mathbb{E}(UV) = \sum_i \sum_j (i \cdot j) \cdot \mathbb{P}(U=i, V=j)$
6. COVARIANZA: $$Cov(U, V) = \mathbb{E}(UV) - \mathbb{E}(U)\mathbb{E}(V)$$
7. VARIANZA DI UNA COMBINAZIONE LINEARE: 
$$Var(aX + bY) = a^2Var(X) + b^2Var(Y) + 2abCov(X, Y)$$
	Se $X$ e $Y$ sono indipendenti, allora $Cov(X,Y) = 0$ e la formula si riduce a $a^2Var(X) + b^2Var(Y)$.

8. INDIPENDENZA E COVARIANZA:
	**Indipendenza** $\implies$ **Covarianza Nulla:** Se $X$ e $Y$ sono indipendenti, esse sono sempre _scorrelate_ $\implies Cov(X,Y) = 0$.
    
    **Covarianza Nulla** $\centernot\implies$ **Indipendenza:** Se $Cov(X,Y) = 0$, le variabili sono scorrelate, ma **NON è detto che siano indipendenti** (questa è una domanda a trabocchetto classicissima nei test a risposta multipla!). Per dimostrare l'indipendenza, devi verificare cella per cella che $\mathbb{P}(X=x, Y=y) = \mathbb{P}(X=x)\mathbb{P}(Y=y)$.



---

## CAPITOLO 5
#### Somme di Variabili, Chebyshev e Gaussiana (TCL)

Sia $S_n = \sum_{i=1}^n X_i$ una somma di $n$ variabili aleatorie indipendenti, ciascuna con media $\mu$ e varianza $\sigma^2$. Sia $Y = \frac{S_n}{n}$ la loro media campionaria (ARITMETICA).

1. PARAMETRI DELLE SOMME
	Per la Somma **$S_n$:** $\mathbb{E}(S_n) = n\mu$ e $Var(S_n) = n\sigma^2$
	Per la Media Campionaria **$Y$:** $\mathbb{E}(Y) = \mu$ e $Var(Y) = \frac{\sigma^2}{n}$

2. DISUGUAGLIANZA DI CHEBYSHEV
	Forma per la Minorazione: $$\mathbb{P}(|Y - \mu| \le \epsilon) \ge 1 - \frac{Var(Y)}{\epsilon^2}$$
	Forma per la Maggiorazione: $$\mathbb{P}(|Y - \mu| > \epsilon) \le \frac{Var(Y)}{\epsilon^2}$$

3. TEOREMA CENTRALE DEL LIMITE (TCL) E GAUSSIANA
	Standardizzazione della Somma **$S_n$:**

$$Z = \frac{S_n - n\mu}{\sigma\sqrt{n}}$$
	Calcolo delle Probabilità in un intervallo **$[a, b]$:**

$$\mathbb{P}(a < S_n \le b) \approx \Phi\left(\frac{b - n\mu}{\sigma\sqrt{n}}\right) - \Phi\left(\frac{a - n\mu}{\sigma\sqrt{n}}\right)$$
	Regole per le tavole $\Phi$:
	- Valori negativi: $\Phi(-z) = 1 - \Phi(z)$
    - Coda destra (maggiore di): $\mathbb{P}(Z > z) = 1 - \Phi(z)$