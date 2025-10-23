---
title: "Introduction to </br> Digital Humanities"
subtitle: "(Large Language Models -- LLMs)"
author: Maciej Eder
date: 2025/10/17
format: 
  revealjs:
    katex: true
    theme: files/pp.scss
    logo: files/DigiTS-RGB-short-SMALL.svg
    css: files/big_logo_DigiTS.css
    self_contained: false
---



## Overview

- What are LLMs?
- Why they matter for Digital Humanities (DH)
- Key concepts & terminology
- Architecture & training pipeline
- Common models & use‑cases
- Ethics, bias & responsible use
- Quick hands‑on demo
- Resources & next steps

---

## What is a Language Model?

- **Definition** – A statistical model that predicts the next word (or
token) in a sequence.
- **Goal** – Capture the structure, style, and content of natural
language.
- **From n‑gram to neural**
  - *n‑gram*: count‑based, limited context
  - *Neural*: learn continuous representations, long‑range dependencies

> *Speaker note:* Emphasise that the “language model” is the core of many
NLP systems: translation, summarisation, chat, etc.

---

## Why LLMs Matter for DH

| DH Task | How LLMs Help |
|---------|---------------|
| **Textual Analysis** | Generate summaries, sentiment, topic models |
| **Digital Archiving** | Automate metadata extraction, OCR post‑processing |
| **Translation & Localization** | Bridge language gaps in primary sources |
| **Creative Projects** | Co‑authoring, generating prompts for digital art |
| **Interoperability** | Convert legacy formats, standardise vocabularies |

*Illustration idea:* Show a workflow diagram: *Source Text → LLM →
Enriched Metadata*

---

## Key Concepts & Terminology

| Term | Simple Explanation |
|------|--------------------|
| **Token** | A unit of text (word, sub‑word, punctuation). |
| **Embedding** | Dense vector representation of a token. |
| **Attention** | Mechanism that weighs the influence of tokens on each other. |
| **Self‑Attention** | Tokens attend to all tokens in the same sequence. |
| **Parameter** | Numerical weight learned during training (e.g., 175B for GPT‑3). |
| **Prompt** | Input text that guides the model’s output. |
| **Fine‑tuning** | Further training on a specific domain or task. |
| **Zero‑shot / Few‑shot** | Using the model without, or with minimal, task‑specific examples. |

---

## The Training Pipeline

1. **Data Collection**
   - Web scrapes, books, Wikipedia, news, code, etc.
2. **Tokenisation**
   - Byte‑pair encoding (BPE) or WordPiece → sub‑word units.
3. **Pre‑training Objective**
   - *Masked Language Modelling* (BERT style)
   - *Causal Language Modelling* (GPT style)
4. **Optimization**
   - Gradient descent, Adam optimiser, large‑batch training.
5. **Evaluation**
   - Perplexity on held‑out data, benchmark tests (GLUE, SuperGLUE).


---

## Transformer Architecture

- **Encoder‑decoder vs. Decoder‑only**
  - GPT, LLaMA = decoder‑only
  - BERT = encoder‑only
- **Self‑Attention Formula**

$$ \text{Attention}(Q,K,V) = \text{softmax}\left(\frac{QK^{\top}}{\sqrt{d_k}}\right)V $$

- **Layer Composition**
  1. Multi‑head self‑attention
  2. Add & Norm (residual connection)
  3. Position‑wise Feed‑Forward (dense layers)
  4. Add & Norm

- **Positional Encoding**
  - Adds sequence order information (sin/cos or learned).

> *Illustration idea:* Show a block diagram of a single transformer layer.


---

## Popular LLMs & Their Origins

| Model | Release | Parameter Count | Training Data | Key Features |
|-------|---------|-----------------|---------------|--------------|
| **GPT‑4** | 2023 | 1 trillion+ (approx.) | Web + proprietary | Multimodal, low‑prompt‑overhead |
| **Claude 2** | 2023 | ~52B | Anthropic curated | Safety‑first design |
| **LLaMA 2** | 2023 | 7B, 13B, 70B | Meta‑public corpora | Open‑source, fine‑tune friendly |
| **Mistral 7B** | 2023 | 7B | Public data | Efficiency, low‑latency |
| **BERT** | 2018 | 110M | Wikipedia + BookCorpus | Contextual embeddings (bidirectional) |

> *Speaker note:* Emphasise open‑source models (LLaMA, Mistral) give
students a chance to run locally.

---

## How LLMs Work in Practice

```
User prompt  -->  Tokenise  -->  Model Forward Pass  -->  Generate Tokens
-->  Detokenise  -->  Output
```

- **Prompt Engineering** – Style, length, and context shape the answer.
- **Temperature** – Controls randomness (0.1 = deterministic, 1.0 =
creative).
- **Top‑k / Top‑p (nucleus)** – Sampling strategies.

> *Interactive demo idea:* Show live generation of a short poem about “The
Library of Alexandria”.

---

## Use Cases in Digital Humanities

| Task | Example | Model/Tool | Comments |
|------|---------|------------|----------|
| **Automated Cataloguing** | Extract author, title, date from scanned manuscripts | GPT‑4 via prompt | Speed up metadata entry |
| **Textual Commentary** | Generate footnotes for archaic phrases | LLaMA 2 fine‑tuned on critical editions | Requires domain fine‑tuning |
| **Historical Text Summaries** | Summarise newspaper articles | Claude 2, prompt with “Summarise in 3 sentences” | Helps readers skim |
| **Digital Art Prompting** | Create image prompts for DALL‑E from literary descriptions | GPT‑4 or Claude | Bridges literature & visual arts |
| **Code Generation** | Convert OCR errors to clean XML | GPT‑4 code‑generation | Reduce manual post‑processing |
| **Question‑Answering** | Answer queries about Shakespeare’s plays | BERT fine‑tuned on TEI XML | Interactive knowledge base |

---

## Ethical Considerations

| Issue | What it means for DH | Mitigation |
|-------|----------------------|------------|
| **Bias & Stereotype Amplification** | Misrepresentation of minority groups in generated text | Use diverse training data; post‑filtering |
| **Plagiarism & Attribution** | AI can produce text too close to sources | Check originality; attribute AI usage |
| **Data Privacy** | Models trained on personal data (e.g., letters) | Use de‑identified corpora; comply with GDPR |
| **Algorithmic Transparency** | Black‑box decisions in summarisation | Explainable prompts; human oversight |
| **Digital Divide** | Access to large GPU resources | Leverage open‑source, distilled models |

> *Speaker note:* Encourage students to think critically about “ownership”
of AI‑generated content, especially when publishing in DH projects.


---

## Hands‑On Mini‑Demo

1. **Tool** – ChatGPT (free tier) or open‑source LLaMA 2 on Colab.
2. **Prompt** – “Generate a concise metadata record for the following
manuscript excerpt: …”
3. **Show** – Compare model output vs. human‑written record.
4. **Discussion** – Accuracy, missing fields, style.



---

## Limitations & Future Directions

- **Scalability** – Training requires petaflop‑days; inference latency can
be high.
- **Hallucinations** – AI may fabricate facts; fact‑checking is essential.
- **Interpretability** – Understanding why a model makes a decision is
still hard.
- **Multimodality** – Integration of text, images, audio opens new DH
possibilities.
- **Continual Learning** – Models that adapt to new corpora without
forgetting.
- **Open‑source momentum** – More accessible LLMs (e.g., LLaMA 2, Mistral)
democratise research.

---

## Summary

- LLMs are powerful tools that can transform DH workflows.
- Core ideas: tokenisation, embeddings, self‑attention, transformer
layers.
- Training on massive corpora yields broad knowledge but introduces bias.
- Practical use requires careful prompt design, evaluation, and ethical
vigilance.
- The field is rapidly evolving; staying current with literature & tools
is key.

---

## Further Reading & Resources

| Resource | Link |
|----------|------|
| *Attention Is All You Need* (Vaswani et al., 2017) | https://arxiv.org/abs/1706.03762 |
| *Language Models are Few-Shot Learners* (Brown et al., 2020) | https://arxiv.org/abs/2005.14165 |
| *LLaMA 2* (Meta) | https://github.com/facebookresearch/llama/tree/main |
| *Mistral* (Mistral AI) | https://github.com/mistralai/mistral |
| *OpenAI API Documentation* | https://platform.openai.com/docs |
| *Hugging Face Spaces* | https://huggingface.co/spaces |
| *Digital Humanities Association* | https://dhan.org |

---

## Thank You!

Questions?

🔗 Connect on Twitter: @YourUniDH

📧 Email: dhdept@university.edu


# (generated by an AI model!!!)


