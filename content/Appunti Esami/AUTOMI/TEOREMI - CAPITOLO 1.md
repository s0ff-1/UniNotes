
##### THEOREM 1.25 : CLOSURE OF THE UNION OPERATION - (PAGE 45)
#THEOREM1

**THESIS**: The class of regular languages is closed under the union operation. In other words , if $A_1$ and $A_2$ are regular languages so is the union $A_1 \cup A_2$.

**PROOF IDEA**: We know that $A_1$ and $A_2$ are regular, so for each one there is a machine. We will call the machines as $M_1$ and $M_2$. To demonstrate the theorem we will proceed with a **Proof by Construction** creating a new machine $M$ capable of recognize the union $A_1 \cup A_2$.

This machine works simulating both $M_1$ and $M_2$ at the same time so that it needs to read the input string one time only from the beginning to the end.
Obviously that bring up a question like "How will the machine keep track of both if we have limited memory?" and the response to that is in the states, because the machine will only need two remember the last two  states to know at what point they are. Therefore, the set of $M_1$ and $M_2$ states will be obtained from the **Cartesian Product** of the two.

The machine $M$ will ultimately accept the input if at least one of the two simulated machines ($M_1$ or $M_2$) ends its run in an accepting state.

**PROOF**: 
Let $M_1$ recognize $A_1$, where $M_1$ = ($Q_1, \Sigma_1, \delta_1, q_1, F_1$), and 
$M_2$ recognize $A_2$, where $M_2$ = ($Q_2, \Sigma_2, \delta_2, q_2, F_2$).

Construct $M$ = $M_1$ = ($Q, \Sigma, \delta, q_0, F$), .
1. $Q = \{(r_1,r_2) \mid r_1 \in Q_1 \land r_2 \in Q_2\}$, 
   This set is the Cartesian Product $Q_1 \times Q_2$.
2. $\Sigma$ the alphabet, we assume for simplicity that it is the same for both machines. 
   In case it isn't we would simply write $\Sigma = \Sigma_1 \cup \Sigma_2$ .
3. $\delta$ is defined as: 
   $\forall (r_1,r_2) \in Q \text{ and each a} \in \Sigma$, let $\delta((r_1,r_2),a) = (\delta_1(r_1,a),\delta_2(r_2,q)).$
   It combines the two states into one and returns the next.
4. $q_0$ is the pair $(q_1,q_2)$.
5. $F$ is the set of pair in which either member is an accept state. Can be write as:
   $F = \{(r_1,_2)\mid r_1 \in F_1 \lor r_2 \in F_2\} \lor F = (F_1 \times Q_2) \cup (F_2 \times Q_1)$.

This concludes the construction.

---

##### THEOREM 1.26 : CLOSURE OF THE CONCATENATION - (PAGE 47)
#THEOREM2

**THESIS**: The class of regular languages is closed under the concatenation operation. In other words , if $A_1$ and $A_2$ are regular languages so is the union $A_1 \circ A_2$.

**PROOF IDEA**: If we tried to demonstrate this following the path opened by the union one we would get in front of an enormous obstacle. The machine $M$ would have to accept the input string broken in two parts (the first accepted by $M_1$ and the second by $M_2$), but $M$ couldn't have any ideas in advance about where the first one ends and the second one begins.

So to resolve this problem the theory introduces to us the **nondeterminism**.

---

##### THEOREM 1.39 : EQUIVALENCE OF NFAs AND DFAs - (PAGE 55)

