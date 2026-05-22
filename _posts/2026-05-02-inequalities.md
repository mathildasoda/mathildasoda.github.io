---
layout: post
title: "Inequalities"
author: "mathilda"
categories: "main"
---
## References
1. High-dimensional Probability (Vershynin) 
2. [Berkeley's stat210b](https://www.stat.berkeley.edu/~bartlett/courses/2013spring-stat210b/)
3. [Chernoff notes](https://math.mit.edu/~goemans/18310S15/chernoff-notes.pdf)

# Concentration inequalities
Measures deviation of random variable $X$ from its means $\mathbb{E}[X]=\mu$. They typically provide two sided bounds on the tails of $X-\mu$ such as 

$$ \mathbb{P}(|X-\mu|>t)\leq \text{something small} $$

## Hoeffding inequality for bounded random variables
Let $X_1,...,X_N$ be independent random variables s.t $\forall i, X_i\in[a_i,b_i]$. Then, $\forall t>0$

$$ \mathbb{P}\Big(\sum^N_{i=1}(X_i-\mathbb{E}[X_i])\geq t\Big)\leq \exp\Big(-\frac{2t^2}{\sum^N_{i=1}(b_i-a_i)^2}\Big) $$

## Bernstein inequality for bounded distribution
Let $X_1,...X_N$ be independent, mean-zero random variables s.t $\forall i, |X_i|\leq K$. Then, $\forall t\geq 0$

$$ \mathbb{P}(|\sum^N_{i=1}X_i|\geq t)\leq 2\exp\Big(-\frac{t^2/2}{Kt/3+\sum^N_{i=1}\mathbb{E}[X^2_i]}\Big) $$

## Bounded Differences
Suppose $f:\mathcal{X}^n\rightarrow\mathbb{R}$ satisfies the following **bounded differences inequality**: $\forall x_1,..., x_n, x'_i\in\mathcal{X}$, 

$$ |f(x_1,...,x_n)-f(x_1,...,x_{i-1},x'_i, x_{i+1},...,x_n)|\leq B_i $$

Then 

$$ \mathbb{P}(|f(X)-\mathbb{E}[f(x)]|\geq t)\leq 2\exp\left(-\frac{2t^2}{\sum_i B_i^2}\right) $$

# Basic inequalities
## Markov
For any non negative random variable $X$ and $t>0$ 

$$ \mathbb{P}(X\geq t)\leq\frac{\mathbb{E}[X]}{t} $$

## Chebyshev
Let $X$ a random variable with mean $\mu$ and variance $\sigma^2$. hen $\forall t>0$

$$ \mathbb{P}(|X-\mu|\geq t)\leq\frac{\sigma^2}{t^2} $$

## Chernoff
### For Bernoulli rv
Let $X=\sum^n_{i=1}X_i$ with probability $p_i$ and $X_i=0$ with probability $1-p_i$, and all $X_i$ are independent. Let $\mu-\mathbb{E}[X]=\sum^n p_i$. Then 
- **Upper Tail**: $\mathbb{P}(X\geq(1+\delta)\mu)\leq\exp(-\frac{\delta^2\mu}{2+\delta}), \forall\delta\gt 0$
- **Lower Tail**: $\mathbb{P}(X\leq(1-\delta)\mu)\leq\exp(-\frac{\delta^2\mu}{2}), \forall\delta\in(0,1)$
- **Combined**: $\mathbb{P}(|X-\mu|\geq\delta\mu)\leq2\exp(-\frac{\delta^2\mu}{3}), \forall\delta\in(0,1)$
### General
Can be derived from Markov. For $a\gt 0$

$$ \mathbb{P}[X\geq a]\leq\frac{\mathbb{E}[X]}{a} \iff \mathbb{P}[e^{bX}\geq e^{ba}]\leq\frac{\mathbb{E}[e^{bX}]}{e^{ba}} \implies \mathbb{P}[X\geq a]\leq\frac{\mathbb{E}[e^{bX}]}{e^{ba}}$$

## Jensen 
For any random variable $X$ and convex $f:\mathbb{R}\rightarrow\mathbb{R}$, we have 

$$ f(\mathbb{E}[X])\leq \mathbb{E}[f(X)] $$

Since any norm on $\mathbb{R}^n$ is a convex function, Jensen inequality yiels

$$ ||\mathbb{E}[X]||\leq \mathbb{E}[||X||] $$

## Hölder
For any pair of $p, q\in[1,\infty]$ s.t $1/p+1/q=1$. For any random variables $X\in L^p$ and $Y\in L^q$ we have 

$$ ||XY||_{L^1}\leq||X||_{L^p}||Y||_{L^q} $$



# Oracle inequality
## Oracle 

