---
title: ChatGPT Prompt Engineering for Developers
notetype: feed
date: 2023-11-30
---

This is a cool course, which help you understand the tips, tactics to write a better prompt. Check it out [ChatGPT Prompt Engineering for Developers](https://learn.deeplearning.ai/chatgpt-prompt-eng)

## Prompting Principles[¶](https://s172-31-9-39p41461.lab-aws-production.deeplearning.ai/notebooks/l2-guidelines.ipynb#Prompting-Principles)

### Principle 1: Write clear and specific instructions

**Tactic 1**: Use delimiters to clearly indicate distinct parts of the input

```python
text = f"""
You should express what you want a model to do by \ 
providing instructions that are as clear and \ 
specific as you can possibly make them. \ 
This will guide the model towards the desired output, \ 
and reduce the chances of receiving irrelevant \ 
or incorrect responses. Don't confuse writing a \ 
clear prompt with writing a short prompt. \ 
In many cases, longer prompts provide more clarity \ 
and context for the model, which can lead to \ 
more detailed and relevant outputs.
"""
prompt = f"""
Summarize the text delimited by single backticks \ 
into a single sentence.
`{text}`
"""
response = get_completion(prompt)
print(response)
```


**Tactic 2**: Ask for a structured output

```python
prompt = f"""
Generate a list of three made-up book titles along \ 
with their authors and genres. 
Provide them in JSON format with the following keys: 
book_id, title, author, genre.
"""
response = get_completion(prompt)
print(response)
```


**Tactic 3**: Ask the model to check whether conditions are satisfied

```python
text_1 = f"""
Making a cup of tea is easy! First, you need to get some \ 
water boiling. While that's happening, \ 
grab a cup and put a tea bag in it. Once the water is \ 
hot enough, just pour it over the tea bag. \ 
Let it sit for a bit so the tea can steep. After a \ 
few minutes, take out the tea bag. If you \ 
like, you can add some sugar or milk to taste. \ 
And that's it! You've got yourself a delicious \ 
cup of tea to enjoy.
"""
prompt = f"""
You will be provided with text delimited by triple quotes. 
If it contains a sequence of instructions, \ 
re-write those instructions in the following format:

Step 1 - ...
Step 2 - …
…
Step N - …

If the text does not contain a sequence of instructions, \ 
then simply write \"No steps provided.\"

\"\"\"{text_1}\"\"\"
"""
response = get_completion(prompt)
print("Completion for Text 1:")
print(response)
```



**Tactic 4**: ["Few-shot" prompting](https://www.promptingguide.ai/techniques/fewshot)

```python
prompt = f"""
Your task is to answer in a consistent style.

<child>: Teach me about patience.

<grandparent>: The river that carves the deepest \ 
valley flows from a modest spring; the \ 
grandest symphony originates from a single note; \ 
the most intricate tapestry begins with a solitary thread.

<child>: Teach me about resilience.
"""
response = get_completion(prompt)
print(response)
```



### Principle 2: Give the model time to “think”

**Tactic 1**: Specify the steps required to complete a task

```python
text = f"""
In a charming village, siblings Jack and Jill set out on \ 
a quest to fetch water from a hilltop \ 
well. As they climbed, singing joyfully, misfortune \ 
struck—Jack tripped on a stone and tumbled \ 
down the hill, with Jill following suit. \ 
Though slightly battered, the pair returned home to \ 
comforting embraces. Despite the mishap, \ 
their adventurous spirits remained undimmed, and they \ 
continued exploring with delight.
"""
# example 1
prompt_1 = f"""
Perform the following actions: 
1 - Summarize the following text delimited by single \
backticks with 1 sentence.
2 - Translate the summary into French.
3 - List each name in the French summary.
4 - Output a json object that contains the following \
keys: french_summary, num_names.

Separate your answers with line breaks.

Text:
`{text}`
"""

response = get_completion(prompt_1)
print("Completion for prompt 1:")
print(response)
```


**Tactic 2**: Instruct the model to work out its own solution before rushing to a conclusion

```python
prompt = f"""
Your task is to determine if the student's solution \
is correct or not.
To solve the problem do the following:
- First, work out your own solution to the problem including the final total. 
- Then compare your solution to the student's solution \ 
and evaluate if the student's solution is correct or not. 
Don't decide if the student's solution is correct until 
you have done the problem yourself.

Use the following format:
Question:
`
question here
`
Student's solution:
`
student's solution here
`
Actual solution:
`
steps to work out the solution and your solution here
`
Is the student's solution the same as actual solution \
just calculated:
`
yes or no
`
Student grade:
`
correct or incorrect
`

Question:
`
I'm building a solar power installation and I need help \
working out the financials. 
- Land costs $100 / square foot
- I can buy solar panels for $250 / square foot
- I negotiated a contract for maintenance that will cost \
me a flat $100k per year, and an additional $10 / square \
foot
What is the total cost for the first year of operations \
as a function of the number of square feet.
`
Student's solution:
`
Let x be the size of the installation in square feet.
Costs:
1. Land cost: 100x
2. Solar panel cost: 250x
3. Maintenance cost: 100,000 + 100x
Total cost: 100x + 250x + 100,000 + 100x = 450x + 100,000
`
Actual solution:
"""
response = get_completion(prompt)
print(response)
```



**Remark**: Model Limitations: Hallucinations - [[Quality and Safety for LLM Applications]]


### Other use-cases

- **Summarization** - Prompt LLM to summarise, we can also specify the focus or specific information in the context
- **Inferring** - Prompt LLM to classify, extract information, do the sentiment, identify emotions, and etc.
- **Transforming** - Prompt LLM to be a translator from one language to another, convert the tone of the language, format the conversation, spellcheck or grammar check
- **Expanding** - Automate reply email

#llm #chatgpt #prompting #deeplearning-ai