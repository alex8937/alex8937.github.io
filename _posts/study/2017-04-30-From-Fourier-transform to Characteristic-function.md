---
layout: article
title: "From Fourier transform to characteristic function"
categories: study
comments: true
image:
  feature: Stanford-University-1600x500.jpg
---

This is a blog discussing the concept of characteristic function for random variables.

Let us start with the background knowledge why characteristic function ever comes into the picture. Say if we need to prove something about a certain random variable $\color{black}{\mathbf{X}}$, then normally the first step is to check if that can be done in terms of its probability distribution. However, sometimes this approach may become quiet complex. Then what if the derivation can be simply conducted in a new space $\color{black}{\phi_{\mathbf{X}}}$, and the proof still holds when transformed back to the original space? Sounds pretty awesome, doesn't it? Characteristic space is just such a space.

The key point is that there exists a bijection between the probability distribution and its characteristic function. That is, for any two random variables         $\color{black}{\mathbf{X_1}}$ and $\color{black}{\mathbf{X_2}}$, both of them have the same probability distribution if only if $\color{black}{\phi_\mathbf{X_1} = \phi_\mathbf{X_2}}$. Bijection also implies that the characteristic function always exists, when treated as a function of a real-valued argument, unlike the moment-generating function. With this nice property, it allows us to deal with the random variable directly in terms of its characteristic function rather than bothering with the probability distribution.

### Definition

The definition of characteristic function of a random variable $\color{black}{\mathbf{X}\in \mathbb{R}^d}$ is the expected value of $\color{black}{\mathrm{exp}(i\mathbf{t} \cdot \mathbf{x})}$, namely

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{X}}(\mathbf{t}) = E[\mathrm{exp}(i\mathbf{t} \cdot \mathbf{x})]},
\end{split}
\end{equation}$$

where $\color{black}{\mathbf{t}\in \mathbb{C}^d}$ is the argument of characteristic function.

Suppose that $\color{black}{\mathbf{X}}$ has non-negative Lebesgue-integrable function $\color{black}{p(\mathbf{x})}$ as probability distribution function, then its characteristic function can be computed as

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{X}}(\mathbf{t}) =\int_{\mathbb{R}^d}
p(\mathbf{x})
\mathrm{exp({i\mathbf{t}\cdot\mathbf{x}})}d\mathbf{x}
  }.
\end{split}
\end{equation}$$

Comparing this to the non-unitary Fourier transform

$$\begin{equation}
\begin{split}
\color{black}{
\mathfrak{F}[f](\mathbf{t}) :=\int_{\mathbb{R}^d}
f(\mathbf{x})
\mathrm{exp(-{i\mathbf{t}\cdot\mathbf{x}})}d\mathbf{x}
  }.
\end{split}
\end{equation}$$

we can see that the characteristic function is the Fourier transform with sign reversal in complex component. As a matter of fact, all facts and theorems derived in Fourier transform would continue to be equivalently valid regardless of the sign reversal, because one can define the imaginary unit by either $\color{black}i$ or $\color{black}{-i}$, which makes no algebraic difference other than being a complex conjugate.

Here are again some several beautiful properties of characteristic function:

#### 1. Linear transformation

Let a random variable $\color{black}{\mathbf{Y}}$ be linear proportional to another random variable $\color{black}{\mathbf{X}}$, i.e. $\color{black}{\mathbf{Y}=a\mathbf{X}}$. We can express the characteristic function $\color{black}{\phi_\mathbf{Y}}$ as

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{Y}}(\mathbf{t}) ={\phi_{\mathbf{X}}(a\mathbf{t})}
  }.
\end{split}
\end{equation}$$

The proof is pretty straight-forward,

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{Y}}(\mathbf{t})} &=
\color{black}
{\phi_{a\mathbf{X}}(\mathbf{t})}
\\
&
\color{black}{=E[\mathrm{exp}(ia\mathbf{t} \cdot \mathbf{X})]} \\
&
\color{black}{=\phi_{\mathbf{X}}(a\mathbf{t})}
\end{split}
\end{equation}$$

A more generalized version of this property is that for a linear transform of random variable $\color{black}{\mathbf{X}}$, i.e. $\color{black}{a\mathbf{X} + b}$, its characteristic function becomes  $\color{black}
{\phi_{a\mathbf{X} + b}(\mathbf{t}) ={\mathrm{exp}(ib\mathbf{t})\phi_{\mathbf{X}}(a\mathbf{t})}}$.


#### 2. Moments:

If a characteristic function $\color{black}{\phi_{\mathbf{X}}(\mathbf{t}) }$ has a $\color{black}{k^{th}}$ derivative at $\color{black}{\mathbf{t} = \mathbf{0}}$, then we can relate it with the $\color{black}{k^{th}}$ moment of the random variable

$$\begin{equation}
\begin{split}
\color{black}
{\phi^{(k)}_{\mathbf{X}}(\mathbf{0}) = (i)^kE[\mathbf{X}^{k}] }
\end{split}
\end{equation}$$

To prove this, let us recall that the Maclaurin expansion of $\color{black}{\mathrm{exp}(i\mathbf{t} \cdot \mathbf{x})}$ is

$$\begin{equation}
\begin{split}
\color{black}
{\mathrm{exp}(i\mathbf{t} \cdot \mathbf{x}) =
\sum_{k = 0}^{\infty}\frac{(i\mathbf{t} \cdot \mathbf{x})^{k}}{k!}

.}
\end{split}
\end{equation}$$

and the $\color{black}{k^{th}}$ moment of random variable $\color{black}{\mathbf{X}}$ is defined by

$$\begin{equation}
\begin{split}
\color{black}
{E[\mathbf{X}^{k}] = \int_{\mathbb{R}^d}{
p(\mathbf{x})
\mathrm{\mathbf{x}^{k}}d\mathbf{x}}}
\end{split}
\end{equation}$$

Then the characteristic function can be rewritten by substitution as

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{X}}(\mathbf{t})}
& \color{black}
{=\int_{\mathbb{R}^d}
p(\mathbf{x})
\mathrm{\sum_{k = 0}^{\infty}
\frac{(i\mathbf{t} \cdot \mathbf{x})^{k}}{k!}
}
d\mathbf{x}
  } \\
  & \color{black}
  {=\sum_{k = 0}^{\infty} \left[\frac{(i\mathbf{t})^k}{k!} \cdot \int_{\mathbb{R}^d}
  p(\mathbf{x})
  \mathrm{\mathbf{x}^{k}}d\mathbf{x} \right],
    } \\  
  & \color{black}
  {=\sum_{k = 0}^{\infty}{\frac{(i\mathbf{t})^k}{k!} \cdot E[\mathbf{X}^{k}]}
    } \\
\end{split}
\end{equation}$$

Therefore, by taking the $\color{black}{k^{th}}$ derivative at $\color{black}{\mathbf{t} = \mathbf{0}}$, we obtain

$$\begin{equation}
\begin{split}
\color{black}
{\phi^{(k)}_{\mathbf{X}}(\mathbf{0}) = (i)^kE[\mathbf{X}^{k}] }
\end{split}
\end{equation}$$

or in another form

$$\begin{equation}
\begin{split}
\color{black}
{E[\mathbf{X}^{k}] = (-i)^k \phi^{(k)}_{\mathbf{X}}(\mathbf{0})}
\end{split}
\end{equation}$$

Thanks to this property, it greatly simplifies the procedure of moments computation. It is also worthy of mentioning that not all random variables with continuous distribution have well-defined moments. For instance, Cauchy distribution, which is originated from the ratio of two independent normally distributed Gaussian random variables has infinite first moment ([see details](http://www.itl.nist.gov/div898/handbook/eda/section3/eda3663.htm)).

#### 3. Sum of multiple random variables

Assume two independent random variables $\color{black}{\mathbf{X}}$ and $\color{black}{\mathbf{Y}}$, then their sum $\color{black}{\mathbf{Z} = \mathbf{X} + \mathbf{Y}}$ has a characteristic function given as


$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{Z}}(\mathbf{t}) ={\phi_{\mathbf{X}}(\mathbf{t})\phi_{\mathbf{Y}}(\mathbf{t})}
  }.
\end{split}
\end{equation}$$

To show this, we first express the probability distribution function of $\color{black}{\mathbf{Z}}$ as

$$\begin{equation}
\begin{split}
\color{black}
{p_\mathbf{Z}(\mathbf{z})}
& \color{black}
{=\int_{\mathbb{R}^d}
p_\mathbf{X}(\mathbf{x}) p_\mathbf{Y}(\mathbf{z-x})
d\mathbf{x}
  } \\
  & \color{black}
  {=\left (p_\mathbf{X} \circ p_\mathbf{Y} \right)(\mathbf{z})} \\  
\end{split}
\end{equation}$$

It is clear that $\color{black}{p_\mathbf{Z}(\mathbf{z})}$ is the convolution between $\color{black}{p_\mathbf{X}(\mathbf{x})}$ and $\color{black}{p_\mathbf{Y}(\mathbf{y})}$. Recall the fact that characteristic function can be treated as the Fourier transform of the probability distribution function and also convolution in spatial space is equivalent to multiplication in Fourier domain as discussed in [last post](https://alex8937.github.io/study/From-Fourier-transform-to-Characteristic-function/). Thus,


$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{Z}}(\mathbf{t})}
&\color{black}
{=\mathfrak{F}[{p_\mathbf{Z}}](\mathbf{t})} \\
&\color{black}
{=\mathfrak{F}[{p_\mathbf{X} \circ p_\mathbf{Y}}](\mathbf{t})} \\
&\color{black}{=\phi_{\mathbf{X}}(\mathbf{t})\phi_{\mathbf{Y}}(\mathbf{t})}
  .
\end{split}
\end{equation}$$

This property can be further extended from two random variables to multiple random variables. That is, for a random variable $\color{black}{\mathbf{Z} = \sum_{i}\mathbf{X}_i}$, its characteristic function can be computed as

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{\mathbf{Z}}(\mathbf{t}) =\prod_{i} {\phi_{\mathbf{X}_i}(\mathbf{t})}
  },
\end{split}
\end{equation}$$

This property is essential in deriving weak Law of Large Numbers and Central Limit Theorem. More details will be discussed in later post.

### Characteristic function of normal random variables

Here we will provide the proof that the characteristic function of the standardized normal random variable $\color{black}{X \sim \mathcal{N}(0, 1) }$ is

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{X}(t) = \mathrm{exp}(-\frac{t^2}{2})
  }.
\end{split}
\end{equation}$$

There are a few interesting properties of this characteristic function and this result will serve as lemma in following post.

Given the probability distribution of the standardized normal random variable

$$\begin{equation}
\begin{split}
\color{black}
{p_X(x;\mu= 0, \sigma^2=1) = \frac{1}{\sqrt{2\pi}}\mathrm{exp}(-\frac{x^2}{2})
  },
\end{split}
\end{equation}$$

its characteristic function is, by definition,


$$\begin{equation}
\begin{split}
\color{black}
{\phi_{X}(t)}& \color{black}{= E[\mathrm{exp}(itx)]} \\
&\color{black}{=\int_{-\infty}^{\infty}
\frac{1}{\sqrt{2\pi}}\mathrm{exp}(-\frac{x^2}{2})
\mathrm{exp}({itx})dx
  } \\
  &\color{black}{=\frac{\mathrm{exp}(\frac{-t^2}{2})}{\sqrt{2\pi}}\int_{-\infty}^{\infty}
  \mathrm{exp}\left[-\frac{(x-it)^2}{2} \right]dx
    }. \\
\end{split}
\end{equation}$$

The integral above can be solved by taking a closed rectangular path  $\color{black}{\Gamma}$ and its clost path integral $\color{black}{\oint_{\Gamma}f\left(z\right)dz=0}$ according to the [Cauchy integral theorem](https://en.wikipedia.org/wiki/Cauchy%27s_integral_theorem). By splitting the closed path into four horizontal and vertical segments and solving each integral segment by segment, it can be shown that

$$\begin{equation}
\begin{split}
\color{black}{\int_{-\infty}^{\infty}
  \mathrm{exp}\left[-\frac{(x-it)^2}{2} \right]dx = \sqrt{2\pi}
    }. \\
\end{split}
\end{equation}$$

More detailed proof can be found [ here](https://www.dsprelated.com/freebooks/sasp/Gaussian_Integral_Complex_Offset.html). All in all, this finishes the proof

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{X}(t) = \mathrm{exp}(-\frac{t^2}{2})
  }.
\end{split}
\end{equation}$$

An interesting fact is that a the characteristic function of the standardized normal distribution is also a standardized normal distribution in the Fourier domain. In other words, the standardized normal distribution is the eigenfunction of Fourier transform. In a more general case, normal random variable that obeys $\color{black}{X \sim \mathcal{N}(0, \sigma^2) }$ has a characteristic function as

$$\begin{equation}
\begin{split}
\color{black}
{\phi_{X}(t) = \mathrm{exp}\left[-\frac{(\sigma t)^2}{2}\right]
  },
\end{split}
\end{equation}$$

which can also be found consistent with the scaling property of Fourier transform discussed in [last post](https://alex8937.github.io/study/From-Fourier-transform-to-Characteristic-function/).


### Spoiler:

In next post, we will look into the Law of Large Numbers from the perspective of characteristic function. See you next time.
