---
title: "Essential Mathematics — Overview"
description: "What math knowledge is needed for AI and machine learning, and why"
date: "2026-03-12"
slug: "math-essentials-overview"
tags:
  - Machine Learning
  - Mathematics
  - Computer Vision
---

This is the intro to the «Essential Mathematics» series — an overview of which math areas are needed for AI and machine learning, and what they are used for.

## Linear Algebra

**What you need:** vectors, matrices, matrix multiplication, linear transformations, dot product, vector norm, eigenvalues and eigenvectors (advanced).

**Why:**
- Vectors — the basic way to represent data: a word, an image, or a model's «thought» is encoded as a vector of numbers
- Matrices — all neural network operations (convolutions, attention, linear layers) boil down to matrix multiplication
- Linear transformations — understanding how a layer «mixes» and combines features
- Without linear algebra you cannot read formulas in papers or understand what the code does (e.g. `W @ x` is weight matrix times input vector)[^1]

[^1]: `W @ x` — in Python (NumPy, PyTorch) the matrix multiplication operator: the weight matrix W is multiplied by the input vector x. The result is the output vector. A linear layer essentially computes `W·x + b`.

## Derivatives

**What you need:** derivatives, partial derivatives, gradient, chain rule, function optimization.

**Why:**
- Neural networks are trained via gradient descent: we move weights in the direction that reduces the error
- Gradient — a vector of partial derivatives showing which way to «tweak» each parameter
- Chain rule is the backbone of backpropagation — the algorithm that computes gradients for all layers
- Without calculus you cannot understand where weight updates come from or why training works at all

## Probability and Statistics

**What you need:** distributions (normal, Bernoulli, etc.), expectation, variance, conditional probability, Bayes' theorem, maximum likelihood estimation (MLE).

**Why:**
- Models are often formulated probabilistically: «probability of the next word», «how confident is the model»
- Loss functions often derive from likelihood (cross-entropy, MSE, etc.)
- Statistics for working with data: normalization, quality assessment, understanding metrics (precision, recall, AUC)
- Bayes — foundation of many classical algorithms and the way to «update beliefs» on new data

## Computer Vision (CV)

**On top of the general minimum:** discrete convolution (2D), affine and projective transformations, basic image geometry (camera calibration, epipolar geometry).

**Why:**
- Convolution — the core of CNNs: understanding how a filter «slides» over an image, and what kernel, padding, stride mean
- Affine transformations (rotation, scale, shift) — for augmentations and understanding invariance
- Projective geometry and homographies — for stereo vision, 3D reconstruction, AR
- For classical methods (SIFT, optical flow) — image derivatives and per-pixel gradients are useful

## Optional but helpful

- **Information theory** (entropy, cross-entropy) — deeper understanding of loss functions and data compression
- **Convex optimization** — when the problem is «nice» and when SGD converges
- **Differential geometry** — for advanced topics (diffusion models, representations)

## Practical minimum

To comfortably read papers and code:
- Be able to multiply matrices and understand what a linear layer does
- Understand what a gradient is and why it matters for training
- Know basic distributions and quality metrics

You can pick up the rest as needed — when it appears in a specific problem or paper.