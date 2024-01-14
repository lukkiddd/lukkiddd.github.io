---
title: Chain-of-Table Evolving Tables in the Reasoning Chain forTable Understanding
notetype: feed
date: 2024-01-14
---
**Reference**: [https://arxiv.org/pdf/2401.04398.pdf](https://arxiv.org/pdf/2401.04398.pdf)

### Summary
- Working with table is hard
- Generic Reasoning, won't work, mostly due to difficulty in extractions
- [Program-aided Reasoning](https://www.promptingguide.ai/techniques/pal), won't work, due to format of the data
- Propose Chain-of-thought approach, by let LLM plan dynamically based on the given pool, till answer derived.
- As a result, CoTable outperforms all generic reasoning methods and program-aided reasoning methods.


![cot-table](/assets/img/cot-table.png)


![cot-table-2](/assets/img/cot-table-2.png)

#llm #prompting 