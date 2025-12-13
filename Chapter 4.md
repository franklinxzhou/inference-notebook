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

