---

---

---
##### TURING MACHINES

The **Church–Turing thesis** states that Turing machines capture the intuitive notion of an algorithm: every reasonable model of computation is equivalent in power to a Turing machine. The TM is therefore the central model of computability theory.

A **Turing machine (TM)** is similar to a finite automaton but has an **unlimited, unrestricted memory**: an infinite **tape** with a **read–write head** that can move both left and right. Initially the tape contains only the input and is blank elsewhere. The machine halts only when it enters the accept or reject state; otherwise it may go on forever.

**Differences from finite automata:**
1. A TM can both **write** on the tape and **read** from it.
2. The read–write head can move **both left and right**.
3. The tape is **infinite**.
4. The accepting and rejecting states take effect **immediately**.

**Example — $M_1$ for $B = \{w\#w \mid w \in \{0,1\}^*\}$.** The machine checks whether the two halves around `#` are identical by **zig-zagging** across the tape and **crossing off** symbols as they are matched. If everything matches it accepts; on a mismatch (or if no `#` is found) it rejects.

###### $M_1$ ANIMATION:

![[tm-m1-w-hash-w.gif|700]]


---
##### FORMAL DEFINITION OF A TURING MACHINE

> [!example] DEFINITION:
> A **Turing machine** is a **7-tuple** $(Q, \Sigma, \Gamma, \delta, q_0, q_{accept}, q_{reject})$, where $Q, \Sigma, \Gamma$ are finite sets and
> 	1. $Q$ is the set of the **states**,
> 	2. $\Sigma$ is the **input alphabet**, not containing the blank symbol $\sqcup$,
> 	3. $\Gamma$ is the **tape alphabet**, where $\sqcup \in \Gamma$ and $\Sigma \subseteq \Gamma$,
> 	4. $\delta : Q \times \Gamma \longrightarrow Q \times \Gamma \times \{L, R\}$ is the **transition function**,
> 	5. $q_0 \in Q$ is the **start state**,
> 	6. $q_{accept} \in Q$ is the **accept state**, and
> 	7. $q_{reject} \in Q$ is the **reject state**, with $q_{reject} \ne q_{accept}$.

**Computation:** The input $w = w_1\cdots w_n \in \Sigma^*$ occupies the leftmost $n$ squares of the tape; the rest is blank. The head starts on the leftmost square. If the machine tries to move left off the tape, the head stays put. The computation halts when it enters $q_{accept}$ or $q_{reject}$; otherwise it runs forever.

**Configurations:** A **configuration** is a setting of the current state, tape contents, and head position. We write $uqv$ for the configuration with state $q$, tape contents $uv$, and head at the first symbol of $v$. For example, $1011q_7 01111$ represents tape $101101111$, state $q_7$, and head on the second `0`.

**Yields:** Configuration $C_1$ **yields** $C_2$ if the machine can go from $C_1$ to $C_2$ in a single step:
- $ua\,q_i\,bv$ yields $u\,q_j\,acv$ if $\delta(q_i,b) = (q_j,c,L)$;
- $ua\,q_i\,bv$ yields $uac\,q_j\,v$ if $\delta(q_i,b) = (q_j,c,R)$.

Special cases handle the ends of the tape. The **start configuration** on $w$ is $q_0w$; an **accepting** configuration has state $q_{accept}$; a **rejecting** configuration has state $q_{reject}$. Accepting and rejecting configurations are **halting** and yield nothing further.

$M$ **accepts** $w$ if a sequence of configurations $C_1, C_2, \dots, C_k$ exists such that $C_1$ is the start configuration on $w$, each $C_i$ yields $C_{i+1}$, and $C_k$ is accepting. The **language of $M$**, written $L(M)$, is the set of strings $M$ accepts.

> [!example] DEFINITION:
> A language is **Turing-recognizable** if some Turing machine recognizes it.

When started on an input, a TM may **accept**, **reject**, or **loop**. A TM that halts on every input is called a **decider**.

> [!example] DEFINITION:
> A language is **Turing-decidable** (or simply **decidable**) if some Turing machine decides it.

>[!warning] RULE:
>Every decidable language is Turing-recognizable, the converse is false  ([[CAPITOLO 4]]).

---

##### EXAMPLES OF TURING MACHINES

> [!info] EXAMPLE 1 — $M_2$:
> $M_2$ decides $A = \{0^{2^n} \mid n \ge 0\}$. On input $w$:
> 	1. Sweep left to right, crossing off every other `0`.
> 	2. If in stage 1 the tape contained a single `0`, **accept**.
> 	3. If more than a single `0` remained and the number of `0`s was odd, **reject**.
> 	4. Return the head to the left-hand end of the tape.
> 	5. Go to stage 1.
>
> Each sweep halves the number of `0`s. If the count is ever odd and greater than 1, it cannot be a power of 2.

![[figure3.8.png]]


> [!info] EXAMPLE 2 — $M_1$ (formal):
> $M_1 = (Q, \Sigma, \Gamma, \delta, q_1, q_{accept}, q_{reject})$, where
> $$Q = \{q_1, \dots, q_8, q_{accept}, q_{reject}\},\quad \Sigma = \{0,1,\#\},\quad \Gamma = \{0,1,\#,x,\sqcup\}.$$
> The transition function is given by the state diagram (Figure 3.10). Transitions to $q_{reject}$ are implicit whenever a state lacks an outgoing arrow for the current symbol.

![[figure3.10.png]]


---
###### MULTITAPE TURING MACHINES

A **multitape TM** has $k$ tapes, each with its own head. The input appears on tape 1; the others start blank. The transition function is
$$\delta : Q \times \Gamma^k \longrightarrow Q \times \Gamma^k \times \{L,R,S\}^k.$$

> [!info] THEOREM 3.13: Every multitape Turing machine has an equivalent single-tape Turing machine.
> **Proof idea:** store the $k$ tapes on the single tape, separated by `#`, and mark each virtual head with a **dotted** symbol. Simulate each move with two passes: one to read the symbols under the virtual heads, one to update the tapes.

> [!info] COROLLARY 3.15: A language is Turing-recognizable if and only if some multitape Turing machine recognizes it.

##### THEOREMS LINKED:
- [[TEOREMI - CAPITOLO 3#THEOREM 3.13 MULTITAPE → SINGLE-TAPE - (PAGE 177)|THEOREM 3.13]]

---
###### NONDETERMINISTIC TURING MACHINES

A **nondeterministic TM** may have several possible moves at each step:
$$\delta : Q \times \Gamma \longrightarrow \mathcal{P}(Q \times \Gamma \times \{L,R\}).$$
Its computation is a **tree**; the machine accepts if **some branch** reaches the accept state.

> [!info] THEOREM 3.16: Every nondeterministic Turing machine has an equivalent deterministic Turing machine.
> **Proof idea:** let $D$ try all branches of $N$'s computation tree. A **depth-first** search is wrong: it could follow an infinite branch forever and miss an accepting configuration on another branch. Use **breadth-first search**, which visits all nodes at depth $d$ before any node at depth $d+1$.

##### THEOREMS LINKED:
- [[TEOREMI - CAPITOLO 3#THEOREM 3.16 NONDETERMINISTIC → DETERMINISTIC - (PAGE 178)|THEOREM 3.16]]