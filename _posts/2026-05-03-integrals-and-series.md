---
layout: post
title: "Integrals and series"
author: "mathilda"
categories: "main"
---
## References
1. [Jeffrey & Zwillinger Tables of Integrals, Series, and Products](http://web.phy.ntnu.edu.tw/~hongyi/notes/Books/Gradshteyn,%20Ryzhik_Table%20of%20Integrals%20,Series%20and%20Products_2007_MC.pdf)
2. [Gaussian integral wiki page](https://en.wikipedia.org/wiki/Gaussian_integral) 
3. [List of handy inequality](https://www.lkozma.net/inequalities_cheat_sheet/ineq.pdf)

## Gaussian(-ish) integrals

$$ \int^\infty_{-\infty} \exp(-a(x+b)^2)dx = \sqrt{\frac{pi}{a}} $$

$$ I(a) = \int^\infty_{-\infty}e^{-ax^2}dx = \sqrt{\frac{\pi}{a}} $$

$$ I(a) = \int^\infty_{-\infty}(-x^2)e^{-ax^2}dx = -\frac{1}{2}\frac{\sqrt{\pi}}{a^{3/2}} $$

And generally: with $\gamma = \frac{m+1}{n}=1,2,...$

$$ \int x^m\exp(-\beta x^n) dx = -\frac{(\gamma-1)!}{n}\exp(-\beta x^n)\sum^{\gamma-1}_{k=0}\frac{x^{nk}}{k!\beta^{\gamma-k}} $$

## Taylor 
### General 

$$ f(a+x)=\sum^\infty_{k=0}\frac{x^k}{k!}f^{(k)}(a) $$

### For Log 
For $-1\lt x\leq 1$

$$ \ln(1+x)=x-\frac{1}{2}x^2 + \frac{1}{3}x^3 - \frac{1}{4}x^4 +... = \sum^\infty_{k=1}(-1)^{k+1}\frac{x^k}{k} $$

## Numerical series

For $\mid x\mid \lt 1$

$$ \frac{a}{1-x}=\sum^\infty_{k=0}ax^k $$



