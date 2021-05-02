---
title: motivations
description: problem formulations for manifold optimization
toc: true
authors:
tags:
categories:
series:
date: '2020-10-16'
lastmod: '2020-10-16'
draft: false
---

Formulations that motivate manifold optimization.


## Logistic regression

Taking a well known formulation from linear algebra and teasing out a curvy
structure.

Consider $x_1,\ldots,x_m \in \xi$ each with a corresponding binary label
$y_1,\ldots,y_m \in \\{0,1\\}$.

We can define some vector $\theta \in \xi$ that we can "grab onto" with each
$x_i$ using an inner-product defined over the space. Applying a logistic
transform $\sigma$, we can obtained well-behaved probabilities:

$$P[y=1|x,\theta] = \sigma(\lang\theta, x_i\rang)  $$
$$P[y=0|x,\theta] = 1 - \sigma(\lang\theta, x_i\rang)  $$

(Recall $\sigma : \mathbb{R}\rightarrow(0,1)$)

If we want to learn a good $\theta$, we want optimize w.r.t. the likelihood
function:

$$L(\theta) =
\prod_{i=1}^{m}\sigma(\lang\theta,x_i\rang)^{y_i}\sigma(-\lang\theta,x_i\rang)^{1-y_i}$$

The compressed notation is just Bayes rule. First marginalize over $y$, then sum
over all $x$ to get the full posterior.

We can reframe as the convex optimization objective:

  $$ \min_{\theta \in \xi} L(\theta) + \lambda \lVert\theta\rVert^2$$

Where the constraints now define a smooth manifold.

## Sensor network localization

$$ \ldots $$

## Extreme singular values

## Dictionary learning
