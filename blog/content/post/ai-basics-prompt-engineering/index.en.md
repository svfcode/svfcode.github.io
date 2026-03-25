---
title: "AI basics – prompt engineering"
description: "Prompt engineering: goals, zero-shot and few-shot, chain-of-thought, roles, step-back, and where good prompts come from"
date: "2026-03-25"
slug: "ai-basics-prompt-engineering"
tags:
  - Artificial Intelligence
  - Machine Learning
  - База
image: cover.jpg
---

A «Bare minimum» article on how to phrase requests to large language models.

### Goal and essence {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Goal and essence</summary>
<div style="margin-top: 0.75em;">

<p><strong>A prompt is a short technical spec for the model.</strong> You state what to do, how to format the answer, and what to rely on. The clearer the spec, the less the model has to guess.</p>

<ul>
<li><strong>Quality.</strong> Clear instructions reduce vagueness and improve usefulness of text, code, or structured output.</li>
<li><strong>Predictability.</strong> Fixed formats (lists, JSON, paragraph templates) and explicit constraints make outputs repeatable across runs.</li>
<li><strong>Building blocks.</strong> Treat the prompt as a mini-spec: role, context, task, output format, examples (if needed), success criteria.</li>
</ul>

</div>
</details>

### Zero-shot prompting {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Zero-shot prompting</summary>
<div style="margin-top: 0.75em;">

<p><strong>The task is given with no input–output examples.</strong> The model leans on pretraining plus your instruction in the current request.</p>

<ul>
<li>Works well for simple, unambiguous tasks when the desired format is obvious or one line away.</li>
<li><strong>Example:</strong> sentiment classification (“label as positive / neutral / negative”) with no labeled examples in the prompt.</li>
</ul>

<p>If zero-shot drifts, few-shot examples or explicit step-by-step reasoning (CoT) usually help.</p>

</div>
</details>

### Few-shot prompting {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Few-shot prompting</summary>
<div style="margin-top: 0.75em;">

<p><strong>In-context learning:</strong> you add one or more “input → gold output” pairs so the model picks up style, fields, and constraints.</p>

<ul>
<li>Especially useful when you need a <strong>strict or unusual format</strong> — tables, JSON with fixed keys, report templates.</li>
<li>Examples act as a contract for the answer: fewer arbitrary interpretations.</li>
</ul>

<p>Do not overload context: keep examples relevant, representative, and within the context window.</p>

</div>
</details>

### Chain-of-Thought (CoT) {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Chain-of-Thought (CoT)</summary>
<div style="margin-top: 0.75em;">

<p><strong>Reasoning chain:</strong> the model emits intermediate steps, then the final answer. That tends to stabilize logic, arithmetic, and multi-step tasks.</p>

<ul>
<li><strong>Few-shot CoT:</strong> examples show not only the answer but the reasoning path — the model mimics that pattern.</li>
<li><strong>Zero-shot CoT:</strong> phrases like “think step by step” / “explain your reasoning first, then answer” often suffice.</li>
<li><strong>Uncertainty-routed CoT:</strong> explore multiple reasoning lines or alternatives when the task is ambiguous, then compare or pick a justified conclusion.</li>
</ul>

<p>CoT lengthens responses and latency; for trivial tasks a short instruction without reasoning may be enough.</p>

</div>
</details>

### Where prompts come from {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Where prompts come from</summary>
<div style="margin-top: 0.75em;">

<ul>
<li><strong>You define the goal.</strong> The primary source is your statement of task, audience, and quality bar.</li>
<li><strong>LLM-generated drafts.</strong> Ask the model for a structured prompt (role, steps, format), then edit manually.</li>
<li><strong>Reverse engineering.</strong> From a desired output (or a great response), reconstruct and refine what in the prompt made it work.</li>
</ul>

<p>In practice people combine model drafts, hard constraints, and iteration on real outputs.</p>

</div>
</details>

### Role-based prompting {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Role-based prompting</summary>
<div style="margin-top: 0.75em;">

<p><strong>Explicit role and perspective:</strong> “you are an editor”, “economist for non-experts”, “comedian in the style of …”. That steers tone, depth, and granularity.</p>

<ul>
<li>Especially helpful for <strong>open-ended</strong> work: explanations, creative writing, advice when there is no single “right” format.</li>
<li><strong>Role examples:</strong> public speaker, domain expert, comedian, teacher — role changes vocabulary, structure, and how bold the model can be.</li>
</ul>

<p>Role complements but does not replace a clear task and constraints; “you are an expert” without context helps less than expert + goal + format.</p>

</div>
</details>

### Step-back prompting {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Step-back prompting</summary>
<div style="margin-top: 0.75em;">

<p><strong>A CoT-style variation:</strong> first step back to general principles, definitions, or a standard method, <strong>then</strong> apply them to the specific case.</p>

<ul>
<li>Start with guiding questions: which laws, patterns, or concepts matter for this task?</li>
<li>Then map onto your instance: data, constraints, desired output.</li>
</ul>

<p>Useful when failures come from jumping to an answer without anchoring on the right background knowledge.</p>

</div>
</details>
