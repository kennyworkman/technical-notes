---
title: lsc directions
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

Directions for future work...

# Background

We represent some image $I \in \mathbb{R^D}$ as

$$ I = WR(s)W^T\phi\alpha  + \epsilon $$

Where $\phi \in \mathbb{R^{DxK}}$ is our dictionary of templates and $\alpha \in
\mathbb{R^K}$ is our code.

$$ WR(s)W^T\phi\alpha  + \epsilon $$

Few notes:

  * Each template, or column of $\mathbb{R^{DxK}}$, has unit L2 norm. This
    ensures that each discrete pattern is qualitatively unique irrespective of
    scaling. 

### Transform distribution proposal

We recognize that an overcomplete template basis necessitates learning
smaller and more specific parts.

Perhaps we were able to learn a single transform on our composition of parts
because each part was really a digit. And our code amounted to just choosing the
correct digit.

With a true sparse-code, our parts will be more fickle, and we will want far
more control over the manipulation of their poses for accurate reconstruction.

The following formulation is 

Our objective is assign a transform $ T(s)=W R(s) W^T $ to each template in
$\phi$.


As a summation:

$$ I = \sum_{k=1}^{K=20} \alpha_k W_k R(s_k) W_k^T \phi_k : W \in
\mathbb{R^{Dx2}}$$
