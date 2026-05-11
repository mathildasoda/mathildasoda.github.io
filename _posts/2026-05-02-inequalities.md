---
layout: post
title: "Inequalities"
author: "mathilda"
categories: "main"
---
## References
1. High-dimensional Probability (Vershynin) 
2. 

# Concentration inequalities
Measures deviation of random variable $X$ from its means $\mathbb{E}[X]=\mu$. They typically provide two sided bounds on the tails of $X-\mu$ such as 

$$ \mathbb{P}(|X-\mu|>t)\leq \text{something small} $$

## Hoeffding inequality for bounded random variables
Let $X_1,...,X_N$ be independent random variables s.t $\forall i, X_i\in[a_i,b_i]$. Then, $\forall t>0$

$$ \mathbb{P}\Big(\sum^N_{i=1}(X_i-\mathbb{E}[X_i])\geq t\Big)\leq \exp\Big(-\frac{2t^2}{\sum^N_{i=1}(b_i-a_i)^2}\Big) $$

## Bernstein inequality for bounded distribution
Let $X_1,...X_N$ be independent, mean-zero random variables s.t $\forall i, |X_i|\leq K$. Then, $\forall t\geq 0$

$$ \mathbb{P}(|\sum^N_{i=1}X_i|\geq t)\leq 2\exp\Big(-\frac{t^2/2}{Kt/3+\sum^N_{i=1}\mathbb{E}[X^2_i]}\Big) $$

# Basic inequalities
## Markov
For any non negative random variable $X$ and $t>0$ 

$$ \mathbb{P}(X\geq t)\leq\frac{\mathbb{E}[X]}{t} $$

## Chebyshev
Let $X$ a random variable with mean $\mu$ and variance $\sigma^2$. hen $\forall t>0$

$$ \mathbb{P}(|X-\mu|\geq t)\leq\frac{\sigma^2}{t^2} $$

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

