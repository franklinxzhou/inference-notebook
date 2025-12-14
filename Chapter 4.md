Classical Methods

*Remark*: The Chapter 3 does not address much of "how to find a rule" question, but this chapter will dive into this question.

## 4.1 Introduction
**Def** Pivotal quantity AKA pivot
A random variable $Q(\mathbf{X},\theta)$ is a *pivotal quantity* (or *pivot*) if the distribution of $Q(\mathbf{X},\theta)$ is independent of all parameters. That is, if $\mathbf{X}\sim F(\mathbf{x}\mid \theta)$, then $Q(\mathbf{X}, \theta)$ has the same distribution for all values of $\theta$. 

**Examples** Gaussian and Exponential Data
(a) Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim} \mathcal{N}(\mu, \sigma^2)$ (with $\sigma^2$ known), then $$Z = \frac{\overline{X} - \mu}{\sigma/\sqrt{n}}\sim \mathcal{N}(0,1)$$ is a pivotal quantity.
(b) Suppose $X_1,\dots, X_n\overset{\text{iid}}{\sim}\mathrm{Exponential}(\lambda)$, $\lambda\in \mathbb{R}_+$, then $$Z = \lambda \overline{X} \sim\mathrm{Gamma}(n,n)$$ is a pivotal quantity. This is a sample mean scaled from the rate (inverse of mean): 
$$\sum_{i=1}^n X_i\sim \mathrm{Gamma}(n,\lambda)$$$$\overline{X} = \frac{1}{n}\sum_{i=1}^n X_i\sim \mathrm{Gamma}(n,n\lambda),$$ so
 $$\lambda \overline{X} \sim \mathrm{Gamma}(n,n).$$
 As a quick reminder, for $Y\sim \mathrm{Gamma}(n,\lambda)$, $cY\sim Gamma(n, \lambda/c)$. 
  
 For the very same distribution, $Z = 2\lambda \sum X_i$ is another pivotal quantity. $$2\lambda \sum_{i=1}^n X_i\sim \mathrm{Gamma}\left(n, \frac{1}{2}\right) = \chi^2_{2n}$$
*Remark*: After defining pivotal quantities, we have a practical way to construct a good rule:
* Find a good estimator $\widehat{\zeta} = \widehat{\zeta}(\mathbf{X})$,
* Construct a pivotal quantity relating the estimator to the true values of the parameters, and
* Use the pivot's known distribution to make inference (create a confidence interval or a test).
* Sometimes, if it is not possible to construct a pivot with the feature of interest and its estimator, throw in a *nuisance* quantity $\sigma$ 
	* plug in a good estimator $\widehat{\sigma}$ and define $\tilde{Z} = g(\widehat{\zeta}(\mathbf{X}), \zeta(P), \widehat{\sigma}(\mathbf{X}))$ (approximate pivot)

A detailed depiction of making inference with pivots:
Suppose $Z$ has reference cdf $F(z)$ (independent on $P$) then $$\mathbb{P}(l\le Z \le u) = 1-\alpha$$ where $l = F^{-1}(\alpha/2)$ and $u = F^{-1}(1-\alpha/2)$. This defines a $100(1-\alpha)\%$ confidence set rule, $$\gamma(\mathbf{x}) = \{\zeta: l\le g(\widehat{\zeta}(\mathbf{x}), \zeta)\le u\}$$
In Chapter 3, the N-P testing rule of size $\alpha$ can be written as $$\delta(\mathbf{x}) = \begin{cases}\text{accept }H_0 & \zeta_0\in \gamma(\mathbf{x}) \\ \text{accept }H_1 & \zeta_0\notin \gamma(\mathbf{x})\end{cases}$$
*Why?* $$\mathbb{P}_\zeta(\zeta_0\in \gamma(\mathbf{x})) = \mathbb{P}(Z\in [l,u]) = 1-\alpha$$ where $Z = g(\widehat{\zeta}(\mathbf{x}), \zeta)$. 

**Example** Gaussian and Exponential Data, revisited
Now, we want to write $100(1-\alpha)\%$ confidence interval rules.
(a) We have shown that if $X_1, \dots, X_n\overset{\text{iid}}{\sim} \mathcal{N}(\mu, \sigma^2)$, $$Z = \frac{\overline{X} - \mu}{\sigma/\sqrt{n}}\sim \mathcal{N}(0,1)$$
Then, we can write $$\begin{align*}\gamma(\mathbf{x}) &= \left\{\mu: \Phi^{-1}(\alpha/2)\le \frac{\overline{x} - \mu}{\sigma/\sqrt{n}}\le \Phi^{-1}(1-\alpha/2)\right\}\\
&= \left\{\mu:\mu\in \left[\overline{x} - \frac{\sigma}{\sqrt{n}}\Phi^{-1}\left(1-\frac{\alpha}{2}\right), \overline{x} - \frac{\sigma}{\sqrt{n}}\Phi^{-1}\left(\frac{\alpha}{2}\right)\right]\right\}\end{align*}$$
Set $a = \Phi^{-1}\left(1-\frac{\alpha}{2}\right)$, $$\gamma(\mathbf{x}) = \left\{\mu: \mu\in \left[\overline{x} - a\frac{\sigma}{\sqrt{n}}, \overline{x}+a\frac{\sigma}{\sqrt{n}}\right]\right\}$$
Specifically, if $\alpha = 0.05$, $a = 1.96$. 

Here, $\sigma$ is a nuisance quantity, so the $Z$ here is an *extended pivot*. The discussion above is solely based on the assumption that *$\sigma^2$ is known*, but usually it is not the case. One practical way is to plug in an estimator of $\sigma$
, $S$, and notice the resulting approximate pivot follows $t_{n-1}$ distribution instead. The rule becomes $$\gamma(\mathbf{x}) = \left\{\mu: \mu\in\left[\overline{x} - t_{1-\alpha/2, n-1}\frac{S}{\sqrt{n}}, \overline{x} + t_{1-\alpha/2, n-1}\frac{S}{\sqrt{n}}\right]\right\}$$
(b) We ahve shown that if $X_1,\dots, X_n\overset{\text{iid}}{\sim}\mathrm{Exponential}(\lambda)$, $\lambda\in \mathbb{R}_+$, $$Z = 2\lambda \sum_{i=1}^n X_i\sim\chi^2_{2n}$$ is a pivot. Then, we can write: $$\begin{align*}
\gamma(\mathbf{x}) &= \left\{\lambda: \chi^2_{2n, \alpha/2}\le 2\lambda \sum_{i=1}^n x_i \le \chi^2_{2n, 1-\alpha/2} \right\}\\
&= \left\{\lambda: \lambda\in \left[\frac{\chi^2_{2n, \alpha/2}}{2\sum x_i}, \frac{\chi^2_{2n, 1-\alpha/2}}{2\sum x_i}\right]\right\}
\end{align*}$$
## 4.2 Asymptotic Evaluations
**Def** Consistent sequence of estimators
A sequence of estimators $W_n = W_n(X_1, \dots, X_n)$ is a *consistent sequence of estimators* of the parameter $\theta$ if, for every $\epsilon>0$ and every $\theta\in \Theta$, $$\lim_{n\to\infty} \mathbb{P}_\theta(|W_n - \theta|<\epsilon) = 1$$ or $$W_n\overset{p}{\to}\theta$$

**Def** Limiting variance
For an estimator $T_n$, if $$\lim_{n\to\infty}k_n \mathbb{V}\mathrm{ar}(T_n) = \tau^2<\infty,$$ where $\{k_n\}$ is a sequence of constants, then $\tau^2$ is the *limiting variance* or *limit of the variances*. 

*Remark*: What $\{k_n\}$ do we use a lot? $\{\sqrt{n}\}$. 

**Def** Asymptotically normal estimator; asymptotic variance
For an consistent estimator $T_n$, if $$k_n(T_n - \tau(\theta))\Rightarrow \mathcal{N}(0, \sigma^2),$$ for all $\theta\in \Theta$, then it is called *asymptotically normal*. The parameter $\sigma^2$ is called the *asymptotic variance* or *variance of the limit distribution* of $T_n$. 

**Example** Estimating the Rate $\lambda$ of Exponential Distribution
Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim}\mathrm{Exponential}(\lambda)$, with $\lambda \in \mathbb{R}_+$. For each $X_i$, $$f(x_i\mid \lambda) = \lambda e^{-\lambda x_i}\mathbb{I}_{x_i\in \mathbb{R}_+}$$
For $\mathbf{X}$, $$f(\mathbf{x}\mid \lambda) = \lambda^n \exp\left(-\lambda \sum_{i=1}^n x_i\right)\mathbb{I}_{x_1, \dots, x_n\in \mathbb{R}_+}$$
With WLLN, $\overline{X} \overset{p}{\to}\mathbb{E} = 1/\lambda$. This follows $1/\overline{X}\overset{p}{\to} \lambda$. Let $\widehat{\lambda} = 1/\overline{X}$, then $\widehat{\lambda}\overset{p}{\to}\lambda$, so $\widehat{\lambda}$ is a consistent estimator. With CLT, notice that $\overline{X}\sim \mathrm{Gamma}(n, n\lambda)$. We then see $$\sqrt{n}\left(\overline{X} - \frac{1}{\lambda}\right)\Rightarrow \mathcal{N}\left(0, \frac{1}{\lambda^2}\right)$$
Use Delta Theorem to change the variable: Let $g(\overline{X}) = \frac{1}{\overline{X}}$, then $g(x) = \frac{1}{x}$, $g'(x) = -\frac{1}{x^2}$. This follows $$\sqrt{n}\left(\widehat{\lambda} - \lambda\right)\Rightarrow \mathcal{N}\left(0, \lambda^2\right)$$
The asymptotic variance of $\widehat{\lambda}$ is therefore $\lambda^2$. Notice also we can put $\widehat{\lambda}$ into the asymptotic variance, $\widehat{\sigma}^2$, then $$\widehat{\sigma}^2 = \frac{1}{\overline{x}^2}\overset{p}{\to} \lambda^2$$If we want to construct a 95% confidence interval, we can surely construct the pivot. $$Z = \frac{\sqrt{n}\left(\widehat{\lambda} - \lambda\right)}{\sigma}$$
Using Slutsky's theorem, we can construct the approximate$$\tilde{Z} = \frac{\sqrt{n}\left(\widehat{\lambda} - \lambda\right)}{\widehat{\sigma}}\Rightarrow \mathcal{N}(0,1)$$
Recall, we can identify an asymptotic confidence set by $$\begin{align*}\gamma(\mathbf{x}) &= \left\{\lambda: \Phi^{-1}(\alpha/2)\le \frac{\sqrt{n}\left(\widehat{\lambda} - \lambda\right)}{\widehat{\sigma}}\le \Phi^{-1}(1-\alpha/2)\right\}\\
&= \left\{\lambda:\lambda\in \left[\widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\Phi^{-1}\left(1-\frac{\alpha}{2}\right), \widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\Phi^{-1}\left(\frac{\alpha}{2}\right)\right]\right\}\end{align*}$$ with $\mathbb{P}(\lambda\in \gamma) = 1-\alpha$. Specifically, if we want an asymptotically 95% interval rule, we can have $$\gamma(\mathbf{x}) = \left\{\lambda:\lambda\in \left[\widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\cdot 1.96, \widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\cdot 1.96\right]\right\}$$
Compare this with an exact 95% interval rule, where we use the exact pivot $2\lambda n\overline{X}\sim \chi^2_{2n}$. We have illustrated previously that $$\begin{align*}
\gamma(\mathbf{x}) &= \left\{\lambda: \chi^2_{2n, \alpha/2}\le 2\lambda \sum_{i=1}^n x_i \le \chi^2_{2n, 1-\alpha/2} \right\}\\
&= \left\{\lambda: \lambda\in \left[\frac{\chi^2_{2n, \alpha/2}}{2\sum x_i}, \frac{\chi^2_{2n, 1-\alpha/2}}{2\sum x_i}\right]\right\}
\end{align*}$$
## 4.3 Methods to Find Estimators
### 4.3.1 Estimation via Sample Averages (Method of Moment Estimation, MoM)
Suppose that we estimate $\zeta(f) = \mathbb{E}[h(X_1)|f]$. One way to estimate this population feature is through using the corresponding sample average: $$\hat{\zeta} = \overline{H}_n = \frac{1}{n} \sum_{i=1}^n h(X_i)$$
* This estimator is **consistent** due to WLLN.
* This estimator is **asymptotically normal** with, scaled by $\sqrt{n}$, an asymptotic variance equal to the true variance $\sigma^2(f) = \mathbb{V}ar[H_1|f]$. 

The true variance $\sigma^2(f)$ usually depends on unknown population moments $\mu_i(f)$, so we typically need an estimator for the variance, $\widehat{\sigma}^2(f)$. By continuous mapping theorem, if $$\sigma^2(f) = g(\mu_1(f), \dots, \mu_k(f))$$ and $$\widehat{\sigma}^2(f) = g(\widehat{\mu}_1, \dots, \widehat{\mu}_k),$$ then $\widehat{\sigma}^2$ is a consistent estimator of $\sigma^2$. 

**Example** Opinion Poll, revisited
We can write the binomially distributed count data $X$ as $X = Y_1 + \dots + Y_n$ with $Y_i\overset{\text{iid}}{\sim}\mathrm{Bernoulli}(\phi)$. We want to estimate $\phi = \mathbb{E}[Y_1\mid \phi]$. We use $$\widehat{\phi} = \overline{Y}_n = \frac{X}{n}.$$
It is a CAN estimator (WLLN; CLT) of $\phi$ with $$\sigma^2(\phi) = \mathbb{V}\mathrm{ar}(Y_1) = \phi(1-\phi)$$
The $\phi$ is unknown, so we plug in $\widehat{\phi}$. $$\widehat{\sigma}^2 = \widehat{\phi}(1-\widehat{\phi})$$
We have $$\sqrt{n}(\widehat{\phi} - \phi)\Rightarrow \mathcal{N}(0, \widehat{\phi}(1-\widehat{\phi}))$$
If we want an asymptotically valid 95% confidence interval, it should satisfy $$\begin{align*}\gamma(\mathbf{y}) &= \left\{\phi: -1.96\le \frac{\sqrt{n}\left(\widehat{\phi} - \phi\right)}{\sqrt{\widehat{\phi}(1-\widehat{\phi})}}\le 1.96\right\}\\
&= \left\{\phi:\phi\in \left[\widehat{\phi} - 1.96\cdot \sqrt{\frac{\widehat{\phi}(1-\widehat{\phi})}{n}}, \widehat{\phi} + 1.96\cdot \sqrt{\frac{\widehat{\phi}(1-\widehat{\phi})}{n}}\right]\right\}\end{align*}$$

**Example** Food Expenditure
Suppose that Surya surveyed $n$ students at Duke about their food expenditure, recorded as $X_1,\dots, X_n$. To model this data, we use a nonparametric model space $$\mathscr{F} = \{\text{all pdfs with }\mathbb{E}(X_1) <\infty\text{ and }\mathbb{V}\mathrm{ar}(X_1)<\infty\},$$ and the quantity of interest is the population mean, $\mu(f) = \int xf(x)\,dx$. The sample mean $\overline{X}$ is a MoM estimator (and a CAN estimator) of $\mu$. The asymptotic variance of $\overline{X}$ is $\sigma^2(f) = \mu_2(f) - (\mu(f))^2$. A consistent estimator for $\sigma^2$ is $$\widehat{\sigma}^2 = \frac{1}{n-1}\sum_{i=1}^n (X_i - \overline{X}_n)^2 = S^2$$ Then, we land on $$\sqrt{n}(\overline{X} - \mu)\Rightarrow \mathcal{N}(0, S^2),$$ which follows an asymptotically valid 95% confidence interval, $$\begin{align*}
\gamma(\mathbf{x}) &= \left\{\mu:-1.96\le \frac{\sqrt{n}(\overline{X} - \mu)}{S^2} \le 1.96\right\}\\
&= \left\{\mu: \mu\in \left[\overline{X} - 1.96\cdot \frac{S}{\sqrt{n}}, \overline{X} + 1.96\cdot \frac{S}{\sqrt{n}}\right]\right\}
\end{align*}$$
**Example** Food expenditure, but this time estimating variance (Multivariate Estimation)
We want to estimate $\nu(f) = \mathbb{V}\mathrm{ar}(X_1\mid f)$. We discern that $$\nu(f) = \mu_2(f) - \mu(f)^2$$ $$\nu(f) = g(\mu(f), \mu_2(f))$$ if we define $g(x,y) = y - x^2$. 

The vector-valued estimator $(\overline{X}, \overline{X^2})^\top$ is a CAN estimator of $(\mu(f), \mu_2(f))^\top$. Then, $$\sqrt{n}\left(\begin{pmatrix}\overline{X} \\ \overline{X^2}\end{pmatrix} - \begin{pmatrix} \mu(f) \\ \mu_2(f) \end{pmatrix}\right)\Longrightarrow \mathcal{N}_2(0, \Sigma(f))$$  where $\Sigma$ is the covariance matrix. $$\Sigma(f) = \begin{pmatrix}
\mathbb{V}\mathrm{ar}(X_1\mid f) & \mathbb{C}\mathrm{ov}(X_1, X_1^2\mid f)\\
\mathbb{C}\mathrm{ov}(X_1, X_1^2\mid f) & \mathbb{V}\mathrm{ar}(X_1^2\mid f)
\end{pmatrix}$$
We can't just report the interval rule of this vector: We need to apply the Delta Method to change the variable. Use the $g$ defined above, $$\lambda(f) = \begin{pmatrix}
\frac{\partial g}{\partial \mu(f)} \\ \frac{\partial g}{\partial \mu_2(f)}
\end{pmatrix} = \begin{pmatrix}
-2\mu(f)\\ 1
\end{pmatrix}$$
The asymptotic variance of $\sqrt{n}(S_n^2-v(f))$ is $$\tau^2(f) = \lambda(f)^\top\Sigma(f)\lambda(f) = \begin{pmatrix}
-2\mu(f) & 1
\end{pmatrix}\begin{pmatrix}
\mathbb{V}\mathrm{ar}(X_1\mid f) & \mathbb{C}\mathrm{ov}(X_1, X_1^2\mid f)\\
\mathbb{C}\mathrm{ov}(X_1, X_1^2\mid f) & \mathbb{V}\mathrm{ar}(X_1^2\mid f)
\end{pmatrix}\begin{pmatrix}
-2\mu(f)\\ 1
\end{pmatrix}$$
Then, we obtain $$\sqrt{n}(S_n^2 - \nu(f))\Longrightarrow \mathcal{N}(0, \tau^2(f))$$
However, we do not know $\Sigma(f)$, so we choose $$\widehat{\Sigma}(f) = \begin{pmatrix}
\frac{1}{n}\sum(X_i - \overline{X})^2 & \frac{1}{n}\sum (X_i - \overline{X})(X_i^2 - \overline{X^2})\\
\frac{1}{n}\sum (X_i - \overline{X})(X_i^2 - \overline{X^2}) & \frac{1}{n}\sum (X_i^2 - \overline{X^2})^2
\end{pmatrix}$$ and $$\widehat{\lambda} = \begin{pmatrix}
-2\overline{X}\\ 1
\end{pmatrix},$$ which follows $$\widehat{\tau^2} = \widehat{\lambda}^\top\widehat{\Sigma}\widehat{\lambda}.$$
Now, we can conclude $$\sqrt{n}(S_n^2 - \nu(f))\Longrightarrow \mathcal{N}(0, \widehat{\tau^2}(f))$$ and subsequently obtain an interval rule centered at $S_n^2$. I have zero interest in evaluating the numerical result, so the discussion ends here.

### 4.3.2 Maximum Likelihood Estimation (MLE)
The likelihood function is defined by $$\mathcal{L}(\boldsymbol{\theta} \mid \mathbf{x}) = \prod_{i=1}^n f(x_i\mid \boldsymbol{\theta})$$
**Def** MLE
For each sample point $\mathbf{x}$, let $\widehat{\theta}(\mathbf{x})$ be a parameter value at which $\mathcal{L}(\theta\mid \mathbf{x})$ attains its maximum as a function of $\theta$, with $\mathbf{x}$ held fixed. A *maximum likelihood estimator (MLE)* of the parameter $\theta$ on a sample $\mathbf{X}$ is $\widehat{\theta}(\mathbf{X})$. 

**Thm** Invariance property of MLEs
If $\widehat{\theta}$ is the MLE of $\theta$, then for any function $\tau(\theta)$, the MLE of $\tau(\theta)$ is $\tau(\widehat{\theta})$. 

**Example** Exponential Distribution (again)
Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim}\mathrm{Exponential}(\lambda)$, $\lambda>0$. The likelihood is $$\mathcal{L}(\lambda\mid \mathbf{x}) = \prod_{i=1}^n\lambda e^{\lambda x_i} = \lambda^n \exp\left(-\lambda \sum_{i=1}^n x_i\right)$$
The log-likelihood is $$\ell(\lambda\mid \mathbf{x}) = n\log \lambda - \lambda \sum_{i=1}^n x_i$$
Set its derivative to zero, $$\dot{\ell}(\lambda) = \frac{n}{\lambda} - \sum_{i=1}^n x_i \overset{\text{set}}{=} 0$$ $$\widehat{\lambda} = \frac{n}{\sum X_i} = \frac{1}{\overline{X}}$$
Verify that the log-likelihood indeed attains the maximum, $$\ddot{\ell}(\lambda) = -\frac{n}{\lambda^2}<0$$
We can invoke the invariance property to find the MLE of $\sigma^2$: $$\sigma^2(\lambda) = \mathbb{V}\mathrm{ar}(X_1\mid \lambda) = \frac{1}{\lambda^2}$$ $$\widehat{\sigma^2} = \frac{1}{\widehat{\lambda}} = \overline{X}^2$$
**Example** Food Expenditure, revisited
Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim}\mathrm{LogNormal}(\lambda, \tau^2)$, $\lambda\in \mathbb{R}$, $\tau\in \mathbb{R}_+$, with the pdf
$$f(x\mid \lambda, \tau^2) = \frac{1}{x\sqrt{2\pi\tau^2}}\exp\left\{-\frac{(\log x - \lambda)^2}{2\tau^2}\right\}$$
$$\mathcal{L}(\lambda, \tau^2\mid \mathbf{x}) \propto \prod_{i=1}^n \frac{1}{\sqrt{\tau^2}}\exp\left\{-\frac{(\log x_i - \lambda)^2}{2\tau^2}\right\}$$ $$\ell(\lambda, \tau^2\mid \mathbf{x}) = -\frac{n}{2}\log \tau^2 - \frac{\sum_{i=1}^n (x_i - \lambda)^2}{2\tau^2}$$
For the simplicity of the notation, let $\kappa = \tau^2$. $$\ell(\lambda, \kappa\mid \mathbf{x}) = -\frac{n}{2}\log \kappa - \frac{\sum_{i=1}^n (x_i - \lambda)^2}{2\kappa}$$
We find the derivative against $\lambda$: $$\nabla_\lambda \ell = \frac{\sum_{i=1}^n(x_i - \lambda)}{\kappa} = \frac{n(\overline{x} - \lambda)}{\kappa} \overset{\text{set}}{=} 0,$$ which follows $\widehat{\lambda} = \overline{X}$. 

We find the derivative against $\kappa$, $$\nabla_\kappa\ell = -\frac{n}{2\kappa}+ \frac{\sum_{i=1}^n (x_i - \lambda)^2}{2\kappa^2}\overset{\text{set}}{=}0,$$ which follows $\widehat{\kappa} = S^2_n$. 

We are supposed to verify that the Hessian matrix, $$\nabla^2\ell(\lambda, \kappa\mid \mathbf{x}) = \begin{pmatrix}
\frac{\partial^2}{\partial \theta_1^2}\ell & \frac{\partial^2}{\partial \theta_1\partial \theta_2}\ell\\
\frac{\partial^2}{\partial \theta_2\partial \theta_1}\ell & \frac{\partial^2}{\partial \theta_2^2}\ell
\end{pmatrix}$$ is negative definite. Since it is tedious work, omitted!

*Remark*: The discussion in this section below assumes the following conditions, known as *regularity conditions*: 
- The true parameter $\theta_0$ is interior to the parameter space $\Omega$.
- The support of the pdf $\{x : f(x|\theta) > 0\}$ does not depend on $\theta$ (e.g., this fails for the Uniform$(0, \theta)$ distribution).
- The pdf $f(x|\theta)$ is thrice differentiable with respect to $\theta$.

**Thm** Consistency of MLEs
Let $X_1, \dots, X_n \overset{\text{iid}}{\sim} f(x\mid \theta)$, and let $\mathcal{L}(\theta\mid \mathbf{x}) = \prod_{i=1}^n f(x_i\mid \theta)$ be the likelihood function. Let $\widehat{\theta}$ denote the MLE of $\theta$. Let $\tau(\theta)$ be a continuous function of $\theta$. Under the regularity conditions on $f(x\mid \theta)$ and, hence, $\mathcal{L}(\theta\mid \mathbf{x})$, $\forall \theta\in \Theta$, $$\tau(\widehat{\theta})\overset{p}{\to}\tau(\theta).$$ In other words, $\tau(\widehat{\theta})$ is a consistent estimator of $\tau(\theta)$. 

*Remark*: This course did not introduce the concept of almost sure convergence, so we cannot prove this theorem. Just take it. 

I will refrain from using C&B as a reference for the AN part of MLE behavior, because C&B discussion is always associated with something like asymptotic efficiency - save it to next chapter. 

**Def** Unit Score Function; Fisher's Information
The gradient of the log-likelihood for a single observation is called *the unit score function*, $$S(x,\theta) = \nabla_\theta\log f(x\mid\theta), \quad (x,\theta)\in \mathcal{X}\times \Theta$$ It assumes the expected value of 0. 
*Remark*: It associates with $\dot{\ell}$ by $$\dot{\ell}(\theta) = \sum_{i=1}^n S(x_i, \theta)$$
The variance of the unit score function is called *the unit Fisher's Information*, $$\begin{align*}
I(\theta) &= \mathbb{V}\mathrm{ar}(S(X_1, \theta)\mid \theta)\\
&= -\mathbb{E}[\nabla^2 \log f(X|\theta)]
\end{align*}$$
*Remark*: We continue the discussion with an emphasis of application side. The unit score function is the asymptotic variance of the scaled error, $$\sqrt{n}(\widehat{\theta}_\text{MLE} - \theta) \Rightarrow N(0, I(\theta)^{-1})$$ (There is a sweaty proof on p. 48 of Surya's lecture notes.)

At this stage, we might want to find the asymptotic distribution of some population feature as a function $\zeta(\theta)$. Follows the continuous mapping theorem is the consistency of MLE $\widehat{\zeta}$. We primarily rely on the Delta Method to derive the asymptotic variance of $\sqrt{n}(\widehat{\zeta} - \zeta(\theta))$. $$\sqrt{n}(\widehat{\zeta}_\text{MLE} - \zeta(\theta))\Rightarrow\mathcal{N}(0, \sigma^2(\theta)),$$ where $\sigma^2 = \zeta'(\theta)^\top I(\theta)^{-1}\zeta'(\theta)$. 

There are two ways to calculate the unit Fisher Information: 
- Directly use the definition, $I(\theta) = \mathbb{V}\mathrm{ar}(S(X_1, \theta)\mid \theta)$
- Use the Hessian of the log-likelihood, $I(\theta) = -\mathbb{E}[\dot{S}(X_1, \theta)\mid\theta] = -\mathbb{E}[\nabla^2_\theta \log f(X|\theta)]$

The consistent estimator of $\sigma^2(\theta)$ is obtained by plug in $\theta = \widehat{\theta}_\text{MLE}$ and apply the invariance property of MLE. $$\widehat{\sigma}^2 = \zeta'(\widehat{\theta}_\text{MLE})^\top\widehat{I}^{-1}\zeta'(\widehat{\theta}_\text{MLE})$$
As a recap, Surya, in his solution to Homework 7, has included a "general strategy" for finding asymptotic variance of some sample. 

*General Strategy*: First find the score function $S(x, \theta) = \frac{\partial}{\partial \theta} \log f(x|\theta)$ and the second derivative $\dot{S}(x, \theta) = \frac{\partial}{\partial \theta} S(x, \theta)$. Calculate unit Fisher information either as $I(\theta) = -E[\dot{S}(X_1, \theta)]$ or as $I(\theta) = \mathbb{V}\text{ar}(S(X_1, \theta)|\theta)$, whichever seems easier to carry out. To find an expression for the MLE, set up the first and second order conditions $$ 0 = \dot{\ell}(\hat{\theta}_{\text{MLE}}) = \sum_{i=1}^{n} S(X_i, \hat{\theta}_{\text{MLE}}), \qquad 0 \ge \ddot{\ell}(\hat{\theta}_{\text{MLE}}) = \sum_{i=1}^{n} \dot{S}(X_i, \hat{\theta}_{\text{MLE}}), $$ and solve the first order condition and verify the second order condition. Find the expression of $\zeta = \zeta(\theta)$ and derive $\hat{\zeta}_{\text{MLE}} = \zeta(\hat{\theta}_{\text{MLE}})$. The AV of $\hat{\zeta}_{\text{MLE}}$ is $\dot{\zeta}(\theta)^2 I(\theta)^{-1}$, and $\widehat{\text{AV}}$ is found by plugging in $\hat{\theta}_{\text{MLE}}$ in the expression of AV. 

**Example** Assorted Samples to Illustrate the General Strategy
(a) $X_1, \dots, X_n \overset{\text{iid}}{\sim} \text{Geometric}(p)$, $p \in (0,1)$, with pmf $P(X=x) = (1-p)^{x-1}p$.
Feature of interest: $\zeta = \text{Var}(X_1) = \frac{1-p}{p^2}$.

The unit score function is $$S(x,p) = -\frac{x-1}{1-p}+\frac{1}{p}$$ and the second derivative is $$\dot{S}(x,p) = -\frac{x-1}{(1-p)^2}-\frac{1}{p^2}<0$$
We can find the Fisher information, $$I(\theta) = -\mathbb{E}\left(-\frac{X_1-1}{(1-p)^2} - \frac{1}{p^2}\right) = \frac{\mathbb{E}(X_1)-1}{(1-p)^2}+\frac{1}{p^2} = \frac{1}{p^2(1-p)}$$ (*skipping a couple of steps in between*)

Set the score function to zero, $$\dot{\ell}(\widehat{p}) = \sum_{i=1}^n S(X_i, \widehat{p}) = 0$$ and it follows $$\widehat{p} = \frac{n}{\sum x_i} = \frac{1}{\overline{X}}$$
Put this into the second derivative, it is indeed negative, making it a point where the likelihood function attains its maximum. 

With the invariance property of MLE, we can write $$\widehat{\zeta} = \frac{1-\frac{1}{\overline{X}}}{\frac{1}{\overline{X}^2}} = \overline{X}^2 - \overline{X}$$
The asymptotic variance is given by $$\sigma^2 = (\zeta')^2I(p)^{-1} = \left(-\frac{2}{p^3}+\frac{1}{p^2}\right)^2p^2(1-p) = \left(-\frac{2}{p^2}+\frac{1}{p}\right)^2(1-p) = \frac{(p-2)^2(1-p)}{p^4},$$ which follows the consistent estimator $$\widehat{\sigma^2} = \text{(very complex, not going to plug in }\widehat{p}_\text{MLE})$$
(b) $X_1, \dots, X_n \overset{\text{iid}}{\sim} \text{Rayleigh}(\theta)$, $\theta > 0$, with pdf $f(x|\theta) = \frac{x}{\theta^2} e^{-x^2/(2\theta^2)}$ for $x > 0$.
Feature of interest: $\zeta = \mathbb{E}[X_1^2]$.
(c) $X_1, \dots, X_n \overset{\text{iid}}{\sim} \text{Beta}(\theta, 1)$, $\theta > 0$, with pdf $f(x|\theta) = \theta x^{\theta-1}$ for $0 < x < 1$.
Feature of interest: $\zeta = \mathbb{E}[X_1]$.
### 4.3.3 M-Estimators

## 4.4 Bootstrap


