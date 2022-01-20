name: inverse
layout: true
class: center, middle, inverse
---
# ENSE 350: Math for Software Eng.

### Lecture 6: Introduction to Number Theory

Adam Tilson, M.A.Sc., Engineer-in-Training

---
layout: false
.left-column[
  ## Agenda
]
.right-column[
1. Lecture 5 Review
2. Divisibility
3. Linear Combinations 
4. Properties of GCD
5. Euclidean Algorithm
6. Die Hard Problem
7. Extended Euclidean
8. Prime Numbers
]
---
Todo: Review Lec 5
---
layout: false
.left-column[
## Divisibility
]
.right-column[
$a$ divides $b \iff a \cdot k = b$ for some $k$  
$a \mid b \iff a \cdot k = b$ for some $k$  

e.g. $2 \mid 6$ 
- $6 = 3 \cdot 2$
- $0 = 3 \cdot 0$
- $0 = n \cdot 0$ 
  - $0$ divides all numbers
]
---
layout: false
.left-column[
## Divisibility
### Properties
]
.right-column[
1: If $a \mid b$, then $a \mid b \cdot c $ for all $ c$
- assume $b = k \cdot a$
- $bc = (k \cdot c) \cdot a$
- $bc = (k_1) \cdot a$
- $\therefore a \mid b \cdot c$

2: If $a \mid b$, and $b \mid c$, then $a \mid c$
- $b = k_1 \cdot a$
- $c = k_2 \cdot b$
- $c = k_1 \cdot k_2 \cdot a$
- $\therefore a \mid c$

]

---
layout: false
.left-column[
## Divisibility
### More Properties
]
.right-column[
3: If $a \mid b$, and $a \mid c$, then $a \mid s \cdot b + t \cdot c $ for all $s$ and $t$.
- $b = k_1 \cdot a$
- $c = k_2 \cdot a$
- $s\cdot b + t \cdot c = s \cdot k_1 \cdot a + t \cdot k_2 \cdot a$
- $s\cdot b + t \cdot c = (s \cdot k_1 + t \cdot k_2) \cdot a$
- since $ (s \cdot k_1 + t \cdot k_2)$ is an integer
  - $a \mid s \cdot b + t \cdot c$
  
4: For all $c \neq 0, a \mid b \iff c\cdot a \mid c \cdot b$
- Can prove with the same principles
]


---
layout: false
.left-column[
## Divisibility
### Division Theorem
]
.right-column[
Let $n$ and $d$ be integers such that $g \gt 0$. There there exists a unique pair of integers, $p, q$, such that $n = q \ \cdot d + r \wedge 0 \leq r \leq d$
- $n := $numerator
- $d := $denominator
- $q := $quotient
- $r := $remainder
- if $r = 0, d \mid n$
- e.g. $7 = 3 \cdot 2 + 1$
- not an e.g. $9 = 2 \cdot 2 + 5$
  - $5 \not \lt 2$
- e.g. $9 = 4 \cdot 2 + 1.$
]


---
layout: false
.left-column[
## Divisibility
### Integer Linear Combi- nations
]
.right-column[
$s \cdot a + t \cdot b$
- e.g., $a = 3, b = 5$
- Linear combinations of a and b:
  - $3 \cdot 3 - 6 \cdot 5$
  - $4 \cdot 3 + 2 \cdot 5$
  - $-17 \cdot 3 - 18 \cdot 5$
  ]


---
layout: false
.left-column[
## Divisibility
### Greatest Common Divisor (GCD)
]
.right-column[
- The greatest number which divides both terms
- $\text{gcd}(14,7) = 7$
  - $7 \mid 7, 7 \mid 14$
- $\text{gcd}(9, 3) = 3$
- $\text{gcd}(11,0) = 11$
  - $11 \mid 11, 11 \mid 0$
- $\text{gcd}(12, 0) = 12$
- $\text{gcd}(6, 11) = 1$
  - these numbers are called "relatively prime"
- $\text{gcd}(2 \cdot 7 \cdot 3, 2 \cdot 3 \cdot 5)$
  - $2 \cdot 3 = 6$
]


---
layout: false
.left-column[
## Divisibility
### GCD and Integer Linear Combi- nations
]
.right-column[
Theorem: The greatest common divisor of $a$ and $b$ is equal to the smallest positive linear combination of $a$ and $b$.

e.g.: $\text{gcd}(4,8) = 4$
- $-2 \cdot 4 + 1 \cdot 8 = 0$ (not positive)
- $2 \cdot 4 + 1 \cdot 8 = 12$ (not gcd)
- $-1 \cdot 4 + 1 \cdot 8 = 4$ (gcd)
]

---
## GCD and Integer Linear Combination
Proof: By Well Ordering Principle
- Let $m$ := the smallest positive linear combination,
- We will show that $m \leq \text{gcd}(a,b)$ and $m \geq \text{gcd}(a,b)$
- First, prove $\text{gcd}(a,b) \leq m$
- Assume there is an integer $c$ such that $c \mid a$ and $c \mid b$, i.e. $c$ is a common divisor to $a,b$
- Then $c \mid s \cdot a + t \cdot b$
- $\text{gcd}(a,b) \mid s \cdot a + t \cdot b$.
  - since $m$ is also a linear combination of $a,b$
  - thus $\text{gcd}(a,b) \mid m$
  - thus $\text{gcd}(a,b) \leq m \checkmark$ 
---
## GCD and Integer Linear Combination
Now we will show that $\text{gcd}(a,b) \geq m$. We will do this by proving that $m \mid a$ and $m \mid b$, which means that $m$ is a common divisor of $a, b$. This means $m \leq \text{gcd}(a,b)$.

Now we must prove $m \mid a$ 

For any integers $m$ and $a$ we can find $q$ and $r$ using the division theorem
- $a = q \cdot m + r, 0 \leq r \lt m$
- $m = $ a linear combination of a and b
- $m = s_1 \cdot a + t_1 \cdot b$

---
## GCD and Integer Linear Combination
- $m = s_1 \cdot a + t_1 \cdot b$
- $a = (s_1 \cdot a + t_1 \cdot b) \cdot q + r$ AND $0 \leq r \lt m$ 
- = $(s_1 \cdot q \cdot a + t_1 \cdot q \cdot b) + r$ AND $0 \leq r \lt m$
- $r = a - (s_1 \cdot q \cdot a + t_1 \cdot q \cdot b)$ AND $0 \leq r \lt m$
- $r = a - s_1 \cdot q \cdot a - t_1 \cdot q \cdot b$ AND $0 \leq r \lt m$
- $r = a - a(s_1 \cdot q) - b(t_1 \cdot q)$ AND $0 \leq r \lt m$
- $r = a(1 - s_1 \cdot q) - b(t_1 \cdot q)$ AND $0 \leq r \lt m$
- $r = as_2 - bt_2$ AND $0 \leq r \lt m$
- Thus, we have shown $r$ is a linear combination of $a$ and $b$. $m$ is the smallest linear combination of $a$ and $b$, and $r$ is smaller than $m$.
- $0 \leq r \lt m$

---
## GCD and Integer Linear Combination
- $0 \leq r \lt m$
- This is only possible if $r = 0$
- Thus this division has no remainder
- This implies $m \mid a$
- Therefore $m$ is the smallest linear combination. $\square$
---


.left-column[
## GCD
### Properties of the GCD
]
.right-column[
1: Every common divisor of $a$ and $b$ divides $\text{gcd}(a,b)$
- $\text{gcd}(a,b) = s \cdot a + t \cdot b$
- 
i.e. We can write a gcd as a linear combination.  
]
---


.left-column[
## GCD
### Properties of the GCD
]
.right-column[
2: $\text{gcd}(ka, kb) = k \cdot \text{gcd}(a,b)$ for all $k \gt 0$
- $\text{gcd}(a,b) = sa + tb$
- $\text{gcd}(ka,kb) = ksa + ktb$
- $ = k(sa + tb)$
- $ = k \cdot \text{gcd}(a,b)$
]
---


.left-column[
## GCD
### Properties of the GCD
]
.right-column[
3: If $\text{gcd}(a, b) = 1,$ and $\text{gcd}(a,c) = 1,$ then $ \text{gcd}(a,bc) = 1$
- $1 = sa + tb$
- $1 = ua + vc$
- $1 = (sa+tb)(ua+vc)$ for some $s, t, u, v$
- $1 = saua +savc + tbua +tbvc$
- $1 = a(sau + svc + tbv) + (bc)(tv)$
- $1 = as_1 + (bc) t_1$
]
---


.left-column[
## GCD
### Properties of the GCD
]
.right-column[
4: If $a \mid bc$ and $\text{gcd}(a, b) = 1$, then $a \mid c$
- if $\text{gcd}(a,b) = 1$, $a$ and $b$ have no common factors besides $1$.
- thus, the only way $a$ could divide $bc$, is if $a$ divided $c$.
]
---
.left-column[
## GCD
### Properties of the GCD
]
.right-column[
5: $\text{gcd}(a, b) = \text{gcd}(b, \text{rem}(a,b))$
- Using the division theorem:
- $a = qb + r$
- $r = a - qb$
- Any common divisor of $a$ and $b$ would also divide $r$
- $\text{gcd}(a,b) = \text{gcd}(a,r) = \text{gcd}(b,r)$
- This property is known as Euclid's Algorithm
]
---
.left-column[
## GCD
### Euclid's Algorithm
### Example
]
.right-column[
- $\text{gcd}(771,100) = \text{gcd}(100,71)$
- $\text{gcd}(100,71) = \text{gcd}(71, 29)$
- $\text{gcd}(71,29) = \text{gcd}(29,13)$
- $\text{gcd}(29,13) = \text{gcd}(13,3)$
- $\text{gcd}(13,3) = \text{gcd}(3,1)$
- $\text{gcd}(3,1) = \text{gcd}(1,0) = 1$

- Why is this useful? Because we can implement it in code!
- But we can actually take this further!
]
---
.left-column[
## The Die Hard Problem
]
.right-column[
In Die Hard 3, John MacClane must disarm a bomb by placing exactly 4 gallons of water on the scale. He is given only a 5 and 3 gallon jug. 

![](die-hard.png)

We can solve it by trial and error, but is there a systematic approach to solve it?
]
---

## The Die Hard Problem

- Define our system as a state machine
let $a$ be the size of the smaller jug
let $b$ be the size of the larger jug
let $x$ be the number of gallons in the smaller jug
let $y$ be the number of gallons in the larger jug.

- State
$(x,y)$

Operations:

- Emptying
  - $(x,y) \rightarrow (0,y)$
  - $(x,y) \rightarrow (x,0)$

---

## The Die Hard Problem

- Filling
  - $(x,y) \rightarrow (a,y)$
  - $(x,y) \rightarrow (x,b)$

- Pouring:
  - We can pour in either direction
  - Two situations
    - in one, we pour all the contents of one jug to the other
    - in the other we pour some of the contents to the other jug and some remains

---
## The Die Hard Problem

- $(x,y) \rightarrow (0, x+y), x+y \leq b$
- $(x,y) \rightarrow (x-(b-y)), b) = (x+y-b),b); x+y \geq b$
- $(x,y) \rightarrow (x+y, 0), x+t \leq a$
- $(x,y) \rightarrow (a, x+y-a), x+y \geq a$

Solution, using these operations

- $a=3, b=5, (0,0)$

- $(0,0) \rightarrow (0,5) \rightarrow (3,2) \rightarrow (0,2) \rightarrow (2,0)$
- $(2,0) \rightarrow (2,5) \rightarrow (3,4)\rightarrow (0,4)$. done.
---
### What if...
- The mastermind genius villain was having an off day, and instead gave a 3 gallon and a 6 gallon jug. Could we still make 4 gallons?
- No...
- Why?
  - We can only make 0, 3, 6.
  - How can we investigate further?
---
### Exploring the System
- What do we know about this system? Do we have an invariant?
- Lemma: The amount of water in each jug is a linear combination of the capacities of each jug
  - We could prove this by cases 
    - show each operation can be broken down into $sa+tb$.
- Theorem: The $\text{gcd}(a,b)$ is equal to the smallest positive linear combination of $a$ and $b$. (From the Text)
- Theorem: An integer is a linear combination of $a, b$ iff it is a multiple of $\text{gcd}(a,b)$
  - $\text{gcd}(a,b) = sa + tb$
  - $k \text{gcd}(a,b) = ksa + ktb$
---
### Consequence
This means that...
- $\text{gcd}(3,5) = 1$
- $4 = 1 \cdot 4 = 2 \cdot 5 - 2 \cdot 3 \checkmark$
  
Vs...

- $\text{gcd}(3,6) = 3$
- $4 = 3 \cdot ??? \times$

Take away: as long as the GCD between two numbers is 1, any number can be made as a linear combination of them!
---
### The Extended Euclidean Algorithm (Pulverizer)
It would be nice if there was a way to reliably calculate the s,t in the equations:
$\text{gcd}(a,b) = sa+tb$
- In particular, the lowest combination.
- e.g. computer the gcd(220, 41)

---
### Pulverizer Algorithm
- Rewrite the GCD so the larger number is first, and call these $x, y, x > y$
- compute $x / y$, keeping track of quotient, $q$, remainder, $r$
- multiply through $y$ such that $x = q \cdot y + r$ 
- rearrange into $r = s \cdot x + t \cdot q$
  - If needed, re-write this in terms of the original $x,y$ using previously computed values
  - Recurse, such that $x \leftarrow y$, $y \leftarrow r$ (This part is just Euclid's)

Let's do an example!
- e.g. compute s, t, such that $gcd(220, 41) = s \cdot 220 + t \cdot 41$

---

|$x$|$y$|$x/y$|$r=x-q \cdot y$|
|---|---|---|---|
|$220$|$41$|$5 r 15$ |$15 = 220 - 5 \cdot 41$|
|$41$|$15$|$2 r 11$ |$11 = 41 - 2 \cdot 15$|
|    |    | |$11 = 41 - 2 \cdot (220 - 5 \cdot 41)$|
|    |    | |$11 = -2 \cdot 220 + 11 \cdot 41 $|
|$15$|$11$|$1 r 4$ |$4 = 15 - 1 \cdot 11$|
| |  || $4 = (220 - 5 \cdot 41) - 1 \cdot (-2 \cdot 220 + 11 \cdot 41)$|
| |  || $4 = 3 \cdot 220 - 16 \cdot 41$|
|$11$|$4$|$2 r 3$|$3 = 11 - 2 \cdot 4$|
|||| $3 = (-2 \cdot 220 + 11 \cdot 41) - 2 \cdot (3 \cdot 220 - 16 \cdot 41)$|
|||| $3 = -8 \cdot 220 + 43 \cdot 41$|
|$4$|$3$ |$1 r 1$| $1 = 4 - 1 \cdot 3$|
|||| $1 = (3 \cdot 220 - 16 \cdot 41) - 1 \cdot (-8 \cdot 220 + 43 \cdot 41)$|
|||| $1 = 11 \cdot 220 - 59 \cdot 41$|


---
### References

- Dr. Abdul Bais's ENSE 350 Slides
- Tom Leighton, and Marten Dijk. 6.042J Mathematics for Computer Science. Fall 2010, Lecture 4. Massachusetts Institute of Technology: MIT OpenCourseWare, https://ocw.mit.edu. License: Creative Commons BY-NC-SA.
---

name: inverse
layout: true
class: center, middle, inverse
---
# Questions?
