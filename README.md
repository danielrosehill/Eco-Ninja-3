# Eco Ninja 3: Sustainability Data Retrieval Genie

## How far can LLMs be stretched for data retrieval and analysis?

02-Dec-24

<img align="left" width="200" src="images/econinja.png">

My decision to give this a whimsical name and share this on the internet was motivated primarily by the fact that after spending so much time working on these prompts and configurations it felt out of character *not* to want to pass it along.

My "Eco Genie" prompt has already gone through far more than three rounds of iteration but parking it here seems like a comfortable place for version control: it's had a couple of fitting starts and requires much more tinkering. 

"Eco Ninja" is *not* a prompting strategy that I expected to work out of the box. I've played around with various ways to run this including LangChain, as an "assistant" (I think the most logiclal implementation) and - for testing, etc - casual prompting. 

So far, I've been pleasantly surprised by the accuracy and it has maintained good accuracy over runs of a couple of hundred inputs (for LangChain, I used an input file called `companies.txt` to provide a list to iterate through). I like testing this agent and prompt config because it represents, for me, something of a moonshot idea in seeing how far chain-of-thought prompting can stretch way beyond the realm of conversational instruction into more exploratory territory. 

Asking for only one humble variable from the user, the config throws an *awful* lot of wants at the kitchen sink of whatever large language model is unlucky enough to run into it (I experimented with a more elaborate version but through it not worth including):

- Retrieve the right data!  
- Parse those long sustainability PDFs!  
- Retrieve the exact correct metric from a long table of lookalikes!  
- Perform some calculations!  
- Summarise and format the output

To my mind, it represents a good challenge to see what LLMs enriched with RAG and computational augments *are* already capable of. Its accuracy is imperfect and verification and review of its findings are a must, but it has nevertheless consistently surprised me.

## Config For Agent

Nested under:

`agent-config`

Try on:

- Hugging Face  
- OpenAI Platform 
-  Etc
-  

## Agent --> Prompt

To "convert" this to a prompt template, rewrite (or ask an LLM to!). This works nicely with LangChain.


## Versions

Core prompt body:

V3 - Word count about 356 chars

488 tokens (GPT4-o)

## Model Requirements

- Choose an instructional model  
- Training data cutoff must be after Y/E 2023 *or* RAG pipeline beyond that  

## Prompting Strategies

- The thumbnail request was added as I was working on creating a visualisation for this in Streamlit
- The random ID would be better scripted but as a second best I added it into the config. The idea is that it could facilitate correlating similar reports after the initial first pass data generation. 

## Output Formatting Methods

The strategy I've been experimenting with to use this to ingest data in a standardised format was to provide a header row of `CSV` with the instruction to adhere exactly to this format. Something very like:

```csv
company,company name,sector,country,reporting year,scope 1 emissions,scope 2 emissions,scope 3 emissions,scope 1 emissions monetized,scope 2 emissions monetized,scope 3 emissions monetized,scope 1 units,scope 2 units,scope 3 units,units text,report URL,report title,report publication date,all scopes,all scopes monetized,EBITDA,EBITDA source,EBITDA URL,EBITDA reporting year,monetized emissions over EBITDA ratio,monetization rate,scope 3 reporting type
```

## Experiment: Hey LLM, What Would YOU Add?!

I *love* the fact that working with prompts is such fertile ground for creative techhies. 

I like seeing if an LLM can ideate any variables that it may wish to scoop in to its output (yes, I'm a polite prompter):

>Please generate one iteration on this prompt template. Its purpose is to retrieve information to analyze the potential correlation in different industrial sectors between sustainability performance and financial profitability. You may add up to five more values and you have total liberty to think what those might be. Just make sure to add them into the main body of the template and also add them as values in the CSV row to ensure that the data is returned in the same format. Here is the current template. {template}