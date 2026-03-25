---
title: "AI basics – overview"
description: "Overview of large language models: capabilities, how they work, prompting, RAG, key concepts, and limits"
date: "2026-03-25"
slug: "ai-basics-overview"
tags:
  - Artificial Intelligence
  - Machine Learning
  - База
image: cover.jpg
---

This overview for the «Bare minimum» series is an outline:

- large language models;
- architecture;
- usage patterns;
- trends.

**Video (~9 min):** [Watch on YouTube](https://youtu.be/xHLP2f2WVpU)

## Large language models (LLMs)

### What is it? — A tool first; then capabilities and use cases {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">What is it? — A tool first; then capabilities and use cases</summary>
<div style="margin-top: 0.75em;">

<p><strong>Text generation</strong></p>
<ul>
<li>Articles, stories, marketing materials</li>
<li>Automated reports and documentation</li>
<li>Creative writing and content across genres</li>
</ul>

<p><strong>Question answering</strong></p>
<ul>
<li>Intelligent customer-support chatbots</li>
<li>Q&amp;A systems for information retrieval</li>
<li>Virtual assistants for everyday tasks</li>
</ul>

<p><strong>Language analysis</strong></p>
<ul>
<li>Text classification by category and sentiment</li>
<li>Summarization of long documents</li>
<li>Translation between languages with context preserved</li>
</ul>

<p><strong>Programming and code</strong></p>
<ul>
<li>Code generation from natural-language descriptions</li>
<li>Debugging and fixing errors</li>
<li>Comments and explanations for complex code</li>
</ul>

</div>
</details>

*Powerful — but it helps to know how they work and where they fail.*

### What is it technically? - A huge statistical machine {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">What is it technically? - A huge statistical machine</summary>
<div style="margin-top: 0.75em;">

<p><strong>Definition and how it works</strong></p>
<p>Neural models trained to predict the next token from context.</p>
<p>They use statistical regularities in language to generate text.</p>

<p>An LLM uses the full context to pick the most likely next word.</p>

<p><img src="llm-context.png" alt="Diagram: model uses full context for the next token" loading="lazy" /></p>

<p><strong>LLM token prediction flow</strong></p>
<p><strong>Input context (Russian tongue-twister):</strong> «Карл у Клары украл…»</p>
<p><strong>Context analysis:</strong></p>
<ul>
<li>Карл (subject)</li>
<li>у Клары (whose / from whom)</li>
<li>украл (action)</li>
</ul>
<p><strong>Prediction:</strong> the model analyzes all prior tokens and their relations, recognizes the familiar tongue-twister pattern</p>
<p>→ «кораллы» (“corals”)</p>
<p><strong>Probability:</strong> 85%</p>

<p><img src="llm-token-flow.png" alt="Token prediction flow" loading="lazy" /></p>

<p><strong>Transformers and architecture</strong></p>
<p>Self-attention for sequences (sounds simple — in practice, it isn’t).</p>

<p><img src="attention.png" alt="Self-attention mechanism" loading="lazy" /></p>

<p>Parallel processing of data instead of a purely recurrent pipeline.</p>

<p><img src="parallel-vs-rnn.png" alt="Parallel processing vs recurrent style" loading="lazy" /></p>

<p>Multi-layer structure with billions of parameters (weight heatmap).</p>

<p><img src="layer-weights-heatmap.png" alt="Layers and parameter scale" loading="lazy" /></p>

<p><strong>Training on text</strong></p>
<ul>
<li>Self-supervised learning on billions of text examples</li>
<li>Pre-training on broad data, then specialization</li>
<li>Scaling data and compute</li>
</ul>

</div>
</details>

### How to use them? - Overview of techniques for working with LLMs {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">How to use them? - Overview of techniques for working with LLMs</summary>
<div style="margin-top: 0.75em;">

<p><strong>Prompt engineering</strong></p>
<ul>
<li>The craft of phrasing requests for better results</li>
<li>Structuring instructions with roles, examples, and context</li>
<li>Iteratively refining prompts for accurate answers</li>
</ul>

<p>Deep dive by technique (zero-shot, few-shot, CoT, roles, step-back, …): <a class="link" href="/en/p/ai-basics-prompt-engineering/">AI basics – prompt engineering</a>.</p>

<p><strong>Fine-tuning</strong></p>
<ul>
<li>Adapting the model to specific tasks and domains</li>
<li>Using small labeled datasets</li>
<li>RLHF (reinforcement learning from human feedback)</li>
</ul>

<p><strong>RAG (Retrieval-Augmented Generation)</strong></p>
<ul>
<li>Extending the model with retrieval from a knowledge base</li>
<li>Combining external sources with generation</li>
<li>Reducing hallucinations by grounding in verified facts</li>
</ul>

<p><strong>Chain-of-thought</strong></p>
<ul>
<li>Step-by-step reasoning for hard problems</li>
<li>Intermediate computation and logical steps</li>
<li>Better math and logic when the model is guided through steps</li>
</ul>

</div>
</details>

### Popular models {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Popular models</summary>
<div style="margin-top: 0.75em;">

<p><strong>GPT (OpenAI)</strong></p>
<ul>
<li>A family from GPT-3 through GPT-5.4-class releases, industry leaders</li>
<li>Commercial APIs with a wide range of capabilities</li>
<li>ChatGPT as the mass-market product built on these models</li>
</ul>

<p><strong>Claude (Anthropic)</strong></p>
<ul>
<li>Emphasis on safety and long context</li>
<li>Constitutional-style alignment with human values</li>
<li>Very large context (up to ~1M tokens in flagship offerings)</li>
</ul>

<p><strong>LLaMA</strong></p>
<ul>
<li>Open(ish) models from Meta for the research community</li>
<li>Base for many derivatives (Alpaca, Vicuna, …)</li>
<li>Compact variants for local deployment</li>
</ul>

<p><strong>Regional / domestic stacks</strong></p>
<ul>
<li>YandexGPT with strong Russian support</li>
<li>Sber’s GigaChat for business use</li>
<li>Vikhr and other specialized models for niche tasks</li>
</ul>

</div>
</details>

### Key concepts {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Key concepts</summary>
<div style="margin-top: 0.75em;">

<p><strong>Token</strong></p>
<ul>
<li>Smallest unit of text the model processes</li>
<li>Can be a word, subword, or symbol</li>
<li>Examples: “hello” ≈ 1 token; “unpredictability” often 2–3 tokens</li>
<li>Tokenization splits text into a sequence of tokens</li>
</ul>

<p><strong>Temperature</strong></p>
<ul>
<li>Low (0.1–0.3): more predictable, precise text</li>
<li>Mid (0.7–0.9): balance of creativity and coherence</li>
<li>High (1.5–2.0): more creative, less coherent
<p style="margin: 0.5rem 0 0 0;"><img src="overview-temperature-high.png" alt="Infographic: LLM generation temperature from predictable to highly diverse output" style="max-width: 100%; height: auto; border-radius: 8px;" loading="lazy" /></p></li>
</ul>

<p><strong>Model types by role</strong></p>
<ul>
<li>Foundation: pre-trained on large text corpora</li>
<li>Instruction-tuned: trained to follow user instructions</li>
<li>Chat: tuned for dialogue and multi-turn conversation</li>
<li>Specialized: tuned for code, medicine, law, etc.
<p style="margin: 0.5rem 0 0 0;"><img src="overview-model-specialized.png" alt="Diagram: from foundation models to specialized models (code, medicine, law)" style="max-width: 100%; height: auto; border-radius: 8px;" loading="lazy" /></p></li>
</ul>

<p><strong>Context window</strong></p>
<ul>
<li>Cap on how much text the model processes in one pass</li>
<li>Various ways to extend context (roughly 8K–100K tokens in many systems)</li>
<li>Information loss on very long documents</li>
</ul>

</div>
</details>

### Problems and limitations {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Problems and limitations</summary>
<div style="margin-top: 0.75em;">

<p><strong>Hallucinations</strong></p>
<ul>
<li>The model may invent facts while sounding confident</li>
<li>Plausible but false content</li>
<li>Hard to verify everything it generates</li>
</ul>

<p><strong>Compute</strong></p>
<ul>
<li>Powerful GPUs/TPUs for training and inference</li>
<li>High energy use for training large models</li>
<li>Cost of building and running infrastructure</li>
</ul>

<p><strong>Ethics</strong></p>
<ul>
<li>Bias and stereotypes in training data</li>
<li>Safety risks and malicious use</li>
<li>Copyright and intellectual property issues</li>
</ul>

</div>
</details>

### Future and trends {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Future and trends</summary>
<div style="margin-top: 0.75em;">

<p><strong>Multimodality</strong></p>
<ul>
<li>Text, images, audio, and video</li>
<li>Understanding and generating content in multiple formats</li>
<li>Integrating modalities for richer understanding</li>
</ul>

<p><strong>LLM agents</strong></p>
<ul>
<li>Autonomous systems for complex tasks</li>
<li>Planning actions and making decisions</li>
<li>Using external tools and APIs</li>
</ul>

<p><strong>Model optimization</strong></p>
<ul>
<li>Quantization and distillation for speed</li>
<li>More efficient architectures</li>
<li>Trade-off between size and capability</li>
</ul>

<p><strong>On-device / local</strong></p>
<ul>
<li>Models on personal devices</li>
<li>Privacy without sending data to the cloud</li>
<li>Specialized hardware for LLM inference</li>
</ul>

</div>
</details>
