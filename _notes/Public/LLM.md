---
title: LLM
notetype: feed
date: 2023-12-05
---
> [[Resources for Large Language Model]]

## Prerequisite
It would be easier if we have knowledge on NLP or Embedding, I would recommend [Databricks course](https://www.edx.org/course/large-language-models-application-through-production), the course start from the NLP knowledge till putting LLM to production.

## What is LLM
LLM stands for Large Language Model, which aim to predict the next words. There are long history of LLM from word2vec, LSTM, Transformer, [BERT, ELMo](https://jalammar.github.io/illustrated-bert/), till the PaLM, GPT (Generative Pre-training Transformer), an [interesting blog post explain how GPT3 works](https://jalammar.github.io/how-gpt3-works-visualizations-animations/) , and the [Gemini, multimodal model](https://deepmind.google/technologies/gemini/#introduction) from google

> [Any model lead to the same results, the only difference is dataset](https://nonint.com/2023/06/10/the-it-in-ai-models-is-the-dataset/)

The model itself trying to predict the probability distribution of the next word, after training for the very large dataset, and massive parameters, as a result we can use it to do most of the work. On the other hand, since it is a next word prediction, it can produce the hallucination result.


## What we should know about it

We can read a good comprehensive [blog post by Eugene - compile the patterns for building LLM-based system](https://eugeneyan.com/writing/llm-patterns/), and also great [blog post by Chip - addressing the challenges in LLM research](https://huyenchip.com/2023/08/16/llm-research-open-challenges.html)

## To start using it
- The easiest way to start using is to use ChatGPT
- Then we start to learn different type of [prompting technique](https://learn.deeplearning.ai/chatgpt-prompt-eng)
- Then we may would like to apply LLM with our own data, so I recommend start learning about [RAG](https://stackoverflow.blog/2023/10/18/retrieval-augmented-generation-keeping-llms-relevant-and-current)
- Then we may would like to create our own application, I would recommend start learning about [LangChain](https://www.langchain.com/) or [LlamaIndex](https://www.llamaindex.ai/)
- At this point, I may recommend to start reading the below information, to understand the overview, approaches, and technique of LLM.

The first few courses, we would learn about LangChain from Deep Learning.AI, these courses are easy to follow, and we can start building our PoC right away.
- [[LangChain for LLM App Development]]: [Link](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/)
- [[LangChain Chat with Your Data]]: [Link](https://www.coursera.org/projects/langchain-chat-with-your-data-project)
- [[Functions, tools, and Agents with LangChain]]: [Link](https://learn.deeplearning.ai/functions-tools-agents-langchain)
- Bonus: if we have no experience with building PoC website using python, we can check out the streamlit or Gradio
	- [Building Generative AI Applications with Gradio](https://www.deeplearning.ai/short-courses/building-generative-ai-applications-with-gradio/)

## Evaluations
As mention by Eugene, evaluation is crucial. Then we would need to learn how to evaluate our LLM or RAG.
- [[Quality and Safety for LLM Applications]]: [Link](https://learn.deeplearning.ai/quality-safety-llm-applications)
- [[Building and Evaluating Advanced RAG]]: [Link](https://learn.deeplearning.ai/building-evaluating-advanced-rag)
- [Ragas](https://github.com/explodinggradients/ragas)
- [WhyLogs](https://github.com/whylabs/whylogs)
- [Span Markers](https://github.com/tomaarsen/SpanMarkerNER)
- LLM Security
	- [Jailbreak Chat](https://www.jailbreakchat.com/)
	- [LLM Security](https://llmsecurity.net/)

## To maximizing LLM performance
I would recommend starting with [youtube video from OpenAI](https://www.youtube.com/watch?v=ahnGLM-RC1Y&ab_channel=OpenAI), it will give us an overview of RAG and fine-tuning with the result.

Starting with prompting
- I would recommend learning this course [[ChatGPT Prompt Engineering for Developers]]: [Link](https://learn.deeplearning.ai/chatgpt-prompt-eng)
- [Component of Prompts](https://promptengineering.org/what-are-large-language-model-llm-agents/)
- Then we can explore different type of prompting in [promptingguide.ai](https://www.promptingguide.ai/), which will summarise different prompting technique with the example such as zero-shot prompting, ReAct prompting
- There are also some challenges with the long text address in the Chip blog, and we can read more the detail [Lost in the Middle: How Language Models Use Long Contexts](https://arxiv.org/pdf/2307.03172.pdf), also with the [new findings from Anthropic on their model Claude 2.1 which said, only adding 'Here is the most relevant sentence in the context:' yield the better result](https://www.anthropic.com/index/claude-2-1-prompting?)

Then if we focusing on the RAG, we read the follow.
-  [Retrieval augmented generation: Keeping LLMs relevant and current](https://stackoverflow.blog/2023/10/18/retrieval-augmented-generation-keeping-llms-relevant-and-current)
- [10 Ways to Improve the Performance of Retrieval Augmented Generation Systems](https://towardsdatascience.com/10-ways-to-improve-the-performance-of-retrieval-augmented-generation-systems-5fa2cee7cd5c)
-  [A Guide on 12 Tuning Strategies for Production-Ready RAG Applications](https://towardsdatascience.com/a-guide-on-12-tuning-strategies-for-production-ready-rag-applications-7ca646833439)
- [Enterprise LLM Challenges and how to overcome them - Snorkel](https://snorkel.ai/enterprise-llm-challenges-and-how-to-overcome-them/)

__WE can skip this for later__ - To go deeper on improving RAG, we can go deeper to understand how vector store works, and different retrieval algorithms, or strategies.
- We may start by learning the course by [weaviate](https://www.deeplearning.ai/short-courses/vector-databases-embeddings-applications/)
- Then scan through [different retrievers implemented by LLamaIndex](https://docs.llamaindex.ai/en/latest/module_guides/querying/retriever/retrievers.html)
- Also start reading about [vector store](https://www.pinecone.io/learn/vector-database/)
- Finally, there are a different ANN embedding approach mention in Eugene blog also a good to read through (LSH, FAISS, HNSW, and ScaNN)


Then it's a good time to start exploring about different model, and how to fine-tune them
- To start with course from [LAMINI](https://www.lamini.ai/) on DeepLearning.ai: [Fine-tuning Large Language Models](https://learn.deeplearning.ai/finetuning-large-language-models)
- then read [a good summary from Eugene](https://eugeneyan.com/writing/llm-patterns/#how-to-apply-fine-tuning)
- Then you will need to prepare your dataset
- Select the pre-trained models
- Update model architecture
- Pick a fine-tuning approach
- Training them
- A great courses by [Databricks: Large Language Models: Foundation Models from the Ground Up](https://www.edx.org/course/large-language-models-foundation-models-from-the-ground-up)

## Put the model to production
Start by reading [Emerging Architectures for LLM Application](https://a16z.com/emerging-architectures-for-llm-applications/), this help us paint the big picture of the solutions we should apply in production, with additional resources to read from on different component.
- [Databricks: Large Language Models: Application through Production](https://www.edx.org/course/large-language-models-application-through-production)
- [GPTCache](https://github.com/zilliztech/GPTCache)
- [LangSmith](https://www.langchain.com/langsmith)
- [LangFuse](https://langfuse.com/)
- [Fiddler](https://www.fiddler.ai/)


## Other Resources
- [Rivert - Open Source AI agent environment](https://rivet.ironcladapp.com/)
- [Semantic Kernel from Microsoft](https://github.com/microsoft/semantic-kernel)
- [Meta LLaMa](https://ai.meta.com/llama/)
- [OpenThaiGPT](https://openthaigpt.aieat.or.th/)
- Vector databases
	- [Pinecone](https://www.pinecone.io/learn/vector-database)
	- [ChromaDB](https://www.trychroma.com/)
	- [Weaviate](https://weaviate.io/)
- [What Are Large Language Model (LLM) Agents and Autonomous Agents](https://promptengineering.org/what-are-large-language-model-llm-agents/)
- [Generative AI](https://www.coursera.org/learn/generative-ai-with-llms)✍️