Optimal Learning

This chapter starts with introducing the power function (*finally*). The Casella & Berger definition of $\alpha$ and $\beta$ heavily rely on this concept, but since Surya uses $\beta$ = 1 - Power function, to make it logically smooth, we have to refrain from using the power function as the one, unified tool to understand $\alpha$ and $\beta$, but instead understand them as the probabilities of Type I Error and Type II Error, respectively. 

## 5.1 Uniformly More Powerful (UMP) Test

**Def** Power function 
Suppose that the region of $\mathbf{X}$ to accept $H_1$ is $R$. Then, the *power function* is the probability that $\mathbf{X}$ is in R. $$\mathrm{power}(\mathbf{x}; P) = P(\mathbf{X}\in R), P\in \mathscr{P}$$
As noted in the definition, the power function is dependent on the probability law of choice. Suppose $\delta$ is the test rule, if $P\in \mathscr{P}_0$, then $$\mathrm{power}(\delta; P) = \mathbb{P}(\text{Type I Error})$$ $$\mathrm{size}(\delta) = \max_{P\in \mathscr{P}_0}\mathrm{power}(\delta; P)$$
If $P\in \mathscr{P}_1$, $$\mathrm{power}(\delta; P) = 1-\mathbb{P}(\text{Type II Error})$$
*Remark*: For any two tests with identical size, we should use the one with more power at the alternative.

**Example** 
Suppose $X \sim \mathcal{N}(\mu, 1)$, $$H_0: \mu\le 0, \qquad H_1: \mu >0$$ let the rule be $\delta$: reject $H_0$ if $X>1.64$. $$\begin{align*}
\mathrm{power}(\delta; \mu) &= \mathbb{P}(X>1.64\mid \mu)\\
&= 1- \Phi(1.64-\mu)\\
&= \Phi(\mu - 1.64)
\end{align*}$$
**Def** Uniformly More Powerful (UMP) Test
Let $\mathcal{C}$ be the class of all level $\alpha$ tests. A test in class $\mathcal{C}$, with rule $\delta$, is called the *Uniformly More Powerful (UMP)* test if $$\mathrm{power}(\delta; P)\ge \mathrm{power}(\delta'; P)$$ for every $P\in \mathscr{P}_1$ and every $\delta'$ that is a test rule of a test in $\mathcal{C}$. 

**Thm** Neyman-Pearson Lemma
Consider testing $H_0: P\in \mathscr{P}_0$ versus $H_1: P\in \mathscr{P}_1$, and the corresponding rule is accepting $H_1$ if $\mathbf{x}\in R$ and accepting $H_0$ if $\mathbf{x}\in R^c$. Assume that $p_0(\mathbf{x})$ and $p_1(\mathbf{x})$ give the pdfs or pmfs under probability laws $P_0$ and $P_1$. The testing rule $$\mathbf{x}\in R\quad \text{if} \quad p_1(\mathbf{x})>kp_0(\mathbf{x})$$ and $$\mathbf{x}\in R^c \quad \text{if} \quad p_1(\mathbf{x})<kp_0(\mathbf{x}),$$ for some $k\ge 0$ and $\alpha = P(\mathbf{X}\in R)$, results in a UMP level $\alpha$ test. Denoting the ratio of $p_1(\mathbf{x})/p_0(\mathbf{x})$ as $\Lambda$, $$\alpha = P_0(\Lambda\ge k).$$
**Corr** 
Consider testing $H_0: P\in \mathscr{P}_0$ versus $H_1: P\in \mathscr{P}_1$, and the corresponding rule is accepting $H_1$ if $\mathbf{x}\in R$ and accepting $H_0$ if $\mathbf{x}\in R^c$. Suppose there is a statistic $T = T(\mathbf{X})$ s.t. $\forall P\in \mathscr{P}_1$, assuming that $p_0(\mathbf{x})$ and $p_(\mathbf{x})$ give the pdfs or pmfs under probability laws $P_0$ and $P$, $$\Lambda_P(\mathbf{X}) = \frac{p(\mathbf{X})}{p_0(\mathbf{X})}$$ is monotonically increasing, then $\forall c>0$, if $$R = \{\mathbf{x}: T(\mathbf{x})\ge c\}$$ then the corresponding test is UMP level $\alpha$ test, where $\alpha = P_0(T\ge c)$. Furthermore, using the test statistic $T$ is equivalent to using the maximum likelihood test statistic. 

**Example** Poll Question, revisited
Suppose $X\sim \mathrm{Bin}(n, \phi)$, $n=500$. We test $H_0: \phi = 0.5$ vs. $H_1: \phi = 0.55$. $$\begin{align*}
\Lambda(x) &= \frac{f(x\mid n=500, \phi = 0.55)}{f(x\mid n=500, \phi = 0.5)}\\
&= \frac{\begin{pmatrix} n\\x \end{pmatrix}0.55^x \times 0.45^{n-x}}{\begin{pmatrix} n\\x \end{pmatrix}0.5^n}\\
&= \mathrm{constant}\times\left(\frac{0.55}{0.45}\right)^x
\end{align*}$$
Notice that $\Lambda(x)$ increases as $x$ increases, and more likely $x$ fall into the region where $H_1$ is accepted. This observation is consistent with the prior analysis. 

**Example** Three Scenarios with Metal Plates Analysis (revisited)
(a) $\mathcal{N}$ vs simple $\mathcal{N}$ alternative with the same variance
Suppose we test $H_0: \mu =2$ vs. $H_1: \mu=3$ based on $X_1, \dots, X_n\overset{\text{iid}}{\sim}\mathcal{N}(\mu, \sigma^2)$ with $\sigma = 0.5$. $$\begin{align*}
\Lambda(\mathbf{X}) &= \frac{\exp\{-\frac{n(\overline{X} - 3)^2}{2\sigma^2}\}}{\exp\{-\frac{n(\overline{X} - 2)^2}{2\sigma^2}\}}\\
&= \exp\left\{-\frac{n}{2\sigma^2}\left((\overline{X} - 3)^2-(\overline{X} - 2)^2\right)\right\}\\
&= \exp\left\{-\frac{n}{2\sigma^2}\left((2\overline{X}-5)(-1)\right)\right\}\\
&= \exp\left\{\frac{n(\overline{X} - 2.5)}{\sigma^2}\right\}
\end{align*}$$
Citing the monotonically increasing nature of $\Lambda(\mathbf{X})$, this is equivalently to "accept $H_1$ if $\overline{X}\ge c$" for some $c$. 
(b) $\mathcal{N}$ vs one-sided $\mathcal{N}$ alternative with the same variance
Suppose $H_1$ is now $\mu>2$. $$\Lambda(\mathbf{X}; \mu) = \exp\left\{\frac{n(\mu-2)(\overline{X} - \frac{2+\mu}{2})}{\sigma^2}\right\}$$
Here, we apply the **Corr** above, using $T(\mathbf{X}) = \overline{X}$. Then, $$\Lambda(\mathbf{X};\mu)>k \Leftrightarrow \overline{X} >c$$ and since $\alpha = P_0(T\ge c)$, $\overline{X}\sim \mathcal{N}(\mu, \sigma^2/n)$, $$\overline{X}>c \Leftrightarrow \overline{X} > 2+\frac{\sigma}{\sqrt{n}}z_{1-\alpha}$$
(c) $\mathcal{N}$ vs two-sided $\mathcal{N}$ alternative - UMP may not exist. 

**Def** Likelihood Ratio Test Statistic (LRT)
The *likelihood ratio test* statistic for $H_0: \theta\in \Theta_0$ vs. $H_1: \theta\in \Theta_c^c$ is $$\Lambda(\mathbf{X}) = \frac{\sup_{\theta\in \Theta}\mathcal{L}(\theta; \mathbf{x})}{\sup_{\theta\in \Theta_0}\mathcal{L}(\theta; \mathbf{x})} = \frac{\mathcal{L}(\widehat{\theta}_\text{MLE}; \mathbf{x})}{\mathcal{L}(\widehat{\theta}_\text{MLE}; \mathbf{x})}$$
## 5.2 Asymptotic Relative Efficiency
**Def** Asymptotic Relative Efficiency (ARE)
If two estimators $W_n$ and $V_n$ satisfy $$\sqrt{n}(W_n - \tau(\theta))\Rightarrow \mathcal{N}(0, \sigma^2_W)$$ $$\sqrt{n}(V_n - \tau(\theta))\Rightarrow \mathcal{N}(0, \sigma^2_V),$$ the *asymptotic relative efficiency* (ARE) of $V_n$ wrt to $W_n$ is $$\mathrm{ARE}(V_n, W_n) = \frac{\sigma^2_W}{\sigma^2_V}$$
*Remark*: ARE denotes the excess sample size needed by rules based on $W_n$ relative to those based on $V_n$ guaranteeing the same error controls. For example, the 95% confidence interval with margin of error $\epsilon$. $$\epsilon = 1.96\times \frac{\sigma_W}{\sqrt{n_W}} = 1.96\times \frac{\sigma_V}{\sqrt{n_V}}$$ $$\frac{n_W}{n_V} = \frac{\sigma^2_W}{\sigma^2_V}$$
**Thm** The Cramer-Rao Lower Bound
Let $T = T(\mathbf{X})$ be a statistic with finite variance and let $m(\theta) = \mathbb{E}(T\mid \theta)$. Then $$\mathbb{V}\mathrm{ar}(T\mid \theta)\ge \frac{\nabla_\theta m(\theta)^\top[I(\theta)]^{-1}\nabla_\theta m(\theta)}{n}$$ where $I(\theta)$ denotes the unit Fisher information.

*Proof*: Suppose $T = T(X_1, \dots, X_n)$ and $S = S(X_1, \theta) + \dots + S(X_n, \theta)$, where $S(X_i, \theta) = \nabla \log f(X_i\mid \theta)$. We know that $\mathbb{E}(S) = 0$ and $\mathbb{V}\mathrm{ar}(S) = nI(\theta)$. This follows $$\begin{align*}
\mathbb{C}\mathrm{ov}(T,S) &= \mathbb{E}(TS) - \mathbb{E}(T)\mathbb{E}(S)\\ &= \mathbb{E}(TS)
\end{align*}$$
Over the joint density $$p_\theta(\mathbf{x}) = \prod_{i=1}^n f(x_i\mid \theta),$$ $$\mathbb{E}(TS) = \int T(\mathbf{x})S(\mathbf{x}, \theta)p_\theta(\mathbf{x})\,d\mathbf{x}$$
Here, we have a trick: $$\begin{align*}
S(\mathbf{x}) &= \prod_{i=1}^n S(x_1, \theta)\\
&= \sum_{i=1}^n\nabla_\theta \log f(x_i\mid \theta)\\
&= \nabla_\theta \left(\sum_{i=1}^n\log f(x_i\mid \theta)\right)\\
&= \nabla_\theta\log p_\theta(\mathbf{x})\\
&= \frac{\nabla_\theta p_\theta(\mathbf{x})}{p_\theta(\mathbf{x})}
\end{align*}$$
Plug in this into the integral, $$\int T(\mathbf{x})S(\mathbf{x}, \theta)p_\theta(\mathbf{x})\,d\mathbf{x} = \int T(\mathbf{x})\nabla_\theta p_\theta(\mathbf{x})\, d\mathbf{x}$$
Under the regularity conditions, swapping the derivative and integral is allowed. $$\int T(\mathbf{x})\nabla_\theta p_\theta(\mathbf{x})\, d\mathbf{x} = \nabla_\theta \int T(\mathbf{x})p_\theta(\mathbf{x})\,d\mathbf{x} = \nabla_\theta \mathbb{E}[T] = \nabla_\theta m(\theta)$$
This leads to $\mathbb{C}\mathrm{ov}(T,S) = \nabla_\theta m(\theta)$. We can construct the covariance matrix for $(T,S)^\top$. $$M = \begin{pmatrix}
\mathbb{V}\mathrm{ar}(T) & \mathbb{C}\mathrm{ov}(T,S)\\
\mathbb{C}\mathrm{ov}(S,T) & \mathbb{V}\mathrm{ar}(S)
\end{pmatrix} = \begin{pmatrix}
\mathbb{V}\mathrm{ar}(T) & [\nabla_\theta m(\theta)]^\top\\
\nabla_\theta m(\theta) & nI(\theta)
\end{pmatrix}$$ and this matrix must be positive semi-definite. $$\mathbb{V}\mathrm{ar}(T)\ge \frac{\nabla_\theta m(\theta)^\top[I(\theta)]^{-1}\nabla_\theta m(\theta)}{n}$$
*Remark*: If $\widehat{\zeta}$ is unbiased, then $$\mathbb{V}\mathrm{ar}(T)\ge \frac{\dot{\zeta}(\theta)^\top[I(\theta)]^{-1}\dot{\zeta}(\theta)}{n}$$
As $n\to\infty$, $\widehat{\zeta}_\text{MLE}$ is CAN for $\zeta$ with asymptotic variance $\sigma^2(\theta) = \dot{\zeta}(\theta)^\top[I(\theta)]^{-1}\dot{\zeta}(\theta)$. It is nearly unbiased (per the definition of a consistent estimator) and the limit of its variance is CRLB. 

**Def** Risk 
Suppose that we have an estimator $\widehat{\mu}$ for some parameter $\mu$. Then, the *risk* of $\widehat{\mu}$ is expected value of any loss function $L$. $$R(\hat{\mu}, \mu) = \mathbb{E}[L(\hat{\mu}, \mu)]$$
One common example of risk is the mean squared error risk, $$\text{MSE}(\hat{\mu}) = \mathbb{E}[(\hat{\mu} - \mu)^2]$$
## 5.3 Empirical Bayes
Suppose that we have $p$ independent observations $Y_j \sim N(\mu_j, 1)$ and we want to estimate all $\mu_j$ at once. MLE approach estimates each $\mu_j$ with its own corresponding $Y_j$, but this is suboptimal with large $p$. 

Instead of believing each data point entirely, we "shrink" the estimates toward a common value (like the grand mean $\bar{Y}$ or 0). $$\hat{\mu}_j = \bar{Y} + r_+ \cdot (Y_j - \bar{Y})$$
When $r_+ = 0$, it is a full shrinkage.

This sacrifices a little bit of bias (moving estimates away from their observed values) to gain a large reduction in variance, resulting in lower overall total error (Risk).

This relies on the "Indirect Evidence" premise. Extreme observations are likely to be outliers. By shrinking them, you correct for the noise that pushes observations to extremes.

**Example** The James-Stein Estimator

The James-Stein adaptive shrinkage factor is $$r = 1 - \frac{p-3}{(p-1)S^2}$$