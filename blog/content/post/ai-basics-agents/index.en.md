---
title: "AI basics – LLM agents"
description: "LLM-based AI agents: beyond chat, planning, memory, tools, ReAct, multi-agent patterns"
date: "2026-03-25"
slug: "ai-basics-agents"
tags:
  - Artificial Intelligence
  - Machine Learning
  - База
image: cover.jpg
---

A «Bare minimum» article on **AI agents** built around language models: systems that **plan**, **retain context**, **call tools**, and iterate toward a goal—not just emit a single reply.

### Chat vs agent {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Chat vs agent</summary>
<div style="margin-top: 0.75em;">

<p><strong>A plain LLM chat</strong> is mostly “prompt → answer”: the model predicts tokens from the prompt and in-context history. It is <strong>not required</strong> to initiate real-world side effects on its own.</p>

<p>An <strong>agent</strong> wraps the model (and often other parts) so it pursues a <strong>goal</strong>, decomposes work, and when needed <strong>does things</strong>: calls APIs, runs code, searches the web or a document store until the task is done or a step budget is hit.</p>

<p>A useful metaphor: the <strong>LLM is the engine</strong> (reasoning and wording); the <strong>agent is the driver</strong> choosing route, when to stop, and which levers (tools) to pull. An engine without a driving scenario does not take you anywhere by itself.</p>

</div>
</details>

### What makes an agent {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">What makes an agent</summary>
<div style="margin-top: 0.75em;">

<p>People often sketch three pillars—an “anatomy of an agent” diagram.</p>

<p><strong>Planning.</strong> Breaking a large task into subgoals and steps. This overlaps with <strong>chain-of-thought</strong> style reasoning, explicit plans, and <strong>self-reflection</strong> (re-read a draft, check constraints, adjust).</p>

<p><strong>Memory.</strong></p>
<ul>
<li><strong>Short-term</strong> — the live context window: recent turns and intermediate notes in one session.</li>
<li><strong>Long-term</strong> — stored facts, docs, prior sessions; often implemented with <strong>vector stores and RAG</strong> so relevant snippets are retrieved into the prompt (see the <a class="link" href="/en/p/ai-basics-rag/">RAG article</a>).</li>
</ul>

<p><strong>Tools.</strong> Formalized actions the model can request: HTTP APIs, code execution (e.g. Python), web search, filesystem hooks, calendar or DB queries. Without tools the “agent” remains text-only with no outward levers.</p>

</div>
</details>

### How to think about agents {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">How to think about agents</summary>
<div style="margin-top: 0.75em;">

<p>The mindset shift is closer to delegating to a junior teammate than to typing a single search query.</p>

<ul>
<li><strong>Delegate, don’t only prompt.</strong> State the goal, success criteria, and allowed sources/tools the way you would brief a colleague.</li>
<li><strong>Set boundaries and a role.</strong> A clear persona (“research assistant”, “no payment actions”) and guardrails reduce scope creep and unsafe surprises.</li>
<li><strong>Expect iteration.</strong> Agents misstep and dead-end; a normal pattern is try → observe → replan. That drives step limits, logging, and human oversight.</li>
<li><strong>Provide resources.</strong> If facts live in docs, wire search or RAG; if numbers matter, supply a runtime. Without the right levers the model falls back to guessing.</li>
</ul>

</div>
</details>

### ReAct: reason and act {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">ReAct: reason and act</summary>
<div style="margin-top: 0.75em;">

<p><strong>ReAct</strong> (*Reasoning and Acting*) is a common loop drawn as thought → action → observation.</p>

<ul>
<li><strong>Thought:</strong> what do I know, what is missing, what is the next sensible move?</li>
<li><strong>Action:</strong> invoke a specific tool with arguments (search, API, code, …).</li>
<li><strong>Observation:</strong> the tool’s raw result is fed back into context.</li>
<li>Then another <strong>Thought</strong>—adjust the plan or finish with a final user-facing answer.</li>
</ul>

<p>This alternates <strong>natural-language reasoning</strong> with <strong>grounded steps</strong> instead of hallucinating when fresh data or computation is required.</p>

</div>
</details>

### Multi-agent systems {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Multi-agent systems</summary>
<div style="margin-top: 0.75em;">

<p>Hard problems are sometimes split across <strong>several agents</strong> with different roles—a “manager and workers” picture.</p>

<ul>
<li>A <strong>coordinator</strong> assigns subtasks, merges outputs, keeps the end result coherent.</li>
<li><strong>Specialists</strong> might focus on coding, testing, literature search, or report formatting.</li>
</ul>

<p>Upsides: modularity and parallelism. Downsides: harder debugging, model-call cost, and risk of diverging context between agents. For prototypes, spell out the handoff protocol—who passes what, in what schema.</p>

</div>
</details>

### Who uses them {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Who uses them</summary>
<div style="margin-top: 0.75em;">

<p>Agentic setups appear when a single chat reply is not enough—you need an <strong>action chain</strong> tied to tools or corpora.</p>

<ul>
<li><strong>Researchers.</strong> Scanning many PDFs, summaries, checking phrasing against sources—often with RAG and search.</li>
<li><strong>Students and academics.</strong> Source discovery and draft surveys with explicit citations—never replacing fact-checking.</li>
<li><strong>Developers.</strong> Multi-step debugging, refactors, automating ticket/CI/docs flows—with code review and caution.</li>
<li><strong>Enterprises.</strong> Internal assistants over CRM, wikis, APIs—with strict access policy, action audit trails, and human gates on critical operations.</li>
</ul>

</div>
</details>
