---
layout: post
title: "Proof of Monte Carlo integration"
author: "mathilda"
categories: "MCMC"
---

For some random variable $x \sim p_X$, we approximate multidimensional integral $\int_X f(x) dx$ with some sum $\frac{1}{N}\sum^N_{i=1, x_i\sim p_X} \frac{f(x_i)}{p_X(x_i)}$

$$\begin{eqnarray}
\mathbf{E}[\frac{1}{N}\sum^N_{i=1} \frac{f(x_i)}{p_X(x_i)}] &=& \frac{1}{N}\sum^N_{i=1}\mathbf{E}[\frac{f(x_i)}{p_X(x_i)}]      \nonumber \\
&=& \frac{1}{N}\sum^N_{i=1}\int_X \frac{f(x)}{p_X(x)} p_X(x) \\
&=& \frac{1}{N}N\int_X f(x) \\
&\int_X f(x) 
\end{eqnarray}$$

Law of large number states that $\frac{1}{n}\sum^n x_i \xrightarrow[n\rightarrow\infty]{} \mu$, "partial averages converges a.s to the means". 

To be verbose, this means $\frac{1}{N}\sum^N_{i=1} \frac{f(x_i)}{p_X(x_i)} \xrightarrow[n\rightarrow\infty]{} \mathbf{E}[\frac{1}{N}\sum^N_{i=1} \frac{f(x_i)}{p_X(x_i)}]=\int_X f(x)dx $,



