---
layout: post
title: "Basic statistics"
author: "mathilda"
categories: "main"
---
## References
1. [Berkeley's stat210a](https://stat210a.berkeley.edu/fall-2024/)

## Exponential family
We say the model $\mathcal{P}=\{\mathcal{P}_\nu:\nu\in\Xi\}$ is an $s$-parameter exponential family if it is defined by a family of densities of the form

$$ p_\nu(x)=\exp(\nu'T(x)-A(\nu))h(x) $$

all w.r.t a common dominating measure $\mu$, i.e. a measure $\mu$ s.t $P_\nu\ll\mu$ for all $\nu\in\Xi$. With 

- $T:\mathcal{X}\rightarrow\mathbb{R}^s$ the sufficient statistics
- $h:\mathcal{X}\rightarrow[0,\infty)$ the carrier density/base density
- $\nu\in\Xi\subseteq \mathbb{R}^s$ the natural parameters
- $A:\Xi\rightarrow\mathbb{R}$ the log-partition function/ normalization constant

## Moment-generating function and cumulant-generating function
The MGF of a $d$-dimensional r.v $X\sim P$ is defined as $M^X(u)=\mathbb{E}[e^{u'X}]$ for $u\in\mathbb{R}^d$. We can use it to calculate moments of $X$ by evaluating its derivatives at 0.

For example, to evaluae the first moment of $X_j$, we can differentiate once w.r.t $u_j$ 

$$ \frac{\partial}{\partial u_j}M^X(u)=\int_\mathcal{X}\frac{\partial}{\partial u_j}e^{u'x}dP(x)=\int_\mathcal{X} x_j e^{u'x}dP(x) = \int_\mathcal{X} x_j e^{u'x}dP(x)$$

And evaluating at $u=0$ gives $\frac{\partial}{\partial u_j} M^X(0)=\int_\mathcal{X} x_j dP(x)=\mathbb{E}[X_j]$. 

The cumulant-generating function is the log of the MGF.

## Sufficiency
A statistics $T(X)$ is any r.v which is a function of the data $X$ and which does not depend on the unknown parameters $\theta$. Such statistics is called sufficient for th model $\mathcal{P}$ if $P_\theta(X\mid T)$ does not depend on $\theta$.

## Completeness
A statistics $T(X)$ is complete for a family of distribution $\mathcal{P}=\{P_\theta:\theta\in\Theta}$ if no nontrivial function of $T$ can have expectation zero for every distribution in the family

$$ \mathbb{E}_\theta f(T(X))=0,\forall\theta\in\Theta\implies f(T)=0 $$

Generally, if $T(X)$ is a complete statistic then there can be at most one unbiased estimator that runs through $T$.

Complete sufficient statistics are **minimal**

## Score function
Assume family $\mathbb{P}$ has densities $p_\theta$ w.r.t a measure $\mu$ for $\theta\in\Theta\subseteq\mathbb{R}^d$. 

Recall the log-likelihood is $l(\theta;X)=\log p_\theta(X)$. Then the score function is $\nabla l_\theta(X)$

## Fisher information matrix
Is the variance of the score

$$ J(\theta):=Var_\theta(\nabla l(\theta;X)) $$

and is always positive semidefinite. 

## Cramér-Rao Lower Bound
Let $\delta(X)$ be any real-valued statistics. Let $g(\theta)=\mathbb{E}_\theta[\delta]$. In the multivariate case, we have

$$ Var_\theta(\delta(X))\geq \nabla g(\theta)'J(\theta)^{-1}\nabla g(\theta) $$

The interpretation of this identity is that no unbiased estimator for $g(\theta)$ can have variance smaller than $\nabla g(\theta)'J(\theta)^{-1}\nabla g(\theta)$. 

## Bayes
- Densities: Prior:$\pi(\theta)$; Lieklihood: $p(x\mid\theta)$; Joint density $p(\theta, x)=\pi(\theta)p(x\mid\theta)$
- Marginal denity: $q(x)=\int p(\theta,x)d\theta$; Posterior density: $\pi(\theta\mid x)=p(\theta, x)/q(x)$

When the prior and the posterior is from the same family, we say the prior is conjugate to the likelihood


## Others
other topics not written here but I might like to revise include: sufficiency and completeness, more bayesian, MLE and stuffs, hypothesis testing etc, bootstrap
