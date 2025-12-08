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
"You know the rules (the theory/model), and you predict the data."
### 2.2.2 Inductive Reasoning
"You have the data, and you try to infer the rules."

**Remark** There are two major challenges of inductive reasoning:
1. **Non-falsifiability:** The observed data $x_{obs}$ could technically be produced by _any_ of the candidate theories (even unlikely ones). You can never strictly prove a theory is wrong, only that it is unlikely.
2. **Sampling Variability:** If you repeated the experiment, you would get different data. Therefore, any conclusion you draw is subject to uncertainty.

#### 2.2.2.1 Toolbox for Inductive Reasoning
1. *Large Sample Theory*/the Frequentist Assurance: 
2. The Likelihood Function
3. Sufficiency

## 2.3 Likelihood Function

## 2.4 Sufficiency
C&B Reference: $\S$ 6.2 The Sufficiency Principle