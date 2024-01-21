---
title: Self-Ask - Measuring and Narrowing the Compositionality Gap in Language Models
notetype: feed
date: 2024-01-21
---
**Compositionality Gap** - describe the fraction of compositional questions that the model answers incorrectly out of all the compositional questions for which the model answers the sub-questions correctly.

**Compositional questions** require more computation and knowledge retrieval than 1-hop ones; however, by using naive prompting (which expects the answer to be output immediately after the question), we always give the model approximately the same number of steps to answer questions.
### Self-ask

Prompt LLM to ask itself whether need to ask a follow up question or not, and what is that follow up question. Leverage the findings of Chain-of-Thought.

![self-ask-prompting](/assets/img/self-ask-prompting.png)


### Improving Self-ask with a Search Engine

![self-ask-with-search](/assets/img/self-ask-with-search.png)


You may interested
- [Single-Step Query Decomposition - llmaindex](https://docs.llamaindex.ai/en/stable/optimizing/advanced_retrieval/query_transformations.html#single-step-query-decomposition)

**References**
- [Code](https://github.com/ofirpress/self-ask)
- [Paper](https://arxiv.org/abs/2210.03350)

#llm #prompting #rag