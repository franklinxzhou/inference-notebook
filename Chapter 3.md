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

## 3.2 Neyman-Pearson Frequentism
