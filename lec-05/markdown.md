name: inverse
layout: true
class: center, middle, inverse
---
# ENSE 350: Math for Software Eng.

### Lecture 5: Well Ordering Principle, Examples

Adam Tilson, M.A.Sc., Engineer-in-Training

---
layout: false
.left-column[
## Agenda
]
.right-column[
1. Review: Lecture 4 Highlights
1. Well Ordering Principle
1. Examples
]

---
## Review: Invariant
- The invariant is some property of the system which is true in the start state of the system, and true in every legal move. 
- We can use this to prove if the system is in a winnable state, or an unwinnable state.

---

### Review: Strong Induction Comparison
- Last class we say: Solve a Tougher Problem
- We can also use a stronger form of induction

Ordinary Induction:

$\dfrac{P(0), \forall n \in \mathbb{N}, P(n) \Rightarrow P(n+1)}{\forall m \in \mathbb{N}, P(m)}$

Strong Induction:

$\dfrac{P(0), \forall n \in \mathbb{N}, P(0) \wedge P(1) \wedge P(2) \wedge ... \wedge P(n) \Rightarrow P(n+1)}{\forall m \in \mathbb{N}, P(m)}$

???
Which problem did we look at that would have been solved by strong induction?

---

### Review: When to use Strong Induction
When to use strong induction
- When there is no obvious connection between $P(n)$ and $P(n+1)$
- i.e. we can't use $P(n)$ directly to prove $P(n+1)$
- However, we may be able to use some combination of $P(0), P(1), P(2) ... P(N)$

---

### Review: How to use Strong Induction: Proof Template
- State that we are solving the problem by strong induction
- Define our Induction Hypothesis, $P(n)$, defining the induction variable $n$
- Prove the base case: $P(0)$ is true
- Prove the inductive step: $P(0) \wedge P(1) \wedge P(2) \wedge ... \wedge P(n) \Rightarrow P(n+1)$
- By induction, conclude P(n) is true for all $n \in \mathbb{D}$

---
## Well-Ordering Principle
The well-ordering principle states that:
- every nonempty set 
- of non-negative integers 
- has a smallest element
This seems very obvious, but can actually be used to formulate some powerful proofs.
---
## Well-Ordering Principle Common Template
- Define the set C, of counter-examples to P being true
- $C := {n \in \mathbb{N}, \neg P(n)}$
- Proof by contradiction
- Assume that $C$ is non-empty
- By the well-ordering principle, show that $C$ contains a smallest element, $n$, and thus is non-empty
- Reach a contradiction (open ended)
- e.g. show that $n \not\in C$
- Conclude that C must be empty
---
## Well-Ordering Principle - Another Formulation
- Goal: prove some $P(n)$ is FALSE
- Define the set $S$, of examples for which $P(n)$ is true
- By the well-ordering principle, define $s$ as the lowest element in $S$
- Proof by contradiction
- Show that a value smaller than $s$ satisfies $P(n)$
- Thus that value is also in $S$
- Thus $s$ was not the lowest value in $S$
- Contradiction
- By the well-ordering principle, $S$ must be empty

---

## Examples:

We already used the Well-Ordering principle when we proved $\sqrt{2}$ is not rational!
- Recall we defined rational numbers as the fraction of two integers, a and b in smallest terms
- Because all rational numbers can be expressed in lowest terms
- We then showed that each of these numbers was even, meaning there must be a smaller term which satisfies the ratio
- Thus, by the well ordering principle, there are lower numbers in the set

---

## Proof - Sum of Cents - Well Ordering Principle

- Theorem: Any amount of money of least 8¢ can be made using 3¢ and 5¢ coins.
- Proof: By the well-ordering principle
- Suppose NOT any amount of money...
- Let $m$ be the least counterexample.
- Since is $m$ is the least number which cannot be made of 3¢ and 5¢ coins, any number smaller than it can.
- $m \neq 0$, because $8 = 3 + 5$
- $m \neq 1$, because $9 = 3 + 3 + 3$
- $m \neq 2$, because $10 = 5 + 5$
- Hence, $m \geq 3$.

---
## Proof - Sum of Cents - Well Ordering Principle

- Hence, $m \geq 3$.
- i.e. $(m-3)$ is not a counterexample
- but then $m$ is also not a countersample, since $(m-3)+3¢ = m$
- We have reached a contradiction
- Thus, {counterexamples} is empty. ⨳. $\square$
---

## Proof - Sum of Cents - Strong Induction

Theorem: Any amount of money of least 8¢ can be made using 3¢ and 5¢ coins.
 
Proof: By strong induction
- Base Case: $8¢ = 3¢ + 5¢. \checkmark$

Induction Hypothesis: $P(n) := 8¢+ n$ can be made using $3$¢ and $5$¢ coins. $\forall n \in \mathbb{N}, P(n)$.

Induction Step: $P(0) \wedge P(1) \wedge P(2) \wedge ... \wedge P(n) \Rightarrow P(n+1)$

---

## Proof - Sum of Cents - Strong Induction

Induction Step: $P(0) \wedge P(1) \wedge P(2) \wedge ... \wedge P(n) \Rightarrow P(n+1)$

Case 1: $n \lt 2$:
-1.1 n=0: $8¢ = 3¢ + 5¢. \checkmark$
-1.2 n=1: $9¢ = 3¢ + 3 + 3¢. \checkmark$
Case 2: if $n \geq 2, P(n-2)$ is true.
- $\forall n > n-2,$ we can make P(n+1) with +(n-2) + 3¢.
- $P(n+1)$ is true. $\checkmark$

---

## Proof - Product of Primes by Well-ordering

Theorem: Every integer > 1 is a product of primes.
- We already proved this with strong induction. Let's prove it with Well Ordering Principle.
- Proof: By well-ordering principle, by contradiction
- Suppose {nonproducts} is non-empty. By W.o.P., there is at least $m \gt 1$ that is a non-product.
    - $m$ is not a prime. (as it would then also be a product of 1 prime)
- Every integer > 1 is a product of primes.

---

## Proof - Product of Primes by Well-ordering

- So $m = j \times k$ for integer $j,k$ where $m \gt j,k > 1$. 
  - Now $j,k < m$ so both are prime products.
  - $j = p_1 \times p_2 \times ... \times p_x$
  - $k = q_1 \times q_2 \times ... \times q_y$
- $m = j \times k = p_1 \times p_2 \times ... \times p_x \times q_1 \times q_2 \times ... \times q_y$
  - Thus, $m$ is a prime product, which is a contradiction
- Thus, {nonproducts} is empty. ⨳. $\square$

---

## Proof - Geometric Sums
Theorem:
$1 + r + r^2 + r^3 + ... + r^n = \dfrac{r^{n+1}-1}{r-1}$
- holds for all real numbers $r \geq 1$, all integers $n \in \mathbb{N}$
- Proof by the W.O.P.
- Let $m$ be smallest $n$ where this equality does not hold.
- n=0? 1=1 Holds.
  - so m>0
- Since m is the lowest example for which this does not hold, we assume the following equality holds:
- $1 + r + r^2 + r^3 + ... + r^{m-1} = \dfrac{r^{(m-1)+1}-1}{r-1}$
---
## Proof - Geometric Sums
- $1 + r + r^2 + r^3 + ... + r^{m-1} = \dfrac{r^{(m-1)+1}-1}{r-1}$
- $1 + r + r^2 + r^3 + ... + r^{m-1} = \dfrac{r^m}{r-1}$
- Lets add $r^m$ to both sides.
- LHS: $1 + r + r^2 + r^3 + ... + r^{m-1} + r^m$
- RHS: $\dfrac{r^m}{r-1} + r^m = \dfrac{r^m}{r-1} + \dfrac{r^{m+1} - r}{r-1} =\dfrac{r^{m+1}-1}{r-1} $
- This is the identity we claimed did not hold. ⨳
- Thus the set of counterexamples must be empty.  $\square$
---


### References

- Dr. Abdul Bais's ENSE 350 Slides
- Albert Meyer, and Adam Chlipala. 6.042J Mathematics for Computer Science. Spring 2015. Massachusetts Institute of Technology: MIT OpenCourseWare, https://ocw.mit.edu. License: Creative Commons BY-NC-SA.
---
name: inverse
layout: true
class: center, middle, inverse
---
# Questions?