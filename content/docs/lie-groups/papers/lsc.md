---
title: lie group sparse coding
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

[ Disentangling Images with Lie Group Transformations and Sparse Coding ](https://arxiv.org/abs/2012.12071)

# Background

### Transformation Parameterization

We first walk through some background for the modeling of the learned transform:

$$ T(s)=W R(s) W^T $$


#### Peter-Weyl Theorem

$$\ldots$$

#### CCC Lie Groups

$$\ldots$$

## Formulation

We represent some image $I \in \mathbb{R^D}$ as

$$ I = WR(s)W^T\phi\alpha  + \epsilon $$

Where $\phi \in \mathbb{R^{DxK}}$ is our dictionary of templates and $\alpha \in
\mathbb{R^K}$ is our code.

$$ WR(s)W^T\phi\alpha  + \epsilon $$

Few notes:

  * Each template, or column of $\mathbb{R^{DxK}}$, has unit L2 norm. This
    ensures that each discrete pattern is qualitatively unique irrespective of
    scaling. 

##  Learning algorithm

$$  \theta = \\{ W, \phi \\} \leftarrow \\{ W_0, \phi_0 \\} $$

Where our coefficient vector $\alpha$ is initialized as i.i.d. Exponential r.v.s:

$$  \alpha \leftarrow \alpha_0 : \alpha \in \mathbb{R^K},  a_k \sim Exp(\lambda) $$

$$ P_\theta(s|I, \alpha) $$

To compute the MAP estimate $\hat\alpha$ we need to perform gradient ascent over
the log posterior $ln P_\theta(\alpha|I)$:

$$\nabla_\alpha ln P_\theta(\alpha|I) = \nabla_\alpha ln P_\theta(I|\alpha) +
\nabla_\alpha ln P_\theta(\alpha)$$



We first take expectation of the joint density by
[marginalizing](https://stats.stackexchange.com/questions/72613/subscript-notation-in-expectations/72614)
w.r.t $s$, and take the gradient of the remaining expression that is still a
function of $\alpha$.

$$ \Delta\alpha \leftarrow E_{s \sim P_\theta(s|I,\alpha)}[\nabla_\alpha ln
P_\theta(I|s,\alpha)] $$

We then 
What is $\nabla_\alpha ln P_\theta(\alpha)$?

What we are left with is:

$$ \Delta\alpha \leftarrow E_{s \sim P_\theta(s|I,\alpha)}[\nabla_\alpha ln
P_\theta(I|s,\alpha)] +
\nabla_\alpha ln P_\theta(\alpha)  $$

Which we use to iteratively update our coefficients using [$FISTA$](https://www.ceremade.dauphine.fr/~carlier/FISTA) like so:

$$\alpha \leftarrow FISTA(\alpha, \nabla\alpha)$$  
