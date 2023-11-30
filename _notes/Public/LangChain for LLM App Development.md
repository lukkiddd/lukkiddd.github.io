---
title: LangChain for LLM App Development
notetype: feed
date: 2023-11-23
---

## Summary:

The [LangChain for LLM Application Development Course](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/), focuses on utilizing the LangChain Python/TypeScript framework to streamline the creation of Language Model (LLM) applications. The course highlights key processes specific to Retrieval-Augmented Generation (RAG), emphasizing four crucial aspects:

**Building Vector Database** :
- Extracting information from documents to construct a vectors database.

**Query and Similar Document Retrieval** :
- Employing queries to identify similar documents efficiently.

**Parsing Documents to LLM** :
- Processing the selected documents through the LLM to generate meaningful responses.

### The course introduce you a LangChain framework with

**LLM Model Compatibility** :
- Compatibility with various LLM models, such as OpenAI.

```python
from langchain.chat_models import ChatOpenAI
chat = ChatOpenAI(temperature=0.0, model="gpt-3.5-turbo")
```


**Reusable Templates** :
- Obtaining results based on customizable prompts with reusable templates.

```python
template_string = """Translate the text \
that is delimited by triple backticks \
into a style that is {style}. \
text: ```{text}```
"""

from langchain.prompts import ChatPromptTemplate

prompt_template = ChatPromptTemplate.from_template(template_string)

customer_style = """American English \
in a calm and respectful tone
"""

customer_email = """
Arrr, I be fuming that me blender lid \
flew off and splattered me kitchen walls \
with smoothie! And to make matters worse, \
the warranty don't cover the cost of \
cleaning up me kitchen. I need yer help \
right now, matey!
"""

customer_messages = prompt_template.format_messages(
                    style=customer_style,
                    text=customer_email)
```

**Result Parsing** :
- Parsing results into dictionaries or JSON format.

```python
from langchain.output_parsers import ResponseSchema
from langchain.output_parsers import StructuredOutputParser
gift_schema = ResponseSchema(name="gift",
                             description="Was the item purchased\
                             as a gift for someone else? \
                             Answer True if yes,\
                             False if not or unknown.")
delivery_days_schema = ResponseSchema(name="delivery_days",
                                      description="How many days\
                                      did it take for the product\
                                      to arrive? If this \
                                      information is not found,\
                                      output -1.")
price_value_schema = ResponseSchema(name="price_value",
                                    description="Extract any\
                                    sentences about the value or \
                                    price, and output them as a \
                                    comma separated Python list.")

response_schemas = [gift_schema, 
                    delivery_days_schema,
                    price_value_schema]
output_parser = StructuredOutputParser.from_response_schemas(response_schemas)
format_instructions = output_parser.get_format_instructions()
```

```python
response = chat(messages)
output_dict = output_parser.parse(response.content)
```

**Memory Module** :
- Utilizing a Memory module to enable LLMs to remember context, particularly useful for chatbots.

```python
from langchain.chat_models import ChatOpenAI
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory

llm = ChatOpenAI(temperature=0.0, model=llm_model)
memory = ConversationBufferMemory()
conversation = ConversationChain(
    llm=llm, 
    memory = memory,
    verbose=True
)

##---##
print(memory.buffer)
memory.load_memory_variables({})
memory.save_context({"input": "Hi"}, 
                    {"output": "What's up"})
                    
##-- Window Memory --##
from langchain.memory import ConversationBufferWindowMemory
memory = ConversationBufferWindowMemory(k=1)               
memory.save_context({"input": "Hi"},
                    {"output": "What's up"})
memory.save_context({"input": "Not much, just hanging"},
                    {"output": "Cool"})


##-- Token Buffer --##
from langchain.memory import ConversationTokenBufferMemory
from langchain.llms import OpenAI
llm = ChatOpenAI(temperature=0.0, model=llm_model)

memory = ConversationTokenBufferMemory(llm=llm, max_token_limit=50)
memory.save_context({"input": "AI is what?!"},
                    {"output": "Amazing!"})
memory.save_context({"input": "Backpropagation is what?"},
                    {"output": "Beautiful!"})
memory.save_context({"input": "Chatbots are what?"}, 
                    {"output": "Charming!"})

##-- Summary Memory --##
from langchain.memory import ConversationSummaryBufferMemory

# create a long string
schedule = "There is a meeting at 8am with your product team. \
You will need your powerpoint presentation prepared. \
9am-12pm have time to work on your LangChain \
project which will go quickly because Langchain is such a powerful tool. \
At Noon, lunch at the italian resturant with a customer who is driving \
from over an hour away to meet you to understand the latest in AI. \
Be sure to bring your laptop to show the latest LLM demo."

memory = ConversationSummaryBufferMemory(llm=llm, max_token_limit=100)
memory.save_context({"input": "Hello"}, {"output": "What's up"})
memory.save_context({"input": "Not much, just hanging"},
                    {"output": "Cool"})
memory.save_context({"input": "What is on the schedule today?"}, 
                    {"output": f"{schedule}"})
memory.load_memory_variables({})

conversation = ConversationChain(
    llm=llm, 
    memory = memory,
    verbose=True
)

conversation.predict(input="What would be a good demo to show?")
memory.load_memory_variables({})
```

**Chaining Input/Output** :
- Employing the Chain module to link input/output across different LLM responses, including the router chain for routing specific responses to designated prompts.

```python
from langchain.chat_models import ChatOpenAI
from langchain.prompts import ChatPromptTemplate
from langchain.chains import LLMChain
from langchain.chains import SimpleSequentialChain

llm = ChatOpenAI(temperature=0.9, model=llm_model)

# prompt template 1
first_prompt = ChatPromptTemplate.from_template(
    "What is the best name to describe \
    a company that makes {product}?"
)

# Chain 1
chain_one = LLMChain(llm=llm, prompt=first_prompt)
# prompt template 2
second_prompt = ChatPromptTemplate.from_template(
    "Write a 20 words description for the following \
    company:{company_name}"
)
# chain 2
chain_two = LLMChain(llm=llm, prompt=second_prompt)
overall_simple_chain = SimpleSequentialChain(chains=[chain_one, chain_two],
                                             verbose=True
                                            )
overall_simple_chain.run(product)
```


```python
from langchain.chains import SequentialChain
llm = ChatOpenAI(temperature=0.9, model=llm_model)

# prompt template 1: translate to english
first_prompt = ChatPromptTemplate.from_template(
    "Translate the following review to english:"
    "\n\n{Review}"
)
# chain 1: input= Review and output= English_Review
chain_one = LLMChain(llm=llm, prompt=first_prompt, 
                     output_key="English_Review"
                    )
second_prompt = ChatPromptTemplate.from_template(
    "Can you summarize the following review in 1 sentence:"
    "\n\n{English_Review}"
)
# chain 2: input= English_Review and output= summary
chain_two = LLMChain(llm=llm, prompt=second_prompt, 
                     output_key="summary"
                    )
# prompt template 3: translate to english
third_prompt = ChatPromptTemplate.from_template(
    "What language is the following review:\n\n{Review}"
)
# chain 3: input= Review and output= language
chain_three = LLMChain(llm=llm, prompt=third_prompt,
                       output_key="language"
                      )

# prompt template 4: follow up message
fourth_prompt = ChatPromptTemplate.from_template(
    "Write a follow up response to the following "
    "summary in the specified language:"
    "\n\nSummary: {summary}\n\nLanguage: {language}"
)
# chain 4: input= summary, language and output= followup_message
chain_four = LLMChain(llm=llm, prompt=fourth_prompt,
                      output_key="followup_message"
                     )
# overall_chain: input= Review 
# and output= English_Review,summary, followup_message
overall_chain = SequentialChain(
    chains=[chain_one, chain_two, chain_three, chain_four],
    input_variables=["Review"],
    output_variables=["English_Review", "summary","followup_message"],
    verbose=True
)

overall_chain(review)
```

and also RouterChain


**Loader and Q/A Chain** :

- Creating Question-and-Answer LLMs using the Loader and Q/A chain.

```python
from langchain.document_loaders import CSVLoader
loader = CSVLoader(file_path=file)
docs = loader.load()

from langchain.embeddings import OpenAIEmbeddings
embeddings = OpenAIEmbeddings()

db = DocArrayInMemorySearch.from_documents(
    docs, 
    embeddings
)
query = "Please suggest a shirt with sunblocking"
docs = db.similarity_search(query)


## -- OR
retriever = db.as_retriever()
qa_stuff = RetrievalQA.from_chain_type(
    llm=llm, 
    chain_type="stuff", 
    retriever=retriever, 
    verbose=True
)
query =  "Please list all your shirts with sun protection in a table \
in markdown and summarize each one."
response = qa_stuff.run(query)

##-- OR
index = VectorstoreIndexCreator(
    vectorstore_cls=DocArrayInMemorySearch,
    embedding=embeddings,
).from_loaders([loader])
response = index.query(query, llm=llm)
```

**Evaluation and Testing** :
- Using LLMs for result evaluation and generating examples for testing purposes. -- This seems to be the same technique as use in why labs which mentioned in [[Quality and Safety for LLM Applications]]


> [Evaluation Prompt](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/evaluation/qa/eval_prompt.py)


```python
from langchain.evaluation.qa import QAGenerateChain

file = 'OutdoorClothingCatalog_1000.csv'
loader = CSVLoader(file_path=file)
data = loader.load()

example_gen_chain = QAGenerateChain.from_llm(ChatOpenAI(model="gpt-3.5-turbo"))
new_examples = example_gen_chain.apply_and_parse(
    [{"doc": t} for t in data[:5]]
)
```


```python
from langchain.evaluation.qa import QAEvalChain
llm = ChatOpenAI(temperature=0, model=""gpt-3.5-turbo"")
eval_chain = QAEvalChain.from_llm(llm)

examples = [
    {
        "query": "Do the Cozy Comfort Pullover Set\
        have side pockets?",
        "answer": "Yes"
    },
    {
        "query": "What collection is the Ultra-Lofty \
        850 Stretch Down Hooded Jacket from?",
        "answer": "The DownTek collection"
    }
]
predictions = qa.apply(examples)

graded_outputs = eval_chain.evaluate(examples, predictions)
for i, eg in enumerate(examples):
    print(f"Example {i}:")
    print("Question: " + predictions[i]['query'])
    print("Real Answer: " + predictions[i]['answer'])
    print("Predicted Answer: " + predictions[i]['result'])
    print("Predicted Grade: " + graded_outputs[i]['text'])
    print()
```


**Agents Module** :
- Leveraging the ReAct prompting in the Agents module to enable LLMs to perform various actions.



> - [Wikipedia tool](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/tools/wikipedia/tool.py)
> - [LLM Math](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/chains/llm_math/prompt.py)
> - [PythonREPLTool](https://github.com/langchain-ai/langchain/blob/master/libs/experimental/langchain_experimental/tools/python/tool.py)


```python
from langchain.agents.agent_toolkits import create_python_agent
from langchain.agents import load_tools, initialize_agent
from langchain.agents import AgentType
from langchain.tools.python.tool import PythonREPLTool
from langchain.python import PythonREPL
from langchain.chat_models import ChatOpenAI

llm = ChatOpenAI(temperature=0, model="gpt-3.5-turbo")
tools = load_tools(["llm-math","wikipedia"], llm=llm)
agent= initialize_agent(
    tools, 
    llm, 
    agent=AgentType.CHAT_ZERO_SHOT_REACT_DESCRIPTION,
    handle_parsing_errors=True,
    verbose = True)

## Math example
agent("What is the 25% of 300?")

## Wikipedia example
question = "Tom M. Mitchell is an American computer scientist \
and the Founders University Professor at Carnegie Mellon University (CMU)\
what book did he write?"
result = agent(question) 
```



```python
## Python Agent
agent = create_python_agent(
    llm,
    tool=PythonREPLTool(),
    verbose=True
)
customer_list = [["Harrison", "Chase"], 
                 ["Lang", "Chain"],
                 ["Dolly", "Too"],
                 ["Elle", "Elem"], 
                 ["Geoff","Fusion"], 
                 ["Trance","Former"],
                 ["Jen","Ayai"]
                ]
agent.run(f"""Sort these customers by \
last name and then first name \
and print the output: {customer_list}""") 
```


```python
## Create your own tool
from langchain.agents import tool
from datetime import date

@tool
def time(text: str) -> str:
    """Returns todays date, use this for any \
    questions related to knowing todays date. \
    The input should always be an empty string, \
    and this function will always return todays \
    date - any date mathmatics should occur \
    outside this function."""
    return str(date.today())
    
agent= initialize_agent(
    tools + [time], 
    llm, 
    agent=AgentType.CHAT_ZERO_SHOT_REACT_DESCRIPTION,
    handle_parsing_errors=True,
    verbose = True)

try:
    result = agent("whats the date today?") 
except: 
    print("exception on external access")
```

In essence, the course provides a comprehensive overview of the LangChain framework, empowering developers to rapidly create and enhance LLM applications with diverse functionalities.

#llm #chatgpt #langchain #deeplearning-ai