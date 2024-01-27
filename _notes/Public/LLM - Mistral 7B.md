---
title: LLM - Mistral 7B
notetype: feed
date: 2024-01-27
---

**Paper**: [Mistral 7B](https://arxiv.org/pdf/2310.06825.pdf)

![mistral-architecture](/assets/img/mistral-1.png)

Our model, Mistral 7B, demonstrates that a carefully designed language model can **deliver high performance while maintaining an efficient inference**.

Mistral 7B outperforms the best open 13B model (Llama 2) across all evaluated benchmarks, and the best released 34B model (Llama 1) in reasoning, mathematics, and code generation.

Our model leverages **[grouped-query attention (GQA)](https://arxiv.org/abs/2305.13245)** for faster inference, coupled with **[sliding window attention (SWA)](https://arxiv.org/abs/1904.10509)** to effectively handle sequences of arbitrary length with a reduced inference cost.


#llm #llm-model #generative-ai 