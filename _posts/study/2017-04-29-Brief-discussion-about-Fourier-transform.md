---
layout: article
title: "Brief discussion about Fourier transform"
categories: study
comments: true
image:
  feature: Stanford-University-1600x500.jpg
---

This is a blog discussing a brief discussion about Fourier transform.

Let us consider real- or complex-valued functions $\color{black}{f(\mathbf{x})}$, where $\color{black}{\mathbf{x}\in \mathbb{R}^d}$. The Fourier transform maps functions $\color{black}{f(\mathbf{x})}$ on spatial domain to Fourier domain $\color{black}{\hat{f}(\mathbf{w})}$, which is defined by

$$\begin{equation}
\begin{split}
\color{black}{
\mathfrak{F}[f](\mathbf{w}) :=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}
f(\mathbf{x})
\mathrm{exp({-i\mathbf{w}\cdot\mathbf{x}})}d\mathbf{x}
  }.
\end{split}
\end{equation}$$


Its inverse Fourier transform is

$$\begin{equation}
\begin{split}
\color{black}{
\mathfrak{F}^{-1}[f](\mathbf{x}):=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}
\hat{f}(\mathbf{w})
\mathrm{exp({i\mathbf{w}\cdot\mathbf{x}})}d\mathbf{w}
  },
\end{split}
\end{equation}$$


where $\color{black}{\mathbf{w}\cdot\mathbf{x}}$ is the inner product between the spatial variables $\color{black}{\mathbf{x}}$ and its dual $\color{black}{\mathbf{w}}$.

Here are the several beautiful properties of Fourier transform:

#### 1. Fourier inversion theorem:

$$
\begin{equation}
\begin{split}
\color{black}{\mathfrak{F} \circ \mathfrak{F}^{-1} = \mathfrak{F}^{-1} \circ \mathfrak{F} = \mathbf{I}}
\end{split}
\end{equation}
$$

Fourier inversion theorem says that for many types of functions it is possible to recover a function from its Fourier transform. Intuitively it may be viewed as the statement that if we know all frequency and phase information about a wave then we may reconstruct the original wave precisely.

#### 2. Differentiation:

$$
\begin{equation}
\begin{split}
\color{black}{\mathfrak{F} [\partial_{\mathbf{x}}f]=i\mathbf{w}\mathfrak{F}[f]}
\end{split}
\end{equation}
$$


The differentiation property implies that to take a differentiation in the spatial domain is equivalent to simply multiply by $\color{black}{i\mathbf{w}}$ in Fourier domain. Here gives the proof:

First let us apply Fourier inversion theorem and rewrite  



$$
\begin{equation}
\begin{split}
\begin{aligned}
\color{black}{f(\mathbf{x})}&=\color{black}{\mathfrak{F^{-1}} \circ \mathfrak{F}[f](\mathbf{x})} \\
  &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}
  \mathfrak{F}[f](\mathbf{w})
  \mathrm{exp({i\mathbf{w}\cdot\mathbf{x}})}d\mathbf{w}}
\end{aligned}
\end{split}
\end{equation}
$$

Keeping in mind that only $\color{black}{\mathrm{exp({i\mathbf{w}\cdot\mathbf{x}})}}$ in the equation above depends on  $\color{black}{\mathbf{x}}$, we take a differentiation corresponding to  $\color{black}{\mathbf{x}}$,

$$
\begin{equation}
\begin{split}
\begin{aligned}
\color{black}{\partial _{\mathbf{x}}f(\mathbf{x})}&=\color{black}{\partial _{\mathbf{x}}\left [\mathfrak{F^{-1}} \circ \mathfrak{F}[f](\mathbf{x}) \right]} \\
  &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}
  \mathfrak{F}[f](\mathbf{w})
  \partial _{\mathbf{x}}[\mathrm{exp({i\mathbf{w}\cdot\mathbf{x}})}]d\mathbf{w}} \\
  &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}
  i\mathbf{w}\mathfrak{F}[f](\mathbf{w})
  \mathrm{exp({i\mathbf{w}\cdot\mathbf{x}})}d\mathbf{w}} \\
  &\color{black}{=\mathfrak{F}^{-1} \circ
    i\mathbf{w}\mathfrak{F}[f]} \\  
\end{aligned}
\end{split}
\end{equation}
$$

Therefore, by applying Fourier transform on both sides and taking use of Fourier inversion theorem, we obtain $\color{black}{\mathfrak{F} [\partial_{\mathbf{x}}f]=i\mathbf{w}\mathfrak{F}[f]}$. Furthormore, this property can be generalized to $\color{black}{n^{th}}$ order of differentiation as $\color{black}{\mathfrak{F} [\partial^n_{\mathbf{x}}f]=(i\mathbf{w})^n\mathfrak{F}[f]}$.  This becomes especially of help when high order differentiation needs to be calculated, thanks to the fact that [Fast Fourier transform (FFT)](https://en.wikipedia.org/wiki/Fast_Fourier_transform) only takes linearithmic time $\color{black}{O(nlogn)}$ for data with size of

#### 3. Convolution theorem:

$$
\begin{equation}
\begin{split}
\color{black}{\mathfrak{F}[f\circ g] = (2\pi)^{\frac{d}{2}}\mathfrak{F}[f]\cdot \mathfrak{F}[g]}
\end{split}
\end{equation}
$$


The convolution theorem states that the Fourier transform of a convolution is the pointwise product of Fourier transforms. In other words, convolution in the spatial domain equals point-wise multiplication in frequency domain. Proof is provided as following:

Let us consider a convolution

$$\begin{equation}
\begin{split}
\color{black}{(f\circ g)(\mathbf{x}) = \int_{\mathbb{R}^d}
f(\mathbf{y})g(\mathbf{x-y})d\mathbf{y}}
\end{split}
\end{equation}
$$

Its Fourier transform reads

$$
\begin{equation}
\begin{split}
\begin{aligned}
\color{black}{\mathfrak{F}[f\circ g](\mathbf{w})}
  &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}
  \int_{\mathbb{R}^d}
  f(\mathbf{y})g(\mathbf{x-y})
  \mathrm{exp({-i\mathbf{w}\cdot\mathbf{x}})}d\mathbf{x}d\mathbf{y}
    }\\
  &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}f(\mathbf{y})\left[
  \int_{\mathbb{R}^d}
  g(\mathbf{x-y})
  \mathrm{exp({-i\mathbf{w}\cdot\mathbf{x}})}d\mathbf{x}\right]d\mathbf{y}
    }\\
    &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}f(\mathbf{y})\left[
    \int_{\mathbb{R}^d}
    g(\mathbf{x-y})
    \mathrm{exp \left[{-i\mathbf{w}\cdot(\mathbf{x-y})}\right]}d\mathbf{x}
    \right]\mathrm{exp({i\mathbf{w}\cdot\mathbf{y}})}d\mathbf{y}
      }\\
\end{aligned}
\end{split}
\end{equation}
$$


Let $\color{black}{\mathbf{z = x - y}}$ and incidentally $\color{black}{d\mathbf{z} = d\mathbf{x}}$,

$$
\begin{equation}
\begin{split}
\begin{aligned}
\color{black}{\mathfrak{F}[f\circ g](\mathbf{w})}
  &\color{black}{=2\pi^{-\frac{d}{2}}\int_{\mathbb{R}^d}f(\mathbf{y})\left[
      \int_{\mathbb{R}^d}
      g(\mathbf{z})
      \mathrm{exp \left[{-i\mathbf{w}\cdot(\mathbf{z})}\right]}d\mathbf{z}
      \right]\mathrm{exp({i\mathbf{w}\cdot\mathbf{y}})}d\mathbf{y}
        }\\
        &\color{black}{=\mathfrak{F}[g](\mathbf{w})\int_{\mathbb{R}^d}f(\mathbf{y})
        \mathrm{exp({i\mathbf{w}\cdot\mathbf{y}})}d\mathbf{y}
              }\\
              &\color{black}{=2\pi^{-\frac{d}{2}}\mathfrak{F}[g] \cdot
              \mathfrak{F}[f](\mathbf{w})
                    }\\
\end{aligned}
\end{split}
\end{equation}
$$

It is worthy mentioning that this is a very useful property of Fourier transform, particularly when proving central limit theorem for random variables that are independent. More applications will be covered in later posts.

#### 4. Scaling:

$$\begin{equation}
\begin{split}
\color{black}{\mathfrak{F}[f(a\mathbf{x})] = \frac{1}{\left| a \right|}  \mathfrak{F}[f]{(\mathbf{w}/a)}}
\end{split}
\end{equation}$$

By using change of variable, it should not be hard to derive the scaling property of Fourier transform. Despite its simplicity, this property has profound significance when it is related to probability theory. It suggests that if the data has a large variance, i.e. strong dislocation in space, then it has high location in frequency domain and vice versa. It is noted that this is a specific representation of Heisenberg's uncertainty principle.

### Spoiler:

In next post, the relation between Fourier transform and characteristic function will be discussed. In particular, the characteristic function of normal distribution will be derived. See you next time.
