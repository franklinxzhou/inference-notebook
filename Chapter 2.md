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

**Example** 
Suppose $X_1, \dots, X_n\sim \mathrm{Exponential}(\lambda)$ with $f(x\mid \lambda) = \lambda e^{-\lambda x}$. Let $T(\mathbf{X}) = \overline{X}$. Then, the likelihood function is given by $$L(\lambda; \mathbf{x}) = \prod_{i=1}^n \lambda e^{-\lambda x_i} = \lambda^n e^{-\lambda \sum x_i} = \lambda^n e^{-\lambda (n\overline{x})}$$
Satisfying Condition II (Factorization Theorem), we notice that $g(T(\mathbf{x})\mid \theta) = \lambda^n e^{-\lambda (n\overline{x})}$ and $h(\mathbf{x}) = 1$. 



