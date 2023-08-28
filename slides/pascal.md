## Large Language Models (LLMs)

#### What they are & how to deploy them


## Raise your hand if you have used ChatGPT



## Part 1 - What is an LLM?


A LLM is an AI model that can predict the next word in a sentence:

* "She went to the" → "She went to the *cinema*"


We can use this to complete useful sentences, like instructions:

```markdown
### Instruction
Tell me about the French Revolution
```
→
```markdown
### Response
The French Revolution (1789-1799) was a period of radical social and political upheaval in France 
```


So it's like autocomplete on steroids?

Right! It's autocomplete, but with a brain attached. <!-- .element: class="fragment" -->


### The difference between autocomplete and a LLM is a few billion numbers.


To understand what these few billion numbers are, we need to understand how to build an artificial brain.


A slice of an artificial brain

![Brain nodes](images/neural-net-1.png "Artificial brain nodes") <!-- .element: style="max-height: 400px" -->

Given the preceding words, the model predicts "cinema" as the most likely completion.


How is the most likely completion calculated?

![Brain edges](images/neural-net-2.png "Artificial brain edges") <!-- .element: style="max-height: 400px" -->

Very roughly, by adding and multiplying the numbers on the edges - the arrows connecting nodes.


In fact, we don't actually know what the nodes represent, like how we can't really say what a single neuron in a human brain represents.

![Brain no nodes](images/neural-net-3.png "Artificial brain no nodes") <!-- .element: style="max-height: 400px" -->


The beauty is, we don't need to understand the nodes. 

All of the information in an artificial brain is contained in the numbers on the arrows:  the weights, or the **parameters** of the model.

| 0  | 0  |  0.3 | 0 | 0.5  | 
|---|---|---|---|---|
| 0.6  | 0  | 0  | 0.2  | 0  |
| 0  | 0.2  | 0.4  | 0.8  | 0  |
| 0.9  | 0.3  | 0  | 0.4  | 0  |
<!-- .element: style="font-size: 30px" -->


And all we need to do is "multiply" our input by these numbers, and we get our output.

"She went to the" → [10, 28, 78, 49]
  
Every token (partial word) known to the model is represented by a number <!-- .element: style="font-size: 30px" -->

[10, 28, 78, 49] x 
| 0  | 0  |  0.3 | 0 | 0.5  | 
|---|---|---|---|---|
| 0.6  | 0  | 0  | 0.2  | 0  |
| 0  | 0.2  | 0.4  | 0.8  | 0  |
| 0.9  | 0.3  | 0  | 0.4  | 0  |
<!-- .element: style="font-size: 30px" -->
= [10, 28, 78, 49, *82*] → "She went to the *cinema*"


* How many neurons are there in a human brain?
  * 86 billion
* How many weights are there in a LLM?
  * GPT3 - 175 billion
  * GPT4 - (supposedly) 220 billion x 8 expert models
  * Llama2 (can run locally) - 70 billion


### We're just getting started - today's LLMs are very unoptimized, but GPT-4 can already pass the bar exam.



## Part 2 - How to deploy LLMs


As with any service, there are two options:
1. Use an API, e.g. OpenAI, Google Vertex, Anthropic
2. Run LLMs privately on your own infrastructure, e.g. Llama, MPT, etc


## IMPORTANT
Don't expect too much from an LLM, like with a single prompt saying "make me a millionaire".

All LLMs are far more useful when you ask them to do very specific tasks - we don't have an Artificial **General** Intelligence yet, so we have to surround LLM completions with our own logic.


That means we have to **orchestrate** calls to LLMs, by providing context to prompts, feeding some prompt output back as input, filtering output, etc - typical workflow stuff.

Pipelines aren't going anywhere.


LangChain is a good library for fast prototyping of LLM pipelines, in Python and JavaScript.

Be wary of LangChain in production - it can be hard to adjust for every use case. Use it to figure out what works, then implement some of those things yourself.


How about running LLMs on your own infrastructure, without depending on a third-party API?
* Either you need some hefty GPUs - e.g. AWS instances with 24GB VRAM, to multiply weights fast.
* Or use llama.cpp, which runs LLM inference adequately fast on CPU + RAM, with GPU acceleration if available.



## Part 3 - What we're doing with LLMs


### We're automating ourselves, by building a fully-automated AI senior developer.


But didn't you say that LLMs are only good at specific tasks, not general tasks like being a developer?


Right! To be a good senior developer, you have to:
* Understand the underlying business
* Understand the codebase
* Capture requirements, by talking to stakeholders
* Be able to plan and execute complex changes
* React to changing requirements
* Take in feedback from the running system, as you make changes, and update your plans
* Be able to validate your changes
* Learn from your mistakes, and your successes


We are building LLM pipelines - AI Architecture - that can do all of these things.

But we have to start small, and build up from there.


* We will soon start solving small development tasks for you, to train our AI systems on real world problems.
* We will also soon launch a service for you that takes ideas, feedback and bugs from anyone in your company, and delivers high-quality tickets in Trello.


Looking forward to building the future of product development with you! <!-- .element: style="font-size: 60px" -->