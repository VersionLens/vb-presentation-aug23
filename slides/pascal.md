## Large Language Models (LLMs)

#### What they are & how to deploy them


## Raise your hand if you have used ChatGPT



## Part 1 - What is an LLM?

An AI model that can predict the next word in a sentence:

* "She went to the" → "She went to the *cinema*"


So it's like autocomplete on steroids?

Right... if autocomplete had a brain. <!-- .element: class="fragment" -->


### The difference between autocomplete and a LLM is a few billion numbers.


To understand what these few billion numbers are, we need to understand how to build an artificial brain.


A slice of an artificial brain

![Brain nodes](/images/neural-net-1.png "Artificial brain nodes") <!-- .element: style="max-height: 400px" -->

Given the preceding words, the model predicts "cinema" as the most likely completion.


How is the most likely completion calculated?

![Brain edges](/images/neural-net-2.png "Artificial brain edges") <!-- .element: style="max-height: 400px" -->

Very roughly, by adding and multiplying the numbers on the edges - the arrows connecting nodes.


In fact, we don't actually know what the nodes represent, like how we can't really say what a single neuron in a human brain represents.

![Brain no nodes](/images/neural-net-3.png "Artificial brain no nodes") <!-- .element: style="max-height: 400px" -->


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