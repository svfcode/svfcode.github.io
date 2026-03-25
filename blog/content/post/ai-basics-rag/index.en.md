---
title: "AI basics – RAG systems"
description: "RAG (Retrieval-Augmented Generation): why add retrieval to LLMs, pipeline stages, chunking, naive vs advanced RAG"
date: "2026-03-25"
slug: "ai-basics-rag"
tags:
  - Artificial Intelligence
  - Machine Learning
  - База
image: cover.jpg
---

A «Bare minimum» article on **retrieval-augmented generation**: how to ground a language model in external documents and up-to-date knowledge.

### What RAG is {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">What RAG is</summary>
<div style="margin-top: 0.75em;">

<p><strong>Retrieval-Augmented Generation</strong> means the model answers not only from weights learned at training time but also from <strong>fragments retrieved</strong> from an external store.</p>

<p><strong>The LLM-only issue:</strong> knowledge is largely <strong>static</strong> after training — the model does not automatically learn what happened next, <strong>does not self-update</strong>, and reflects the world <strong>as of the training cutoff</strong>. That is weak for fresh facts, internal playbooks, or a personal paper library.</p>

<ul>
<li>RAG is the <strong>technology of wiring external sources</strong> into the generation step.</li>
<li>It <strong>mitigates stale knowledge</strong> by pulling relevant chunks from a current corpus.</li>
<li>The model is <strong>augmented with document context</strong>, not just pre-trained parameters.</li>
</ul>

<p>RAG does not eliminate hallucinations, but it grounds answers in retrievable snippets that humans (or rules) can verify more easily.</p>

</div>
</details>

### Stages of a RAG pipeline {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Stages of a RAG pipeline</summary>
<div style="margin-top: 0.75em;">

<p>Think of two phases: offline indexing and the online user query.</p>

<ul>
<li><strong>Ingestion and chunking.</strong> Documents enter the system and are split into pieces sized for the index and the context window.</li>
<li><strong>Vector index build.</strong> Each chunk gets an embedding; similarity search finds chunks “close” to the query in meaning.</li>
<li><strong>Retrieval.</strong> For a user question, the system selects the most relevant chunks from the index.</li>
<li><strong>Generation.</strong> Those chunks are placed in the prompt (with instructions and the question), and the LLM produces an answer conditioned on that context.</li>
</ul>

<p>Concrete choices (embeddings, vector DB, how many chunks to inject) strongly affect quality, but the pattern <em>retrieve → inject → generate</em> stays the same.</p>

</div>
</details>

### Chunking {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Chunking</summary>
<div style="margin-top: 0.75em;">

<p><strong>Chunking</strong> splits documents into smaller segments. Those segments are the <strong>basic units of indexing and search</strong> — what you embed and what you pass to the model.</p>

<ul>
<li>The LLM sees <strong>fragments, not whole documents</strong> at once — full docs rarely fit the window, and search needs granular matches.</li>
<li><strong>Chunk quality drives whether facts are reachable:</strong> split a coherent block in the wrong place and retrieval may miss it; make chunks huge and noise dilutes the signal.</li>
</ul>

<p>In practice people tune chunk size, overlap between neighbors, and sometimes structure-aware splits (headings, paragraphs) instead of fixed character counts only.</p>

</div>
</details>

### Types of RAG systems {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Types of RAG systems</summary>
<div style="margin-top: 0.75em;">

<p>People loosely contrast “naive” and “advanced” pipelines — the boundary is fuzzy, but the labels help navigate complexity.</p>

<ul>
<li><strong>Naive RAG:</strong> query → nearest-chunk search → chunks go straight into the model <strong>without extra processing</strong>. Easy to ship; quality hinges on corpus, chunks, and embeddings.</li>
<li><strong>Advanced RAG:</strong> adds steps around retrieval and generation: <strong>query rewriting or expansion</strong>, <strong>reranking</strong> with a cross-encoder or another model, <strong>deduplication</strong> of overlapping hits, sometimes metadata filters. Goal: sharper, cleaner context for the LLM.</li>
</ul>

<p>For coursework or a research prototype, naive RAG is a common start; you add sophistication where you see failure modes like wrong paragraph, duplicates, or vocabulary mismatch between query and docs.</p>

</div>
</details>

### Who uses it {.toc-heading-only}

<details class="post-accordion">
<summary style="cursor: pointer; font-weight: 600;">Who uses it</summary>
<div style="margin-top: 0.75em;">

<p>Teams adopt RAG when answers must be grounded in a <strong>chosen document set</strong> — internal, customer-facing, or personal — rather than only in the model’s training-time knowledge.</p>

<ul>
<li><strong>Enterprises.</strong> Knowledge bases, policies, support playbooks: employees or customers ask questions, the system retrieves relevant snippets, and the model answers with reference to up-to-date org text.</li>
<li><strong>Developers and product teams.</strong> Assistants over docs, wikis, tickets: less guessing about APIs from the open web — a controlled corpus sets the boundary.</li>
<li><strong>Education and research.</strong> Working with a curated stack of papers, notes, and PDFs: ask questions over course materials or a literature review without replacing source checks.</li>
<li><strong>Regulated or expert domains.</strong> Legal, clinical, finance, and similar settings where tying answers to company or regulatory text matters — always with human verification and data-access policies.</li>
</ul>

</div>
</details>
