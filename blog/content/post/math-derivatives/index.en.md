---
title: "Math Analysis — Derivatives"
description: "Derivative, gradient, and chain rule — the backbone of neural network training"
date: "2026-03-13"
slug: "math-derivatives"
tags:
  - Machine Learning
  - Mathematics
---

> **Without this you can't understand how neural networks learn.**

A common example is the speed of a car. We'll do the same.

## What is speed?

It's the ratio of distance to time.

A car traveling at an average speed of 60 km/h — if we increase time \( t \) by one unit, distance \( s \) increases by 60 units. If we multiply \( t \) by 10, \( s \) is multiplied by 10 as well. The growth is linear; on a graph it's a straight line.

{{< chart_linear_st title="s = 60t" >}}

But over time the car moves unevenly — speed increases and decreases.

{{< chart_nonuniform_st_vt labelS="s(t) — distance" labelV="v(t) — velocity" >}}

<details style="background: rgba(239, 68, 68, 0.08); padding: 0.75em 1em; border-radius: 8px; margin: 0.5em 0; border-left: 3px solid #ef4444;">
<summary>Impossible</summary>

Distance traveled cannot decrease. Such an s(t) graph would be wrong:

{{< chart_impossible_st label="s(t) — wrong" >}}

</details>

{{< quiz_nonuniform lang="en" >}}
