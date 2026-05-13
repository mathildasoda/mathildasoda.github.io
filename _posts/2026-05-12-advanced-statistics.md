---
layout: post
title: "Advanced statistics"
author: "mathilda"
categories: "main"
---
## References
1. [Berkeley's stat210b](https://www.stat.berkeley.edu/~bartlett/courses/2013spring-stat210b/)
2. Van der Vaart - Asymptotic statistics. Chapter 5.

## Empirical Risk Minimization
Suppose $Z_1,...,Z_n$ are i.i.d according to $P$

$$ L_n(\theta)=P_n\mathcal{l}(\theta, Z)=\frac{1}{n}\sum^n_{i=1}\mathcal{l}(\Theta,Z_i) $$

chooses $\theta$ to minimize $L_n(\theta)$

e.g $p_\theta$ a density, $X\sim P, p_{\theta^*}, \mathcal{l}(\theta,z)=-\log p_\theta (z)$ where ERM is maximum likelihood

## M-estimators
To estimate parameter $\theta$ of distribution $P$ of observations $X_1,...,X_n$. We define a criterion in terms of functions $m_\theta:\mathcal{X}\rightarrow\mathbb{R}$

$$ M_n(\theta)=P_nm_\theta $$

The estimator $\hat \theta = \arg\max_{\theta\in\Theta} M_n(\theta)$ is called an **M-estimator** (M for maximum).

E.g: maximum likelihood uses $m_\theta(x)=\log p_\theta(x)$

### Z-estimator
Can maximize by setting derivatives to zero:

$$ \Psi_n(\theta) = P_n\psi_\theta = 0 $$

Basically M-estimator.

E.g: maximum likelihood $\psi_\thetea(x)=\nabla_\theta \log p_\theta(x)$

### Consistency of M- and Z-estimators
We want to show that $\hat\theta\xrightarrow{P}\thetea_0$ where $\hat\theta$ approximately maximizes $M_n(\theta)=P_n m_\theta$ and $\theta_0$ maximizes $M(\theta)=Pm_\theta$. We use a uniform law of large number

**Theorem**: suppose that
1. $\sup_{\theta\in\Theta}|M_n(\theta)-M(\theta)|\xrightarrow{P}0$
2. $\forall\epsilon>0,\sup\{M(\theta):d(\theta,\theta_0)\geq\epsilon\}\lt M(\theta_0)$
3. $M_n(\hat\theta_n)\geq M_n(\theta_0)-o_P(1)$

Then $\hat\thetea_n\xrightarrow{P}\theta_0$

## Asymptotic testing
Consider the asymptotics of a test. We have
- A parametric model $P_\theta$ for $\theta\in\Theta$
- A null hypothesis $\theta=\theta_0$
- An alternative hypothesis $\theta=\theta_0+h$
Test: compute the log likelihood ratio 

$$ \lambda=\log\prod^n_{i=1} \frac{dP_{\theta_0+h}(X_i)}{dP_{\theta_0}(X_i)}$$

and reject the null hypothesis if it is sufficiently large.

An example: the exponential family with sufficient statistics $T$ has density $$

## Contiguity

## Local Asymptotic Normality
Log likelihood ratio of local alternative to true parameter is asymptotically normal.



## Taylor series
Say we have a density $p_\theta$ w.r.t some measure, and the log likelihood $\mathcal{l}_\theta(x)=\log p_\theta(x)$ is twice diff w.r.t $\theta$, and can be approximated by its second order Taylor series

$$ \mathcal{l}_{\theta+h}(x)= \mathcal{l}_{\theta}(x)+h^T \mathcal{l'}_{\theta}(x)+\frac{1}{2}h^T \mathcal{l'''}_{\theta}(x)h + o(||h||^2)


