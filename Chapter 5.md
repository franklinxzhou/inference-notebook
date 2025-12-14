Optimal Learning

This chapter starts with introducing the power function (*finally*). The Casella & Berger definition of $\alpha$ and $\beta$ heavily rely on this concept, but since Surya uses $\beta$ = 1 - Power function, to make it logically smooth, we have to refrain from using the power function as the one, unified tool to understand $\alpha$ and $\beta$, but instead understand them as the probabilities of Type I Error and Type II Error, respectively. 

Anyway, 

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
**Example** Poll Question, revisited
Suppose $X\sim \mathrm{Bin}(n, \phi)$, $n=500$. We test $H_0: \phi = 0.5$ vs. $H_1: \phi = 0.55$. $$\begin{align*}
\Lambda(x) &= \frac{f(x\mid n=500, \phi = 0.55)}{f(x\mid n=500, \phi = 0.5)}\\
&= \frac{\begin{pmatrix} n\\x \end{pmatrix}0.55^x \times 0.45^{n-x}}{\begin{pmatrix} n\\x \end{pmatrix}0.5^n}\\
&= \mathrm{constant}\times\left(\frac{0.55}{0.45}\right)^x
\end{align*}$$
Notice that $\Lambda(x)$ increases as $x$ increases, and more likely $x$ fall into the region where $H_1$ is accepted. This observation is consistent with the prior analysis. 

**Example** Three Scenarios with Metal Plates Analysis (revisited)
(a) $\mathcal{N}$ vs $\mathcal{N}$ with the same variance
Suppose we test $H_0: \mu =2$ vs. $H_1: \mu=3$ based on $X_1, \dots, X_n\overset{\text{iid}}{\sim}\mathcal{N}(\mu, \sigma^2)$ with $\sigma = 0.5$. $$\begin{align*}
\Lambda(\mathbf{X}) &= \frac{\exp\{-\frac{n(\overline{X} - 3)^2}{2\sigma^2}\}}{\exp\{-\frac{n(\overline{X} - 2)^2}{2\sigma^2}\}}\\
&= \exp\left\{-\frac{n}{2\sigma^2}\left((\overline{X} - 3)^2-(\overline{X} - 2)^2\right)\right\}\\
&= \exp\left\{-\frac{n}{2\sigma^2}\left((2\overline{X}-5)(-1)\right)\right\}\\
&= \exp\left\{\frac{n(\overline{X} - 2.5)}{\sigma^2}\right\}
\end{align*}$$

