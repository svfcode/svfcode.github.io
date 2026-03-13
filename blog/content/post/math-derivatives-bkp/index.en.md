---
title: "Math Analysis — Derivatives"
description: "Derivative, gradient, and chain rule — the backbone of neural network training"
date: "2026-03-12"
slug: "math-derivatives-bkp"
tags:
  - Machine Learning
  - Mathematics
---

Second article in the «Essential Mathematics» series — on derivatives, gradient, and chain rule.

> **Without this you can't understand how neural networks learn.**

**Prerequisites:** limits — foundation for defining the derivative and continuity.

## Contents

1. [What is a derivative](#what-is-a-derivative)
   - [Simple explanation](#simple-explanation)
   - [The simplest explanation](#the-simplest-explanation)
   - [Rules and basic derivative facts](#rules-and-basics)
   - [Numerical example: linear function \( g(x) = 3x - 1 \)](#numerical-example-linear-function)
   - [Numerical example: quadratic function \( f(x) = x^2 \)](#numerical-example-quadratic-function)
   - [Interactive exercise](#interactive-exercise)
   - [Self-check tasks](#self-check-tasks)
2. [Summary](#summary)

## What is a derivative

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

*If it didn't click — open the simple explanation.*

### Simple explanation {#simple-explanation}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>Simple explanation</summary>

**The speedometer** — that's essentially a derivative: how fast the distance traveled changes. Accelerating — speed goes up. Braking — it drops. So the derivative answers: "how much does one quantity change when you change another one a little?"

**A hill.** The steepness of a slope — "how far down you go when you take a step forward." Steep slope — large derivative. Gentle — small. Flat road — zero.

**A function graph.** If you have a graph \( y = f(x) \), the derivative at a point is the **slope** of the graph at that point. For a straight line \( y = kx + b \) the slope is the familiar coefficient \( k \). For a curve, each point has its own slope — that's the derivative.

- Graph steeply going up → positive derivative
- Going down → negative derivative  
- Flat (top or bottom) → derivative equals zero

</details>

*If it's still not crystal clear — open the simplest explanation.*

### The simplest explanation {#the-simplest-explanation}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>The simplest explanation</summary>

**A car drives at constant speed.** Distance \( s \) (km) depends on time \( t \) (h): \( s(t) = 60t \). In one hour we cover 60 km.

Speed is "how many km per hour." The ratio of change in distance to change in time:

\[
\text{speed} = \frac{s(1) - s(0)}{1 - 0} = \frac{60 - 0}{1} = 60 \text{ km/h}
\]

That's the derivative: the **rate of change** of one quantity (distance) with respect to another (time).

**Numeric example:**

| \( t \) (h) | \( s(t) \) (km) | \( s(t+0.5) - s(t) \) | \( \frac{\Delta s}{\Delta t} \) |
|-------------|-----------------|------------------------|--------------------------------|
| 0           | 0               | 30                     | 60                             |
| 1           | 60              | 30                     | 60                             |
| 2           | 120             | 30                     | 60                             |

Everywhere we get 60. **Yes: 60 (the speed in km/h) is the derivative** — \( s'(t) = 60 \). It's constant because the speed doesn't change.

**The graph** — a straight line. The slope of this line is also 60 — the same number:

<div style="margin: 1em 0; aspect-ratio: 320/160; min-height: 160px; max-height: 320px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-graph-linear.html" style="width: 100%; height: 100%; border: none; display: block; background: #1a1a1a;" title="Graph of y = 3x − 1" scrolling="no"></iframe>
</div>

---

**What if the speed varied?** First 30 min at 40 km/h, next 30 min at 80 km/h. Total: 20 + 40 = 60 km in 1 h. **Average** speed is 60 km/h — but at each moment it was either 40 or 80.

<div style="margin: 1em 0; aspect-ratio: 320/160; min-height: 160px; max-height: 320px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-graph-piecewise.html" style="width: 100%; height: 100%; border: none; display: block; background: #1a1a1a;" title="Graph of s(t) and s'(t): smooth acceleration" scrolling="no"></iframe>
</div>

*The graph shows a smooth variant: speed increases from 40 to 80 km/h. Green curve — distance s(t), dashed line — derivative s'(t) (instantaneous speed).*

We compute the **instantaneous** speed (derivative) at several points — using \( \frac{s(t+h) - s(t)}{h} \) with small \( h = 0.1 \) h:

| \( t \) (h) | \( s(t) \) (km) | \( s(t+0.1) - s(t) \) | \( \frac{\Delta s}{\Delta t} \) |
|-------------|-----------------|------------------------|--------------------------------|
| 0.1         | 4               | 4                      | **40**                         |
| 0.25        | 10              | 4                      | **40**                         |
| 0.5         | 20              | —                      | 40 (from left) / **80** (from right) |
| 0.75        | 40              | 8                      | **80**                         |
| 1           | 60              | 8                      | **80**                         |

In the first half-hour the derivative is 40 everywhere; in the second, 80. At \( t = 0.5 \) the graph has a "kink": slope 40 on the left, 80 on the right. The average 60 is just an average over the whole trip; the derivative tells you the speed **at that exact moment**.

</details>

### Rules and basic derivative facts {#rules-and-basics}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>Main rules and facts</summary>

**The derivative is the rate of change.** How fast the function grows (or decreases) for a small shift in the argument. Geometrically — the **slope of the tangent** to the graph.

**Sign and behavior:**
- \( f'(x) > 0 \) — function is increasing
- \( f'(x) < 0 \) — function is decreasing
- \( f'(x) = 0 \) — possible minimum or maximum (peak, valley)

**Main rules (brief):**

| Function | Derivative | Description |
|----------|------------|-------------|
| \( C \) (constant) | \( 0 \) | constant does not change; rate of change is zero |
| \( x \) | \( 1 \) | linear growth at rate 1 |
| \( x^n \) | \( n \cdot x^{n-1} \) | exponent "comes down" as factor; power decreases by 1 |
| \( kx + b \) | \( k \) | linear function: slope equals coefficient \( k \) |
| \( f + g \) | \( f' + g' \) | derivative of sum equals sum of derivatives |
| \( C \cdot f \) | \( C \cdot f' \) | constant can be factored out of the derivative |

**Examples:** \( (5)' = 0 \), \( (x^2)' = 2x \), \( (x^3)' = 3x^2 \), \( (7x - 2)' = 7 \).

**Why it matters in ML:** training minimizes the loss. The derivative points in the direction of increase; gradient descent moves the opposite way (\( -\nabla L \))[^1] so the loss decreases.

[^1]: \( \nabla L \) — the gradient of the loss (vector of partial derivatives). It points in the direction of steepest increase of \( L \). So \( -\nabla L \) is the direction of steepest decrease; we move that way in gradient descent.

<details style="background: rgba(16, 185, 129, 0.08); padding: 0.6em 0.9em; border-radius: 6px; margin-top: 0.75em; border-left: 3px solid #10b981;">
<summary>Why \( (x^n)' = n \cdot x^{n-1} \)?</summary>

For natural \( n \) we can derive from the definition. Example for \( n = 2 \):

\[
\frac{(x+h)^2 - x^2}{h} = \frac{x^2 + 2xh + h^2 - x^2}{h} = 2x + h \to 2x
\]

As \( h \to 0 \) we get \( (x^2)' = 2x \). For \( n = 3 \): expanding \( (x+h)^3 \), the \( h^2 \) term vanishes in the limit, leaving \( 3x^2 \).

**Intuition:** the power \( n \) «comes down» as a multiplier; the exponent drops by 1. Higher power means steeper growth — so the derivative has \( n \) and \( x^{n-1} \).

**Example: parabola \( y = x^2 \)** — in detail

For \( f(x) = x^2 \) the formula gives \( f'(x) = 2x \). Each point has its own slope:

| Point \( x \) | \( f(x) = x^2 \) | \( f'(x) = 2x \) (slope) |
|---------------|------------------|--------------------------|
| 0             | 0                | 0                        |
| 1             | 1                | 2                        |
| 2             | 4                | **4**                    |
| 3             | 9                | 6                        |
| 4             | 16               | **8**                    |

At \( x = 2 \): the parabola is tangent to a line with slope 4 (tangent \( y = 4x - 4 \) passes through (2, 4)).  
At \( x = 4 \): slope is 8 — the parabola is steeper, tangent \( y = 8x - 16 \).  
At \( x = 0 \): vertex of the parabola, slope 0 — tangent is horizontal.

<div style="margin: 0.75em 0; aspect-ratio: 320/240; min-height: 200px; max-height: 400px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-graph-parabola.html" style="width: 100%; height: 100%; border: none; display: block; background: #1a1a1a;" title="Parabola y = x² and tangents" scrolling="no"></iframe>
</div>

*On the graph:* green curve — \( y = x^2 \); dashed lines — tangents at (2, 4) and (4, 16). Slopes 4 and 8 match \( f'(2) = 4 \), \( f'(4) = 8 \).

**Example: square** — \( x \) as side length, area \( A(x) = x^2 \)

ΔA is the increment (change) of area A. If area is given by function \( A(x) \), then:
\[
\Delta A = A(x + \Delta x) - A(x)
\]
So ΔA is how much area is added when side \( x \) increases by Δx.

Increase the side by \( \Delta x \). To the original square we add: two "strips" of area \( x \cdot \Delta x \) (right and top) and a small square \( (\Delta x)^2 \) in the corner. So:
\[
\Delta A = 2x \cdot \Delta x + (\Delta x)^2,\quad \frac{\Delta A}{\Delta x} = 2x + \Delta x \to 2x
\]
as \( \Delta x \to 0 \). Derivative \( A'(x) = 2x \) — for the same \( \Delta x \), larger \( x \) gives more area gain.

<div style="margin: 0.75em 0; min-height: 360px;">
  <iframe src="/games/derivative-square-area-en.html" style="width: 100%; height: 360px; border: none; display: block; background: #1a1a1a; border-radius: 8px;" title="Square: area and increment"></iframe>
</div>

*Change x and Δx* — observe how the "strips" and \( \Delta A / \Delta x \approx 2x \) change.

It's important to distinguish two cases.

\( \Delta A/\Delta x \approx 2x \) — yes, this is an approximation. It holds when \( \Delta x \) is small but nonzero. The smaller \( \Delta x \), the more accurate:
\[
\frac{\Delta A}{\Delta x} = 2x + \Delta x \approx 2x \quad \text{for small } \Delta x
\]

The formula \( (x^n)' = nx^{n-1} \) — this is not an approximation, but an exact expression. The derivative is defined as the limit:
\[
f'(x) = \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}
\]
We take this limit first, then obtain the exact formula.

\( \Delta A/\Delta x \) — approximation, because \( \Delta x \) is still finite. \( A'(x) = 2x \) and \( (x^n)' = nx^{n-1} \) — exact formulas, because they are the result of the limit \( \Delta x \to 0 \).

*In short:* approximation applies to finite differences; the derivatives themselves and their formulas are exact.

</details>

<details style="background: rgba(16, 185, 129, 0.08); padding: 0.6em 0.9em; border-radius: 6px; margin-top: 0.75em; border-left: 3px solid #10b981;">
<summary>Why \( (C \cdot f)' = C \cdot f' \)?</summary>

The constant can be factored out of the derivative because it does not depend on \( x \) and merely scales the rate of change of the function.

**From the definition:**
\[
(C \cdot f)'(x) = \lim_{h \to 0} \frac{C \cdot f(x+h) - C \cdot f(x)}{h} = C \cdot \lim_{h \to 0} \frac{f(x+h) - f(x)}{h} = C \cdot f'(x)
\]

The constant \( C \) does not depend on \( h \), so it can be taken outside the limit.

**Examples:** \( (5x^2)' = 5 \cdot 2x = 10x \), \( (-3x^3)' = -3 \cdot 3x^2 = -9x^2 \).

</details>

</details>

*Now a few numerical examples.*

### Numerical example: linear function \( g(x) = 3x - 1 \) {#numerical-example-linear-function}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>Numerical example: linear function \( g(x) = 3x - 1 \)</summary>

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

</details>

### Numerical example: quadratic function \( f(x) = x^2 \) {#numerical-example-quadratic-function}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>Numerical example: quadratic function \( f(x) = x^2 \)</summary>

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

</details>

### Interactive exercise {#interactive-exercise}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>Car and Bezier curve</summary>

**1. Car.** Change the speed — the distance graph \( s(t) \) and derivative table update. Derivative \( s'(t) \) = speed (constant for uniform motion).

<div style="margin: 1em 0; min-height: 380px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-car-interactive-en.html" style="width: 100%; height: 420px; border: none; display: block; background: #1a1a1a;" title="Car: speed and derivative" scrolling="no"></iframe>
</div>

**2. Draw a Bezier curve.** Drag 4 control points — a cubic Bezier curve is built. Place the orange point on the curve — the derivative calculation appears on the right.

<div style="margin: 1em 0; min-height: 420px; overflow: hidden; border-radius: 8px; background: #1a1a1a;">
  <iframe src="/games/derivative-draw-curve-en.html" style="width: 100%; height: 520px; border: none; display: block; background: #1a1a1a;" title="Bezier curve and derivative" scrolling="no"></iframe>
</div>

</details>

### Self-check tasks {#self-check-tasks}

<details style="background: rgba(59, 130, 246, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #3b82f6;">
<summary>Tasks with hints and verification</summary>

Solve the tasks. Open the hint if needed. Enter your answer and click "Check".

<div style="margin: 0.5em 0; min-height: 480px;">
  <iframe src="/games/derivative-selfcheck-en.html" style="width: 100%; height: 480px; border: none; display: block; background: #1a1a1a; border-radius: 6px;" title="Self-check tasks"></iframe>
</div>

</details>

## Summary

- **Derivative** — rate of change, direction of increase
- **Partial derivative** — with respect to one variable, others fixed
- **Gradient** — vector of partial derivatives, direction of steepest increase
- **Chain rule** — how to compute derivatives along a chain of layers
- **Gradient descent** — update weights in the \( -\nabla L \) direction [^1]

PyTorch, TensorFlow, etc. compute gradients automatically (autograd) — but understanding what happens under the hood helps when you hit «exploding gradients» or «model won't learn».