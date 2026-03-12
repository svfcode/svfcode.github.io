---
title: "Math Analysis — Derivatives"
description: "Derivative, gradient, and chain rule — the backbone of neural network training"
date: "2025-03-12"
slug: "math-derivatives"
tags:
  - Machine Learning
  - Mathematics
---

Second article in the «Essential Mathematics» series — on derivatives, gradient, and chain rule. Without this you can't understand how neural networks learn.

## What is a derivative

### Simple explanation

**The speedometer** — that's essentially a derivative: how fast the distance traveled changes. Accelerating — speed goes up. Braking — it drops. So the derivative answers: "how much does one quantity change when you change another one a little?"

**A hill.** The steepness of a slope — "how far down you go when you take a step forward." Steep slope — large derivative. Gentle — small. Flat road — zero.

**A function graph.** If you have a graph \( y = f(x) \), the derivative at a point is the **slope** of the graph at that point. For a straight line \( y = kx + b \) the slope is the familiar coefficient \( k \). For a curve, each point has its own slope — that's the derivative.

- Graph steeply going up → positive derivative
- Going down → negative derivative  
- Flat (top or bottom) → derivative equals zero

### Formal definition

The derivative of a function at a point shows the **rate of change**: how fast the function grows (or decreases) for a small shift in the argument.

For a single-variable function \( f(x) \), the derivative \( f'(x) \) is the limit of the ratio of the change in \( f \) to the change in \( x \) as the change goes to zero:

\[
f'(x) = \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}
\]

Here \( \Delta x \) is the increment of the argument (a small step). In the examples below we use \( h \) for the same quantity.

Geometrically — the slope of the tangent line at \( x \):
- \( f'(x) > 0 \) — function is increasing
- \( f'(x) < 0 \) — function is decreasing
- \( f'(x) = 0 \) — possible minimum or maximum

### Numerical example: linear function \( g(x) = 3x - 1 \)

For a straight line the slope is the same everywhere. At any point, e.g. \( x = 5 \):

\[
\frac{g(5 + h) - g(5)}{h} = \frac{(3(5+h) - 1) - g(5)}{h} = \frac{14 + 3h - 14}{h} = \frac{3h}{h} = 3
\]
where \( g(5) = 3 \cdot 5 - 1 = 14 \).

For any \( h \neq 0 \) we get **3** — the derivative is constant, same as the coefficient of \( x \) in the line equation.

| \( x \) | \( g(x) \) | \( g(x+0.1) - g(x) \) | \( \frac{g(x+0.1)-g(x)}{0.1} \) |
|---------|------------|------------------------|--------------|
| 5       | 14         | 0.3                    | 3            |
| 10      | 29         | 0.3                    | 3            |
| -2      | -7         | 0.3                    | 3            |

<div style="margin: 1em 0; aspect-ratio: 320/160; min-height: 160px; max-height: 320px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-graph-linear.html" style="width: 100%; height: 100%; border: none; display: block; background: #1a1a1a;" title="Graph of y = 3x − 1" scrolling="no"></iframe>
</div>

### Numerical example: quadratic function \( f(x) = x^2 \)

Approximate the derivative at \( x = 2 \) using "change in \( f \) over change in \( x \)". Take a small step \( h \):

\[
\frac{f(2 + h) - f(2)}{h} = \frac{(2+h)^2 - 4}{h}
\]

**At \( x = 2 \)** (\( f(2) = 4 \)):

| \( h \) | \( f(2+h) \) | \( f(2+h) - f(2) \) | \( \frac{f(2+h)-f(2)}{h} \) |
|--------|--------------|---------------------|-----------------------------|
| 1      | 9            | 5                   | 5                           |
| 0.1    | 4.41         | 0.41                | 4.1                         |
| 0.01   | 4.0401       | 0.0401              | 4.01                        |
| 0.001  | 4.0004…      | 0.004…              | 4.001                       |

The ratio tends to **4** → \( f'(2) = 4 \).

**At \( x = 4 \)** (\( f(4) = 16 \)):

\[
\frac{f(4 + h) - f(4)}{h} = \frac{(4+h)^2 - 16}{h} = \frac{8h + h^2}{h} = 8 + h \to 8
\]

| \( h \) | \( f(4+h) \) | \( f(4+h) - f(4) \) | \( \frac{f(4+h)-f(4)}{h} \) |
|--------|--------------|---------------------|-----------------------------|
| 1      | 25           | 9                   | 9                           |
| 0.1    | 16.81        | 0.81                | 8.1                         |
| 0.01   | 16.0801      | 0.0801              | 8.01                        |

The ratio tends to **8** → \( f'(4) = 8 \). By \( (x^2)' = 2x \): at \( x = 2 \) we get 4, at \( x = 4 \) — 8. For a curve, the derivative is different at each point.

<div style="margin: 1em 0; aspect-ratio: 320/240; min-height: 240px; max-height: 480px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-graph-parabola.html" style="width: 100%; height: 100%; border: none; display: block; background: #1a1a1a;" title="Graph of y = x² and tangent" scrolling="no"></iframe>
</div>

**Why it matters in ML:** training is minimization of the loss function. We need to know which direction to change the weights so that the loss decreases. The derivative points in the direction of increase; we go the opposite way so the loss drops.

## Partial derivative

A neural network has many weights — the loss depends on thousands or millions of variables. We need to know how the loss changes when we change **each** weight separately.

A **partial derivative** \( \frac{\partial f}{\partial x} \) — the derivative with respect to one variable, treating the others as constants.

Example: \( f(x, y) = x^2 + xy \)
- \( \frac{\partial f}{\partial x} = 2x + y \)
- \( \frac{\partial f}{\partial y} = x \)

## Gradient

The **gradient** \( \nabla f \) — the vector of all partial derivatives:

\[
\nabla f = \left( \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2}, \ldots, \frac{\partial f}{\partial x_n} \right)
\]

The gradient points in the direction of **steepest increase** of the function. So \( -\nabla f \) is the direction of steepest **decrease**.

**Gradient descent** — iterative weight updates:

\[
w_{new} = w_{old} - \alpha \cdot \frac{\partial L}{\partial w}
\]

where \( \alpha \) is the learning rate (step size), \( L \) is the loss. We move in the direction opposite to the gradient so the loss decreases.

## Chain rule

A neural network is a chain of layers: each layer's output is fed to the next. The loss depends on the outputs, and those depend on the weights. To get \( \frac{\partial L}{\partial w} \), we need to «propagate» the derivative backward through this chain.

**Chain rule** for composed functions: if \( z = f(y) \) and \( y = g(x) \), then

\[
\frac{dz}{dx} = \frac{dz}{dy} \cdot \frac{dy}{dx}
\]

For many variables it works the same way: the derivative with respect to an earlier layer's weight is the product of derivatives along the path from that weight to the loss.

**Backpropagation** — the algorithm that does this efficiently: one backward pass through the network computes all needed gradients at once.

## Example: linear regression

Loss — mean squared error: \( L = \frac{1}{2}(y - \hat{y})^2 \), where \( \hat{y} = wx + b \).

\[
\frac{\partial L}{\partial w} = \frac{\partial L}{\partial \hat{y}} \cdot \frac{\partial \hat{y}}{\partial w} = -(y - \hat{y}) \cdot x
\]

The larger the error \( (y - \hat{y}) \) and the larger \( x \), the more we adjust \( w \). Makes sense: a big error and an «important» input require a larger update.

## Summary

- **Derivative** — rate of change, direction of increase
- **Partial derivative** — with respect to one variable, others fixed
- **Gradient** — vector of partial derivatives, direction of steepest increase
- **Chain rule** — how to compute derivatives along a chain of layers
- **Gradient descent** — update weights in the \( -\nabla L \) direction

PyTorch, TensorFlow, etc. compute gradients automatically (autograd) — but understanding what happens under the hood helps when you hit «exploding gradients» or «model won't learn».