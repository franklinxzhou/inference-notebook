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
## Worked Out Example: Multinomial distribution
(Slide 2, Week 1) Suppose 30 US employees in food and beverage are randomly selected from the population with replacement and $\mathbf{X} = (X_1, \dots, X_6)$ denotes the category counts of their industry types. $$\mathbf{X}\sim \operatorname{Mult}(30, \mathbf{p})$$
where $\mathbf{p} = (0.31, 0.15, 0.12, 0.09, 0.09, 0.24)\in \Delta^5$. *Note* on the notation: $\Delta^d = \{(p_1, \dots, p_{d+1})\in \mathbb{R}^{d+1}: p_i\ge 0, p_1 + \dots + p_{d+1}=1\}$.

Surya made a couple of points about the multinomial distribution:
- Each sum of categories (super-category) count is binomial: e.g., $X_1\sim \operatorname{Binomial}(30, 0.31)$ and $X_1+X_5\sim \operatorname{Binomial}(30,0.4)$
- *Distinct* super-categories and remaining categories are multinomial: e.g., $(X_1 + X_5, X_2 + X_3 + X_4, X_6)\sim \operatorname{Mult}(30, (0.4, 0.36, 0.24))$
- Conditioned on a category/super-category count, remaining categories follow conditional multinomial rules: e.g., $(X_2+X_4, X_3+X_6)\mid (X_1 + X_5 = 10)\sim \operatorname{Mult}(20, \frac{0.15+0.09, 0.12+0.24}{0.6})$

*Proof*: 
**Marginal pmf of individual, e.g., $X_1$**
Given the joint pmf of $\mathbf{X}\sim \operatorname{Mult}(n, \mathbf{p})$ is $$p(\mathbf{x}) = \begin{pmatrix} n \\ x_1, \dots, x_d \end{pmatrix}\cdot p_1^{x_1}\dots p_d^{x_d}\cdot \mathbb{I}_{\mathbf{x}\in \mathscr{C}_{n,d}} = \frac{n!}{x_1!x_2!\cdots x_d!}\cdot p_1^{x_1}\dots p_d^{x_d}\cdot \mathbb{I}_{\mathbf{x}\in \mathscr{C}_{n,d}}$$
To find the marginal pmf of $X_1$,
$$\begin{align*}
p_{X_1}(x_1) &= \sum_{(x_2, \dots, x_d)\in \mathscr{C}_{n-x_1,d-1}} p(x_1, x_2, \dots, p_d)\\
&= \sum_{(x_2, \dots, x_d)\in \mathscr{C}_{n-x_1,d-1}}\frac{n!}{x_1!x_2!\cdots x_d!}p_1^{x_1}p_2^{x_2}\cdots p_d^{x_d}\\
&= \frac{n!}{x_1!(n-x_1)!}p_1^{x_1}(1-p_1)^{x_2+\dots+x_d}\sum_{(x_2, \dots, x_d)\in \mathscr{C}_{n-x_1,d-1}}\frac{(n-x_1)!}{x_2!\cdots x_d!}\left\{\frac{p_2}{1-p_1}\right\}^{x_2}\cdots\left\{\frac{p_d}{1-p_1}\right\}^{x_d}
\end{align*}$$
Notice that $$\sum_{(x_2, \dots, x_d)\in \mathscr{C}_{n-x_1,d-1}}\frac{(n-x_1)!}{x_2!\cdots x_d!}\left\{\frac{p_2}{1-p_1}\right\}^{x_2}\cdots\left\{\frac{p_d}{1-p_1}\right\}^{x_d}$$ is a pmf of $(X_2, \dots, X_d)\sim \operatorname{Mult}(n-x_1, \tilde{p})$, where $$\tilde{p} = \left(\frac{p_2}{1-p_1}, \dots, \frac{p_d}{1-p_1}\right)\in \Delta^{d-2}$$
$$p_{X_1}(x_1) = \begin{pmatrix}n \\ x_1\end{pmatrix}p_1^{x_1}(1-p_1)^{n-x_1}$$

**Super Category pmf, e.g., $Y = X_1+X_2$**
$$\begin{align*}
p_Y(y) &= \begin{pmatrix} n \\ y \end{pmatrix}(p_1+p_2)^y(1-p_1-p_2)^{n-y}\\
&\times \begin{pmatrix} y \\ x_1, x_2 \end{pmatrix} \left(\frac{p_1}{p_1+p_2}\right)^{x_1}\left(\frac{p_2}{p_1+p_2}\right)^{x_2}\\
&\times \begin{pmatrix} n-y \\ x_3, \dots, x_d \end{pmatrix} \left(\frac{p_3}{1-p_1-p_2}\right)^{x_3}\cdots \left(\frac{p_d}{1-p_1-p_2}\right)^{x_d}\\
&= \begin{pmatrix} n \\ y \end{pmatrix}(p_1+p_2)^y(1-p_1-p_2)^{n-y}
\end{align*}$$

**Conditional pmf, e.g., $X_3, \dots, X_d\mid Y=y$**
$$\begin{align*}
p_{X_3, \cdots, X_d}(x_3, \dots, x_d\mid Y = y) &= \frac{p_{Y, X_3, \dots, X_d}(y, x_3, \dots, x_d)}{p_Y(y)}\\
&= \frac{\frac{n!}{y!x_3!\cdots x_d!}(p_1+p_2)^y p_3^{x_3}\dots p_d^{x_d}}{\frac{n!}{y!(n-y)!}(p_1+p_2)^y(1-p_1-p_2)^{n-y}}\\
&= \frac{(n-y)!}{x_3!\cdots x_d!}\left\{\frac{p_3}{1-p_1-p_2}\right\}^{x_3}\cdots \left\{\frac{p_d}{1-p_1-p_2}\right\}^{x_d}
\end{align*}$$
## Worked Out Example: Dirichlet distribution
(Slide 10, Week 1) Pólya's Urn scheme

Suppose we have an urn with 7 red, 5 blue, 3 green, and 1 brown balls. Draw one ball from the urn, put it back and *add to the urn another ball of the same color*. Repeat *ad infinitum*. 

Let $\mathbf{X} = (X_1, X_2, X_3, X_4)\in \Delta^3$ be the limiting fractions of red, blue, green, and brown balls in the urn. Then $\mathbf{X}\sim \operatorname{Dirichlet(7,5,3,1)}$. 

Dirichlet distribution has many similar properties:
Distinct super-categories and remaining categories are Dirichlet:
- $(X_1+X_2, X_3, X_4)\sim \operatorname{Dirichlet}(12,3,1)$
- $(X_1+X_2, X_3+X_4)\sim \operatorname{Dirichlet}(12,4)$

$(U,1-U)\sim \operatorname{Dirichlet}(a,b)$ is also written as $U\sim \operatorname{Beta}(a,b)$.
- $X_1\sim \operatorname{Beta}(7,9)$
- $X_2\sim \operatorname{Beta}(5,11)$
- $X_1+X_2\sim \operatorname{Beta}(12,4)$

Conditioned on $X_4 = 0.1$, we have to renormalize since the sum of limiting probabilities $X_1+X_2+X_3 = 0.9$.

*Derivation of marginal pmf of* $X_1$:
Let $\mathbf{X} = (X_1, \dots, X_d)\sim\operatorname{Dirichlet}(\alpha_1, \dots, \alpha_d)$. On the domain $\tilde{\Delta}^{d-1} = \{(x_1, \dots, x_{d-1})\in \mathbb{R}^{d-1}: x_i\ge 0, \sum x_i \le 1\}$, the joint pdf of $\mathbf{X}_{-d}$ is 
$$p(X_1, \dots, X_{d-1}) = \frac{1}{D(\alpha_1, \dots, \alpha_d)}x_1^{\alpha_1-1}\cdots x_{d-1}^{\alpha_{d-1}-1}\left(1-\sum_{i=1}^{d-1}\right)^{\alpha_d-1}$$
$$\begin{align*}
p_{X_1}(x_1) &= \int \cdots \int p(x_1, \dots, x_{d-1})\, dx_2\dots \,dx_{d-1}\\
&= \int \cdots \int\frac{1}{D(\alpha_1, \dots, \alpha_d)}x_1^{\alpha_1-1}\cdots x_{d-1}^{\alpha_{d-1}-1}\left(1-\sum_{i=1}^{d-1}\right)^{\alpha_d-1}\, dx_2\dots \,dx_{d-1}\\
&= \frac{x_1^{\alpha_1-1}}{D(\alpha_1, \dots, \alpha_d)}\int\cdots\int\left(\prod_{i=2}^{d-1} x_i^{\alpha_i-1}\right)\left(1-x_1-\sum_{j=2}^{d-1} x_j\right)^{\alpha_d-1}\, dx_2\dots \,dx_{d-1}
\end{align*}$$
Here, we can apply a change of variable: Let $$z_i = \frac{x_i}{1-x_i}, \qquad\text{for }i=2, \dots, d-1$$
$$\begin{align*}
p_{X_1}(x_1) &= \frac{x_1^{\alpha_1-1}}{D(\boldsymbol{\alpha})} \int \cdots \int \left( \prod_{i=2}^{d-1} [z_i(1-x_1)]^{\alpha_i-1} \right) \left[ (1-x_1)\left(1 - \sum_{j=2}^{d-1} z_j\right) \right]^{\alpha_d-1} (1-x_1)^{d-2} dz_2 \cdots dz_{d-1}\\
&= \frac{x_1^{\alpha_1-1}(1-x_1)^{\sum_{i=2}^{d-1}(\alpha_i-1) + (\alpha_d-1) + (d-2)}}{D(\alpha_1, \dots, \alpha_d)}\int\cdots\int \left(\prod_{i=2}^{d-1}z_i^{\alpha_i-1}\right)\left(1-\sum_{j=2}^{d-1}\right)^{\alpha_d-1}\,dz_2\dots\,dz_{d-1}\\
&= \frac{x_1^{\alpha_1-1}(1-x_1)^{(\sum_{i=2}^{d}\alpha_i) -1}}{D(\alpha_1, \dots, \alpha_d)}D(\alpha_2, \dots, \alpha_d)
\end{align*}$$

Let $\beta_i = (\sum_{i=2}^{d}\alpha_i)$, 
$$p_{X_1}(x_1) = \frac{x_1^{\alpha_1-1}(1-x_1)^{\beta_1 -1}}{B(\alpha_1, \beta_1)}$$

This shows that $X_1\sim \operatorname{Beta}(\alpha_1, \beta_1)$.
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
## 1.6 *Expectation*
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

## 1.7 *Moments*
C&B 2.3 (univariate), 4.5 (multivariate)
**Def** Moments, Central moment
For each integer $n$, the $n$-th *moment* of $X$, $\mu'_n$, is $$\mu'_n = \mathbb{E}(X^n)$$
The $n$-th *central moment* of $X$, $\mu_n$, is $$\mu_n = \mathbb{E}[(X-\mu)^n]$$
where $\mu = \mu'_1 = \mathbb{E}(X)$. 

**Def** Variance
The *variance* of a random variable $X$ is its second central moment, $\mathbb{V}\text{ar}(X) = \mathbb{E}[(X-\mathbb{E}(X))^2]$. The positive square root of $\mathbb{V}\text{ar}(X)$ is the *standard deviation* of $X$. 

Additional properties of variance:
(a) $\mathbb{V}\text{ar}(aX+b) = a^2\mathbb{V}\text{ar}(X)$
*Proof*: Use $\mathbb{E}[(X-\mathbb{E}(X))^2]$. Expand with brutal force.

(b) (Chebyshev) $\mathbb{P}(|Y-\mathbb{E}(Y)|>t)\le \mathbb{V}\text{ar}(Y)/t^2$ for $t>0$
*Proof*: Consider the condition inside the probability. With $t>0$, squaring both sides preserves the order. $$(Y - \mathbb{E}(Y))^2 > t^2$$
Therefore, $$\mathbb{P}(|Y-\mathbb{E}(Y)|>t) = \mathbb{P}((Y - \mathbb{E}(Y))^2 > t^2)$$
By Markov's inequality, $$\mathbb{P}((Y - \mathbb{E}(Y))^2 > t^2) \le \frac{\mathbb{E}[(Y-\mu)^2]}{t^2}$$
Notice that $\mathbb{E}[(Y-\mu)^2]$ is equal to $\mathbb{V}\text{ar}(Y)$. This gives $$\mathbb{P}((Y - \mathbb{E}(Y))^2 > t^2) \le \frac{\mathbb{V}\text{ar}(Y)}{t^2}$$
$$\mathbb{P}(|Y-\mathbb{E}(Y)|>t) \le \frac{\mathbb{V}\text{ar}(Y)}{t^2}$$

(c) (Total Law) $\mathbb{V}\text{ar}(Y) = \mathbb{E}[\mathbb{V}\text{ar}(Y\mid X)] + \mathbb{V}\text{ar}[\mathbb{E}(Y\mid X)]$
*Proof*: Conditioning on $X$ does not alter the definition of $\mathbb{V}\text{ar}(Y\mid X)$. Hence, $$\mathbb{V}\text{ar}(Y\mid X) = \mathbb{E}[Y^2\mid X] - (\mathbb{E}[Y\mid X])^2$$
Take the expectation, $$\mathbb{E}[\mathbb{V}\text{ar}(Y\mid X)] = \mathbb{E}[Y^2] - \mathbb{E}[(\mathbb{E}[Y\mid X])^2]$$
For the expectation inside variance, $$\mathbb{V}\text{ar}(\mathbb{E}[Y\mid X]) = \mathbb{E}[(\mathbb{E}[Y\mid X])^2] - (\mathbb{E}[Y])^2$$
Add the two, $$\mathbb{E}[\mathbb{V}\text{ar}(Y\mid X)] + \mathbb{V}\text{ar}(\mathbb{E}[Y\mid X]) = \mathbb{E}[Y^2] - (\mathbb{E}[Y])^2 = \mathbb{V}\text{ar}(Y)$$
**Example** Find the $k$-th moments of the Standard Normal distribution ($Y \sim \mathcal{N}(0,1)$), with $k$ even.
(Slides 3, Week 2)

This derivation involves the *Law of the Unconscious Statistician/Lazy Statistician's Theorem*, $$\mathbb{E}[g(y)] = \int g(y)f_Y(y)\,dy$$Notice that for $\mathcal{N}(0,1)$, $$f_Y(y) = \frac{1}{\sqrt{2\pi}}\exp(-y^2/2)$$
$$\begin{align*}
\mathbb{E}[Y^k] &= \int_{-\infty}^\infty y^k\frac{1}{\sqrt{2\pi}}e^{-\frac{y^2}{2}}\,dy\\
&= \frac{2}{\sqrt{2\pi}}\int_0^\infty y^k e^{-\frac{y^2}{2}}\,dy\\
\end{align*}$$
We pause here to perform change of variable. Let $z = y^2/2$, 
$$\begin{align*}
\mathbb{E}[Y^k] &= \frac{2}{\sqrt{2\pi}}\int_0^\infty 2^{k/2}z^{k/2}e^{-z}\left(\frac{1}{\sqrt{2}}z^{-1/2}\right)\,dz\\
&= \frac{2^{k/2}}{\sqrt{\pi}}\int_0^\infty z^{\frac{k+1}{2}-1}e^{-z}\,dz\\
&= \frac{2^{k/2}}{\sqrt{\pi}}\Gamma\left(\frac{k+1}{2}\right)
\end{align*}$$

What is special about this? $$\begin{align*}
\mathbb{E}[Y^{k+2}] &= \frac{2^\frac{k+2}{2}}{\sqrt{\pi}}\Gamma\left(\frac{k+2+1}{2}\right)\\
&= 2\cdot \frac{2^{k/2}}{\sqrt{\pi}}\Gamma\left(\frac{k+1}{2}+1\right)\\
&= 2\cdot \frac{2^{k/2}}{\sqrt{\pi}}\left(\frac{k+1}{2}\right)\Gamma\left(\frac{k+1}{2}\right)\\
&= (k+1)\mathbb{E}[Y^k]
\end{align*}$$
Therefore, with $E[Y^2] = 1$, $\mathbb{E}[Y^4]= 1\times 3$, $\dots$

**Def** Moment Generating Function
Let $X$ be a random variable with cdf $F_X$. The *moment generating function (mgf)* of $X$, denoted by $M_X(t)$, is $$M_X(t) = \mathbb{E}(e^{tX}),$$ provided that such expectation exists for $t$ in some neighborhood of 0. 

**Thm** If $X$ has mgf $M_X(t)$, then $$\mathbb{E}(X^n) = M^{(n)}_X(0)$$ where we define $$M_X^{(n)}(0) = \frac{d^n}{dt^n} M_x(t)\mid_{t=0}$$
*Proof*: $$\frac{d}{dt}M_x(t) = \frac{d}{dt}\int_\mathbb{R}e^{tx}f_X(x)\,dx$$
Assuming we can differentiate under the integral sign (see C&B section 2.4), $$\frac{d}{dt}M_X(t) = \int_\mathbb{R}\left(\frac{d}{dt}e^{tx}\right)f_X(x)\,dx$$
$$\frac{d}{dt}M_X(t) = \int_\mathbb{R}(xe^{tx})f_X(x)\,dx$$
$$\frac{d}{dt}M_X(t) = \mathbb{E}(Xe^{tX})$$
When $n=1$, the case of $M'_X(t)$, $$\frac{d}{dt}M_X(t)\mid_{t=0} = \mathbb{E}(Xe^{tX})\mid_{t=0} = E(X)$$
$$\vdots$$
$$\frac{d^n}{dt^n}M_X(t)\mid_{t=0} = \mathbb{E}(X^ne^{tX})\mid_{t=0} = \mathbb{E}(X^n)$$

**Thm** Uniqueness of Moments
Let $F_X(x)$ and $F_Y(y)$ be two cdfs all of whose moments exist.
(a) If $X$ and $Y$ have bounded support, then $F_X(u) = F_Y(u)$ for all $u$ if and only if $\mathbb{E}[X^r] = \mathbb{E}[Y^r]$ for all integers $r = 0,1,2,\dots$. 
(b) If the moment generating functions exist and $M_X(t) = M_Y(t)$ for all $t$ in some neightborhood of 0, then $F_X(u) = F_Y(u)$ for all $u$. 

**Thm** Convergence of mgfs
Suppose $\{X_i, i = 1,2,\dots\}$ is a sequence of random variables, each with mgf $M_{X_i}(t)$. Furthermore, suppose that $$\lim_{i\rightarrow \infty} M_{X_i}(t) = M_X(t), \quad \text{for all }t\text{ in a neighborhood of 0,}$$ and $M_{X_i}(t)$ is an mgf. Then there is a unique cdf $F_X$ whose moments are determined by $M_X(t)$ and, for all $x$ where $F_X(x)$ is continuous, we have $$\lim_{i\rightarrow \infty} F_{X_i}(x) = F_X(x).$$
That is, convergence, for $|t|<h$, of mgfs to an mgf implies convergence of cdfs. 

*Special remark on multivariate mgf.* The mgf of a random vector $\mathbf{Y}\in \mathbb{R}^d$ is defined as the funciton $M_\mathbf{Y}: \mathbf{R}^d\to \mathbf{R}$ given by $$M_\mathbf{Y}(\mathbf{t}) = \mathbb{E}\left(e^{\mathbf{t}^\top \mathbf{Y}}\right)\qquad t\in \mathbb{R}^d$$
## Worked Out Example
## 1.8 *Multivariate Normal Distribution*
