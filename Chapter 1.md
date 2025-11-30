Probability Review
*Note*: Surya likes using $p$ for pmf and pdf. I will use it in his exams, but stick to $f$ elsewhere.
## 1.1 Definitions
### 1.1.1 *Probability space*
**Def** Sample space
The set, $\Omega$, of all possible outcomes of a particular experiment is called the *sample space* of the experiment. 

**Def** Event space
An *event* is any collection of possible outcomes of an experiment, that is, any subset of $\Omega$. A collection $\mathscr{E}$ of events is called an event space. 

**Def** Probability space
The triple of $\Omega$, $\mathscr{E}$, and a probability function $\mathbb{P}: \mathscr{E}\rightarrow \mathbb{R}$ (defined after sigma algebra) is called a probability space.
### 1.1.2 $\sigma$-*algebra* (1.3 merged in)
**Def** Sigma algebra
A collection of subsets of $S$ is called a *sigma algebra* (or *Borel field*), denoted by $\mathcal{B}$, if it satisfies the following three properties:
(a) $\varnothing \in \mathcal{B}$ (the empty set is an element of $\mathcal{B}$)
(b) If $A\in \mathcal{B}$, then $A^c\in \mathcal{B}$. ($\mathcal{B}$ is closed under complementation)
(c) If $A_1, A_2, \dots \in \mathcal{B}$, then $\bigcup_{i=1}^\infty A_i\in \mathcal{B}$. ($\mathcal{B}$ is closed under countable unions)

The event space *is* a sigma algebra, as it satisfies:
(a) Trivial.
(b) If $A\in \mathscr{E}$, then $A^c = \Omega\backslash A\in \mathscr{E}$.
(c) If $A_1, A_2, \dots \in \mathscr{E}$, then $A_1\cup A_2 \cup \dots \in \mathscr{E}$. 
Conditions (b) and (c) further implies that if $A_1, A_2, \dots \in \mathscr{E}$, then $A_1\cap A_2\cap \dots \in \mathscr{E}$. 

**Def** Probability function; Axioms of probability/Kolmogorov Axioms
Given a sample space $\Omega$ and an associated sigma algebra $\mathscr{E}$, a *probability function* is a function $\mathbb{P}$ with domain $\mathscr{E}$ that satisfies:
(a) $\mathbb{P}(A)\ge 0$, $\forall A\in \mathscr{E}$.
(b) $\mathbb{P}(\Omega) = 1$. 
(c) If $A_1, A_2, \dots \in \mathscr{E}$ are pairwise disjoint, then $$\mathbb{P}\left(\bigcup_{i=1}^\infty A_i\right) = \sum_{i=1}^\infty \mathbb{P}(A_i)$$
**Thm** Discrete function pmf
Let $S = \{s_1, \dots, s_n\}$ be a finite set. Let $\mathcal{B}$ be any sigma algebra of subsets of $S$. Let $p_1, \dots, p_n$ be nonnegative numbers that sum to 1. For any $A\in \mathcal{B}$, define $\mathbb{P}(A)$ by $$\mathbb{P}(A) = \sum_{\{i:s_i\in A\}}p_i.$$ The sum over an empty set is defined to be 0. Then $\mathbb{P}$ is a probability function on $\mathcal{B}$. This remains true if $S = \{s_1, s_2, \dots\}$ is a countable set.

Similarly, we can have a definition of continuous function PDF:

Let $S$ be a sample space (typically $S = \mathbb{R}$ or an interval within $\mathbb{R}$). Let $\mathcal{B}$ be a sigma-algebra of subsets of $S$ (typically the Borel sigma-algebra). Let $f: S \to \mathbb{R}$ be a function satisfying the following properties:
1. $f(x) \geq 0$ for all $x \in S$.
2. $\int_S f(x) \, dx = 1$.

For any event $A \in \mathcal{B}$, define $\mathbb{P}(A)$ by
$$\mathbb{P}(A) = \int_A f(x) \, dx.$$
Then $\mathbb{P}$ is a probability function on $\mathcal{B}$, and $f(x)$ is called the probability density function (pdf) of the distribution.

The lecture notes $\S$ 1.3.3 also proposed the following definition of the probability map for a product space:

Let the sample space be the product space $S = S_1 \times S_2$, where $S_1$ is a countable set (discrete support, e.g., $\mathbb{Z}$) and $S_2$ is a continuous space (e.g., $\mathbb{R}$).

Let $p(\mathbf{x}, \mathbf{y})$ be a function defined on $S$ such that $p(\mathbf{x}, \mathbf{y}) = p(\mathbf{x})p(\mathbf{y}|\mathbf{x})$, satisfying:
1. $p(\mathbf{x}, \mathbf{y}) \geq 0$ for all pairs.
2. $\sum_{\mathbf{x} \in S_1} \int_{S_2} p(\mathbf{x}, \mathbf{y}) \, d\mathbf{y} = 1$.

For any event $E$ of the form $A \times B$ (where $A \subseteq S_1$ and $B \subseteq S_2$), define $\mathbb{P}(E)$ by: $$\mathbb{P}(A \times B) = \sum_{\mathbf{x} \in A} \left( \int_{B} p(\mathbf{x}, \mathbf{y}) \, d\mathbf{y} \right)$$
Then $\mathbb{P}$ is a probability map on the product space.

Read C&B 1.2.2 - 1.2.4 for some extra tools dealing with probability. 

**Example** A quick refresher of the counting: NY state lottery (6 numbers out of 44)
1. Ordered, without replacement
$$\text{Total number of possible tickets} = \frac{44!}{38!} = 44\times 43\times 42\times 41\times 40\times 39 = 5,082,517,440$$
2. Ordered, with replacement
$$\text{Total number of possible tickets} = 44^6 = 7,256,313,856$$
3. Unordered, without replacement
$$\text{Total number of possible tickets} = \frac{44!}{6!38!} = 7,059,052$$
4. Unordered, with replacement (43 walls and 6 markers)
$$\text{Total number of possible tickets} = \frac{49!}{6!43!} = 13,983,816$$
A summary ($r$ numbers out of $n$)

|           | Without Replacement                  | With Replacement                         |
|-----------|--------------------------------------|------------------------------------------|
| Ordered   | $\frac{n!}{(n-r)!}$                  | $n^r$                                    |
| Unordered | $\begin{pmatrix} n\\r \end{pmatrix}$ | $\begin{pmatrix} n+r-1\\r \end{pmatrix}$ |
### 1.1.3 *Conditioning and Independence*
**Def** Conditional probability
If $A$ and $B$ are events in $\Omega$, and $\mathbb{P}(B)>0$, then the *conditional probability* of $A$ given $B$, written as $\mathbb{P}(A\mid B)$, is $$\mathbb{P}(A\mid B) = \frac{\mathbb{P}(A\cap B)}{\mathbb{P}(B)}$$
**Example** Three Prisoners *(See also: Exercise 1, Chapter 2, Monty Hall)*
Let $A$, $B$, and $C$ be the events that the respective prisoner is pardoned. Since the governor chooses at random, the prior probabilities are: $$P(A) = P(B) = P(C) = \frac{1}{3}$$
Let $W$ be the event that the warden says, "Prisoner B will be executed."

The warden observes who is pardoned and follows a specific set of rules to determine his statement $W$:
- If B is pardoned ($B$ occurs): The warden cannot say "B will be executed." $$P(\mathcal{W}|B) = 0$$
- If C is pardoned ($C$ occurs): The warden cannot say "C" (because that is the pardoned one) and cannot say "A" (because he cannot speak to A about A's fate). He is forced to say B. $$P(\mathcal{W}|C) = 1$$
- If A is pardoned ($A$ occurs): The warden can say either "B" or "C" will be executed. The text assumes he chooses freely between them with equal probability. $$P(\mathcal{W}|A) = \frac{1}{2}$$
*Warden's Reasoning*: Each prisoner has an equal chance (1/3) of being pardoned. Either B or C will be executed, so I have given A no information about whether A will be pardoned.

*A's Reasoning*: Given that B will be executed, then either A or C will be pardoned. My chance of being pardoned has risen to 1/2. 

We will see that warden's reasoning is correct. What will happen here:

| Prisoner pardoned | Who dies according to the warden |
| ----------------- | -------------------------------- |
| A                 | B                                |
| A                 | C                                |
| B                 | C                                |
| C                 | B                                |
WLOG, assume that the warden says B will die. Then, we want to calculate the probability of A being pardoned, conditioned on B will die. $$\mathbb{P}(A\mid \mathcal{W}) = \frac{\mathbb{P}(A\cap\mathcal{W})}{\mathbb{P}(\mathcal{W})}$$ where $\mathcal{W}$ is the event that B will die. When A is pardoned, the warden will say either B or C dies, each with equal probability. The probability of A being pardoned and B being executed is 
$$\mathbb{P}(A\cap \mathcal{W}) = \frac{1}{3}\times\frac{1}{2} = \frac{1}{6}$$

Although I may appear to use the law of total expectation, I am just reading off the table: $$\begin{align*}\mathbb{P}(\mathcal{W}) &= \mathbb{P}(\text{B dies and A pardoned}) + \mathbb{P}(\text{B dies and B pardoned}) + \mathbb{P}(\text{B dies and C pardoned})\\ &= \frac{1}{3}\times \frac{1}{2} + 0 + \frac{1}{3}\\ &= \frac{1}{2}\end{align*}$$
Therefore, $$\mathbb{P}(A\mid \mathcal{W}) = \frac{1/6}{1/2} = \frac{1}{3}$$
**Def** Independence
Two events, $A$ and $B$, are *statistically independent* if $$\mathbb{P}(A\cap B) = \mathbb{P}(A)\mathbb{P}(B)$$
### 1.1.5 *Conditional Independence*
**Def**
Two events, $A$ and $B$, are *conditionally independent* given $C$ if $$\mathbb{P}(A\cap B\mid C) = \mathbb{P}(A\mid C)\mathbb{P}(B\mid C)$$
## 1.2 *Probability Calculus*
**Thm** If $\mathbb{P}$ is a probability function and $A$ is any set in $\mathcal{B}$, then
(a) (Null event) $\mathbb{P}(\varnothing)=0$
(b) (Complementation) $\mathbb{P}(A^c) = 1-\mathbb{P}(A)$

**Thm** If $\mathbb{P}$ is a probability function and $A$ and $B$ are any sets in $\mathcal{B}$, then
(a) $\mathbb{P}(B\cap A^c) = \mathbb{P}(B)-\mathbb{P}(A\cap B)$
(b) $\mathbb{P}(A\cup B) = \mathbb{P}(A) + \mathbb{P}(B) - \mathbb{P}(A\cap B)$
(c) If $A\subset B$, then $\mathbb{P}(A)\le \mathbb{P}(B)$

Additional conclusions:
(a) If $\mathbb{P}$ is a probability function and $A_i$ are any sets in $\mathcal{B}$, then $\mathbb{P}(A_1 \cap A_2 \cap A_3\cdots) = \mathbb{P}(A_1)\mathbb{P}(A_2\mid A_1) \mathbb{P}(A_3\mid A_2\cap A_1)\cdots$

**Thm** If $\mathbb{P}$ is a probability function, then
(a) $\mathbb{P}(A) = \sum_{i=1}^\infty \mathbb{P}(A\cap C_i)$ for any partition $C_1, C_2, \cdots$. 
(b) $\mathbb{P}(\bigcup_{i=1}^\infty A_i)\le \sum_{i=1}^\infty \mathbb{P}(A_i)$ for any sets $A_1, A_2, \cdots$. 
*Note*: (a) is equivalent to **the law of total probability**, which says $$\mathbb{P}(A) = \sum_{i=1}^\infty \mathbb{P}(A\mid C_i)\mathbb{P}(C_i)$$
(b) assumes the equality when $A_i$ are disjoint sets.

**Thm** Bayes' Rule
Let $A_1, A_2, \dots$ be a partition of the sample space, and let $B$ be any set. Then, for each $i = 1, 2, \dots$, $$\mathbb{P}(A_i\mid B) = \frac{\mathbb{P}(B\mid A_i)\mathbb{P}(A_i)}{\sum_{j=1}^\infty \mathbb{P}(B\mid A_j)\mathbb{P}(A_j)}$$
## 1.4 *Random Variables*
A *random variable* $Y$ is any function $Y: \Omega\rightarrow \mathbb{R}$ such that $\{Y<a\}\in \mathscr{E}$ for every $a\in \mathbb{R}$.  

### 1.4.1 *Probability Law*
*Note*: The lecture notes $\S$ 1.4 provides a generalized definition of C&B $\S$ 
**Def** Probability Law
Let $Y$ be any random variable on a probability space $(\Omega, \mathscr{E}, \mathbb{P})$. Then, the probability map $\mathbb{P}_Y$ is given by: $$\mathbb{P}_Y(B) = \mathbb{P}(Y\in B),$$ where $B\in \mathscr{B}$ (a sigma algebra typically used when $\Omega = \mathbb{R}$). Then, we call $\mathbb{P}_Y$ a *probability law* of $Y$.  

### 1.4.2 *Joint Probability Law*
*Refer to C&B $\S$ 4.1*
**Def** An *n-dimensional random vector* is a function from a sample space $\Omega$ into $\mathbb{R}^n$, n-dimensional Euclidean space.

*Note*: Before, we discuss the probability space $(\mathbb{R}, \mathscr{B}, \mathbb{P}_Y)$. Name the random vector $\mathbf{Y}$. In this way, a random vector defines a new probability map $\mathbb{P}_\mathbf{Y} = \mathbb{P}(\mathbf{Y}\in B), B\in \mathscr{B}_d$. Now, we form a new probability space $(\mathbb{R}^d, \mathscr{B}_d, \mathbb{P}_\mathbf{Y})$. 

**Def** Joint PMF
Let $(X,Y)$ be a discrete bivariate random vector. Then the function $f_{X,Y}(x,y)$ from $\mathbb{R}^2$ to $\mathbb{R}$ defined by $f_{X,Y}(x,y) = \mathbb{P}(X=x,Y=y)$ is the joint pmf of $(X,Y)$.  This definition can be extended to other dimensions.

**Thm** Marginalization of joint PMF
Let $(X,Y)$ be a discrete bivariate random vector with joint pmf $f_{X,Y}(x,y)$. Then, the marginal pmfs of $X$ and $Y$, $f_X(x) = \mathbb{P}(X=x)$ and $f_Y(y) = \mathbb{P}(Y=y)$, are given by $$f_X(x) = \sum_{y\in \mathbb{R}}f_{X,Y}(x,y)\quad \text{and} \quad f_Y(y) = \sum_{x\in \mathbb{R}}f_{X,Y}(x,y).$$
**Def** Joint PDF
A function $f_{X,Y}(x,y)$ from $\mathbb{R}^2$ to $\mathbb{R}$ is called a joint pdf of the continuous bivariate random vector $(X,Y)$ if, for every $A\subset \mathbb{R}^2$, $$\mathbb{P}((X,Y)\in A) = \int\int_A f_{X,Y}(x,y)\,dx\,dy$$
**Thm** Marginalization of joint PDF
Let $(X,Y)$ be a continuous bivariate random vector with joint pdf $f_{X,Y}(x,y)$. Then, the marginal pdfs of $X$ and $Y$ are given by $$f_X(x) = \int_\mathbb{R}f_{X,Y}(x,y)\,dy\quad \text{and} \quad f_Y(y) = \int_\mathbb{R}f_{X,Y}(x,y)\,dx$$
(Read: Examples 4.1.2, 4.1.4, 4.1.5, 4.1.7, 4.1.8, 4.1.9 \[discrete\], 4.1.11, 4.1.12 \[continuous\]).

### 1.4.4 *Conditional Law*
**Def** Conditional PMF
Let $(X,Y)$ be a discrete bivariate random vector with joint pmf $f_{X,Y}(x,y)$ with marginal pmfs $f_X(x)$ and $f_Y(y)$. For any $x$ such that $\mathbb{P}(X=x) = f_X(x)>0$, the *conditional pmf* of $Y$ given $X=x$ is the function of $y$ denoted by $f_{Y\mid X}(y\mid x)$ and defined by $$f_{Y\mid X}(y\mid x) = \mathbb{P}(Y=y\mid X=x) = \frac{f_{X,Y}(x,y)}{f_X(x)}$$
For any $y$ such that $\mathbb{P}(Y=y) = f_Y(y)>0$, the *conditional pmf* of $X$ given $Y=y$ is the function of $x$ denoted by $f_{X\mid Y}(x\mid y)$ and defined by $$f_{X\mid Y}(x\mid y) = \mathbb{P}(Y=y\mid X=x) = \frac{f_{X,Y}(x,y)}{f_Y(y)}$$
**Def** Conditional PDF
Let $(X,Y)$ be a continuous bivariate random vector with joint pmf $f_{X,Y}(x,y)$ with marginal pmfs $f_X(x)$ and $f_Y(y)$. For any $x$ such that $f_X(x)>0$, the *conditional pdf* of $Y$ given $X=x$ is the function of $y$ denoted by $f_{Y\mid X}(y\mid x)$ and defined by $$f_{Y\mid X}(y\mid x) = \frac{f_{X,Y}(x,y)}{f_X(x)}$$
For any $y$ such that $f_Y(y)>0$, the *conditional pdf* of $X$ given $Y=y$ is the function of $x$ denoted by $f_{X\mid Y}(x\mid y)$ and defined by $$f_{X\mid Y}(x\mid y) = \frac{f_{X,Y}(x,y)}{f_Y(y)}$$
*Note*: Taking the above definition by the word, we will run into trouble because for a continuous random variable $X$, the density of $X$ at a particular $x$ is zero. This is what is called *Borel Paradox*. In the lecture notes $\S$ 1.4.4, Surya proposes to relax the condition $X=x$ to $X\in [x,x+\Delta]$ for $\Delta>0$ and take limit $\Delta\rightarrow 0$. $$\mathbb{P}_Y(B\mid X=x) = \lim_{\Delta\rightarrow 0}\mathbb{P}_Y(B\mid X\in [x,x+\Delta]), B\in \mathscr{B}$$
C&B proposes to take a sequence $B_n\rightarrow x$, and define $$\mathbb{P}_Y(Y\mid X=x) = \lim_{n\rightarrow \infty}\mathbb{P}_Y(Y\mid X\in B_n)$$
### 1.4.5 *Chaining, Total Law, and Bayes Rule*
Chaining rule of random variables: Suppose $\mathbf{X}$ is a $d_1$-dimensional random vector, $\mathbf{Y}$ is a $d_2$-dimensional random vector, then $$f_{\mathbf{X}, \mathbf{Y}}(\mathbf{x}, \mathbf{y}) = f_\mathbf{X}(\mathbf{x})f_\mathbf{Y}(\mathbf{y}\mid \mathbf{X} = \mathbf{x}), \quad \mathbf{x}\in \mathbb{R}^{d_1}, \mathbf{y}\in \mathbb{R}^{d_2}$$
Law of total probability:
The chaining rule, with marginalization specified above, enables a way to remove condition:
$$f_\mathbf{Y}(\mathbf{y}) = \int_{\mathbb{R}^{d_1}}f_\mathbf{X}(\mathbf{x})f_\mathbf{Y}(\mathbf{y}\mid \mathbf{X} = \mathbf{x})\, d\mathbf{x}$$
Bayes' rule:
Put the above identity into Bayes' theorem, $$f_\mathbf{X}(\mathbf{x}\mid \mathbf{Y} = \mathbf{y}) = \frac{f_\mathbf{X}(\mathbf{x})f_\mathbf{Y}(\mathbf{y}\mid \mathbf{X} = \mathbf{x})}{\int_{\mathbb{R}^{d_1}}f_\mathbf{X}(\mathbf{x})f_\mathbf{Y}(\mathbf{y}\mid \mathbf{X} = \mathbf{x})\, d\mathbf{x}}$$
### 1.4.6 *Checking Independence*
**Def** Independence
Let $(X,Y)$ be a bivariate random vector with joint pdf or pmf $f_{X,Y}(x,y)$ and marginal pdfs or pmfs $f_X(x)$ and $f_Y(y)$. Then $X$ and $Y$ are called *independent random variables* if, for every $x\in \mathbb{R}$ and $y\in \mathbb{R}$, $$f_{X,Y}(x,y) = f_X(x)f_Y(y)$$
If $X$ and $Y$ are independent, then the conditional pdf of $Y$ given $X=x$ is $$\begin{align*}f_Y(y\mid x) &= \frac{f_{X,Y}(x,y)}{f_X(x)}\\ &= \frac{f_X(x)f_Y(y)}{f_X(x)}\\ &= f_Y(y)\end{align*}$$
Same for the conditional pdf of $X$ given $Y = y$. 

It is very tedious to directly use the definition to verify the independence of $X$ and $Y$, because it requires the knowledge of the explicit form of three probability laws. Here is a lemma (C&B 4.2.7):
**Lemma** Let $(X,Y)$ be a bivariate random vector with joint pdf or pmf $f_{X,Y}(x,y)$. Then $X$ and $Y$ are independent random variables if and only if there exists functions $g(x)$ and $h(y)$ such that, for every $x\in \mathbb{R}$ and $y\in \mathbb{R}$, $$f(x,y) = g(x)h(y)$$
## 1.5 *Change of Variable*
*Case of univariate transformations, according to C&B 2.1*

**Thm** CDF method, C&B 2.1.3
Let $X$ have cdf $F_X(x)$, let $Y = g(X)$, and let $\mathcal{X}$ and $\mathcal{Y}$ be defined by $$\mathcal{X} = \{x:f_X(x)>0\} \quad \text{and} \quad \mathcal{Y} = \{y:y = g(x)\text{ for some }x\in \mathcal{X}\}$$ 
(a) If $g$ is an increasing function on $\mathcal{X}$, $F_Y(y) = F_X(g^{-1}(y))$ for $y\in\mathcal{Y}$.
(b) If $g$ is a decreasing function on $\mathcal{X}$ and $X$ is a continuous random variable, $F_Y(y) = 1 - F_X(g^{-1}(y))$ for $y\in \mathcal{Y}$. 

**Thm** In the lecture notes $\S$ 1.5, or C&B 2.1.5
Let $X$ have pdf $f_X(x)$ and let $Y = g(X)$, where $g$ is a monotone function. Let $\mathcal{X}$ and $\mathcal{Y}$ be defined by $$\mathcal{X} = \{x:f_X(x)>0\} \quad \text{and} \quad \mathcal{Y} = \{y:y = g(x)\text{ for some }x\in \mathcal{X}\}$$
Suppose that $f_X(x)$ is continuous on $\mathcal{X}$ and that $g^{-1}(y)$ has a continuous derivative on $\mathcal{Y}$. Then the pdf of $Y$ is given by $$f_Y(y) = \begin{cases}f_X(g^{-1}(y))\left\lvert\frac{d}{dy}g^{-1}(y)\right\rvert & y\in \mathcal{Y}\\ 0 & \text{otherwise.} \end{cases}$$
*Note*: This theorem is derived from 2.1.3.

**Thm** What if the function is not globally invertible? C&B 2.1.8
Let $X$ have pdf $f_X(x)$, let $Y = g(X)$, and define the sample space $\mathcal{X}$ as $$\mathcal{X} = \{x:f_X(x)>0\}$$
Suppose there exists a partition, $A_0, A_1, \dots, A_k$ of $\mathcal{X}$ such that $\mathbb{P}(X\in A_0) = 0$ and $f_X(x)$ is continuous on each $A_i$. Further, suppose there exist functions $g_1(x), \dots, g_k(x)$, defined on $A_1, \dots, A_k$, respectively, satisfying 
(a) $g(x) = g_i(x)$, for $x\in A_i$,
(b) $g_i(x)$ is monotone on $A_i$,
(c) the set $\mathcal{Y} = \{y:y = g_i(x)\text{ for some }x\in A_i\}$ is hte same for each $i = 1, \dots, k$, 
(d) $g^{-1}_i(y)$ has a continuous derivative on $\mathcal{Y}$, for each $i = 1, \dots, k$.

Then $$f_Y(y) = \begin{cases}\sum_{i=1}^k f_X(g_i^{-1}(y))\left\lvert \frac{d}{dy}g_i^{-1}(y) \right\rvert & y\in \mathcal{Y} \\0 & \text{otherwise.} \end{cases}$$
In C&B $\S$ 4.3, this definiton has been extended to bivariate change-of-variable transformations. Let $(X,Y)$ be a continuous random vector with joint pdf $f_{X,Y}(x,y)$, then we can try to express the joint pdf of the random vector $(U,V)$ with $f_{X,Y}(x,y)$. Let $$\mathcal{A} = \{(x,y):f_{X,Y}(x,y)>0\} \quad \text{and} \quad \mathcal{B} = \{(u,v): u=g_1(x,y), v=g_2(x,y)\}$$
Assuming the transformation $u = g_1(x,y), v=g_2(x,y)$ is a injective transformation $\mathcal{A}\rightarrow \mathcal{B}$. By the definition of $\mathcal{B}$, this transformation is also surjective. Then, this transformation is bijective and hence invertible. There exists $h_1,h_2$ such that $x = h_1(u,v), y = h_2(u,v)$. We need a *Jacobian of the transformation* in place of the derivative in the univariate case. $$|\mathbf{J}|=\begin{vmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\
\frac{\partial y}{\partial u} & \frac{\partial y}{\partial v}\end{vmatrix} = \begin{vmatrix}
\frac{\partial h_1(u,v)}{\partial u} & \frac{\partial h_1(u,v)}{\partial v} \\
\frac{\partial h_2(u,v)}{\partial u} & \frac{\partial h_2(u,v)}{\partial v}
\end{vmatrix}$$
Then, $$f_{U,V}(u,v) = f_{X,Y}(h_1(u,v), h_2(u,v))|\mathbf{J}|$$
This definition can be extended to multivariate transformation (I will ditch the way to define this in the lecture note, as it is not consistent with the univariate and bivariate cases): Suppose $\mathbf{Y}$ is a continuous random vector with a joint pdf $f_\mathbf{Y}(\mathbf{y})$. We want to express the joint pdf of the random vector $\mathbf{W}$ with $f_\mathbf{Y}(\mathbf{y})$. Again, let $$\mathcal{A} = \{\mathbf{y}:f_\mathbf{Y}(\mathbf{y})>0\}\subset \mathbb{R}^d \quad \text{and} \quad \mathcal{B} = \{\mathbf{w}: \mathbf{w} = \mathbf{g}(\mathbf{y})\}\subset \mathbb{R}^k$$
With the aforementioned argument, it only takes a small assumption, that $\mathbf{g}:\mathcal{A}\rightarrow\mathcal{B}$ is injective, to guarantee the existence of the inverse of $\mathbf{g}$, denoted as $\mathbf{h}$ (notice the dimension change is actually $\mathbf{h}: \mathbb{R}^k\rightarrow \mathbb{R}^d$). $$\lvert \mathbf{J} \rvert = \begin{vmatrix}
\frac{\partial h_1(\mathbf{w})}{\partial w_1} & \frac{\partial h_1(\mathbf{w})}{\partial w_2} & \cdots & \frac{\partial h_d(\mathbf{w})}{\partial w_k}\\
\vdots & \vdots & \ddots & \vdots\\
\frac{\partial h_d(\mathbf{w})}{\partial w_1} & \frac{\partial h_d(\mathbf{w})}{\partial w_2} & \cdots & \frac{\partial h_d(\mathbf{w})}{\partial w_k}
\end{vmatrix}$$
$$f_\mathbf{W}(\mathbf{w}) = f_\mathbf{Y}(\mathbf{h}(\mathbf{w}))\cdot |\mathbf{J}|$$
## 1.6 Expectation
**Def** The *expected value* aka *mean* of a random variable $g(X)$, denoted by $\mathbb{E}(g(X))$, is $$\mathbb{E}(g(X)) = \begin{cases}
\int_\mathbb{R}g(x)f_X(x)\,dx & \text{if }X\text{ is continuous}\\
\sum_{x\in \mathcal{X}}g(x)f_X(x) = \sum_{x\in \mathcal{X}}g(x)\mathbb{P}(X=x) & \text{if }X\text{ is discrete}
\end{cases}$$
**Thm** Fundamental properties of expected value
Let $X$ be a random variable and let $a,b,$ and $c$ be constants. Then for any functions $g_1(x)$ and $g_2(x)$ whose expectations exist
(a) $\mathbb{E}(ag_1(X) + bg_2(X) + c) = a\mathbb{E}(g_1(X)) + b\mathbb{E}(g_2(X)) + c$.
(b) If $g_1(x)\ge 0$ for all $x$, then $\mathbb{E}(g_1(X))\ge 0$. 
(c) If $g_1(x)\ge g_2(x)$ for all $x$, then $\mathbb{E}(g_1(X))\ge \mathbb{E}(g_2(X))$.
(d) If $a\le g_1(x) \le b$ for all $x$, then $a\le \mathbb{E}(g_1(X)) \le b$.

With additional properties in the lecture notes:
(e) If $\mathbb{E}(Y^2) <\infty$, then $\mathbb{E}[(Y-a)^2]$ is minimized at $a=\mathbb{E}(Y)$. 
(f) (Markov) $\mathbb{P}(|Y|>t)\le \mathbb{E}(|Y|)/t$ for every $t>0$. 
*Proof*: Let $I$ be the indicator function of the event $|Y|>t$. $$I = \mathbb{1}_{|Y|>t} = \begin{cases}
0 & \text{if }|Y|\le t\\
1 & \text{if }|Y|>t.
\end{cases}$$
If $|Y|>t$, then $I=1$. $$\frac{|Y|}{t} >1 = I.$$
If $|Y|\le t$, then $I=0$. Since $|Y|\ge 0, t>0$, $$\frac{|Y|}{t}\ge 0 = I$$
Therefore, $$\frac{|Y|}{t}\ge I$$ holds for all cases. Now, we can take the expectation, then $$\mathbb{E}\left(\frac{|Y|}{t}\right)\ge \mathbb{E}(I)$$
As $t$ is a constant, we can pull it out of the expectation. Also notice that $\mathbb{E}(I) = \mathbb{P}(|Y|>t)$. Therefore, we obtain
$$\frac{\mathbb{E}(|Y|)}{t}\ge \mathbb{P}(|Y|>t)$$

(g) (Jensen) If $h(x)$ is convex then $\mathbb{E}(h(X))\ge h(\mathbb{E}(X))$. 
*Proof*: If $h(x)$ is convex, $\forall x_0$ at which $h(x)$ is well-defined, $\exists a\in \mathbb{R}$, $$h(x)\ge h(x_0) + a(x-x_0)$$
Now, set $x_0 = \mathbb{E}(X)$, we have $$h(x)\ge h(\mathbb{E}(X))+a(x-\mathbb{E}(X))$$
As this inequality holds for every $x$ in the domain of $h$, $$h(X)\ge h(\mathbb{E}(X))+a(X - \mathbb{E}(X))$$
Take the expectation, $$\mathbb{E}(h(X))\ge \mathbb{E}(h(\mathbb{E}(X)))+ \mathbb{E}(a(X- \mathbb{E}(X)))$$
$$\mathbb{E}(h(X))\ge h(\mathbb{E}(X)) + a(\mathbb{E}(X) - \mathbb{E}(X))$$
$$\mathbb{E}(h(X))\ge h(\mathbb{E}(X))$$