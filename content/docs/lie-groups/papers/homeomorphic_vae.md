---
title: homeomorphic vae
description: 
toc: true
authors:
tags:
categories:
series:
date: '2021-04-17'
lastmod: '2021-04-17'
draft: false
---

[ Explorations in Homeomorphic Variational Auto-Encoding ](https://arxiv.org/abs/1807.04689)

## Background

### Revisiting VAE

A variational auto-encoder is a generative model that learns a joint
distribution over input data and some latent random variable using [variational
inference](https://ermongroup.github.io/cs228-notes/inference/variational/) techniques.

$$ p(x, z) = p(x|z)p(z) $$

Say we now have some data $X = \\{ x_1 \ldots x_N \\}$.
Our objective is to learn a set of latent random variables that maximize our
ability to reconstruct this set from our latent $\\{z_i\\}$

$$ \frac{1}{N} \log p(X) = \frac{1}{N} \sum_{i=1}^{N} \log \int p(x_i, z_i) dz $$

However, our computing closed form $p(X)$ is often intractable when each latent
$z$ is parameterized by a neural network, so we need to invoke variational
inference to approximate our joint $p(x, z)$. Detailed derivation of our lower
bound in a future note.

$$ \log p(X) \ge E_{q(z)}[\log p(x|z)] - KL(q(z) \mid\mid p(z)) $$

Note:

$$ \log p(X) =  \log \int p(x,z) dz  \ge E_{q(z)}[log p(x|z)] - KL(q(z) \mid\mid p(z)) $$

Using a [reparameterization
trick](https://stats.stackexchange.com/questions/199605/how-does-the-reparameterization-trick-for-vaes-work-and-why-is-it-important)
to enable tractable backpropogation, we arrive at:

$$ \log p(X) \ge E_{q(z|x)}[log p(x|z)] - KL(q(z|x) \mid\mid p(z)) $$

### Lie Groups + Algebras

A group is a set that is equipped with a binary operation that satisfies
properties, namely: 

* associativity over the operation 
* the existence of an identity element invariant to the operation 
* an inverse for each element that will recover the identity

A _Lie group_ $G$ is equipped with a product that satisfies these
properties. However, these groups are also smooth manifolds, which means a derivative is
globally defined, and group elements can be described _continuously_ with
respect to a set of parameters.

There also exists a _lie algebra_, which is the vector space tangent to the
identity element of $G$ and is denoted by $\mathfrak{g}$.

The lie group is connected to the lie algebra through a _exponential map_:

$$ \exp: \mathfrak{g} \mapsto G $$

The mapping is surjective onto our group $G$.

### SO(3)

This notation translates to special orthogonal lie group of 3-dim rotations.


$$ SO(3) := \\{ R \in GL(\mathbb{R^3}) : R^T R = \mathbf{I} \wedge \det(A) = 1 \\}  $$

Where $GL$ is the [general linear
group](https://en.wikipedia.org/wiki/General_linear_group) using the
aforementioned definition of a group in the mathematical sense. Here group
members are clearly both square and invertible matrices.


## Reparameterizing Lie Groups



### Pushforward Measure Proof

$$ \ldots $$

