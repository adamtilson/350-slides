name: inverse
layout: true
class: center, middle, inverse
---
# ENSE 350: Math for Software Eng.

### Lecture 3: Ordinary Induction

Adam Tilson, M.A.Sc., Engineer-in-Training

---
layout: false
.left-column[
    ## Agenda

]
.right-column[
1. Review: Lecture 2 Highlights
1. Ordinary Induction
1. Induction Examples
1. All Horses are the Same Color
1. Tiling Puzzle
1. Prove Something Harder
1. Invariants
1. The 8-Puzzle
]
---

## Ideal Set of Axoims
- Should be *complete* and *consistent*

Consistent - an axiom cannot be proven to be both true and false
- Absolutely required

Complete - an atomic set of axioms which can be used to prove all other axioms
- Unfortunately this doesn't exist
- People have dedicated their careers to finding them

---
## Logical Deduction
- A proof is a set of small, logical steps
- We can further structure our longer proofs with:
  - Theorems (Thm) - An important proposition
  - Lemma - A preliminary proposition used in proving later propositions (like a subroutine)
  - Corollary - A proposition that follows, in a few logical steps, from a lemma or theorem
---

## Writing Rules of Logic
- Premises (Antecedents)
- Conclusion (Consequent)
- Sound rules: A logical rule is sound if any assignment of truth values that make all the antecedents true must also make the consequent true
- e.g. Modus Ponens
$$ \frac{P, P\Rightarrow Q}{Q}$$
- "if P is true, and P implies Q is true, then Q is true"
???
In your mind it's like a big old truth table. Each step you add a column to it, and recompute the T's and F's. They can't ever change from the previous column!
---
.left-column[
## Methods of Proof

]
.right-column[
- Proof by Cases
- Direct Proof (Assume P)
- Indirect Proof
    - Assume the Contrapositive
    - Proof by Contradiction
- Prove and IFF
    - Mutual implication
    - Chain of IFFs
- Today we'll learn another useful tool!
]
---
## Induction

Goal: Prove something true for all values in a sequence.
- (1) We prove that P(0) is true (Base Case)
- We want to prove that...
    - $P(0) \Rightarrow P(1)$
    - $P(1) \Rightarrow P(2)$
    - $P(2) \Rightarrow P(3)$
    - $P(3) \Rightarrow P(4)$ ...
- (2)  We do this symbolically by generalizing all these cases as:
    - $P(n) \Rightarrow P(n+1)$ (Induction Step)
- We conclude this is true for all values in the sequence.

---
## How Induction Works
Symbolically:

$\dfrac{P(0), \forall n \in \mathbb{N}, P(n) \Rightarrow P(n+1)}{\forall m \in \mathbb{N}, P(m)}$

It's like knocking over dominoes 
- you knock over the first domino, 
- if you can prove that the previous domino will knock over the next one (for any arbitrary domino)
    - we conclude all dominoes will get knocked over
---
## Induction Example
- The first person in the queue gets a vaccine
- For all people in the queue
    - If the person gets a vaccine, then the person behind them will get a vaccine
- Thus, we conclude, everyone gets a vaccine. $\square$ 

- This is a "template proof", and very useful

---
## Induction
Template:
- State the strategy (Proof by ordinary induction)
- Define predicate $P(n)$, known as the Inductive Hypothesis
- Prove the Base Case, i.e. that $P(0)$ is true
- Prove the implication $P(n) \Rightarrow P(n+1)$, known as the Inductive Step.
- Conclude, by the principle of induction, that the predicate is true for all values of $n$.

---
## Example 1
Theorem: $\forall n \geq 0, 1+2+3+...+n = \dfrac{n(n+1)}{2}$
We could also write this as:
$$\sum_{i=1}^{n}i = \dfrac{n(n+1)}{2}$$

Proof (by ordinary induction).

Inductive Hypothesis: 
$P(n) := \sum_{i=1}^{n}i = \dfrac{n(n+1)}{2}$
---
## Example 1
Proof (by ordinary induction).  
Inductive Hypothesis: $\forall n \geq 0, P(n) := \sum_{i=1}^{n}i = \dfrac{n(n+1)}{2}$

Base Case:
- $\sum_{i=1}^{0}i = \dfrac{0(0+1)}{2}$
- $0 = 0 \checkmark$
---
## Example 1
Inductive Step: $P(n) \Rightarrow P(n+1)$

$ P(n) + (n+1) = P(n+1)$

$\sum_{i=1}^{n}i + (n+1) = P(n+1)$

$\dfrac{n(n+1)}{2} + (n+1) = \dfrac{(n+1)((n+1)+1)}{2}$

$\dfrac{n(n+1)}{2} + \dfrac{2(n+1)}{2} = \dfrac{(n+1)(n+2)}{2}$

---
## Example 1

$\dfrac{n(n+1)}{2} + \dfrac{2(n+1)}{2} = \dfrac{(n+1)(n+2)}{2}$

$\dfrac{(n+1)(n+2)}{2} = \dfrac{(n+1)(n+2)}{2} \checkmark$

Thus, by ordinary induction, $P(n)$ is true for all $n \geq 0$. $\square$

---
## Example 2

Theorem: $\forall n \in \mathbb{N}, 3 \mid (n^3-n) $

Is this true? Let's try 5? $(5^3-5) = (125-5) = 120.$ $3\mid 120 \checkmark$
- Seeeeems to be true, but remember no number of examples can ever prove something true!

Proof: By Induction

Induction Hypothesis: $\forall n \in \mathbb{N}, P(n) := 3 \mid (n^3-n)$

Base Case:

---
## Example 2

Induction Hypothesis: $\forall n \in \mathbb{N}, P(n) := 3 \mid (n^3-n)$

Base Case:

$P(n)=0^3-0$
$= 0$

$3\mid 0 \checkmark$

---
## Example 2

Induction step: Show $3 \mid P(n) \Rightarrow 3 \mid P(n+1)$ 

$P(n+1) = ((n+1)^3 - (n+1))$

$= ((n+1)^3 - (n+1))$

$= (n^3 + 3n^2 + 3n + 1) - (n + 1)$

$= n^3 + 3n^2 + 2n$ 

? Now what ? We haven't really used the Induction yet.

---
## Example 2

$= n^3 + 3n^2 + 2n - n + n$ 

$= (n^3 -n) + 3n^2 + 3n$ 

$= 3 \mid (n^3 -n) + 3n^2 + 3n$ ?

We know $3 \mid 3n, 3 \mid 3n^2$,

By the inductive hypothesis, we assume $3 \mid (n^3 -n)$

$\because 3 \mid $ each term, $3 \mid P(n+1)$

$\therefore$, by ordinary induction,  $\forall n \in \mathbb{N}, P(n)$ is true. $\square$

---
### Anti Proof - All Horses are the Same Color

Induction seems so powerful. Can anything go wrong with it?
- Let's use it to prove that all horses are the same color.
- Theorem: All horses are same color.
- Proof: By ordinary induction.
- Inductive hypothesis: 
    - In any set of $n \geq 1$ horses, all the horses are the same color.
- Base case: 
    - We have a set of one horse. That horse must be the same color as itself. $\checkmark$

---
### Anti-Proof - All Horses are the Same Color

- Inductive step:
    - Assume $P(n)$ to prove $P(n+1)$
    - Assume a set of $n$ horses all have the same color.
    - Name these horses $h_1$ to $h_n$
    - Remove the leader, $h_1$, so the set is $h_2 ... h_n$ of size $n-1$.
        - All these horses must be the same color. 
    - Let's add to our subset a new arbitrary horse. 
        - This makes a set of $n$ horses 
        - By our assumption, sets of $n$ horses are all the same color
    - Now let's add back in the leader horse to the set
        - Now have a set of $n+1$ horses, all of which are the same color.
---
### Anti-Proof - All Horses are the Same Color

- Thus, we have transitioned from a set of $n$ horses of the same color, to $n+1$ horses of the same color. We completed the induction step.
- $\therefore$ all horses are the same color. $\square$ 

- What went wrong?

---
class: even-split
.column[
![](horses-same-color.png)

]
.column[
- $P(1) \checkmark$
- $P(n) \Rightarrow P(n+1) \checkmark$


- Image credit: Kmhkmh 
    - CC-BY 4.0
]
---
class: even-split
.column[
![](horses-not-the-same-color.png)

]
.column[
- The proof works for the case of $n=1$ 
- $n=3+$
- but does not work for $n=2$
- $P(1) \not \Rightarrow P(2)$
- Our proof relied on there remaining at least one horse in the subset after removing the leader from which to observe a color.

- Image credit: Kmhkmh 
    - CC-BY 4.0
]


---
## Tiling Puzzle

A wealthy benefactor wants to donate money to the university to fund a new green area.
Their requirements :
- The size of the courtyard be some size $2^n$ meter tiles.
- A statue of them is on a tile which touches the center
- The entire space must be tiled using $2 \times 2$ "L-tiles"

---
## L-Tile
![](l-tile.png)

---
## n=0
![](n-0-just-statue.png)
---
## n=1
![](n-1-statue-1-tile.png)
---
## n=2
![](n-2-statue-and-tiles.png)
---
## Proof:
Prove, by induction, that this can be achieved for any $n$.

Theorem: $\forall n \in \mathbb{N}, \exists$ a way to tile a $2^n \times 2^n$ region with a center square missing.

Proof: By Induction.

Induction Hypothesis. $P(n)$ = Theorem.

Base Case: $n=0$. (Demonstrated in the previous slides)

Induction Step: $P(n) \Rightarrow P(n+1)$

---
## Strategy

We need to consider a $2^n \times 2^n$ courtyard, compared to a $2^{n+1} \times 2^{n+1}$ courtyard.

Each time the size doubles.

---
## Relationship between n and n+1...
![](n-vs-n-plus-one.png)
---
## If only we could...
![](if-only-1.png)
---
## If only we could...
![](if-only-2.png)
---
## Solve a Tougher Problem
- Why can't we?
    - Our inductive hypothesis relies on our $n \times n$ region having a center tile missing.
- We could restructure our proof with Lemmas, Corallaries, etc.
    
- Sometimes it's easier to solve a tougher problem!
    - What is a "harder" formulation of this same problem which gives us more freedom?

---
## Solve a Tougher Problem
- Prove instead that we can put the statue in ANY square
- Theorem: $\forall n \in \mathbb{N}, \exists$ a way to tile a $2^n \times 2^n$ region with a any square missing.
- (By inspecting n=0, n=1, n=2, does this theorem seem reasonable?)

Proof: By ordinary induction
- Base Case: $n=0$, Still one tile, still holds  
- Induction Hypothesis: $P(n) \Rightarrow P(n+1)$
    - "If we can tile an $n \times n$ area with any square missing, we can tile an $(n+1) \times (n+1)$ area with any square missing"
---
## Tougher Problem Proof
- Assuming we can place the statue in any square of an $n \times n$ area
- An $(n+1) \times (n+1)$ region consists of four $n \times n$ regions 
- Choose any of the four regions, and place the statue in any square
- In the remaining three regions:
    - Since we can place the empty square anywhere (Induction Hypothesis)
    - We will place the empty square in the center of the new $(n+1) \times (n+1)$ region, i.e., The corner of the respective $n \times n$ region.
    - We tile the three adjacent empty squares with a single L-tile
- Since $P(0), P(n) \Rightarrow P(n+1)$, the theorem is true for all $n$. $\square$

---
## Final Tips on Induction
- Did I prove the base case?
- Did I use the induction hypothesis, i.e. use P(n) somewhere in the proof?
- Did I logically show than, assuming P(n), P(n+1) is also true?
- Are there any steps from 1...n where this induction would not hold?
    - We'll look at strategies for this in the next lecture!

---

class: even-split
### Cheat Sheet o' Math Symbols

.column[
$$\sum_{i=1}^{n}i$$
- The sum of all numbers from 1 to n.

- $\not \Rightarrow$ Not implies
]
.column[

]
---
class: even-split
### Cheat Sheet o' Axoims

.column[
- $\forall n \geq 0, 1+2+3+...+n = \dfrac{n(n+1)}{2}$
- All numbers divide 0


]
.column[

]
---

### References

- Dr. Abdul Bais's ENSE 350 Slides
- Tom Leighton, and Marten Dijk. 6.042J Mathematics for Computer Science. Fall 2010, Lecture 2. Massachusetts Institute of Technology: MIT OpenCourseWare, https://ocw.mit.edu. License: Creative Commons BY-NC-SA.
---
name: inverse
layout: true
class: center, middle, inverse
---
# Questions?