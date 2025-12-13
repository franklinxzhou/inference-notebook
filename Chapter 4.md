Classical Methods

*Remark*: The Chapter 3 does not address much of "how to find a rule" question, but this chapter will dive into this question.

## 4.1 Introduction
**Def** Pivotal quantity AKA pivot
A random variable $Q(\mathbf{X},\theta)$ is a *pivotal quantity* (or *pivot*) if the distribution of $Q(\mathbf{X},\theta)$ is independent of all parameters. That is, if $\mathbf{X}\sim F(\mathbf{x}\mid \theta)$, then $Q(\mathbf{X}, \theta)$ has the same distribution for all values of $\theta$. 

**Examples** Gaussian and Exponential Data
(a) Suppose $X_1, \dots, X_n\overset{\text{iid}}{\sim} \mathcal{N}(\mu, \sigma^2)$ (with $\sigma^2$ known), then $$Z = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}}\sim \mathcal{N}(0,1)$$ is a pivotal quantity.
(b) Suppose $X_1,\dots, X_n\overset{\text{iid}}{\sim}\mathrm{Exponential}(\lambda)$, $\lambda\in \mathbb{R}_+$, then $$Z = \lambda \bar{X} \sim\mathrm{Gamma}(n,n)$$ is a pivotal quantity. This is a sample mean scaled from the rate (inverse of mean): 
$$\sum_{i=1}^n X_i\sim \mathrm{Gamma}(n,\lambda)$$$$\bar{X} = \frac{1}{n}\sum_{i=1}^n X_i\sim \mathrm{Gamma}(n,n\lambda),$$ so
 $$\lambda \bar{X} \sim \mathrm{Gamma}(n,n).$$
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
(a) We have shown that if $X_1, \dots, X_n\overset{\text{iid}}{\sim} \mathcal{N}(\mu, \sigma^2)$, $$Z = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}}\sim \mathcal{N}(0,1)$$
Then, we can write $$\begin{align*}\gamma(\mathbf{x}) &= \left\{\mu: \Phi^{-1}(\alpha/2)\le \frac{\bar{x} - \mu}{\sigma/\sqrt{n}}\le \Phi^{-1}(1-\alpha/2)\right\}\\
&= \left\{\mu:\mu\in \left[\bar{x} - \frac{\sigma}{\sqrt{n}}\Phi^{-1}\left(1-\frac{\alpha}{2}\right), \bar{x} - \frac{\sigma}{\sqrt{n}}\Phi^{-1}\left(\frac{\alpha}{2}\right)\right]\right\}\end{align*}$$
Set $a = \Phi^{-1}\left(1-\frac{\alpha}{2}\right)$, $$\gamma(\mathbf{x}) = \left\{\mu: \mu\in \left[\bar{x} - a\frac{\sigma}{\sqrt{n}}, \bar{x}+a\frac{\sigma}{\sqrt{n}}\right]\right\}$$
Specifically, if $\alpha = 0.05$, $a = 1.96$. 

Here, $\sigma$ is a nuisance quantity, so the $Z$ here is an *extended pivot*. The discussion above is solely based on the assumption that *$\sigma^2$ is known*, but usually it is not the case. One practical way is to plug in an estimator of $\sigma$
, $S$, and notice the resulting approximate pivot follows $t_{n-1}$ distribution instead. The rule becomes $$\gamma(\mathbf{x}) = \left\{\mu: \mu\in\left[\bar{x} - t_{1-\alpha/2, n-1}\frac{S}{\sqrt{n}}, \bar{x} + t_{1-\alpha/2, n-1}\frac{S}{\sqrt{n}}\right]\right\}$$
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
With WLLN, $\bar{X} \overset{p}{\to}\mathbb{E} = 1/\lambda$. This follows $1/\bar{X}\overset{p}{\to} \lambda$. Let $\widehat{\lambda} = 1/\bar{X}$, then $\widehat{\lambda}\overset{p}{\to}\lambda$, so $\widehat{\lambda}$ is a consistent estimator. With CLT, notice that $\bar{X}\sim \mathrm{Gamma}(n, n\lambda)$. We then see $$\sqrt{n}\left(\bar{X} - \frac{1}{\lambda}\right)\Rightarrow \mathcal{N}\left(0, \frac{1}{\lambda^2}\right)$$
Use Delta Theorem to change the variable: Let $g(\bar{X}) = \frac{1}{\bar{X}}$, then $g(x) = \frac{1}{x}$, $g'(x) = -\frac{1}{x^2}$. This follows $$\sqrt{n}\left(\widehat{\lambda} - \lambda\right)\Rightarrow \mathcal{N}\left(0, \lambda^2\right)$$
The asymptotic variance of $\widehat{\lambda}$ is therefore $\lambda^2$. Notice also we can put $\widehat{\lambda}$ into the asymptotic variance, $\widehat{\sigma}^2$, then $$\widehat{\sigma}^2 = \frac{1}{\bar{x}^2}\overset{p}{\to} \lambda^2$$If we want to construct a 95% confidence interval, we can surely construct the pivot. $$Z = \frac{\sqrt{n}\left(\widehat{\lambda} - \lambda\right)}{\sigma}$$
Using Slutsky's theorem, we can construct the approximate$$\tilde{Z} = \frac{\sqrt{n}\left(\widehat{\lambda} - \lambda\right)}{\widehat{\sigma}}\Rightarrow \mathcal{N}(0,1)$$
Recall, we can identify an asymptotic confidence set by $$\begin{align*}\gamma(\mathbf{x}) &= \left\{\lambda: \Phi^{-1}(\alpha/2)\le \frac{\sqrt{n}\left(\widehat{\lambda} - \lambda\right)}{\widehat{\sigma}}\le \Phi^{-1}(1-\alpha/2)\right\}\\
&= \left\{\lambda:\lambda\in \left[\widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\Phi^{-1}\left(1-\frac{\alpha}{2}\right), \widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\Phi^{-1}\left(\frac{\alpha}{2}\right)\right]\right\}\end{align*}$$ with $\mathbb{P}(\lambda\in \gamma) = 1-\alpha$. Specifically, if we want an asymptotically 95% interval rule, we can have $$\gamma(\mathbf{x}) = \left\{\lambda:\lambda\in \left[\widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\cdot 1.96, \widehat{\lambda} - \frac{\widehat{\sigma}}{\sqrt{n}}\cdot 1.96\right]\right\}$$
Compare this with an exact 95% interval rule, where we use the exact pivot $2\lambda n\bar{X}\sim \chi^2_{2n}$. We have illustrated previously that $$\begin{align*}
\gamma(\mathbf{x}) &= \left\{\lambda: \chi^2_{2n, \alpha/2}\le 2\lambda \sum_{i=1}^n x_i \le \chi^2_{2n, 1-\alpha/2} \right\}\\
&= \left\{\lambda: \lambda\in \left[\frac{\chi^2_{2n, \alpha/2}}{2\sum x_i}, \frac{\chi^2_{2n, 1-\alpha/2}}{2\sum x_i}\right]\right\}
\end{align*}$$
## 4.3 Methods to Find Estimators
### 4.3.1 Estimation via Sample Averages (Method of Moment Estimation, MoM)
Suppose that we estimate $\zeta(f) = \mathbb{E}[h(X_1)|f]$. One way to estimate this population feature is through using the corresponding sample average: $$\hat{\zeta} = \bar{H}_n = \frac{1}{n} \sum_{i=1}^n h(X_i)$$
* This estimator is **consistent** due to WLLN.
* This estimator is **asymptotically normal** with, scaled by $\sqrt{n}$, an asymptotic variance equal to the true variance $\sigma^2(f) = \mathbb{V}ar[H_1|f]$. 

The true variance $\sigma^2(f)$ usually depends on unknown population moments $\mu_i(f)$, so we typically need an estimator for the variance, $\widehat{\sigma}^2(f)$. By continuous mapping theorem, if $$\sigma^2(f) = g(\mu_1(f), \dots, \mu_k(f))$$ and $$\widehat{\sigma}^2(f) = g(\widehat{\mu}_1, \dots, \widehat{\mu}_k),$$ then $\widehat{\sigma}^2$ is a consistent estimator of $\sigma^2$. 

**Example** Opinion Poll, revisited
We can write the binomially distributed count data $X$ as $X = Y_1 + \dots + Y_n$ with $Y_i\overset{\text{iid}}{\sim}\mathrm{Bernoulli}(\phi)$. We want to estimate $\phi = \mathbb{E}[Y_1\mid \phi]$. We use $$\widehat{\phi} = \bar{Y}_n = \frac{X}{n}.$$
It is a CAN estimator (WLLN; CLT) of $\phi$ with $$\sigma^2(\phi) = \mathbb{V}\mathrm{ar}(Y_1) = \phi(1-\phi)$$
The $\phi$ is unknown, so we plug in $\widehat{\phi}$. $$\widehat{\sigma}^2 = \widehat{\phi}(1-\widehat{\phi})$$
We have $$\sqrt{n}(\widehat{\phi} - \phi)\Rightarrow \mathcal{N}(0, \widehat{\phi}(1-\widehat{\phi}))$$
If we want an asymptotically valid 95% confidence interval, it should satisfy $$\begin{align*}\gamma(\mathbf{y}) &= \left\{\phi: -1.96\le \frac{\sqrt{n}\left(\widehat{\phi} - \phi\right)}{\sqrt{\widehat{\phi}(1-\widehat{\phi})}}\le 1.96\right\}\\
&= \left\{\phi:\phi\in \left[\widehat{\phi} - 1.96\cdot \sqrt{\frac{\widehat{\phi}(1-\widehat{\phi})}{n}}, \widehat{\phi} + 1.96\cdot \sqrt{\frac{\widehat{\phi}(1-\widehat{\phi})}{n}}\right]\right\}\end{align*}$$
### 4.3.2 Maximum Likelihood Estimation (MLE)

### 4.3.3 M-Estimators

## 4.4 Bootstrap


