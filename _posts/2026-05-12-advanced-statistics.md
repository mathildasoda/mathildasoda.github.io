---
layout: post
title: "Advanced statistics"
author: "mathilda"
categories: "main"
---
## References
1. [Berkeley's stat210b](https://www.stat.berkeley.edu/~bartlett/courses/2013spring-stat210b/)
2. Van der Vaart - Asymptotic statistics. Chapter 5.
3. [CMU's 36-709](https://www.stat.cmu.edu/~arinaldo/Teaching/36709/S19/)

## Master Theorem for Parametric Models
Let
1. $p_\theta$ be the density for the distribution $P_\theta$
2. $L_n(\theta\mid X_n)=\prod p_\theta(x_i)$ be the likelihood function, $l_n(\theta\mid X_n)=\log L_m(\theta\mid X_n)=\sum \log p_\theta(x_i)$
3. $\nabla_\theta l_n(\theta)$ (i.e the score) be the gradient of $l_n(\theta)$; $H l_n(\theta)$ be the Hessian of $l_n(\theta)$
4. $I(\theta)=-\mathbb{E}_x[H l_n(\theta\mid x)]$ be the Fisher Information

Then, under certain regularity conditions (smoothness, identfiability,...) on $P$, let $\tilde \Theta_n$ be a solution to the score equation $\nabla l_n(\theta)=0$ (i,e the MLE). We have:
- $\Theta_n$ exists and $\Theta_n\xrightarrow{p}\Theta_0$ (WLLN)
- $\sqrt{n}(\tilde\Theta_n - \Theta_0)\xrightarrow{d} \mathcal{N}_d(0, I^{-1}(\Theta_0))$ (CLT)
- $2\log\tilde\lambda_n \xrightarrow{d}\Chi^2_d$ where $\tilde\lambda_n=\frac{l_n(\Theta_n\mid X_i)}{\Theta_0\mid X_n} (Wilk's Theorem)
- $n(\Theta_n-\Theta_0)^T\hat I_n(\tilde\Theta_n)(\tilde \Theta_n-\Theta_0)\xrightarrow{d}\Chi^2_d$ (Wald Test)

(Maybe i can work out these for general M-estimator later)

## Sub-gaussian random variable
Rv $X$ is sub0Gaussian with parameter $\sigma$ if, $\forall \lambda\in\mathbb{R}$

$$ \mathbb{E}[\exp(\lambda(X-\mathbb{E}[X]))]\leq\exp(\frac{\lambda^2\sigma^2}{2}) $$

## Sub-exponential random variable
Rv $X$ is sub-exponential with parameters $\nu,\alpha\gt 0$ if, $\forall|\lambda|\lt 1/\alpha$

$$ \mathbb{E}[\exp(\lambda(X-\mathbb{E}[X]))]\leq \exp(\frac{\lambda^2\nu^2}{2}) $$

All sub-gaussian r.v are also sub-exponential

## Empirical Risk Minimization
Suppose $Z_1,...,Z_n$ are i.i.d according to $P$

$$ L_n(\theta)=P_n\mathcal{l}(\theta, Z)=\frac{1}{n}\sum^n_{i=1}\mathcal{l}(\Theta,Z_i) $$

chooses $\theta$ to minimize $L_n(\theta)$

e.g $p_\theta$ a density, $X\sim P, p_{\theta^*}, \mathcal{l}(\theta,z)=-\log p_\theta (z)$ where ERM is maximum likelihood

## M-estimator and Z-estimator
### M-estimator
To estimate parameter $\theta$ of distribution $P$ of observations $X_1,...,X_n$. We define a criterion in terms of functions $m_\theta:\mathcal{X}\rightarrow\mathbb{R}$

$$ M_n(\theta)=P_nm_\theta $$

The estimator $\hat \theta = \arg\max_{\theta\in\Theta} M_n(\theta)$ is called an **M-estimator** (M for maximum).

E.g: maximum likelihood uses $m_\theta(x)=\log p_\theta(x)$

### Z-estimator
Can maximize by setting derivatives to zero:

$$ \Psi_n(\theta) = P_n\psi_\theta = 0 $$

Basically M-estimator.

E.g: maximum likelihood $\psi_\theta(x)=\nabla_\theta \log p_\theta(x)$

### Consistency of M- and Z-estimators
We want to show that $\hat\theta\xrightarrow{P}\theta_0$ where $\hat\theta$ approximately maximizes $M_n(\theta)=P_n m_\theta$ and $\theta_0$ maximizes $M(\theta)=Pm_\theta$. We use a uniform law of large number

**Theorem**: suppose that
1. $\sup_{\theta\in\Theta}\mid M_n(\theta)-M(\theta)\mid\xrightarrow{P}0$
2. $\forall\epsilon>0,\sup\{M(\theta):d(\theta,\theta_0)\geq\epsilon\}\lt M(\theta_0)$
3. $M_n(\hat\theta_n)\geq M_n(\theta_0)-o_P(1)$

Then $\hat\theta_n\xrightarrow{P}\theta_0$

### Asymptotic normality of Z-estimators
Consider: $\Psi_n(\theta)=P_n\psi_\theta$, and $\Psi(\theta)=P\psi_\theta$. 

Suppose $\hat\theta_n\in\mathbb{R}$ is a zero of $\Psi_n,\theta_0\in\mathbb{R}$ is a zero of $\Psi,\hat\theta_n\xrightarrow{P}\theta_0$. Then

$$ \sqrt{n}(\hat\theta_n-\theta_0)=\frac{-\sqrt{n}\Psi_n(\theta_0)}{\Psi_n'(\theta_0)+(1/2)(\hat\theta_n-\theta_0)\Psi_n^{''}(\tilde\theta_n)} $$

where $\tilde\theta_n = \lambda\hat\theta_n + (1-\lambda)\theta_0$ for some $0\leq\lambda\leq 1$.

If $P\psi^2_{\theta_0} $ exists, $P\psi_{\theta_0}'} exists and non-zero, and $\Psi^{'''}_n(\tilde\theta_n)=O_P(1)$. Then 

$$ \sqrt{n}(\hat\theta_n - \theta_0) \rightsquigarrow N(0, P\psi^2_{\theta_0}/(P\psi'_{\theta_0})^2) $$

## Asymptotic testing
Consider the asymptotics of a test. We have
- A parametric model $P_\theta$ for $\theta\in\Theta$
- A null hypothesis $\theta=\theta_0$
- An alternative hypothesis $\theta=\theta_0+h$
Test: compute the log likelihood ratio 

$$ \lambda=\log\prod^n_{i=1} \frac{dP_{\theta_0+h}(X_i)}{dP_{\theta_0}(X_i)}$$

and reject the null hypothesis if it is sufficiently large.

An example: supposer $P_\theta = N(\theta,\sigma^2)$. Then 

$$ \lambda = \log\prod^n_{i=1}\frac{dP_{\theta_0+h}}{dP_{\theta_0}}(X_i)=\log\prod \frac{\exp(-(x-\theta_0-h)^2/(2\sigma^2))}{\exp(-(x-\theta_0)^2/(2\sigma^2))}=\frac{1}{2\sigma^2}\sum^n_{i=1}\left((X_i-\theta_0)^2-(X_i-\theta_0-h)^2\right) = \frac{nh}{\sigma^2}(\bar X -\theta_0)-\frac{nh^2}{2\sigma^2}$$

So under the null hypothesis $X\sim N(\theta_0,\sigma^2)\implies\sum^n X_i\sim N(n\theta_0,n\sigma^2)\implies \bar X\sim N(\theta_0,\sigma^2/n)$. And the log likelihood ratio is $\lambda \sim N(-\frac{nh^2}{2\sigma^2},\frac{nh^2}{\sigma^2}) $

writing these blind are actually pretty tedious :/

For fixed $h\neq 0, \lambda\xrightarrow{P}-\infty$. I.e: asymptotically we do not reject the null hypothesis. Consider instead: $h_n\rightarrow 0, \sqrt{n}h_n\rightarrow h\neq 0$. Then its parameter approaches $N(-h^2/(2\sigma^2), h^2/\sigma^2)$. Then provided $h_n/(2\sigma^2)\gg n^{-1/2}$, we do not reject the null hypothesis. 


## Local Asymptotic Normality
### Taylor series
Say we have a density $p_\theta$ w.r.t some measure, and the log likelihood $\mathcal{l}_\theta(x)=\log p_\theta(x)$ is twice diff w.r.t $\theta$, and can be approximated by its second order Taylor series

$$ \mathcal{l}_{\theta+h}(x)= \mathcal{l}_{\theta}(x)+h^T \mathcal{l'}_{\theta}(x)+\frac{1}{2}h^T \mathcal{l''}_{\theta}(x)h + o(\|h\|^2) $$

then 

$$ \lambda =\log\prod^n_{i=1}\frac{dP_{\theta+h_n}}{dP_\theta}(X_i)=\sum^n\left(\log p_{\theta+h_n}(X_i)-\log p_\theta(X_i)\right)= h^T_n\sum^n \mathcal{l'}_{\theta}(X_i)+\frac{1}{2}h^T_n\sum^n\mathcal{l''}_{\theta}(X_i)h_n + o(n\|h\|^2) $$

### Quadratic mean differentiabilitiy (QMD)
The root density $\theta\mapsto\sqrt{p_\theta}$ for ($\theta\in\mathbb{R}^k$) is **differentiable in quadratic mean** at$\theta$ if $\exists l'_\theta:\mathcal{X}\rightarrow\mathbb{R}^k$ a vector-valued measure function s.t., for $h\rightarrow 0$,

$$ \int\left(\sqrt{p_{\theta+h}}-\sqrt{p_\theta}-\frac{1}{2}h^Tl'_\theta\sqrt{p_\theta}\right)^2d\mu=o(\|h\|^2) $$

### QMD sufficient conditions
**Theorem**: if
- $\Theta$ an open subset of $\mathbb{R}^k$
- $\theta\mapsto\sqrt{p_{\theta}(x)}$ is continuously diff at $\mu$-almost all $x$
- $I_\theta=\int p'_\theta p^{'T}_\theta/p_\theta d\mu$ continuous in $\theta$
Then $\sqrt{p_\theta}$ is QMD at $\theta$, with $l'_\theta=p'_\theta/p_\theta$

E.g: exponential families are QMD

### Local Asymptotic Normality
Log likelihood ratio of local alternative to true parameter is asymptotically normal.
**Theorem**: if $\Theta$ an open subset of $\mathbb{R}^k$ and $P_\theta$ is QMD at $\theta\in\Theta$ then
- $P_\thetal'_\theta =0$
- $I_\theta=P_\thetal'_\thetal^T_\theta$ exists
- $\forall h_n$ satisfying $\sqrt{n}h_n\rightarrow h$

$$ \log\prod^n_{i=1}\frac{p_{\theta+h_n}}{p_\theta}(X_i)=\frac{1}{\sqrt{n}}\sum^n h^Tl'_\theta(X_i)-\frac{1}{2}h^TI_\theta h+oP_\theta(1)\xrightsquigarrow{\theta} N\left(-\frac{1}{2}h^TI_\theta h, h^TI_\theta h\right) $$

i.e: for QMD model $P_\theta$, the loglikelihood ratio $\log\frac{dP^n_{\theta_0+h/\sqrt{n}}}{dP^n_{\theta_0}}(X_i)$ is asymptotically normal.

### Maximum likelihood
**Theorem** suppose
- $(P_\theta:\theta\in\Theta)$ is QMD at $\theta$ with nonsigular Fisher information $I_\theta$
- $\forall x,\theta\mapsto\log p_\theta(x)$ is Lipschitz
- MLE $\hat\theta_n$ is consistent
Then

$$ \sqrt{\hat\theta_n-\theta}\xrightsquigarrow{\theta} N(0,I_\theta^{-1}) $$

## Some other topics to look into
orlicz norm
