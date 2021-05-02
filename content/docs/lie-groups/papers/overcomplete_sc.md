---
title: overcomplete sparse coding
description: 
toc: true
authors:
tags:
categories:
series:
date: '2021-05-01'
lastmod: '2021-05-01'
draft: false
---

[ Highly overomplete sparse coding ](http://www.rctn.org/bruno/papers/highly-overcomplete-SPIE.pdf)

## Background

## Formulation

We wish to model an image $I$ (where $I(\vec{x})$ refers to discrete segments of
the image) as:

$$ I(\vec{x}) = \sum_{i=1}^{M} \alpha_i \phi_i(\vec{x}) + \epsilon(\vec{x})  $$

To evaluate "goodness" of reconstruction we define an energy function:
  
$$ E = \frac{1}{2} \sum_{\vec{x}} [ I(\vec{x}) - \sum_{i=1}^{M} \alpha_i \phi_i(\vec{x}) ]^2 $$

That essentially computes a mean squared error between a dictionary
reconstruction and ground truth for each image segment.

We add an additional L1 constraint on our "code" to enforce sparsity:

$$ \lambda \sum_{i=1}^{M} |a_i| $$

Together our loss becomes:

$$ E = \frac{1}{2} \sum_{\vec{x}} [ I(\vec{x}) - \sum_{i=1}^{M} \alpha_i
\phi_i(\vec{x}) ]^2 + \lambda \sum_{i=1}^{M} |a_i| $$

## Results

A complete dictionary $\phi$. Each tile is a learned transform in the
dictionary.

Complete dictionaries yield basis transforms that are from the [garbor filter](https://en.wikipedia.org/wiki/Gabor_filter)
family.

## Notes 

The goal of a sparse code is not to improve reconstruction!

Reconstruction is perfect if your dictionary has the thing you are trying to
reconstruct. This is trivial.

As Bruno taught us, reconstruction is a proxy to understand how good your latent
representation scheme is. Highly-specialized (sparse) and variate
(overcomplete) part "catalogs" are easier to work with because they produce
parts that are semantic.

Intuitively, if you are forced to 10x the size of your toolbox but you are also
forced to use each tool sparingly, those tools become specialized and good.
