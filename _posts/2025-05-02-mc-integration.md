---
layout: post
title: "Proof of Monte Carlo integration"
author: "mathilda"
categories: "MCMC centric"
---

For some random variable $x \sim p_X$, we approximate $\mathbf{E}[f(x)]$ with some sum $\frac{1}{N}\sum^N_{i=1, x_i\sim p_X}f(x_i)/p_X(x_i)$

$$\begin{eqnarray}
\mathbf{E}[\frac{1}{N}\sum^N_{i=1} \frac{f(x_i)}{p_X(x_i)}] &=& \frac{1}{N}\sum^N_{i=1}\mathbf{E}[{f(x_i)}{p_X(x_i)}]      \nonumber \\
&=& \frac{1}{N}\sum^N_{i=1}\int_X {f(x)}{p_X(x)} p_X(x) \\
&=& \frac{1}{N}N\int_X f(x) \\
&=&\int_X f(x)   \nonumber
& \mathbf{E}[f(x)]
\end{eqnarray}$$

Law of large number states that $\mathbf{P}[lim_{n\rightarrow \infty}\frac{1}{n}\sum^n x_i = \mathbf{E}[x]] = 1$, "partial averages converges a.s to the means".

(1) is due to "Law of the unconscious statistician"


