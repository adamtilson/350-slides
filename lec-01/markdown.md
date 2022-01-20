name: inverse

layout: true

class: center, middle, inverse

---

# ENSE 350: Math for Software Eng.



### Lecture 1: Introduction



Adam Tilson, M.A.Sc., Engineer-in-Training



---

layout: false

.left-column[

  ## Agenda

]

.right-column[

1. Syllabus and Course Overview

2. Proof

3. Proposition

4. Why you can't Prove by Example

5. Compound Proposition

6. Logically Equivalent Statements

7. Predicates

8. Quantifiers

9. Ambiguity

10. Valid Proposition

11. Satisfiable Proposition

]

---

.left-column[

  ## Syllabus

]

.right-column[

Please find the Syllabus posted on URCourses.



Note:

- Late starting date. 

- Midterm and Final dates.

- Lab and Seminar schedules.



]



---

## Discrete Mathematics 



![](bender-is-discreet.png)

---



## Defn: Discrete Mathematics



A branch of mathematics dealing with objects that can assume only discrete / distinct / seperate values

- e.g. The bit. (1 or 0)

- e.g. The integer.

  - The concept, not the data type

  - But also the data type! 

  - Most data types in computers (recall ENSE 352). 

- Natural numbers (Non-negative integers)

---



## Defn: Proof



A method of finding the truth

- Different meanings in different fields

- Courts

  - Legal evidence. Judge and jury.

- Science

  - Observations, experiments, sampling

- Authority. (Religion, Boss, Professor?)

- Conviction

- Burden of proof



---



## Defn: Math Proof



- A verification of a **proposition**

- starting from a set of **axioms**

- through a chain of **logical deductions**



---



## Defn: Propositions

- A statement that can be either true or false

- e.g. 2 + 3 = 5

- not: Hello.

- not: Is it raining?

- e.g.

$$ \forall n \in \mathbb{N}, n^2 + n + 41 \text{ is a prime number} $$ 



---



## Deciphering Math symbols



$$ \forall n \in \mathbb{N}, n^2 + n + 41 \text{ is a prime number}$$ 



"For all numbers n, in the set of natural numbers {0,1,2...}, $ n^2 + n + 41 $ is a prime number"





Is this true?



---



## Is this true?



$$ \forall n \in \mathbb{N}, n^2 + n + 41 \text{ is a prime number}$$ 



$n$ | $n^2 + n + 41$ | prime?

:-:|:-:|:-:

0  | 41 | yes

1  | 43 | yes

2  | 47 | yes

3  | 53 | yes

... | ... | ...

40  | 1681 |no: divisible by 41



Is there a more obvious example?



???



It's 41, because clearly it would be divisible from all 3 terms, 41^2, 41 and 41. What's divisible by each of the terms must be divisible by the sum.



---



## What about this?



$$ \exists a,b,c,d \in \mathbb{Z}^+ , a^4 + b^4 + c^4 = d^4 $$



There exists some numbers a,b,c,d in the set of positive integers {1, 2, 3, 4...} which satisfy this equation. Sure does!



- a = 95, 800

- b = 217, 519

- c = 414, 560

- d = 422, 480 



Euler believed this impossible in 1796, but a solution was found in 1988. How would you figure this out?!



???



So Proof by Authority doesn't work, even with  famous mathematicians!



---



## What about this?



$$ 313 (x^3 + y^3) = z^3 \text{ has no positive integer solutions} $$



The smallest counterexample has over 1000 digits



- Why should we care?

  - The concept of factoring large numbers is vital to modern cryptography algorithms employed today

  - If we could trivially factor these large numbers, we would need a new approach to cryptography

- More immediately, just plugging in a few numbers, observing a trend, and taking it as proof is a bad strategy



---



.left-column[

  ## Compound Propositions

  ### NOT

]

.right-column[

$$ \text{NOT} := \neg $$

$$ P := \text{Some proposition} $$



$ P $ | $ \neg P $

---|---

T | F

F | T



]

---





.left-column[

  ## Compound Propositions

  ### AND

]

.right-column[

$$ \text{AND} := \wedge $$

$$ P := \text{Some proposition} $$

$$ Q := \text{Some proposition} $$



$ P $ | $ Q $ | $ P \wedge Q $  

---|---|---

T | T | T

T | F | F

F | T | F

F | F | F



]

---





.left-column[

  ## Compound Propositions

  ### OR

]

.right-column[

$$ \text{OR} := \vee $$

$$ P := \text{Some proposition} $$

$$ Q := \text{Some proposition} $$



$ P $ | $ Q $ | $ P \vee Q $  

---|---|---

T | T | T

T | F | T

F | T | T

F | F | F



]

---





.left-column[

  ## Compound Propositions

  ### XOR

]

.right-column[

$$ \text{XOR} := \oplus $$

$$ P := \text{Some proposition} $$

$$ Q := \text{Some proposition} $$



$ P $ | $ Q $ | $ P \oplus Q $  

---|---|---

T | T | F

T | F | T

F | T | T

F | F | F



]

---



.left-column[

  ## Compound Propositions

  ### Implies

]

.right-column[

$$ \text{Implies} := \Rightarrow $$

$$ P, Q := \text{Some propositions} $$



$ P $ | $ Q $ | $ P \Rightarrow Q $  

---|---|---

T | T | T

T | F | F

F | T | T

F | F | T



- Confusing. P is the premise, Q is the conclusion.

- Both parts are propositions, can be T or F

- We're evaluating if the implication is true, not either part!

- "Pigs can fly $\Rightarrow$ I'm the king of Moose Jaw"



]

---



.left-column[

  ## Compound Propositions

  ### Implies

]

.right-column[



$ P $ | $ Q $ | $ P \Rightarrow Q $  

---|---|---

T | T | T

T | F | F

F | T | T

F | F | T

Logically: $ (\neg P) \vee Q$



Programatically:

```python

if p:

  return q

else:

  return True

```

]

---



.left-column[

  ## Compound Propositions

  ### Implies

]

.right-column[



Examples (Are these implications T or F?):

- "It's Cloudy $ \Rightarrow $ It's Raining"

  - Can it be cloudy and not raining?

- "It's Raining $ \Rightarrow $ It's Cloudy"

  - Can it be rainy with no clouds?

- If all dogs are good boys, then all chihuahuas are good boys.

  - If all dogs are good boys, but I have a naughty chihuahua, the implication must be false. As worded, it is true, since chihuahuas are a subset of dogs.

- If $n > 7$, then $n > 3$. ( $n>7 \Rightarrow n>3$ )

* We'll look at a trick for this later.

]



???



F

T, assuming it can't rain without clouds

T



---



.left-column[

  ## Compound Propositions

  ### IFF

]

.right-column[

$$ \text{If and only if} := \text{IFF} := \iff $$



$$ P \iff Q \equiv (P \Rightarrow Q) \wedge (Q \Rightarrow P) $$



$P$|$Q$|$P \Rightarrow Q$ | $Q \Rightarrow P$ | $P \iff Q $

---|---|---|---|---

T|T|T|T|T

T|F|F|T|F

F|T|T|F|F

F|F|T|T|T

Examples (Are these iff's T or F?):

- e.g. "It's raining $\iff$ it's cloudy"

- e.g. "You pass the class $\iff$ you get a grade above 50%"

]



???

F

T, unless the course has some gotchas, like must pass all the labs, etc.



---



## Defn: Logical Equivalence 

- "Two statements are logically equivalent if, and only if, their resulting truth tables are identical for each variation of statement variables!*"



- We'll use the $\equiv$ symbol for this



.footnote[.red.bold[*] https://www.csm.ornl.gov/~sheldon/ds/sec1.1.html]



---



## Defn: Contrapositive

$$ (P \Rightarrow Q) \equiv (\neg Q \Rightarrow \neg P) $$



$P$ | $Q$ | $\neg P$ | $\neg Q$ | $P \Rightarrow Q$ | $\neg Q \Rightarrow \neg P$ |  $\equiv$

---|---|---|---|---|---|---

F|F|T|T|T|T|$\checkmark$

F|T|T|F|T|T|$\checkmark$

T|F|F|T|F|F|$\checkmark$

T|T|F|F|T|T|$\checkmark$



With implications, sometimes it's easier to prove the contrapositive!



---



## Contrapositive Examples

- If it is raining, then I take an umbrella

  - If I did not take an umbrella, then it is not raining

- If all dogs are good boys, then all chihuahuas are good boys

  - If not all chihuahuas are good boys, then not all dogs are good boys

  - If at least one chihuahua is bad, then not all dogs are good boys

* Contrapositive is the only negation that is logically equivalent to the positive!

---



## Converse

The converse of

$$ P \Rightarrow Q $$

is

$$ Q \Rightarrow P $$

Are these equivalent? How could we verify?

---



## Converse

$P$|$Q$|$P \Rightarrow Q$ | $Q \Rightarrow P$ | $\equiv $

---|---|---|---|---

T|T|T|T|$\checkmark$

T|F|F|T|$\times$

F|T|T|F|$\times$

F|F|T|T|$\checkmark$

---



## Inverse

The inverse of

$$ P \Rightarrow Q $$

is

$$ \neg P \Rightarrow \neg Q $$

Are these equivalent? How could we verify?

---

## Inverse

$P$ | $Q$ | $\neg P$ | $\neg Q$ | $P \Rightarrow Q$ | $\neg P \Rightarrow \neg Q$ |  $\equiv$

---|---|---|---|---|---|---

T|T|F|F|T|T|$\checkmark$

T|F|F|T|F|T|$\times$

F|T|T|F|T|F|$\times$

F|F|T|T|T|T|$\checkmark$

Is this logically equivalent to anything we've already looked at? By which rules are they logically equivalent?

???

Yep. Converse is logically equivalent to the inverse. 

This is because the converse is the contrapositive of the inverse. 

My head hurts.



---

## Predicate

A proposition whose truth value depends on the value of a variable, or multiple variables

- e.g. "$n$ is a prime number"

- e.g. $P(n) := $"$n^2+1$ is a prime number"

  - P(1) = True

  - P(2) = True

  - P(3) ??? 

???

It's false.



---

## Quantifiers



Universal $\forall$

- Always

- For every, For all



Existential $\exists$

- There exists

- Sometimes



---

## Ambiguity



"Every American has a Dream"

- Easy to make ambiguity mistakes in English. 

- Every American has the same Dream?

- Every American has a different Dream?

---



## Resolving Ambiguity with Predicate Logic

"Every American has a Dream"



let D be the set of all possible Dreams



let A be the set of all Americans



$H(a,d) :=$ American, $a$, has Dream, $d$



$$ \forall a \in A, \exists d \in D, H(a,d). $$

$$ \exists d \in D, \forall a \in A, H(a,d). $$



???



In the first one, all Americans have the a different dream

In the second one, all americans have the same dream.

The first part sets up the domain.

---

## Examples



Aristotle is a man



Let a := Aristotle



Let M := the set of all men



$\exists x \in M, x = a$



All men are mortal, thus Aristotle is mortal



Let R := the set of all mortals



$\exists x \in M, x = a \Rightarrow a \in R$



---

## Domains



$\mathbb{N} = {0, 1, 2, ...}$



$\mathbb{Z} = {... -3, -2, -1, 0, 1, 2, ...}$



$\mathbb{Z}^+ = {1, 2, 3, ...}$



$\mathbb{Z}^- = {... -3, -2, -1}$



You can define subsets as needed:



- Let Evens := "The set of all even integers"

- Let Primes := "The set of all prime numbers"

---



## Goldbach Conjecture

"Every even number greater than two is the sum of two prime numbers"



Let Evens := the set of even numbers > 2.



$$ \forall n \in \text{Evens}, \exists p \in \text{Primes},  \exists q \in \text{Primes}, n = p + q.  $$



$$ \forall n \in \text{Evens}, \exists p, q \in \text{Primes}, n = p + q.  $$



---

## Negating Quantifiers



$$\forall n \in \mathbb{N}, P(n)$$



$$\neg (\forall n \in \mathbb{N}, P(n)) \equiv \exists n \in \mathbb{N}, \neg P(n)$$



$$ \neg (\exists n \in \mathbb{N}, Q(n)) \equiv \forall n \in \mathbb{N}, \neg Q(n) $$



???



This too hurts my head



---



## Satisfiability of a Proposition

- There exists at least one way to set the variable which makes the proposition true

- e.g. $ P \wedge (\neg P) $ is not satisfiable



---



## Validity of a Proposition



- A proposition is valid if it evaluates to true regardless of the values assigned to the individual variables

- e.g. we know this equivalence is valid:

$$ (P \Rightarrow Q) \equiv (\neg Q \Rightarrow \neg P) $$

What about:

$$ (P \Rightarrow Q) \equiv (Q \Rightarrow P) $$

- Satisfiable, (If P and Q are both false or true) but not Valid!



---

class: even-split

### Cheat Sheet o' Math Symbols



.column[

- $:=$ defined as

- $\exists$ there exists

- $\forall$ for all

- $\in$ in the set

- $\equiv$ equivalent

- $\mathbb{N}$ {0, 1, 2, ...}

- $\mathbb{Z}$ {..., -2, -1, 0, 1, 2, ...}

- $\mathbb{Z}^+$ {1, 2, 3, ...}

- $\mathbb{Z}^-$ {..., -3, -2, -1}



]

.column[

- $\neg P$ / ~P / $\overline{P}$ not

- $\wedge$ and

- $\vee$ or

- $\oplus$ / $\veebar$ xor

- $\Rightarrow$ / $\rightarrow$ implies

- $\iff$ if and only if

- $\because$ because

- $\therefore$ therefore

- $\square$ / $\blacksquare$ / $QED$ proof done

]









---

### References



- Dr. Abdul Bais's ENSE 350 Slides

- Tom Leighton, and Marten Dijk. 6.042J Mathematics for Computer Science. Fall 2010, Lecture 1. Massachusetts Institute of Technology: MIT OpenCourseWare, https://ocw.mit.edu. License: Creative Commons BY-NC-SA.

---



name: inverse

layout: true

class: center, middle, inverse

---

# Questions?

