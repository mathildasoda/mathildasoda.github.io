---
layout: post
title: "Basic statistics"
author: "mathilda"
categories: "main"
---
## References
1. [Berkeley's stat210a](https://stat210a.berkeley.edu/fall-2024/)
2. [Berkeley's stat210b](https://www.stat.berkeley.edu/~bartlett/courses/2013spring-stat210b/)

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

**Notes**: As $\mathb{P}[X\geq a]=\mathbb{P}[e^{bX}\geq e^{ba}]\forall b\geq 0$. Then applying Markov: 

$$ \mathbb{E}[X\geq a]=\frac{\mathbb{E}[e^{bX}]}{e^{ba}}$$

The MGF of $X$ is $M_X(b) = \mathbb{E}[e^{bX}]$. Applying Taylor

$$ M_X(b) = \mathbb{E}[1+bx+\frac{(bx)^2}{2!}]+\frac{(bx)^3}{3!}]+\frac{(bx)^4}{4!}+...] = \mathbb{E}[\sum^\infty_{n=1}\frac{(bx)^n}{n!}] = \sum^\infty_{n=1}\frac{b^n}{n!}\mathbb{E}[X^n]  $$

Taking $d/db$ $n^{th}$ times get rid of the first $(n-1)^{th}$ variables, leaving us with the wanted expectation. Setting $b=0$ get rid of the rest

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

## Probabilistic big-O notation
Let $X_1, X_2,...$ denotes a sequence of random vectors ($||X_n||\lt\infty$ almost surely). We say the sequence is *bounded in probability* (or sometimes *tight*) if $\forall\epsilon\gt 0, \exists M_\epsilon\gt 0$ a constant, for which 

$$ \mathbb{P}[||X_n||\gt M_\epsilon]\lt\epsilon, \forall n $$

Informally, there is "no mass escaping to infinity" as $n$ grows. 

For a fixed sequence $a_n$, we say $X_n=o_p(a_n)$ if $X_n/a_n\xrightarrow{p} 0$ as $n\rightarrow\infty$ and $X_n=O_p(a_n)$ if the sequence $(X_n/a_n)_{n\geq 1}$is bounded in probability. $o_P$ means strictly slower, $O_P$ means within some constant 

E.g: 
- If $X_n\implies X$ for any random vector $X$, then $X_n=O_p(1)$
- $X_n=o_P(1)\iff X_n\xrightarrow{P}0$
- $X_n=O_P(1)\iff X_n$ uniformly tight


## Convergences
$X_n$ **converges in distribution** (or **weakly converges**) to $X$, written $X_n\rightsquigarrow X$, means that their distribution functions satisfy $F_n(x)\rightarrow F(x)$ at all continuity points of $F$

$X_n$ **converges almost surely** to $X$, written $X_n\xrightarrow{as}X$, means that $d(X_n, X)\rightarrow 0$ a.s.

$X_n$ **converges in probability** to $X$, written $X_n\xrightarrow{P}X$, means that $\forall \epsilon\gt 0, P(d(x_n,X)>\epsilon)\rightarrow 0$

Note that $X_n\xrightarrow{as}X\implies X_n\xrightarrow{P}X\implies X_n\rightsquigarrow X$ and that $X_n\xrightarrow{P}c\iff X_n\rightsquigarrow c$

## Uniformly tight
$X$ is **tight** means that $\forall\epsilon>0,\exists M$ s.t

$$ \mathbb{P}[||X||>M]M\epsilon $$

$\{X_n\}$ is **uniformly tight** or (**bounded in probability**) means that $\forall\epsilon,\exists M$ s.t.

$$ \sup_n \mathbb{P}[||X_n||>M]\lt\epsilon $$

## Martingales
A sequence $Y_n$ of r.v adapted to a filtration $\mathcal{F}_n$ is a **martingale** if, $\forall n$,

$$ \mathbb{E}[|Y_n|]\lt \infty $$

$$ \mathbb{E}[Y_{n+1}\mid\mathcal{F}_n] = Y_n $$

- $Y_n$ is **adapted** to $\mathcal{F}_n$ means that each $Y_n$ is measurable w.r.t $\mathcal{F}_n$
- $\mathcal{F}_n$ is a **filtration** means these $\sigma$-fields are nested: $\mathcal{F}_n \subseteq \mathcal{F}_{n+1}$

## Others
other topics not written here but I might like to revise include: sufficiency and completeness, more bayesian, MLE and stuffs, hypothesis testing etc, bootstrap, martingales
