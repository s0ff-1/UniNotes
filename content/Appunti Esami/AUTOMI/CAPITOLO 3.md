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

![[tm-m1-w-hash-w.gif|676]]


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



