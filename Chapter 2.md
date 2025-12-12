Statistical Inference

## 2.1 Statistical Models
**Def** Data, statistical model, model space
In Surya's language, a statistician's data $\mathbf{X}$ is an uncertain observable quantity best described by a probability space $(\mathscr{S}, \mathscr{E}, P)$, which is typically not unknown, where $\mathscr{S} = \mathbb{R}$ or $\mathbb{R}^d$, $\mathscr{E}$ is the corresponding $\sigma$-algebra, and $P: \mathscr{E}\to \mathbb{R}$ satisfying the axioms of a probability map. As we have multiple possible probability distribution rules account for $\mathbf{X}$, these rules are *statistical models* $P$ and they collectively form a *model space* $\mathscr{P}$, denoted as $$\mathbf{X}\sim P, P\in \mathscr{P}.$$
**Example** Opinion Poll Survey
Surveying 500 randomly chosen Duke students and whom they voted in 2024. Let $X$ be the number of students who voted Kamala. $X\sim \mathrm{Binomial}(500, 0.5)$ is a particular statistical model and $\mathscr{P}$ is the collection of all $\mathrm{Binomial}(500, \phi)$, $\phi\in (0,1)$. 

**Example** Trend of Tropical Cyclone (TC) Counts
The annual counts of TC in some geolocation for the past 100 years are recorded as $\mathbf{X} = (X_1,\dots, X_{100})^\top$. $\mathbf{X}\sim \bigotimes_{t=1}^{100} \mathrm{Poisson}(\alpha\beta^{t-1})$, where $\alpha = 12$ and $\beta=1$ (i.e., $X_t\overset{\text{iid}}{\sim}\mathrm{Poisson}(12)$) is a statistical model and $\mathscr{P} = \{\bigotimes_{t=1}^n \mathrm{Poisson}(\alpha\beta^{t-1}): (\alpha, \beta)^\top\in \mathbb{R}^2_{>0}\}$ is a model space. 

**Def** Parametric model; non-parametric model
If the statistical models in a model space $\mathscr{P}$ are indexed by a finite number of parameters (e.g., $\alpha$, $\beta$ in the aforementioned Trend of TC Counts example), then $\mathscr{P}$ is a parametric model. If the models in a model space $\mathscr{P}$ are too complex to be indexed by a simple vector, then $\mathscr{P}$ is a nonparametric model.

**Example** 
(a) $X_1, \dots, X_n \overset{\text{iid}}{\sim}f, f\in \mathscr{F}$ where $$\mathscr{F} = \{\text{pdfs on }\mathbb{R}\text{ with mean 0 and variance 1}\}$$A parametric model can be a subset of a nonparametric model. For example, if $\mathscr{F}_k$ is a parametric model containing all mixed gaussian distributions with $k$ components, then it is a subset of $\mathscr{F}$. 
(b) Diabetes Progression
The dataset is in the shape of $(Y_i, \mathbf{X}_i)$, where $Y_i$ is a measure of disease progression one year after baseline and $\mathbf{X}_i$ is a vector containing 10 variables: age, sex, Body Mass Index (BMI), blood pressure, and 6 blood serum measurements. The model is defined as $$\mathbb{E}(Y_i\mid \mathbf{X}_i) = \beta_0 + \mathbf{X}_i^\top\boldsymbol{\beta}\qquad \text{and}\qquad \mathbb{V}\mathrm{ar}(Y_i\mid \mathbf{X}_i) = \sigma^2$$
Even though the regression part appears to use finitely many parameters ($\beta_0, \boldsymbol{\beta}, \sigma^2$), the overall model space $\mathscr{P}$ is nonparametric because the error term $g(\epsilon)$ can assume any valid pdf. 

**Def** General terminologies
(a) For any statistical model $X\sim P, P\in \mathscr{P}$, any model element $P$ is a *population*. 
(b) Any scalar/vector summary $\zeta = \zeta(P)$ of the model elements $P$ is a *population feature*.
(c) Any scalar/vector summary $T = T(\mathbf{X})$ of the data is a *statistic*.
(d) For a population feature $\zeta$, if $\mathscr{Z} = \{\zeta(P):P\in \mathscr{P}\}$ is its range of values, then any statistic $T$ that also takes values in $\mathscr{Z}$ is an *estimator* of $\zeta$. 
(e) An estimator $T$ of $\zeta$ is called *unbiased* if $\mathbb{E}(T\mid P) = \zeta(P)$ for every $P\in \mathscr{P}$. 

## 2.2 Inductive Reasoning vs. Deductive Reasoning
### 2.2.1 Deductive Reasoning
"You know the rules (the theory/model), and you predict the data." (Population $\Longrightarrow$ Sample)
### 2.2.2 Inductive Reasoning
"You have the data, and you try to infer the rules." (Sample $\Longrightarrow$ Population)

**Remark** There are two major challenges of inductive reasoning:
1. **Non-falsifiability:** The observed data $x_{obs}$ could technically be produced by _any_ of the candidate theories (even unlikely ones). You can never strictly prove a theory is wrong, only that it is unlikely.
2. **Sampling Variability:** If you repeated the experiment, you would get different data. Therefore, any conclusion you draw is subject to uncertainty.

#### 2.2.2.1 Toolbox for Inductive Reasoning
1. *Large Sample Theory*/the Frequentist Assurance: 
2. The Likelihood Function
3. Sufficiency

## 2.3 Likelihood Function
C&B Reference: $\S$ 6.3 The Likelihood Function Principle
**Def** The Likelihood Function
Let $f(\mathbf{x}\mid \theta)$ denote the joint pdf or pmf of the sample $\mathbf{X} = (X_1,\dots, X_n)$. Then, given that $\mathbf{X} = \mathbf{x}$ is observed, the function of $\theta$ defined by $$\mathcal{L}(\theta\mid \mathbf{x}) = f(\mathbf{x}\mid \theta)$$ is called the *Likelihood function*. 

In C&B $\S$ 6.3, **the Likelihood Principle** is introduced.
If $\mathbf{x}$ and $\mathbf{y}$ are two sample points s.t. $\mathcal{L}(\theta\mid \mathbf{x})$ is proportional to $\mathcal{L}(\theta\mid \mathbf{y})$, that is, $\exists$ a constant $C(\mathbf{x}, \mathbf{y})$ s.t. $$\mathcal{L}(\theta\mid \mathbf{x}) = C(\mathbf{x}, \mathbf{y})\mathcal{L}(\theta\mid \mathbf{y})\qquad (\forall \theta)$$ then the conclusions drawn from $\mathbf{x}$ and $\mathbf{y}$ should be identical. 

See C&B $\S$ 6.3.2, for *Formal Likelihood Principle*, *Formal Sufficiency Principle*, and **Conditionality Principle** - in plain words, if one of two exp. is randomly chosen and the chosen exp. is done, yielding $\mathbf{x}$, the inference about $\theta$ should be made based only on the exp. performed. Also, *Birnbaum's Theorem*: The Formal Likelihood Principle $\Leftrightarrow$ The Formal Sufficiency Principle + The Conditionality Principle. 
## 2.4 Sufficiency
C&B Reference: $\S$ 6.2 The Sufficiency Principle
**Def** Sufficient Statistic
A statistic $T(\mathbf{X})$ is a *sufficient statistic* for $\theta$ if the conditional distribution of the sample $\mathbf{X}$ given the value of $T(\mathbf{X})$ does not depend on $\theta$. 

*Remark*: A sufficient statistic $T(\mathbf{X})$ is said to contain all the information about $\theta$. Consider two experimenters 1 and 2. Exp. 1 observes $\mathbf{X} = x$ and computes $T(\mathbf{X}) = T(\mathbf{x})$. Exp. 2 is only informed $T(\mathbf{X}) = T(\mathbf{x})$ and can compute $\mathbb{P}(\mathbf{X} = \mathbf{y}\mid T(\mathbf{X} = T(\mathbf{x})))$. With this conditional probability, Exp. 2 can generate an observation $\mathbf{Y} = \mathbf{y}$. It will be shown below that $\mathbf{X}$ and $\mathbf{Y}$ have the same unconditional distribution; i.e., $\forall \mathbf{x}, \theta$, $\mathbb{P}_\theta(\mathbf{X} = \mathbf{x}) = \mathbb{P}_\theta(\mathbf{Y} = \mathbf{x})$. 
$$\begin{align*}
\mathbb{P}_\theta(\mathbf{X} = \mathbf{x}) &= \mathbb{P}_\theta(\mathbf{X} = \mathbf{x}, T(\mathbf{X}) = T(\mathbf{x}))\\
&= \mathbb{P}(\mathbf{X} = \mathbf{x}\mid T(\mathbf{X})=T(\mathbf{x}))\mathbb{P}_\theta(T(\mathbf{X}) = T(\mathbf{x}))\\
&= \mathbb{P}(\mathbf{Y} = \mathbf{x}\mid T(\mathbf{X})=T(\mathbf{x}))\mathbb{P}_\theta(T(\mathbf{X}) = T(\mathbf{x}))\\
&= \mathbb{P}_\theta(\mathbf{Y} = \mathbf{x}, T(\mathbf{X}) = T(\mathbf{x}))\\
&= \mathbb{P}_\theta(\mathbf{Y} = \mathbf{x})
\end{align*}$$
By the rule of conditional probability, $$\mathbb{P}_\theta(\mathbf{X}=\mathbf{x}\mid T(\mathbf{X} = T(\mathbf{x}))) = \frac{p(\mathbf{x}\mid\theta)}{q(\mathbf{T}(\mathbf{x})\mid \theta)},$$ where $p$ is the pmf of $\mathbf{X}$ and q is the pmf of $\mathbf{T}(\mathbf{x})$. $T(\mathbf{X})$ is a sufficient statistic if and only if $\forall \mathbf{x}$, the ratios of pmfs is a constant as a function of $\theta$. This will be recorded in the next theorem.

**Thm** Condition for Sufficiency I
If $p(\mathbf{x}\mid \theta)$ is the joint pdf or pmf of $\mathbf{X}$ and $q(t\mid \theta)$ is the pdf or pmf of $T(\mathbf{X})$, then $T(\mathbf{X})$ is a sufficient statistic for $\theta$ if, for every $\mathbf{x}$ in the sample space, the ratio $p(\mathbf{x}\mid \theta)/q(T(\mathbf{x})\mid \theta)$ is constant as a function of $\theta$. 

**Thm** Condition for Sufficiency II (Factorization Theorem)
Let $f(x\mid \theta)$ denote the joint pdf or pmf of a sample $\mathbf{X}$. A statistic $T(\mathbf{X})$ is a sufficient statistic for $\theta$ if and only if there exist functions $g(t\mid \theta)$ and $h(\mathbf{x})$ such that, for all sample points $\mathbf{x}$ and all parameter points $\theta$, $$f(\mathbf{x}\mid \theta) = g(T(\mathbf{x})\mid \theta)h(\mathbf{x})$$
*Proof*: Suppose $T(\mathbf{X})$ is sufficient. Then, Choose $g(t\mid \theta) = \mathbb{P}_\theta(T(\mathbf{X})=t)$, $h(\mathbf{x}) = \mathbb{P}(\mathbf{X} = \mathbf{x}\mid T(\mathbf{X}) = T(\mathbf{x}))$. Then, $$f(\mathbf{x}\mid \theta) = \mathbb{P}_\theta(T(\mathbf{X}) = T(\mathbf{x}))\mathbb{P}(\mathbf{X} = \mathbf{x}\mid T(\mathbf{X} = T(\mathbf{x}))) = g(T(\mathbf{x})\mid \theta)h(\mathbf{x})$$
Observe that since $g(T(\mathbf{x})\mid \theta) = \mathbb{P}_\theta(T(\mathbf{X})=T(\mathbf{x}))$, $g(T(\mathbf{x})\mid \theta)$ is a pmf of $T(\mathbf{X})$.  Suppose the factorization exists. Let $q(t\mid \theta)$ be the pmf of $T(\mathbf{X})$. We examine the ratio of $f(\mathbf{x}\mid \theta)/q(T(\mathbf{x})\mid \theta)$. Let $A_{T(\mathbf{x})} = \{\mathbf{y}: T(\mathbf{y}) = T(\mathbf{x})\}$, $$\begin{align*}
\frac{f(\mathbf{x}\mid \theta)}{q(T(\mathbf{x})\mid \theta)} &= \frac{g(T(\mathbf{x})\mid \theta) h(\mathbf{x})}{q(T(\mathbf{x})\mid \theta)}\\
&= \frac{g(T(\mathbf{x})\mid \theta) h(\mathbf{x})}{\sum_{A_{T(\mathbf{x})}} g(T(\mathbf{y})\mid \theta)h(\mathbf{y})}\\
&= \frac{g(T(\mathbf{x})\mid \theta) h(\mathbf{x})}{ g(T(\mathbf{x})\mid \theta)\sum_{A_{T(\mathbf{x})}}h(\mathbf{y})}\\
&= \frac{h(\mathbf{x})}{\sum_{A_{T(\mathbf{x})}}h(\mathbf{y})},
\end{align*}$$ which is independent of $\theta$. 

*Remark*: The joint pdf or pmf here, $f(\mathbf{x}\mid \theta)$, and the likelihood function are interchangeable. Joint pdf/pmf is used here because in C&B $\S$ 6.2, likelihood function has yet to be formally defined.

**Example** i.i.d. Exponential Distribution
Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim} \mathrm{Exponential}(\lambda)$ with $f(x\mid \lambda) = \lambda e^{-\lambda x}$. Let $T(\mathbf{X}) = \overline{X}$. Then, the likelihood function is given by $$\mathcal{L}(\lambda; \mathbf{x}) = \prod_{i=1}^n \lambda e^{-\lambda x_i} = \lambda^n e^{-\lambda \sum x_i} = \lambda^n e^{-\lambda (n\overline{x})}$$
Satisfying Condition II (Factorization Theorem), we notice that $g(T(\mathbf{x})\mid \theta) = \lambda^n e^{-\lambda (n\overline{x})}$ and $h(\mathbf{x}) = 1$. 

**Example** Order Statistic of a Uniform Distribution
Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim} \mathrm{Unif}(0,\theta)$, let $T(\mathbf{X}) = X_{(n)} = \max(X_1,\dots, X_n)$. A single observation has the density of $$f(x_i\mid \theta) = \frac{1}{\theta}\mathbb{I}_{0\le x\le \theta}$$ which follows that the joint likelihood is $$\mathcal{L}(\theta; \mathbf{x}) = \frac{1}{\theta^n}\prod_{i=1}^n\mathbb{I}_{0\le x_i\le \theta} = \frac{1}{\theta^n}\mathbb{I}_{0\le x_{(n)}\le \theta}.$$ Notice that if $x_{(n)}\le \theta$, then all of $x_i\le \theta$. We notice that this likelihood only depends on $x_{(n)}$. By Condition II, another sufficient statistic.

**Example** The Discrete Mixture
Consider the statistical model $X_1, \dots, X_n\overset{\text{iid}}{\sim} f(x\mid \theta)$, $0<\theta<1$, where $$f(x\mid\theta) = \begin{cases} \frac{1-\theta}{2} & \text{if }x=-1,\\ \theta & \text{if }x=0, \\ \frac{1-\theta}{2} & \text{if }x=1, \\ 0 & \text{otherwise.}\end{cases}$$
We discuss if the following three statistics are sufficient: 
(a) $T_1(\mathbf{X}) = X_1 + \dots + X_n$,
**(b)** $T_2(\mathbf{X}) = |X_1| + \dots + |X_n|$, 
**(c)** $T_3(\mathbf{X})$: the number of zeroes in $X_i$. 

Inspecting the pmf, there are only three possible values, -1, 0, 1. We can write the joint likelihood as $$\mathcal{L}(\theta; \mathbf{x}) = \theta^{\mathbb{I}_{x=0}}\left(\frac{1-\theta}{2}\right)^{n-\mathbb{I}_{x=0}} = \theta^{T_3(\mathbf{X})}\left(\frac{1-\theta}{2}\right)^{n-T_3(\mathbf{X})}$$
By Condition II, $T_3$ is the sufficient statistic. 

Also, notice that $n-T_3 = T_2$ because $|x_i| = 1$ if $x_i = \pm 1$ and $|x_i| = 0$ if $x_i = 0$. The joint likelihood is then $$\mathcal{L}(\theta; \mathbf{x}) = \theta^{n-T_2(\mathbf{X})}\left(\frac{1-\theta}{2}\right)^{T_2(\mathbf{X})}$$
**Example** Normal Distribution with Scaled Means
Suppose $Y_1, Y_2, \dots$ are independently distributed as $Y_j\sim (\theta x_j, 1)$, where $x_j = 1/\sqrt{j}$, and $\theta\in \mathbb{R}$. Consider that the density of a single observation is $$f(y_i\mid \theta) = \frac{1}{\sqrt{2\pi}} \exp\left\{-\frac{1}{2}\left(y_j-\frac{\theta}{\sqrt{j}}\right)^2\right\}$$ This follows that the joint likelihood is $$\begin{align*}
\mathcal{L}(\theta; \mathbf{y}) &\propto \prod_{j=1}^n\exp\left\{-\frac{1}{2}\left(y_j-\frac{\theta}{\sqrt{j}}\right)^2\right\} \\
& = \exp\left\{-\frac{1}{2}\sum_{j=1}^n\left(y_j-\frac{\theta}{\sqrt{j}}\right)^2\right\}\\
& = \exp\left\{-\frac{1}{2}\sum_{j=1}^n\left(y_j^2-\frac{2\theta}{\sqrt{j}}y_j + \frac{\theta^2}{j}\right)\right\}\\
&= \exp\left\{-\frac{1}{2}\sum_{j=1}^n y_j^2\right\}\exp\left\{\frac{1}{2}\sum_{j=1}^n\left(\frac{2\theta}{\sqrt{j}}y_j - \frac{\theta^2}{j}\right)\right\}\\
&= \underbrace{\exp\left\{-\frac{1}{2}\sum_{j=1}^n y_j^2\right\}}_{h(\mathbf{y})}\underbrace{\exp\left\{\theta\sum_{j=1}^n\frac{y_j}{\sqrt{j}} - \frac{1}{2}\sum_{j=1}^n\frac{\theta^2}{j}\right\}}_{g(T(\mathbf{y})\mid \theta)}
\end{align*}$$
As labeled above, we have factorized the joint likelihood and identified $$T(\mathbf{y}) = \sum_{j=1}^n \frac{y_j}{\sqrt{j}}$$ as the sufficient statistic for $\theta$. 

**Def** Minimal Sufficient Statistic
A sufficient statistic $T(\mathbf{X})$ is called a *minimal sufficient statistic* if, for any other sufficient statistic $T'(\mathbf{X})$, $T(\mathbf{X})$ is a function of $T'(\mathbf{X})$. 

*Remark*: C&B $\S$ 6.2 moves on from this point to introduce a couple of related definitions and theorems related to sufficient statistic, but I think they are not in this course's scope anymore. Also, we have introduced a couple of sufficient statistic identified from the Condition II, here is one identifiable the Condition I. 

**Example** Normal Sufficient Statistic (for $\mu$)
Let $X_1, \dots, X_n\overset{\text{iid}}{\sim}\mathcal{N}(\mu, \sigma^2)$, where $\sigma^2$ is known. We want $T(\mathbf{X}) = \overline{X}$ to be a sufficient statistic for $\mu$. We need to show that the ratio of the pdfs of $\mathbf{X}$ and $T(\mathbf{X})$ is independent of $\mu$. Then, we should bear in mind that $\overline{X}\sim \mathcal{N}(\mu, \sigma^2/n)$. The pdf of $\overline{X}$ is $$q(T(\mathbf{x})\mid \mu) = \frac{\sqrt{n}}{\sigma\sqrt{2\pi}} \exp\left\{-\frac{n(\bar{x}-\mu)^2}{2\sigma^2}\right\}$$
The joint pdf of $\mathbf{X}$ is $$\begin{align*}
f(\mathbf{x}\mid \mu) &= \prod_{i=1}^n\frac{1}{\sigma\sqrt{2\pi}} \exp\left\{-\frac{(x_i-\mu)^2}{2\sigma^2}\right\}\\
&= \frac{1}{\sigma\sqrt{2\pi}}\exp\left\{-\sum_{i=1}^n\frac{(x_i-\mu)^2}{2\sigma^2}\right\}\\
&= \frac{1}{\sigma\sqrt{2\pi}}\exp\left\{-\sum_{i=1}^n\frac{(x_i-\bar{x} + \bar{x}-\mu)^2}{2\sigma^2}\right\}\\
&= \frac{1}{\sigma\sqrt{2\pi}}\exp\left\{-\frac{\sum_{i=1}^n(x_i-\bar{x})^2 + n(\bar{x}-\mu)^2}{2\sigma^2}\right\}\\
&= \left(\frac{\sqrt{n}}{\sigma\sqrt{2\pi}} \exp\left\{-\frac{n(\bar{x}-\mu)^2}{2\sigma^2}\right\}\right)\frac{1}{\sqrt{n}}\exp\left\{ - \frac{\sum_{i=1}^n (x_i - \bar{x})^2}{2\sigma^2}\right\}
\end{align*}$$
This follows that the ratio of the two pdfs is $$\frac{f(\mathbf{x}\mid \mu)}{q(T(\mathbf{x})\mid \mu)} = \frac{1}{\sqrt{n}}\exp\left\{ - \frac{\sum_{i=1}^n (x_i - \bar{x})^2}{2\sigma^2}\right\},$$ which is independent of $\mu$. 

In general, what is **the Sufficient Principle**? 
If $T(\mathbf{X})$ is a sufficient statistic for $\theta$, then any inference about $\theta$ should depend on the sample $\mathbf{X}$ only through the value $T(\mathbf{X})$. That is if $\mathbf{x}$ and $\mathbf{y}$ are two sample points s.t. $T(\mathbf{x}) = T(\mathbf{y})$, then the inference about $\theta$ should be the same whether $\mathbf{X} = \mathbf{x}$ or $\mathbf{X} = \mathbf{y}$ is observed. 

(If time permits, to be added: Finding Normal sufficient statistic for $\sigma^2, \mu$ simultaneously unknown; extra book problems about sufficiency)



