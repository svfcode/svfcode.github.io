---
title: "Math Analysis — Example of Analysis (Finding πr²)"
description: "Slicing the circle into rings, unrolling into strips — and area πR² via a triangle"
date: "2026-03-12"
slug: "math-circle-area"
tags:
  - Machine Learning
  - Mathematics
---

How do we find the area of a circle **analytically**?

## Slicing into Rectangles

**Idea:** slice the circle into thin concentric rings and «unroll» each ring into a rectangle.

A ring of radius r and width Δr has circumference 2πr. Unrolled, it becomes a rectangle:
- length: 2πr
- width: Δr
- area: 2πr · Δr

The total area is the sum of all such rings, from r = 0 to r = R. The smaller Δr, the better the approximation.

<svg viewBox="0 0 360 200" xmlns="http://www.w3.org/2000/svg" style="max-width: 360px; display: block; margin: 1em 0;">
  <defs>
    <linearGradient id="ring-en" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#3b82f6"/>
      <stop offset="100%" stop-color="#60a5fa"/>
    </linearGradient>
  </defs>
  <circle cx="100" cy="100" r="85" fill="none" stroke="#4b5563" stroke-width="1"/>
  <path d="M 100 15 A 85 85 0 0 1 185 100 A 85 85 0 0 1 100 185 A 85 85 0 0 1 15 100 A 85 85 0 0 1 100 15" fill="url(#ring-en)" fill-opacity="0.12" stroke="#60a5fa" stroke-width="1.5"/>
  <path d="M 100 30 A 70 70 0 0 1 170 100 A 70 70 0 0 1 100 170 A 70 70 0 0 1 30 100 A 70 70 0 0 1 100 30" fill="url(#ring-en)" fill-opacity="0.2" stroke="#60a5fa" stroke-width="1.5"/>
  <path d="M 100 45 A 55 55 0 0 1 155 100 A 55 55 0 0 1 100 155 A 55 55 0 0 1 45 100 A 55 55 0 0 1 100 45" fill="url(#ring-en)" fill-opacity="0.28" stroke="#60a5fa" stroke-width="1.5"/>
  <path d="M 100 60 A 40 40 0 0 1 140 100 A 40 40 0 0 1 100 140 A 40 40 0 0 1 60 100 A 40 40 0 0 1 100 60" fill="url(#ring-en)" fill-opacity="0.35" stroke="#60a5fa" stroke-width="1.5"/>
  <path d="M 100 75 A 25 25 0 0 1 125 100 A 25 25 0 0 1 100 125 A 25 25 0 0 1 75 100 A 25 25 0 0 1 100 75" fill="url(#ring-en)" fill-opacity="0.5" stroke="#60a5fa" stroke-width="1.5"/>
  <circle cx="100" cy="100" r="12" fill="#1e3a5f" stroke="#3b82f6" stroke-width="2"/>
  <line x1="100" y1="100" x2="100" y2="30" stroke="#f59e0b" stroke-width="2" stroke-dasharray="4 2"/>
  <text x="115" y="60" font-size="14" fill="#f59e0b">R</text>
  <text x="100" y="108" font-size="12" fill="#e5e7eb" text-anchor="middle">r=0</text>
  <text x="250" y="100" font-size="13" fill="#9ca3af">Rings r = 0 … R</text>
</svg>

If we arrange these cut strips (each of length 2πr) on a graph from left to right — from r = 0 to r = R — we get a triangle. Base R, height 2πR: the area of the triangle is ½ · R · 2πR = πR².

<svg viewBox="0 0 320 220" xmlns="http://www.w3.org/2000/svg" style="max-width: 320px; display: block; margin: 1em 0;">
  <defs>
    <linearGradient id="strip-en" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#3b82f6"/>
      <stop offset="100%" stop-color="#60a5fa"/>
    </linearGradient>
  </defs>
  <!-- Axes -->
  <line x1="40" y1="180" x2="260" y2="180" stroke="#6b7280" stroke-width="1.5"/>
  <line x1="40" y1="180" x2="40" y2="20" stroke="#6b7280" stroke-width="1.5"/>
  <!-- Strips: height 2πr at left edge (not above the line), width Δr -->
  <rect x="40" y="172" width="22" height="8" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="62" y="164" width="22" height="16" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="84" y="148" width="22" height="32" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="106" y="132" width="22" height="48" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="128" y="116" width="22" height="64" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="150" y="100" width="22" height="80" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="172" y="84" width="22" height="96" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="194" y="68" width="22" height="112" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="216" y="52" width="22" height="128" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <rect x="238" y="36" width="22" height="144" fill="url(#strip-en)" fill-opacity="0.6" stroke="#60a5fa" stroke-width="1"/>
  <!-- Line 2πr (from r=0 to r=R) -->
  <line x1="40" y1="180" x2="260" y2="20" stroke="#f59e0b" stroke-width="2"/>
  <text x="270" y="185" font-size="14" fill="#9ca3af">r</text>
  <text x="25" y="35" font-size="14" fill="#9ca3af" text-anchor="end">2πr</text>
  <text x="255" y="195" font-size="12" fill="#f59e0b">R</text>
  <text x="35" y="45" font-size="12" fill="#f59e0b" text-anchor="end">2πR</text>
  <text x="150" y="110" font-size="12" fill="#9ca3af" text-anchor="middle">½·R·2πR = πR²</text>
</svg>

**Result:** area of the circle S = πR². The same approach — slicing a shape into «small pieces», summing their areas, and taking the limit — underlies integral calculus and, as we will see, leads to derivatives.
