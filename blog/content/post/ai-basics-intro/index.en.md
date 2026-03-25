---
title: "AI basics – introduction"
description: "A short introduction to the fundamentals of artificial intelligence"
date: "2026-03-03"
slug: "ai-basics-intro"
tags:
  - Artificial Intelligence
  - Machine Learning
  - База
image: cover.jpg
---

This is the first article in the “Bare minimum” series — a concise look at how AI works. Each piece will cover one idea or concept; I’ll try to keep them short and in order.

We’ll start with common terms; elsewhere in the series — [prompt engineering](/en/p/ai-basics-prompt-engineering/), [RAG systems](/en/p/ai-basics-rag/), and [LLM agents](/en/p/ai-basics-agents/) for complex multi-step tasks.

**Video:** [Watch on YouTube](https://youtu.be/z9VBZn0XcVk)

## What a language model is

A language model is a system that, given what has already been said, predicts the next word. And so on in a loop:

> The → The cat → The cat sat → The cat sat on → The cat sat on the → …

Filling its own context with words it has just produced.

## Where we run into them

Any chatbot — whether it’s a support “assistant” that drives us crazy until we ask for a human, or “smart” chats like DeepSeek or ChatGPT — relies on a language model.

The only difference between a support bot and a “smart” one from DeepSeek is scale: the scale of the dataset and the server capacity needed to process it.

## Parameter scale

That leads to **parameter scale**:

- **1–7 billion** — models you can run on a local laptop
- **Trillions** — models that need server clusters

Models in the trillion-parameter range are called **foundation** models: they have absorbed not just statistics of word sequences, but knowledge encoded in language. Language is not only a medium for communication but also a record of collective experience.

## AI, ML, and neural networks — what’s the difference

**AI (artificial intelligence)** is the broadest term: systems and programs that behave “intelligently” — they solve tasks that usually need human intelligence (speech understanding, chess, image recognition, decision-making, and so on). AI can be built without machine learning (e.g. rules, expert systems).

**ML (machine learning)** is a subset of AI: a way to build AI so the system learns from data instead of hand-written rules. The goal is to find patterns in examples (data) and use them for predictions or decisions. ML includes more than neural networks: decision trees, linear models, clustering, and others.

**NNs (neural networks)** are a subset of ML: models inspired by neurons in the brain (layers, weights, activations). One of the most powerful ML tools, especially for images, text, and speech. **Deep learning** is ML with deep (many-layer) neural networks.

The relationship: **AI ⊃ ML ⊃ NN** — neural networks are a kind of machine learning, and machine learning is one way to implement artificial intelligence.

## Practice what you learned

Short games help you check how well you’ve absorbed the material.

Quiz:

<div style="margin: 1.5em 0;">
  <iframe
    src="/games/ai-basics-quiz.html"
    style="width: 100%; max-width: 672px; height: 540px; border: none; border-radius: 12px; display: block; margin: 0 auto; background: #0f1117;"
    title="Quiz: test your AI basics"
  ></iframe>
</div>

Sort the shelf — drag statements onto the right shelves (AI, ML, NN, parameter scale):

<div style="margin: 1.5em 0;">
  <iframe
    src="/games/ai-basics-shelves.html"
    style="width: 100%; max-width: 840px; height: 720px; border: none; border-radius: 12px; display: block; margin: 0 auto; background: #0f1117;"
    title="Sort the shelf"
  ></iframe>
</div>
