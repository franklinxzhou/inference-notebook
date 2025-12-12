Classical Inference

## 3.1 Fisher's Hypothesis Testing

Fisher's program of hypothesis testing:
1. Set up a null hypothesis $H_0: P\in \mathscr{P}_0$ and identify a scalar statistic $T = T(\mathbf{X})$ whose larger values reflect a greater mismatch between theories supported by $H_0$ and data $\mathbf{X}$. 
2. Once data $\mathbf{X} = \mathbf{x}$ has been observed, first calculate the evidence in data against $H_0$ by $t = T(\mathbf{x})$. Next report the $p$-value, $$p = \max_{P\in \mathscr{P}_0} P(T\ge t)$$ as a measure of how significant the evidence is against $H_0$. 

**Example** Opinion Poll
Assessing the hypothesis: Majority of Duke kids will vote red in the next presidential election. 
The researcher collected a sample of $n=500$. 
*Set up a null hypothesis*: $$H_0: X\sim \mathrm{Bin}(500, \phi), \qquad \phi\le 0.5$$ *(Real world meaning for this $H_0$: Most Duke kids will not vote for a GOP candidate.)*
*Identify a good scalar statistic*: The count $X$ itself is good enough! The count $X$ gets larger, the less likely $H_0$ is true.
*Calculate $p$-value*: For example, if $x_\text{obs} = 270$, $$p = \max_{\phi\le 0.5}\mathbb{P}(X\ge 270\mid \phi) = \mathbb{P}(X\ge 270\mid \phi = 0.5) = 0.04$$
*Remark*: Fisher recommended reporting the exact $p$-value instead of the "p<0.05", because, for example, $p = 0.04$ implies either $H_0$ is *false* or *a rare event (with a chance of 4%) has happened*. The statement provides no information about which one is more likely. 

*Remark*: Classical significance testing uses *deductive logic* (reasoning from a hypothesis to expected data), which prevents us from making direct probability statements about the hypothesis itself (which would require *inductive logic*).

**Example** COVID Test
Suppose you take a COVID test with a 3% false positive rate and the result is positive. 
*The Deductive Conclusion*: Either I have COVID or it is a rare event, with only 3% chance, has happened.
*The Inductive Conclusion* (which is fallacious): Either I have COVID (97% chance) or I don't have COVID (only 3% chance). 

Why the inductive conclusion is fallacious? It ignores the baseline prevalence of the disease (the prior). To make a valid inductive conclusion, one must use *Bayesian framing*: Suppose the prior is *33% of people exhibiting symptoms actually have COVID*, and the false negative rate is 40%. $$\begin{align*}
\mathbb{P}(\text{COVID}\mid +) &= \frac{\mathbb{P}(\text{COVID})\mathbb{P}(+\mid \text{COVID})}{\mathbb{P}(\text{COVID})\mathbb{P}(+\mid \text{COVID}) + \mathbb{P}(\neg\text{COVID})\mathbb{P}(+\mid \neg\text{COVID})}\\
&= \frac{0.33\times 0.6}{0.33\times 0.6 + 0.67\times 0.03}\\
&= 0.91
\end{align*}$$
The correct inductive conclusion: Either I have COVID (91% chance) or I do not have COVID (only 9% chance). 

## 3.2 Neyman-Pearson Frequentism
The fundamental shift from Fisher to Neyman-Pearson is moving from "inductive reasoning" (trying to learn what is true about the specific hypothesis) to "inductive behavior" (establishing a rule for taking action).

**Def** Testing Rule
Under N-P frequentism, hypothesis testing is a comparative assessment of $$H_0: P\in \mathscr{P}_0$$ and $$H_1: P\in \mathscr{P}_1$$ where $\mathscr{P}_0$ and $\mathscr{P}_1$ form a partition of the model space $\mathscr{P}$. 

A *testing rule* is a map $\delta: \mathscr{S}\to \{\text{accept }H_0, \text{accept } H_1\}$, according to which we take actions given an observation $X=x$. 

Connecting to Fisherian approach, if $T = T(\mathbf{X})$ is a statistic that measures evidence against $H_0$ in data $\mathbf{X}$, we could fix a critical value $c$ as the cutoff (i.e., $T\ge c$ implies significant evidence against $H_0$) and create the $\delta$: $$\delta(\mathbf{x}) = \begin{cases}
\text{accept }H_1 & \text{if }T(\mathbf{x})\ge c\\
\text{accept }H_0 & \text{if }T(\mathbf{x})< c
\end{cases}$$

**Def** Type I Error, Type II Error
If $P\in \mathscr{P_0}$ but the hypothesis test incorrectly decides to reject $H_0$, then this test has made a *Type I Error*. If, on the other hand, $P\in \mathscr{P}_1$ but the test decides to accept $H_0$, a *Type II Error* has been made.

It can be summarized by the table:

|                | Accept $H_0$     | Accept $H_1$     |
|----------------|------------------|------------------|
| Truth is $H_0$ | Correct decision | Type I Error     |
| Truth is $H_1$ | Type II Error    | Correct decision |
*Remark*: In C&B, the authors like to use $\theta \in \Theta_0$ to denote $H_0$, where $\theta$ is the parameter of interest and $\Theta_0$ is the subset of a parameter space, but Surya likes to use $P\in \mathscr{P}_0$ to denote $H_0$, where $P$ is the model of interest and $\mathscr{P}_0$ is the subset of a model space. Both notations are interchangeable when we only concern one parameter, but Surya's notation is more generalized.

*Remark*: C&B like to say "reject $H_0$" in lieu of "accept $H_1$", but I don't think this Fisherian speak is right in the context of N-P. 

If we only concern one parameter $\theta$, suppose $R$ denotes the region to accept $H_1$ for a test; i.e., if $T(\mathbf{x})\in R$, we accept $H_1$. For $\theta\in \Theta_0$, the test will make a mistake if $T(\mathbf{x}) \in R$ with the probability of a Type I Error being $$\mathbb{P}_\theta(T(\mathbf{X})\in R);$$ for $\theta\in \Theta_1$, the test will make a mistake if $T(\mathbf{x})\in R^c$ with the probability of a Type II Error being $$\mathbb{P}_\theta(T(\mathbf{X})\in R^c).$$ This shows that the function $\mathbb{P}_\theta(T(\mathbf{X})\in R)$ contains all the information about the test that accepts $H_1$ when $T(\mathbf{x})\in R$. $$\mathbb{P}_\theta(T(\mathbf{X})\in R) = \begin{cases}
\text{probability of a Type I Error} & \text{if }\theta\in \Theta_0\\
1-\text{probability of a Type II Error} & \text{if }\theta\in \Theta_1
\end{cases}$$
*Remark*: The term $\mathbb{P}_\theta$ is a family of probability laws indexed by $\theta$. For example, when we calculate the probability of Type I Error, we switch the knob to $\theta\in \Theta_0$; when we calculate the probability of Type II Error, we switch the knob to $\theta\in \Theta_1$. 

**Def** Probability of Type II Error ($\beta$)
ATTENTION: *This definition is following Surya's notation, where the power function is $1-\beta$, instead of the standard notation, where the power function is $\beta$.*

The *probability* of a hypothesis test accepting $H_0$ when $T(\mathbf{x})\in R^c$ is the function of $\theta$ defined by $\beta(\theta) = \mathbb{P}_\theta(T(\mathbf{X})\in R^c)$. This means the power function $$\mathbb{P}_\theta(T(\mathbf{X})\in R) = 1-\beta(\theta)$$
**Def** Size $\alpha$ vs. Level $\alpha$
*Remark*: This distinction is very important wrt to *composite* $H_0$'s. However, for a simple $\mathscr{P}_0$, the size is the level. See the next *Remark*.

For $0\le \alpha \le 1$, a test with power function $\mathbb{P}_\theta(T(\mathbf{X})\in R)$ is a size $\alpha$ test if $$\sup_{\theta\in \Theta_0}\mathbb{P}_\theta(T(\mathbf{X})\in R) = \alpha$$
For $0\le \alpha \le 1$, a test with power function $\mathbb{P}_\theta(T(\mathbf{X})\in R)$ is a level $\alpha$ test if $$\sup_{\theta\in \Theta_0}\mathbb{P}_\theta(T(\mathbf{X})\in R)\le \alpha$$
*Remark*: In Surya's slides, the most simple hypotheses is given: $$\mathscr{P}_0 = \{P_0\} \qquad \text{and} \qquad \mathscr{P}_1 = \{P_1\}$$
The $\alpha$ is defined as $$\alpha = P_0(T(\mathbf{X})\in R)$$ (Under probability law $P_0$, the probability of $T(\mathbf{X})$ is in the region where the test accepts $H_1$) 

The $\beta$ is defined as $$\beta = P_1(T(\mathbf{X})\in R^c)$$ (Under probability law $P_1$, the probability of $T(\mathbf{X})$ is in the region where the test accepts $H_0$)

**Example** Opinion Poll, revisited
Suppose we test $$H_0: X\sim\mathrm{Bin}(500, 0.5)$$ versus $$H_1: X\sim \mathrm{Bin}(500, 0.55).$$ Then, set $R = \{269 \le x \le 500: x\in \mathbb{Z}\}$.

Under $P_0$ ($\mathrm{Bin}(500, 0.5)$), $$\alpha = P_0(X\ge 269) = \sum_{k=269}^{500}\begin{pmatrix} 500 \\ k \end{pmatrix}(0.5)^k(1-0.5)^{500-k} = 0.048945$$
Under $P_1$ ($\mathrm{Bin}(500, 0.55)$), $$\beta =P_1(X< 269) = \sum_{k=1}^{268}\begin{pmatrix} 500 \\ k \end{pmatrix}(0.55)^k(1-0.55)^{500-k} = 0.27920$$

**Example** Normal Distribution with Scaled Means, revisited
Suppose $Y_1, Y_2, \dots$ are independently distributed as $Y_j\sim (\theta x_j, 1)$, where $x_j = 1/\sqrt{j}$, and $\theta\in \mathbb{R}$. Suppose $$T_n = \frac{1}{n}\sum_{i=1}^n \frac{Y_i}{x_i},$$ and we want to identify a test rule based on this statistic for testing $$H_0: \theta\le 0$$ versus $$H_1:\theta>0$$
(to be added after completing the definitions of $\alpha$ and $\beta$)