---
title: "BetterExplained - Part 2 - Arithmetic"
description: >-
  Numbers (N, Z, Q, R), their properties and relations, operations
  <span class="op-pairs"><span class="op-pair">+ and −</span><span class="op-pair">× and /</span><span class="op-pair">\(a^{b}\) and \(\sqrt[n]{a}\)</span></span>
date: "2026-06-01"
slug: "math-better-explained-arithmetic"
tags:
  - Mathematics
  - Machine Learning
  - Basics
image: cover.jpg
---

## Mental tricks

{{< accordion_controls expand="Expand all" collapse="Collapse all" >}}

{{< accordion_group_open >}}

### 60 km/h is 1 km per minute {.toc-heading-only}

<details class="post-accordion">
<summary>60 km/h is 1 km per minute</summary>
<div>

Driver reaction time (notice → decide → act) is ~1 second.

So if an obstacle appears closer than 16 meters (at 60 km/h), you probably cannot do anything in time. If the speed is three times higher, what distance is critical?

</div>
</details>

### 1 year = 250 work days = 2000 work hours {.toc-heading-only}

<details class="post-accordion">
<summary>1 year = 250 work days = 2000 work hours</summary>
<div>

So if you spend 1 hour per day commuting (half an hour each way), you spend 250 hours per year on the road.

</div>
</details>

### Rule of 72: years to double = 72 / interest rate {.toc-heading-only}

<details class="post-accordion">
<summary>Rule of 72: years to double = 72 / interest rate</summary>
<div>

Want 10% annual growth on your investments? They double in 7.2 years.

Want your investments to double in 5 years? You need a rate of 72/5, or about 15%.

You can use this rule for any time period, not just years.

Inflation is 4%? That cuts your money in half in 72/4, or 18 years.

</div>
</details>

### Mental arithmetic {.toc-heading-only}

<details class="post-accordion">
<summary>Mental arithmetic</summary>
<div>

10,000 = hundred hundred

million = thousand thousand

billion = thousand million

trillion = million million

1% of 10k is 100. The Dow is roughly 10k (it's about 12k now). So if the Dow drops 100, it's about a 1% loss.

What's 5k × 50k? That's 250 × thousand × thousand, or 250 million.

</div>
</details>

### Visualizing numbers {.toc-heading-only}

<details class="post-accordion">
<summary>Visualizing numbers</summary>
<div>

12 days = 1 million seconds

1 year = 31 million seconds (about π × 10 million)

30 years = 1 billion seconds

30,000 years = 1 trillion seconds

One “part per million” means an accuracy of 1 second every 12 days. One “part per trillion” means an accuracy of 1 second every 30,000 years.

</div>
</details>

### a% of b = b% of a {.toc-heading-only}

<details class="post-accordion">
<summary>a% of b = b% of a</summary>
<div>

It’s not immediately clear, but it’s true: a% of b = 0.01 × a × b, which is the same as b% of a (0.01 × b × a).

What’s 16% of 25? The same as 25% of 16: 4.

What’s 43% of 200? The same as 200% of 43: 86.

</div>
</details>

{{< accordion_group_close >}}

## Sum from 1 to n

{{< accordion_controls expand="Expand all" collapse="Collapse all" >}}

{{< accordion_group_open >}}

### We're usually just given the formula and told to memorize it {.toc-heading-only}

<details class="post-accordion">
<summary>We're usually just given the formula and told to memorize it</summary>
<div>

\[
\text{Sum from 1 to } n = \frac{n(n+1)}{2}
\]

\[
\text{Sum from 1 to 100} = \frac{100(100+1)}{2} = (50)(101) = 5050
\]

But to build **intuition** and really understand it, you need to **derive the formula yourself**.

Below are four ways to derive it.

</div>
</details>

### 1) Split the sequence in half and add in pairs {.toc-heading-only}

<details class="post-accordion">
<summary>1) Split the sequence in half and add in pairs</summary>
<div>

```
 1   2   3   4   5
10   9   8   7   6
```

Each vertical pair has the same sum: \(1 + 10 = 2 + 9 = \ldots = n + 1\). There are \(\frac{n}{2}\) pairs.

\[
\text{Number of pairs} \times \text{sum of each pair} = \frac{n}{2}(n+1) = \frac{n(n+1)}{2}
\]

</div>
</details>

### 2) Two rows of numbers {.toc-heading-only}

<details class="post-accordion">
<summary>2) Two rows of numbers</summary>
<div>

```
 1   2   3   4   5   6   7   8   9  10
10   9   8   7   6   5   4   3   2   1
```

Add **both** rows: every column sums to \(n + 1\), and there are \(n\) columns:

\[
\text{Sum of both rows} = n(n+1)
\]

We only want **one** row, so divide by 2:

\[
\frac{n(n+1)}{2}
\]

</div>
</details>

### 3) Picture a triangle {.toc-heading-only}

<details class="post-accordion">
<summary>3) Picture a triangle</summary>
<div>

```
x
x x
x x x
x x x x
x x x x x
```

\(n\) rows, row \(k\) has \(k\) cells — \(1 + 2 + \ldots + n\) in total. Imagine fitting two such triangles together tooth-to-tooth to form a rectangle. **Derive the formula yourself** from that picture.

</div>
</details>

### 4) Via the average — the most interesting one, in my view {.toc-heading-only}

<details class="post-accordion">
<summary>4) Via the average — the most interesting one, in my view</summary>
<div>

We all know that

\[
\text{average} = \frac{\text{sum}}{\text{number of items}}
\]

which we can rewrite as

\[
\text{sum} = \text{average} \times \text{number of items}
\]

For \(1, 2, \ldots, n\) the average is easy to eyeball from the **middle** of the range: \(\frac{n+1}{2}\). There are \(n\) items, so:

\[
\text{sum} = \frac{n+1}{2} \cdot n = \frac{n(n+1)}{2}
\]

For \(1 \ldots 100\): average \(\approx 50.5\), sum \(50.5 \times 100 = 5050\).

</div>
</details>

{{< accordion_group_close >}}

## Visual arithmetic

{{< accordion_controls expand="Expand all" collapse="Collapse all" >}}

{{< accordion_group_open >}}

### Every operation is a transformation {.toc-heading-only}

<details class="post-accordion">
<summary>Every operation is a transformation</summary>
<div>

Every operation is a transformation. In the real world there are things we want to slide, smoosh and stretch — arithmetic is exactly what gives us the tools to model that.

</div>
</details>

### Addition gives tools for: {.toc-heading-only}

<details class="post-accordion">
<summary>Addition gives tools for:</summary>
<div>

1) accumulation — counting quantities (total at checkout)
2) slide — move a mark along a scale (temperature)
3) combination — a new quantity from two different ones (sound wave)

</div>
</details>

### Multiplication gives tools for: {.toc-heading-only}

<details class="post-accordion">
<summary>Multiplication gives tools for:</summary>
<div>

1) repetition — several additions in a row
2) scaling — a number grows or shrinks all at once

</div>
</details>

### Negatives and inverses {.toc-heading-only}

<details class="post-accordion">
<summary>Negatives and inverses</summary>
<div>

1) multiply by 1/2: turn a profit of 1 into a profit of 1/2 (“unscale”)
2) multiply by −2: turn a profit of 1 into a loss of 2 (“invert”)

</div>
</details>

### Division gives tools for: {.toc-heading-only}

<details class="post-accordion">
<summary>Division gives tools for:</summary>
<div>

1) share (\(a/b\)) — how much of the whole: ate \(3/8\) of the pizza, tank is \(2/5\) full
2) split (\(a \div b\)) — how many groups of \(b\) in \(a\): \(12 \div 3\) → 4 piles of 3
3) undo scaling — multiplied by 3 → divide by 3 to get back

A fraction looks at **part of a whole**; division looks at **how many times it fits**.

</div>
</details>

### Powers and roots give tools for: {.toc-heading-only}

<details class="post-accordion">
<summary>Powers and roots give tools for:</summary>
<div>

1) repeated multiplication — \(2^3 = 2 \times 2 \times 2\)
2) growth across dimensions — length \(\times 2\) → area \(\times 4\) (\(n=2\)), volume \(\times 8\) (\(n=3\))
3) root — inverse power: \(2^3 = 8 \Leftrightarrow \sqrt[3]{8} = 2\); \(a^{1/n}\) links \(\sqrt[n]{a}\) and \(a^n\)

</div>
</details>

### \(a^n\) and \(\sqrt[n]{a}\) — don’t mix up “reverse” {.toc-heading-only}

<details class="post-accordion">
<summary>\(a^n\) and \(\sqrt[n]{a}\) — don’t mix up “reverse”</summary>
<div>

1) \(a^{-n}\) — “invert” growth: not 8, but \(1/8\)
2) \(a^{1/n}\) — “unscale” the exponent: from 8 back to 2 without flipping sign

</div>
</details>

{{< accordion_group_close >}}
