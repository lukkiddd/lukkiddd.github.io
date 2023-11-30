---
title: Functions, tools, and Agents with LangChain
notetype: feed
date: 2023-11-30
---

## Summary

### OpenAI Function Calling

Recent update from OpenAI to support Function calling

```python
import json

# Example dummy function hard coded to return the same weather
# In production, this could be your backend API or an external API
def get_current_weather(location, unit="fahrenheit"):
    """Get the current weather in a given location"""
    weather_info = {
        "location": location,
        "temperature": "72",
        "unit": unit,
        "forecast": ["sunny", "windy"],
    }
    return json.dumps(weather_info)

# define a function
functions = [
    {
        "name": "get_current_weather",
        "description": "Get the current weather in a given location",
        "parameters": {
            "type": "object",
            "properties": {
                "location": {
                    "type": "string",
                    "description": "The city and state, e.g. San Francisco, CA",
                },
                "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]},
            },
            "required": ["location"],
        },
    }
]

messages = [
    {
        "role": "user",
        "content": "What's the weather like in Boston?"
    }
]

import openai
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo-0613",
    messages=messages,
    functions=functions
)
```


### LangChain Expression Language (LCEL)

We can chain the LLM using pipe symbol (`|`)

```python
prompt = ChatPromptTemplate.from_template(
    "tell me a short joke about {topic}"
)
model = ChatOpenAI()
output_parser = StrOutputParser()

chain = prompt | model | output_parser

chain.invoke({"topic": "bears"})
```

If you would like to map the variables with other functions, such as retriever for RAG, you can use `RunnableMap`

```python
from langchain.schema.runnable import RunnableMap
chain = RunnableMap({
    "context": lambda x: retriever.get_relevant_documents(x["question"]),
    "question": lambda x: x["question"]
}) | prompt | model | output_parser
```


You can also binding with OpenAI functions

```python
model = ChatOpenAI(temperature=0).bind(functions=functions)
```

You can also attached fallbacks, just in case the response is not working

```python
model = ChatOpenAI(temperature=0)
chain = model | StrOutputParser() | json.loads
final_chain = simple_chain.with_fallbacks([chain])
```


You can also use different type of runnable, such as stream or asynchronous
- invoke \[ainvoke\]
- stream \[astream\]
- batch \[abatch\]

```
# Invoke
chain.invoke({"topic": "bears"})

# Batch
chain.batch([{"topic": "bears"}, {"topic": "frogs"}])

# Stream
for t in chain.stream({"topic": "bears"}):
    print(t)

# Async Invoke
response = await chain.ainvoke({"topic": "bears"})
response
```


#llm #chatgpt #langchain #deeplearning-ai