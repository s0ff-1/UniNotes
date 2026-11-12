---

---

---
##### THEOREM 3.13 : MULTITAPE → SINGLE-TAPE - (PAGE 177)
#THEOREM17

**THESIS**: Every multitape Turing machine has an equivalent single-tape Turing machine.

**PROOF IDEA**: Let $M$ be a multitape TM with $k$ tapes. Construct a single-tape TM $S$ that stores the contents of all $k$ tapes on its one tape, separated by the delimiter `#`, and marks the position of each virtual head with a dotted symbol. To simulate one move, $S$ scans the tape to read the symbols under the virtual heads, then makes a second pass to update the tapes.

**PROOF**:
Let $M$ have $k$ tapes. $S$ formats its tape as
$$\#\,w_1w_2\cdots w_n\,\#\,\sqcup\,\#\,\sqcup\,\#\cdots\#$$
with $k+1$ delimiters and a dotted version of each tape symbol to mark the virtual heads.
1. **Initialization.** $S$ writes the input on its tape and formats it to represent all $k$ tapes.
2. **Simulating a move.** $S$ scans from the first `#` to the $(k+1)$-st `#` to determine the symbols under the virtual heads, then makes a second pass to update the tapes according to $M$'s transition function.
3. **Moving onto a blank.** If a virtual head moves right onto a `#`, $S$ writes a blank there and shifts the contents from that cell to the rightmost `#` one unit right, making room for the new tape cell.

$S$ simulates $M$ step by step and accepts exactly when $M$ accepts.

---
##### THEOREM 3.16 : NONDETERMINISTIC → DETERMINISTIC - (PAGE 178)
#THEOREM18

**THESIS**: Every nondeterministic Turing machine has an equivalent deterministic Turing machine.

**PROOF IDEA**: Let $N$ be a nondeterministic TM. Construct a deterministic TM $D$ that tries all branches of $N$'s computation tree. A **depth-first** search is wrong: it could follow an infinite branch forever and never explore an accepting configuration on another branch. Use **breadth-first search**, which visits all nodes at depth $d$ before any node at depth $d+1$.

**PROOF**:
$D$ has three tapes (equivalent to one by Theorem 3.13):
1. tape 1: the input $w$, never altered;
2. tape 2: a copy of $N$'s tape on the current branch;
3. tape 3: the **address** of the current node in $N$'s computation tree.

Every node has at most $b$ children, where $b$ is the maximum number of choices given by $N$'s transition function. Addresses are strings over $\Gamma_b = \{1,\dots,b\}$: the empty string is the root, and $231$ means "second child, then third child, then first child".
1. Initially tape 1 contains $w$; tapes 2 and 3 are empty.
2. Copy tape 1 to tape 2 and set the address on tape 3 to $\varepsilon$.
3. Simulate $N$ on tape 2, using the next symbol of the address to choose among the allowed moves. If the address is exhausted or invalid, or a rejecting configuration is reached, abort this branch and go to stage 4. If an accepting configuration is reached, **accept**.
4. Replace the address by the next string in the string ordering (BFS) and go to stage 2.

BFS guarantees that every node of the tree is eventually visited until an accepting configuration is found. If $N$ has no accepting branch, $D$ may run forever; this is correct for a recognizer.
