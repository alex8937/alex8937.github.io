---
layout: article
title: "Law of large numbers"
categories: study
comments: true
image:
  feature: Stanford-University-1600x500.jpg
---

This is a blog discussing the Law of large numbers (LLN) and proof with characteristic function.

In probability theory, law of large numbers describes the asymptotic behavior of the empirical average of the independent and identically distributed (i.i.d.) random variables converging towards the expectation as number of sample grows.

Consider a sequence of i.i.d. random variables $\color{black}{X_i}$ with mean $\color{black}{\mu = E\left[{X}\right]}$, the law of large numbers comes in two forms, one weak law and one strong law as follows

### Weak law

The weak law of large numbers states that the sample average converges in probability towards the expected value. That is for $\color{black}{\forall \epsilon > 0}$,

$$\begin{equation}
\begin{split}
\color{black}
{\lim_{n \rightarrow \infty}Pr \left( \left| \hat{\mu}_n - \mu \right| \leq \epsilon \right) = 1 .}
\end{split}
\end{equation}$$

In another notation, it is expressed as when $\color{black}{n \rightarrow \infty}$,

$$\begin{equation}
\begin{split}
\color{black}
{\hat{\mu}_n \overset{P}{\rightarrow} \mu,}
\end{split}
\end{equation}$$

where $\color{black}{\overset{P}{\rightarrow}}$ is called convergence in probability. What weak law represents is that as size of sample grows to infinity, the probability that the empirical average $\color{black}{\hat{\mu}_n}$ is within the $\color{black}{\epsilon}$ neighborhood of the expectation $\color{black}{\mu}$ goes to $\color{black}{1}$. In other words, weak law does not guarantee that $\color{black}{\hat{\mu}_n}$ is always within the $\color{black}{\epsilon}$ neighborhood of the expectation $\color{black}{\mu}$. For instance,
it can be the case that for  most of time $\color{black}{\hat{\mu}_n}$ converges to $\color{black}{\mu}$, but with very small probability $\color{black}{\hat{\mu}_n}$ deviates from $\color{black}{\mu}$ and the deviation can keep on increasing.

### Strong law

The strong law of large numbers, instead, states that the sample average converges almost surely to the expected value. Namely

$$\begin{equation}
\begin{split}
\color{black}
{Pr \left( \lim_{n \rightarrow \infty} {\hat{\mu}_n = \mu}\right) = 1 .}
\end{split}
\end{equation}$$

It is sometimes also written as when $\color{black}{n \rightarrow \infty}$,

$$\begin{equation}
\begin{split}
\color{black}
{\hat{\mu}_n \overset{a.s.}{\rightarrow} \mu},
\end{split}
\end{equation}$$

where $\color{black}{\overset{a.s.}{\rightarrow}}$ is called almost sure convergence. What strong law represents is that the probability that the empirical average $\color{black}{\hat{\mu}_n}$ is equal to the expectation $\color{black}{\mu}$ will be equal to $\color{black}{1}$ as the number of sample goes to infinity. In other words, the strong law prevents the occurrence of deviation from happening when $\color{black}{n}$ is sufficiently large.

### Proof of weak law using characteristic function

Here I provide the proof of weak law of large numbers using characteristic function discussed in [last post](https://alex8937.github.io/study/From-Fourier-transform-to-Characteristic-function/). For anyone who is interested in the proof of strong law, please check [here](https://www.math.ucdavis.edu/~tracy/courses/math135A/UsefullCourseMaterial/lawLargeNo.pdf).

In order to prove the weak law, let us introduce [Lévy's continuity theorem](https://en.wikipedia.org/wiki/L%C3%A9vy%27s_continuity_theorem). That is if for $\color{black}{\forall t}$

$$\begin{equation}
\begin{split}
\color{black}
{\lim_{n \rightarrow \infty}{\phi}_{X_{n}}(t) = {\phi}_{X}(t)  }
\end{split}
\end{equation}$$

then $\color{black}{X_{n}(t)}$ converges to $\color{black}{X(t)}$ in probability. Then, to prove the weak law of large numbers becomes equivalent to show

$$\begin{equation}
\begin{split}
\color{black}
{\lim_{n \rightarrow \infty}{\phi}_{\hat{\mu}_{n}}(t) = {\phi}_{\mu}(t)  .}
\end{split}
\end{equation}$$

where the random variable of empirical average $\color{black}{\hat{\mu}_{n}}$ is defined as

$$\begin{equation}
\begin{split}
\color{black}
{\hat{\mu}_{n} = \frac{1}{n}\sum_{i=1}^{n} X_i =\sum_{i=1}^{n} \frac{X_i}{n}}
\end{split}
\end{equation}$$

Due to the fact of each random variable $\color{black}{X_i}$ being i.i.d. drawn from the same probability distribution with $\color{black}{\mu = E\left[{X}\right]}$, the characteristic function of $\color{black}{\hat{\mu}_{n}}$ is then


$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\hat{\mu}_{n}}(t)}
& \color{black}{= \prod_{i=1}^{n}{\phi}_{X_i/n}(t)  }\\
& \color{black}{= \prod_{i=1}^{n}{\phi}_{X_i}\left(\frac{t}{n} \right)  }\\
& \color{black}{= \left[{\phi}_{X}\left(\frac{t}{n} \right) \right]^n }\\
& \color{black}{= \left(E[\mathrm{exp}(i\frac{tX}{n})] \right)^n }\\
\end{split}
\end{equation}$$

Let us expand the exponential term with Taylor series up to first order,

$$\begin{equation}
\begin{split}
\color{black}
{\mathrm{exp}(i\frac{tX}{n}) = 1 + i\frac{tX}{n} + O(t^2)
.}
\end{split}
\end{equation}$$

incidentally its expectation becomes

$$\begin{equation}
\begin{split}
\color{black}
{E\left[\mathrm{exp}(i\frac{tX}{n}) \right]}
&\color{black}{= E\left[1 + i\frac{tX}{n} + O(t^2)\right]} \\
&\color{black}{= 1 + E\left[i\frac{tX}{n}\right] + O(t^2)} \\
&\color{black}{= 1 + \frac{it\mu}{n} + O(t^2)} \\
\end{split}
\end{equation}$$

Also, bearing in mind that

$$\begin{equation}
\begin{split}
\color{black}
{\mathrm{exp}(x) = \lim_{n \rightarrow \infty}\left( 1 + \frac{x}{n}\right)^n,}

\end{split}
\end{equation}$$

we can calculate that

$$\begin{equation}
\begin{split}
\color{black}
{\lim_{n \rightarrow \infty}{\phi}_{\hat{\mu}_{n}}(t)}
& \color{black}{= \lim_{n \rightarrow \infty}\left(E[\mathrm{exp}(i\frac{tX}{n})] \right)^n }\\
& \color{black}{= \lim_{n \rightarrow \infty}\left[1 + \frac{it\mu}{n} + O(t^2)\right]^n} \\
& \color{black}{= \mathrm{exp}(it\mu)} \\
& \color{black}{= {\phi}_{\mu}(t)} \\
\end{split}
\end{equation}$$

By Lévy's continuity theorem, this finishes the proof. Another proof of weak law using [Chebyshev's inequality](https://en.wikipedia.org/wiki/Chebyshev%27s_inequality) can be found [here](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-262-discrete-stochastic-processes-spring-2011/video-lectures/lecture-3-law-of-large-numbers-convergence/MIT6_262S11_lec03.pdf). It is noted that the approach using Chebyshev's inequality assumes the existence of variance for the random variables, whereas the proof with characteristic function holds always.

### Spoiler:

In next post, we will look into the central limit theorem from the perspective of characteristic function. See you next time.
