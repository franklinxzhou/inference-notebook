Franklin's Statistical Inference Notebook
=======================================

This notebook is an expansion of Prof. Surya Tokdar's Statistical Inference course (STA 532) at Duke University. It aims to expand the lecture notes with additional explanations, examples, and derivations. It aligns the content with the textbook "Statistical Inference" by Casella and Berger (2002).

For best viewing experience, open with [Obsidian](https://obsidian.md/).

# Chapter 1: Probability Review
*Probability spaces, conditioning, random variables, expectation, moments, multivariate normal, and limit theory (WLLN, CLT).*

## Casella & Berger Reference
Chapter 1 (probability spaces and conditioning)
 - Set theory, probability axioms, $\S$ 1.1 - 1.2
 - Conditional probability, independence, $\S\S$ 1.1.3 - 1.1.5, 1.4.6
 - Random variables, distribution functions, pmf/pdf, $\S\S$ 1.3, 1.4

Chapter 2 (expectations, moments, moment generating functions)
 - Distribution of functions of a RV, $\S$ 1.5
 - Expected values, moments, mgf, $\S\S$ 1.6 - 1.7
 - Differentiating under the integral sign, $\S\S$ 1.6 - 1.7 (See exercises)

Chapter 4 (multivariate definitions, covariance, and independence)
 - Joint/marginal/conditional distributions, bivariate transforms, $\S\S$ 1.3, 1.4, 1.5
 - Covariance, correlation, multivariate distributions, $\S\S$ 1.7.3 - 1.7.5, 1.8

Chapter 5 (convergence concepts)
 - Convergence concepts (LLN/CLT etc.), $\S$ 1.9
 - Sampling from the normal, chi-square / t / F, $\S$ 8.2, 8.3

# Chapter 2: Statistical Inference
*Statistical models, inductive reasoning, the likelihood function, and distinguishing Bayesian vs. Classical paradigms.*

## Casella & Berger Reference
Chapter 5 (basic concepts of a random sample)
 - “Statistical model + iid sample” framing, $\S$ 2.1

Chapter 6 (the sufficiency principle, the likelihood principle)
 - Sufficient statistics, likelihood function, $\S\S$ 2.2 - 2.3

Chapter 7 - Chapter 9 Introduction
 - Estimation, testing, and indirect interval estimation, $\S$ 2.3

# Chapter 3: Classical Inference
*Fisher's Significance Testing (p-values), Neyman-Pearson Frequentism (Type I/II errors), and Confidence Intervals.*

## Casella & Berger Reference
Chapter 8 (hypothesis testing)
 - Methods of finding tests (Neyman-Pearson lemma, likelihood ratio tests), $\S\S$ 3.2, 3.5, later 5.1
 - Methods of evaluating tests (power, size, error probabilities), $\S\S$ 3.2.2 - 3.2.4

Chapter 9 (interval estimation)
 - Construction and evaluation of confidence intervals, $\S$ 3.4 (coverage, confidence coefficient, interpretation, "how not to interpret")

# Chapter 4: Classical Methods
*Large sample theory, Consistency (CAN estimators), Maximum Likelihood Estimation (MLE), and Bootstrapping.*

## Casella & Berger Reference
Chapter 7 (point estimation)
 - Methods of finding estimators (MLE, MOM, Bayes estimators in a classical frame)
 - Evaluating estimators (bias, variance, MSE, UMVUE)

Chapter 10 (asymptotic evaluations)
 - Asymptotics for point estimators, $\S$ 4.2 (CAN estimators), $\S$ 4.5.2 (asymptotic normality of MLE)
 - Asymptotic tests and intervals, $\S$ 4.2.3
 
*Note*: C&B touches bootstrapping very lightly; see the lecture notes for details.

# Chapter 5: Optimal Learning
*Optimal test rules (UMP tests), Neyman-Pearson Lemma, Cramér-Rao Lower Bound, and Shrinkage (James-Stein).*

## Casella & Berger Reference
Chapter 7 (point estimation)
 - Cramér-Rao inequality,  under methods of evaluating estimators, $\S$ 5.3
 
Chapter 8 (hypothesis testing)
 - UMP/most powerful test ($\S$ 8.3.2), $\S$ 5.1
 
Chapter 10 (asymptotic evaluations)
 - Comparisons of asymptotic efficiency, asymptotic relative efficiency (ARE), $\S$ 5.2

*Note*: $\S$ 5.4, shrinkage and James-Stein estimators, is not covered in C&B. See the lecture notes $\S$ 5.4 for details.

