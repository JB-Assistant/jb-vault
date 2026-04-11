---
title: "How to become an AI Engineer in 6 months (RESOURCES)"
source: "https://x.com/deronin_/status/2033587293064204349?s=46&t=ub4QNKLqvh3yU44VgGVYlQ"
author:
  - "[[@deronin_]]"
published: 2026-03-16
created: 2026-04-11
description: "AI engineering has quickly become one of the most valuable skill sets in techThe problem is that most beginners have no clear idea what they..."
tags:
  - "clippings"
---
![Image](https://pbs.twimg.com/media/HDitxBAWYAAiy-O?format=jpg&name=large)

AI engineering has quickly become one of the most valuable skill sets in tech

The problem is that most beginners have no clear idea what they should actually study

Some start with machine learning theory

Some get stuck endlessly watching tutorials

Others jump straight into prompts and agents without understanding APIs, backend basics, or how real products are actually built

The result is usually the same: a lot of confusion and very little practical skill

If your goal is to become an AI engineer, you don’t need to master every field of artificial intelligence

You need to learn how to build useful AI systems in the real world

**That means learning how to:**

- build end-to-end applications with LLMs
- work with model APIs such as OpenAI and Anthropic
- properly design prompts and context
- use structured outputs and tool calling
- add retrieval when needed
- deploy projects so people can actually use them

This guide was created to give you a practical 6-month roadmap

**The article is 10,000+ WORDS**, so reading it may take a few hours or even longer

But its real value is that for every skill you need to learn, there are resources and clear explanations of what to do

That way, within six months you can reach the level of AI engineering, and start using it for yourself already within the first 1-2 months

**Writing this article took more than 40 HOURS**, and I worked on it together with my friend [@andy\_ai0](https://x.com/@andy_ai0)

He just started building his personal brand on X, but he understands AI very well and helped a lot with this article

I definitely think he deserves your follow and support as he grows

**Now let's start reading the article** ⬇️

## What an AI Engineer actually does

A lot of people hear the phrase "AI engineer" and imagine someone training giant models from scratch

In reality, most modern AI engineers do something much more practical

They build products and systems on top of existing models

**That usually includes:**

- connecting to LLM APIs
- designing prompts and context flows
- building chat, search, or automation systems
- integrating tools, databases, and external APIs
- handling structured outputs
- improving reliability, cost, and latency
- deploying AI features into real applications

**So in practice, an AI engineer often sits somewhere between:**

- software engineering
- product engineering
- automation
- applied AI

This is why the role is growing so fast

Companies do not only need researchers They need people who can take models and turn them into useful products

That is also why this roadmap focuses less on heavy theory and more on practical execution

If you can build real LLM apps, retrieval systems, automations, and production-ready workflows, you are already much closer to being employable than most beginners

⏩------------------------------------------------------------------------⏪

## Month 1: Get solid enough in coding and the fundamentals

Your goal this month: Become a functional Python developer

You don't need to be an expert, you just need to stop Googling basic syntax and be able to build simple programs confidently

AI engineering is first and foremost software engineering

Everything in the later months assumes you can write clean Python, use the terminal, call APIs, and manage a codebase. This month is your foundation

# What to learn

## 1\. Python

Python is the language of AI engineering. Full stop. Almost every library, API, and tutorial you'll encounter over the next six months is in Python

**How to learn it:**

Start with a structured course that forces you to write code, not just watch videos

The most common mistake beginners make is consuming content passively, reading along, nodding, and never opening a code editor

Fight this by coding every single example as you go

**Resources:**

**1\. Python for Everybody (Coursera, free to audit)**

Link: [https://www.coursera.org/specializations/python](https://www.coursera.org/specializations/python)

The best starting point for absolute beginners. Dr. Chuck is one of the most beginner-friendly Python teachers on the internet

**2\. freeCodeCamp Python Course (YouTube, free)**

Link: [https://www.youtube.com/watch?v=rfscVS0vtbw](https://www.youtube.com/watch?v=rfscVS0vtbw)

A comprehensive 4-hour video covering all the fundamentals

**3\. CS50P: Introduction to Programming with Python (Harvard, free)**

Link: [https://cs50.harvard.edu/python/](https://cs50.harvard.edu/python/)

More rigorous. Includes problem sets and a final project. Great if you want structure

**4\. Official Python docs (the tutorial)**

Link: [https://docs.python.org/3/tutorial/](https://docs.python.org/3/tutorial/)

Dry but authoritative, use as a reference

**What to focus on:**

- Variables, data types, loops, conditionals, functions
- Lists, dictionaries, sets, tuples
- File I/O and working with JSON
- Classes and basic OOP (just enough to understand what you're reading)
- Error handling with try/except
- Virtual environments (venv) and pip
- Package management – understanding requirements.txt

Practice project: Build a simple CLI tool in Python. Something like a personal expense tracker that reads/writes to a JSON file, or a script that calls a public API (like a weather API) and prints formatted results

## 2\. Git and GitHub

Git is how professional developers save and share code. You'll need it constantly, to version your projects, collaborate, and showcase your portfolio work on GitHub

**How to learn it:**

Git is confusing at first because the mental model is non-obvious

Don't try to memorize commands instead, understand what problem Git is solving

(tracking changes, enabling collaboration, letting you undo mistakes) and the commands will make sense

**Resources:**

**1\. GitHub Skills (free, interactive)**

**Link:** [https://skills.github.com/](https://skills.github.com/)

Official interactive courses built inside GitHub itself. Start here

**2 . Learn Git Branching (free, interactive)**

**Link:** [https://learngitbranching.js.org/](https://learngitbranching.js.org/)

Hands-down the best visual tool for understanding branches and merges

**3\. Pro Git Book (free online book)**

**Link:** [https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2)

The comprehensive reference. Skip to chapters you need

**What to focus on:**

- git init, add, commit, push, pull
- Branching and merging
- Understanding .gitignore
- Creating repos on GitHub and pushing local projects
- Reading and writing basic README files

**Practice:** From now on, every single project you build, even small scripts, should live in a GitHub repo. This builds the habit and gives you a portfolio

## 3\. CLI / Terminal Basics

As an AI engineer you'll be running scripts, installing packages, managing servers, and navigating files entirely from the command line

Being slow or scared in the terminal is a real bottleneck

**Resources:**

**1\. The 50 most popular Linux & Terminal commands (full course for beginners)**

**Link:** [https://www.youtube.com/watch?v=ZtqBQ68cfJc](https://www.youtube.com/watch?v=ZtqBQ68cfJc)

Good for absolute beginners on Linux/Mac

**2\. The Missing Semester of Your CS Education (MIT, free)**

**Link:** [https://missing.csail.mit.edu/](https://missing.csail.mit.edu/)

Covers shell scripting, terminal tools, and the command line fluency that most CS courses skip

**What to focus on:**

- Navigation: cd, ls, pwd, mkdir, rm
- Reading files: cat, less, grep
- Running Python scripts from the terminal
- Environment variables
- Basic understanding of PATH

## 4\. JSON, APIs, HTTP, and Async Basics

You'll be calling LLM APIs from day one of Month 2

That means you need to understand how web APIs work before you ever touch OpenAI or Anthropic's SDKs

**Resources:**

**1\. HTTP basics – MDN Web Docs (free)**

**Link:** [https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

The clearest explanation of how HTTP requests and responses work

**2\. REST API Tutorial**

**Link:** [https://restfulapi.net/](https://restfulapi.net/)

Short and practical

**3\. Python requests library docs**

**Link:** [https://requests.readthedocs.io/en/latest/](https://requests.readthedocs.io/en/latest/)

Learn how to call any web API in Python

**4\. Python async/await (free)**

Link: [https://realpython.com/async-io-python/](https://realpython.com/async-io-python/)

Understanding async is essential for working with streaming LLM responses later

**What to focus on:**

- GET, POST requests – what they are and how to make them in Python
- Reading and writing JSON
- HTTP status codes (200, 400, 401, 404, 500 – what each means)
- What an API key is and basic auth patterns
- What async def and await do and why they exist

**Practice project:** Write a Python script that calls a free public API (try [Open-Meteo](https://open-meteo.com/) for weather data – no API key needed) and formats the result as a clean JSON output

## 5\. Basic SQL and Pandas

You won't need to be a data scientist, but you will regularly need to inspect, query, and manipulate data

SQL basics and pandas fluency will save you constantly

**Resources:**

**1 . SQLBolt (free, interactive)**

**Link:** [https://sqlbolt.com/](https://sqlbolt.com/)

The fastest way to learn SQL from scratch. 20 short lessons with in-browser exercises

**2\. Pandas official getting started guide**

**Link:** [https://pandas.pydata.org/docs/getting\_started/index.html](https://pandas.pydata.org/docs/getting_started/index.html)

Work through the 10 Minutes to Pandas tutorial

**3\. Kaggle Pandas course (free)**

**Link:** [https://www.kaggle.com/learn/pandas](https://www.kaggle.com/learn/pandas)

Hands-on, practical, short

**What to focus on:**

- SQL: SELECT, WHERE, GROUP BY, JOIN, ORDER BY
- Pandas: loading CSVs, filtering rows, selecting columns, basic aggregations

## 6\. FastAPI

**Resources:**

**1\. FastAPI Official Tutorial (free)**

Link: [https://fastapi.tiangolo.com/tutorial/](https://fastapi.tiangolo.com/tutorial/)

Genuinely one of the best framework docs ever written

Work through it start to finish. Covers path parameters, request bodies, Pydantic validation, and running a dev server

**2\. Python API Development (19-Hour Course, freeCodeCamp, YouTube, free)**

**Link:** [https://www.youtube.com/watch?v=ZtqBQ68cfJc](https://www.youtube.com/watch?v=ZtqBQ68cfJc)

Covers API design fundamentals including routes, serialization, schema validation, and SQL database integration. Builds a full social-media-style API from scratch

**What to focus on:** Creating GET and POST endpoints, path and query parameters, request bodies with Pydantic, running uvicorn, and using FastAPI's built-in /docs interface to test your API without writing a client

## Month 1 Milestone

By the end of this month you should be able to:

- Write Python programs that read/write files, call APIs, and handle errors
- Version your code with Git and push projects to GitHub
- Navigate the terminal without hesitation
- Understand what an HTTP request is and make one in Python
- Query a SQLite database with basic SQL
- Build and run a simple FastAPI app locally

⏩------------------------------------------------------------------------⏪

## Month 2: Master LLM App Development

Your goal this month: Build real AI-powered applications using the OpenAI and Anthropic APIs

By the end you should be comfortable writing prompts that work reliably, getting structured data out of models, making them call your functions, and handling everything that can go wrong

This is the core of AI engineering. Everything else in the roadmap builds on what you learn here

# What to learn

## 1\. Prompting Fundamentals

Prompting isn't just asking questions nicely. It's the craft of writing instructions that produce consistent, reliable outputs from models that are fundamentally probabilistic

As an AI engineer you'll spend a surprising amount of time here

**How to learn it:**

Start with Anthropic's interactive tutorial because it's the most hands-on

Then read OpenAI's official guide. After that, the Prompt Engineering Guide consolidates everything

Work through all three in order – each one reinforces the others

**Resources:**

**1\. Anthropic's Interactive Prompt Engineering Tutorial (free, GitHub)**

**Link:** [https://github.com/anthropics/prompt-eng-interactive-tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial)

A step-by-step course broken into 9 chapters with exercises, designed to give you many chances to practice writing and troubleshooting prompts yourself

Run it as Jupyter notebooks with the Claude API

**2\. Anthropic Prompt Engineering Docs (free)**

**Link:** [https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)

The official reference. Covers everything from basic clarity to XML structuring and agentic systems

**3\. OpenAI Prompt Engineering Guide (free)**

**Link:** [https://platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)

The official guide from OpenAI, covering prompt formats that work well with their models and lead to more useful outputs

**4\.** [PromptingGuide.ai](https://promptingguide.ai/) **(free)**

**Link:** [https://www.promptingguide.ai/](https://www.promptingguide.ai/)

Covers essential techniques from basic prompting to advanced strategies, plus function calling, tool integration, and agentic systems

**What to focus on:** The difference between system and user messages, why specificity matters, chain-of-thought prompting (think step by step), using examples in prompts (few-shot), and how small wording changes can dramatically shift output quality

**Practice:** Take a real task – summarize a document, extract key info from text, classify a piece of feedback – and write 5 different prompts for it. Compare outputs. You'll immediately see how much prompt design affects reliability

## 3\. Structured Outputs / JSON Schemas

In real applications you almost never want raw text from an LLM, you want structured data you can parse, store, and use in your code

Structured outputs solve this by forcing the model to match a schema you define

**Resources:**

**1\. OpenAI Structured Outputs Guide (official docs, free)**

**Link:** [https://platform.openai.com/docs/guides/structured-outputs](https://platform.openai.com/docs/guides/structured-outputs)

Covers the feature that ensures models always generate responses adhering to your JSON Schema, so you don't need to worry about missing keys or hallucinated values

**2\. Instructor library (free, open source)**

**Link:** [https://python.useinstructor.com/](https://python.useinstructor.com/)

The cleanest way to get structured outputs from any LLM provider using Pydantic models

Works with OpenAI, Anthropic, Google, and 15+ other providers using the same code interface, with automatic retries when validation fails

This is what most production AI engineers actually use

**3\. OpenAI Cookbook: Structured Outputs Introduction (free)**

**Link:** [https://developers.openai.com/cookbook/examples/structured\_outputs\_intro/](https://developers.openai.com/cookbook/examples/structured_outputs_intro/)

Practical examples covering chain-of-thought outputs, structured data extraction, and UI generation, good for understanding real-world use cases

**What to focus on:** Defining Pydantic models for your data, passing schemas to the API, understanding the difference between structured outputs and JSON mode, and handling refusals gracefully

**Practice project:** Build an invoice or receipt parser. Give it raw text (e.g. "Invoice #123, $45.99 for 3 widgets, due March 30") and have it return a structured Python object with fields like invoice\_number, amount, items, due\_date

## 4\. Function / Tool Calling

Tool calling is what transforms an LLM from a text generator into something that can take actions – search the web, query a database, call your API, run code. It's one of the most important skills in this entire guide

**How to understand it:** The model doesn't actually execute your functions

It examines the prompt and returns a structured call with the function name and arguments when it decides a tool should be used

Your code then executes the call and sends the result back

**Resources:**

**1\. OpenAI Function Calling Guide (official docs, free)**

**Link:** [https://platform.openai.com/docs/guides/function-calling](https://platform.openai.com/docs/guides/function-calling)

The definitive reference. Covers defining tools, the 5-step calling flow, parallel calls, and best practices

**2\. Anthropic Tool Use Docs (free)**

**Link:** [https://docs.anthropic.com/en/docs/build-with-claude/tool-use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use)

Anthropic's equivalent guide for Claude. The concepts are the same, the syntax is slightly different

**3\. OpenAI Cookbook: How to Call Functions with Chat Models (free, GitHub)**

**Link:** [https://github.com/openai/openai-cookbook/blob/main/examples/How\_to\_call\_functions\_with\_chat\_models.ipynb](https://github.com/openai/openai-cookbook/blob/main/examples/How_to_call_functions_with_chat_models.ipynb)

A complete runnable notebook walking through the full tool-calling loop with real examples

**What to focus on:** Describing functions clearly in JSON Schema, parsing tool call responses, executing the function and feeding results back, handling cases where no tool call is needed, and the concept of tool\_choice: "auto"

**Practice project:** Build a simple assistant that has three tools: get\_weather(city), calculate(expression), and search\_notes(query) (just search a hardcoded dict). Wire them all up and watch the model decide which one to call based on what you ask it

## 5\. Streaming Responses

Streaming means showing the model's output as it's being generated – word by word – rather than waiting for the full response. It makes your apps feel dramatically faster and more alive

**Resources:**

**1\. OpenAI Streaming Docs (official, free)**

**Link:** [https://platform.openai.com/docs/api-reference/streaming](https://platform.openai.com/docs/api-reference/streaming)

The reference for adding stream=True to requests and iterating over chunks

**2\. Anthropic Streaming Docs (official, free)**

**Link:** [https://docs.anthropic.com/en/api/messages-streaming](https://docs.anthropic.com/en/api/messages-streaming)

Anthropic's streaming API reference with Python examples

**3\. How Streaming LLM APIs Work – Simon Willison (free)**

**Link:** [https://til.simonwillison.net/llms/streaming-llm-apis](https://til.simonwillison.net/llms/streaming-llm-apis)

A clear technical breakdown of how Server-Sent Events work under the hood for OpenAI, Anthropic, and Google, useful for understanding what's actually happening at the HTTP level

**What to focus on:** Setting stream=True, iterating over delta chunks, assembling the full response from parts, and wiring streaming into a FastAPI endpoint using StreamingResponse

**Tip:** Streaming is almost always the right choice for user-facing apps. Nobody wants to stare at a loading spinner for 10 seconds waiting for a full response to appear at once

## 5\. Conversation State

LLMs are stateless – they have no memory between calls. Conversation history is something you manage by sending the full message list with every request. Understanding this is fundamental

**Resources:**

**1\. OpenAI Chat Completions Guide, Managing Conversations (official, free)**

**Link:** [https://platform.openai.com/docs/guides/conversation-state](https://platform.openai.com/docs/guides/conversation-state)

The canonical explanation of how the messages array works and how to manage multi-turn conversations

**2\. Anthropic Messages API Docs (official, free)**

**Link:** [https://docs.anthropic.com/en/api/messages](https://docs.anthropic.com/en/api/messages)

Anthropic's equivalent. Same concept, worth reading both to see how they differ

**What to focus on:** The messages array structure, why you append both user and assistant messages, context window limits and what happens when you exceed them, and basic truncation strategies (drop oldest messages, summarize history)

**Practice project:** Build a simple multi-turn chatbot in the terminal. Each turn appends to the messages list. Add a /reset command to clear history, and print the current token count after each exchange

## 6\. Cost, Latency, and Token Basics

Shipping AI apps without understanding costs and tokens is how you end up with surprise bills and slow apps. This is boring but critical

**Resources:**

**1\. OpenAI Pricing Page (official)**

**Link:** [https://openai.com/api/pricing](https://openai.com/api/pricing)

Know what input and output tokens cost per model. Bookmark this and check it whenever you pick a model

**2\. Anthropic Pricing Page (official)**

**Link:** [https://www.anthropic.com/pricing](https://www.anthropic.com/pricing)

Same for Claude models

**3\. OpenAI Tokenizer Tool (free, interactive)**

**Link:** [https://platform.openai.com/tokenizer](https://platform.openai.com/tokenizer)

Paste any text and see exactly how many tokens it is. Use this constantly while you're learning

**4\. Tiktoken (Python library, free)**

**Link:** [https://github.com/openai/tiktoken](https://github.com/openai/tiktoken)

OpenAI's tokenizer library for counting tokens in code before sending requests

**What to focus on:** What a token is (roughly 4 characters / 3/4 of a word), how input vs output tokens are priced differently, how context window size affects what you can do, and the latency trade-off between smaller faster models and larger smarter ones

Also: don't use GPT-4/Opus for everything – cheaper models are often good enough for simple tasks

## 7\. Failure Handling

LLM APIs fail. Rate limits get hit, responses time out, the model returns malformed JSON. Handling failures gracefully is what separates a demo from a production app

**Resources:**

**1\. OpenAI Error Codes Reference (official, free)**

**Link:** [https://platform.openai.com/docs/guides/error-codes](https://platform.openai.com/docs/guides/error-codes)

Every error type you'll encounter and what to do about it

**2\. Anthropic Error Handling Docs (official, free)**

**Link:** [https://docs.anthropic.com/en/api/errors](https://docs.anthropic.com/en/api/errors)

Same for Claude

**3\. Tenacity (Python library, free)**

**Link:** [https://tenacity.readthedocs.io/](https://tenacity.readthedocs.io/)

A clean library for adding retry logic with exponential backoff to any Python function. One decorator and your retries are handled

**What to focus on:** Rate limit errors (429) and exponential backoff, timeout handling with httpx/requests, validating model output before using it, fallback strategies (retry with a different model, return a cached response), and never crashing your app because the LLM returned unexpected output

## 8\. Prompt Injection Awareness

Prompt injection is the #1 security risk in LLM applications

It happens when untrusted user input is combined with system instructions, allowing a user to alter, override, or inject new behavior into the prompt –causing the system to perform unintended actions or generate manipulated outputs

You don't need to be a security expert, but you need to know this exists before you ship anything

**Resources:**

**1\. OWASP Top 10 for LLM Apps – LLM01: Prompt Injection (free)**

**Link:** [https://genai.owasp.org/llmrisk/llm01-prompt-injection/](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)

The authoritative classification covering direct injections (jailbreaking), indirect injections via external content like documents or websites, and real-world attack scenarios

**2\. OWASP Prompt Injection Prevention Cheat Sheet (free)**

**Link:** [https://cheatsheetseries.owasp.org/cheatsheets/LLM\_Prompt\_Injection\_Prevention\_Cheat\_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)

Practical defensive patterns: input validation, privilege control, and output validation

**3\. Evidently AI: What is Prompt Injection (free)**

**Link:** [https://www.evidentlyai.com/llm-guide/prompt-injection-llm](https://www.evidentlyai.com/llm-guide/prompt-injection-llm)

A clear developer-focused explainer on attack types, risks, and design patterns to mitigate them

**What to focus on:** The difference between direct and indirect injection, why system prompts aren't truly "secure", the principle of least privilege for tool access, and never trusting unvalidated LLM output to make consequential decisions automatically

## Month 2 Milestone

By the end of this month you should be able to:

- Write prompts that produce consistent, reliable outputs for a given task
- Get structured JSON data out of any model using Pydantic + Instructor
- Wire up tool calling so a model can call your Python functions
- Stream responses in real time through a FastAPI endpoint
- Manage multi-turn conversation history properly
- Estimate the token cost of a request before sending it
- Handle API errors, timeouts, and bad outputs without crashing
- Explain what prompt injection is and apply basic defenses

⏩------------------------------------------------------------------------⏪

## Month 3: Learn RAG Properly

Your goal this month: Build systems that let LLMs answer questions from your documents, not just from their training data

By the end you should be able to ingest documents, embed and store them, retrieve the right chunks at query time, and produce answers that are grounded, accurate, and citable

RAG is the most in-demand practical skill in AI engineering right now. Almost every real enterprise AI use case – customer support bots, internal knowledge bases, document Q&A – is built on it

Understanding it deeply, not just copying a tutorial, is what separates good engineers from great ones

## 1\. Embeddings

Before you can build a RAG system, you need to understand what embeddings actually are – because they're the foundation everything else is built on

A text embedding is a piece of text projected into a high-dimensional vector space

The position of that text in this space is represented as a long sequence of numbers

Critically, text that is semantically similar ends up close together in that space – which is what makes similarity search possible

**Resources:**

**1 .** Stack Overflow Blog: An Intuitive Introduction to Text Embeddings (free)

**Link:** [https://stackoverflow.blog/2023/11/09/an-intuitive-introduction-to-text-embeddings/](https://stackoverflow.blog/2023/11/09/an-intuitive-introduction-to-text-embeddings/)

The best beginner explanation. Written by a developer who has spent years building NLP products, with a focus on building the right intuition rather than the math

**2\. Google ML Crash Course: Embeddings (free)**

**Link:** [https://developers.google.com/machine-learning/crash-course/embeddings](https://developers.google.com/machine-learning/crash-course/embeddings)

Covers why dense vector representations solve problems that one-hot encoding can't – specifically, capturing semantic relationships between items

**3\. HuggingFace: Getting Started With Embeddings (free)**

**Link:** [https://huggingface.co/blog/getting-started-with-embeddings](https://huggingface.co/blog/getting-started-with-embeddings)

Hands-on guide. Shows how to generate embeddings using the sentence-transformers library, host them, and use them for semantic search over a real FAQ dataset

**4\. OpenAI Embeddings Guide (official docs, free)**

Link: [https://platform.openai.com/docs/guides/embeddings](https://platform.openai.com/docs/guides/embeddings)

The reference for using OpenAI's text-embedding-3-small and text-embedding-3-large models in code

**What to focus on:** What a vector is conceptually, why similar text produces similar vectors, how cosine similarity works, the difference between embedding models (OpenAI, HuggingFace sentence-transformers), and what embedding dimension means in practice

**Practice:** Take 20 sentences on related topics, embed them using OpenAI or sentence-transformers, and write a simple nearest-neighbor search that returns the 3 most similar to a query. This is literally the heart of RAG in miniature

## 2\. Chunking

Your documents are too large to embed as a whole. Chunking is the process of breaking them into smaller pieces before embedding

How you chunk your documents directly affects your system's ability to find relevant information and give accurate answers, even a perfect retrieval system fails if it searches over poorly prepared data

**Resources:**

**1\. Weaviate: Chunking Strategies for RAG (free)**

**Link:** [https://weaviate.io/blog/chunking-strategies-for-rag](https://weaviate.io/blog/chunking-strategies-for-rag)

The most practical guide. Covers fixed-size, recursive, and semantic chunking, with clear guidance on when to use each

**2\. Unstructured: Chunking for RAG Best Practices (free)**

**Link:** [https://unstructured.io/blog/chunking-for-rag-best-practices](https://unstructured.io/blog/chunking-for-rag-best-practices)

A technical deep-dive on chunk sizes, overlap, and how the embedding model's context window imposes hard limits

A good starting point for experimentation is a chunk size of around 250 tokens (approximately 1,000 characters), combined with a 10-20% overlap between consecutive chunks to avoid losing context at boundaries

**3\. LangChain Text Splitters Docs (official, free)**

Link: [https://python.langchain.com/docs/concepts/text\_splitters/](https://python.langchain.com/docs/concepts/text_splitters/)

The practical reference for using RecursiveCharacterTextSplitter, MarkdownTextSplitter, and semantic splitters in code

**What to focus on:** Fixed-size chunking with overlap as your baseline, recursive chunking for structured documents, semantic chunking for better boundary detection, and the core trade-off: chunks that are too large lose retrieval precision; chunks that are too small lose context

**Beginner tip:** Start with RecursiveCharacterTextSplitter from LangChain with chunk\_size=500 and chunk\_overlap=50. This is the most sensible default for most documents and gives you a working baseline to improve from

## 3\. Vector Databases

Once you have embeddings, you need somewhere to store and search them efficiently. This is what vector databases are for

The right choice depends on your situation: use Chroma for fast local prototyping, Pinecone for managed turnkey scale, Weaviate for open-source flexibility with strong hybrid search, Qdrant for complex filters and cost-efficient self-hosting, and pgvector if you're already on PostgreSQL and want to avoid adding another system

**Resources:**

**1\. Chroma Official Docs (free)**

**Link:** [https://docs.trychroma.com/](https://docs.trychroma.com/)

Chroma is perfect for individual developers and small teams who prioritize development speed and simplicity, it runs in-memory or locally with no infrastructure to manage

**2\. Pinecone Learning Center (free)**

**Link:** [https://www.pinecone.io/learn/](https://www.pinecone.io/learn/)

Excellent free tutorials covering vector search concepts, hybrid search, and RAG pipelines. Good provider-agnostic material even if you don't use Pinecone

**3\. Qdrant Documentation (free)**

**Link:** [https://qdrant.tech/documentation/](https://qdrant.tech/documentation/)

Best open-source option for production with advanced filtering. Very fast, flexible, and free to self-host

**4\. pgvector (open source, free)**

**Link:** [https://github.com/pgvector/pgvector](https://github.com/pgvector/pgvector)

If you're building something that already uses PostgreSQL, pgvector adds vector search directly to your existing database with no new infrastructure

**What to focus on:** Creating a collection, inserting embeddings with metadata, querying by similarity with top\_k, and filtering by metadata at query time

You don't need to understand the indexing algorithms (HNSW, IVF) – just understand how to use them

**Practice project:** Index 50-100 pages from any public documentation (e.g. the Python docs, or a Wikipedia article dump) into Chroma with metadata (source URL, section title). Write a query function that retrieves the 5 most relevant chunks for any question

## 4\. Metadata Filtering

Raw similarity search alone isn't enough for real applications. Metadata filtering lets you constrain retrieval to a relevant subset – by date, source, document type, user, category, or any other attribute you store alongside each chunk

**Resources:**

**1\. Pinecone: Metadata Filtering Guide (free)**

**Link:** [https://docs.pinecone.io/guides/data/filter-with-metadata](https://docs.pinecone.io/guides/data/filter-with-metadata)

Clear explanation with code examples of filtering vectors by metadata fields before or during similarity search

**2\. LlamaIndex: Metadata Filters Guide (official docs, free)**

**Link:** [https://docs.llamaindex.ai/en/stable/module\_guides/querying/node\_postprocessors/node\_postprocessors/](https://docs.llamaindex.ai/en/stable/module_guides/querying/node_postprocessors/node_postprocessors/)

Explained how to apply filters at query time in LlamaIndex pipelines

**What to focus on:** Tagging every chunk with relevant metadata at ingestion time (source filename, page number, section, date, category), and using those fields to filter results at query time. This is what makes the difference between a toy demo and a production system where users can ask "only show me results from Q4 2025-Q1 2026 reports"

## 5\. Reranking

Reranking is a technique that adds a semantic boost to the search quality of any keyword or vector search system

After first-stage retrieval returns a candidate set, a reranker re-scores those results based on true contextual relevance to the query – not just vector proximity

The two-stage pattern is: embed and search (fast, approximate) → rerank top-k (slower, more accurate). The result is dramatically better retrieval quality with only a modest latency cost

**Resources:**

**1\. Cohere Reranking Docs (official, free)**

**Link:** [https://docs.cohere.com/docs/reranking-with-cohere](https://docs.cohere.com/docs/reranking-with-cohere)

The best place to start. Covers the full reranking workflow, including semi-structured data like emails and JSON documents. Requires just a single line of code to add to an existing retrieval pipeline

**2\. LangChain: Cohere Reranker Integration (official docs, free)**

**Link:** [https://python.langchain.com/docs/integrations/retrievers/cohere-reranker/](https://python.langchain.com/docs/integrations/retrievers/cohere-reranker/)

Explained how to wire Cohere reranking into a LangChain retriever using ContextualCompressionRetriever

**What to focus on:** The two-stage retrieve-then-rerank pattern, the difference between a bi-encoder (used for first-stage embedding search) and a cross-encoder (used for reranking), and the practical latency/quality trade-off of reranking top-20 vs top-5 results

## 6\. Retrieval Quality Issues

Most RAG failures aren't model failures, they're retrieval failures. Understanding the ways retrieval can go wrong is essential for debugging real systems

**Common issues to learn:**

- **Semantic drift:** The query embedding doesn't match the relevant chunk embedding even though the information is there. Fix: try query rewriting or HyDE (Hypothetical Document Embeddings)
- **Chunk boundary problems:** The relevant information is split across two chunks. Fix: increase overlap or use semantic chunking
- **Missing metadata context:** Chunks are semantically similar to the query but belong to the wrong document, date, or user. Fix: use metadata filtering
- **Top-k too small:** The right chunk exists but isn't in the top 5 retrieved results. Fix: increase top\_k at retrieval and reduce after reranking

**Resources:**

**1\. LangChain: Query Transformations (free)**

**Link:** [https://python.langchain.com/docs/how\_to/#query-analysis](https://python.langchain.com/docs/how_to/#query-analysis)

Covers query rewriting, step-back prompting, and HyDE

**2\. Pinecone: Improving Retrieval Quality (free)**

**Link:** [https://www.pinecone.io/learn/retrieval-augmented-generation/#retrieval-quality](https://www.pinecone.io/learn/retrieval-augmented-generation/#retrieval-quality)

Practical walkthrough of common failure modes with fixes

## 7\. Hallucination Reduction

RAG dramatically reduces hallucinations compared to a vanilla LLM, but it doesn't eliminate them

By supplying the model with retrieved facts at runtime, RAG anchors its responses to real sources rather than relying on training data alone, and the model's output can even cite those sources, increasing transparency and trust

But retrieval failures, bad chunks, and conflicting information can still cause the model to make things up

**Resources:**

**1\. Zep: Reducing LLM Hallucinations – A Developer's Guide (free)**

**Link:** [https://www.getzep.com/ai-agents/reducing-llm-hallucinations/](https://www.getzep.com/ai-agents/reducing-llm-hallucinations/)

Practical developer-focused guide covering prompt grounding strategies, chain-of-thought for factual tasks, and output verification patterns

**2\. Voiceflow: 5 Ways to Reduce LLM Hallucinations (free)**

**Link:** [https://www.voiceflow.com/blog/prevent-llm-hallucinations](https://www.voiceflow.com/blog/prevent-llm-hallucinations)

Good overview of the combined strategy: RAG + chain-of-thought + guardrails together outperform any single approach

What to focus on: Prompting the model to answer only from provided context (and say "I don't know" when the answer isn't there), adding a confidence threshold before surfacing responses, and always validating retrieval quality before blaming the LLM

## 8\. Citations and Grounding

A grounded RAG system doesn't just answer – it tells you where the answer came from. This is critical for user trust and for debugging

**Resources:**

**1\. Anthropic: Giving Claude Sources (docs, free)**

**Link:** [https://docs.anthropic.com/en/docs/build-with-claude/citations](https://docs.anthropic.com/en/docs/build-with-claude/citations)

Explained how to prompt Claude to produce cited responses with source references

**2\. LangChain: RAG with Sources (free)**

**Link:** [https://python.langchain.com/docs/how\_to/qa\_sources/](https://python.langchain.com/docs/how_to/qa_sources/)

Explained how to return source documents alongside answers in a LangChain RAG pipeline

**What to focus on:** Passing chunk metadata (source filename, page number, URL) into your prompt context, instructing the model to reference sources in its answer, and surfacing those sources in your UI or API response

## 9\. Your RAG Framework: LangChain or LlamaIndex

You don't need to build a RAG pipeline from scratch. Two frameworks dominate the space and are worth knowing:

LlamaIndex is optimized for putting search and indexing first it abstracts ingestion, chunking, embedding, and querying into a few lines of code, letting you build a working prototype in an afternoon

LangChain shines when your application looks more like an orchestration engine – it excels with multi-agent workflows, tool calling, and conditional chains that query multiple LLMs or external APIs before generating an answer

For Month 3, start with LlamaIndex for RAG. Move to LangChain when you hit Month 4's agents work

**Resources:**

**1\. LlamaIndex: Introduction to RAG (official docs, free)**

**Link:** [https://developers.llamaindex.ai/python/framework/understanding/rag/](https://developers.llamaindex.ai/python/framework/understanding/rag/)

Covers the five key stages of RAG: loading, indexing, storing, querying, and evaluating – and how LlamaIndex handles each one

**2\. LlamaIndex Starter Tutorial (official docs, free)**

**Link:** [https://developers.llamaindex.ai/python/framework/getting\_started/starter\_example/](https://developers.llamaindex.ai/python/framework/getting_started/starter_example/)

The official quickstart. Build a working RAG system in under 30 lines

**3\. LangChain: Build a RAG Agent (official docs, free)**

**Link:** [https://docs.langchain.com/oss/python/langchain/rag](https://docs.langchain.com/oss/python/langchain/rag)

Shows how to build a Q&A app over unstructured text using a RAG agent, from a 40-line minimal version up to a full retrieval pipeline with reranking

**Practice project:** Build a "chat with your docs" app. Ingest 10–20 PDF or text files (your own notes, a textbook chapter, product documentation – anything). Build a FastAPI endpoint that accepts a question, retrieves the top 5 most relevant chunks with reranking, and returns a cited answer from Claude or OpenAI. This is a real portfolio piece

## Month 3 Milestone

By the end of this month you should be able to:

- Explain what an embedding is and why similar text produces similar vectors
- Chunk any document intelligently using appropriate strategies
- Store and query embeddings in a vector database with metadata filtering
- Add a reranking step to improve retrieval quality
- Debug common retrieval failures systematically
- Build a complete end-to-end RAG pipeline using LlamaIndex or LangChain that ingests documents, retrieves relevant chunks, and returns grounded, cited answers

⏩------------------------------------------------------------------------⏪

## Month 4: Agents, Tools, Workflows, and Evals

Your goal this month: Build AI systems that can take sequences of actions autonomously, wire together multi-step workflows, and critically evaluate whether they're working

By the end you should be able to build a real agent from scratch, understand when agents are the wrong choice, and measure the performance of anything you build

This is where AI engineering gets genuinely complex. The skills from Month 4 are what separate junior AI engineers from people who can own an entire AI feature end to end

## 1\. Agent Loops

An agent is not magic, it's a surprisingly simple pattern

Think of agents as goal-driven systems that constantly cycle through observing, reasoning, and acting

This loop allows them to tackle tasks that go beyond simple questions and answers, moving into real automation, tool usage, and adapting on the fly

The "thinking" happens in the prompt, the "branching" is when the agent chooses between available tools, and the "doing" happens when we call external functions. Everything else is just plumbing

Once you internalize this, even the most complex agent frameworks become readable

**Resources:**

**1\. Anthropic: Building Effective Agents (official, free)**

**Link:** [https://www.anthropic.com/research/building-effective-agents](https://www.anthropic.com/research/building-effective-agents)

The single best piece of writing on agents in production. Read this before writing a single line of agent code

**2\. OpenAI: A Practical Guide to Building Agents (official PDF, free)**

**Link:** [https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)

OpenAI's complementary guide covering agent patterns, guardrails, and safety patterns in production

**3\. freeCodeCamp: The Open Source LLM Agent Handbook (free)**

**Link:** [https://www.freecodecamp.org/news/the-open-source-llm-agent-handbook/](https://www.freecodecamp.org/news/the-open-source-llm-agent-handbook/)

A comprehensive practical guide covering the agent loop, LangGraph, CrewAI, planning, memory, and tool use. Good for getting hands-on quickly

**4\. LangChain Academy: Introduction to LangGraph (free course)**

**Link:** [https://academy.langchain.com/courses/intro-to-langgraph](https://academy.langchain.com/courses/intro-to-langgraph)

The official free course for LangGraph, the most widely used agent orchestration framework. Covers state, memory, human-in-the-loop, and more

**What to focus on:** The perceive → plan → act → observe cycle, how the agent loop terminates, what happens when a tool call fails inside a loop, and why agents are just while loops with an LLM making the branching decisions

**Practice:** Build an agent from scratch without any framework – just the OpenAI or Anthropic API directly. Give it 3 tools, a goal, and a loop. This is the most valuable thing you can do to actually understand what frameworks are abstracting

## 2\. Tool Selection

Writing good tools is half the job. The descriptions for your tools and their parameters are the user manual for the LLM. If the manual is vague, the LLM will misuse the tool. Be painfully, relentlessly explicit

A poorly described tool will be called wrong, called at the wrong time, or ignored entirely. A well-described tool behaves predictably and gets selected correctly across a wide range of inputs

**Resources:**

**1\. OpenAI: Function Calling Best Practices (official docs, free)**

**Link:** [https://platform.openai.com/docs/guides/function-calling/best-practices](https://platform.openai.com/docs/guides/function-calling/best-practices)

The canonical guide to writing tool descriptions that work reliably, with naming conventions and parameter documentation patterns

**2\. Anthropic: Tool Use Best Practices (official docs, free)**

**Link:** [https://docs.anthropic.com/en/docs/build-with-claude/tool-use/implement-tool-use#best-practices-for-tool-definitions](https://docs.anthropic.com/en/docs/build-with-claude/tool-use/implement-tool-use#best-practices-for-tool-definitions)

Anthropic's equivalent. Pay particular attention to the guidance on when to let the model choose vs forcing a specific tool

**What to focus on:** Writing tool names that are self-explanatory verbs, writing descriptions that explain when to call the tool (not just what it does), keeping parameters minimal and well-typed, and designing tools with the LLM as the caller

**Beginner tip:** Test every tool description by asking yourself: "If I had no documentation and only this JSON schema, would I know exactly when and how to call this?" If not, it needs more work

## 3\. State Management

In LangGraph, state is a shared memory object that flows through the graph. It stores all the relevant information – messages, variables, intermediate results, and decision history – and is managed automatically throughout execution

Understanding state is the key to building agents that can handle multi-turn tasks, recover from failures, and hand off between components cleanly

**Resources:**

**1\. LangGraph Official Docs: State Management (free)**

**Link:** [https://langchain-ai.github.io/langgraph/concepts/low\_level/#state](https://langchain-ai.github.io/langgraph/concepts/low_level/#state)

The definitive reference. Covers state schemas, reducers, and how state flows through nodes and edges

**2\. DataCamp: LangGraph Agents Tutorial (free)**

**Link:** [https://www.datacamp.com/tutorial/langgraph-agents](https://www.datacamp.com/tutorial/langgraph-agents)

Covers the fundamentals of state, nodes, and edges with hands-on code, building up to stateful agents with persistent memory across sessions

**3\. Real Python: LangGraph in Python (free)**

**Link:** [https://realpython.com/langgraph-python/](https://realpython.com/langgraph-python/)

A thorough tutorial building a complete stateful LangGraph agent, with detailed explanations of the state graph and conditional edges

**What to focus on:** Defining state schemas with TypedDict, how reducers work for merging parallel updates, the difference between in-memory state and persisted checkpointing, and how human-in-the-loop pauses work by inspecting and modifying state mid-execution

## 4\. Retries and Failure Handling in Agents

Agents fail differently to regular LLM calls. A bad tool call mid-loop can corrupt state, cause infinite loops, or silently produce wrong answers. You need explicit strategies for all of these

**Resources:**

**1\. LangGraph: Error Handling and Retries (official docs, free)**

**Link:** [https://langchain-ai.github.io/langgraph/how-tos/autofill-tool-errors/](https://langchain-ai.github.io/langgraph/how-tos/autofill-tool-errors/)

Explained how to add automatic error handling and retry logic at the tool node level in LangGraph

**2\. OpenAI Practical Agents Guide: Guardrails section (free)**

**Link:** [https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)

Covers guardrails as a layered defense, combining LLM-based checks, rules-based filters like regex, and moderation APIs to vet both inputs and outputs at every stage of the agent loop

**What to focus on:** Maximum iteration limits to prevent infinite loops, per-tool retry with exponential backoff, catching and logging exceptions at the tool execution layer without crashing the agent, and when to surface a failure to the user vs retry silently

## 5\. When NOT to Use Agents

This is one of the most important and most overlooked skills in AI engineering. Agents are exciting but they're also slow, expensive, unpredictable, and hard to debug. Knowing when to reach for something simpler is a sign of good judgment

Anthropic recommends finding the simplest solution possible and only increasing complexity when needed – this might mean not building agentic systems at all

Agentic systems trade latency and cost for better task performance, and you should carefully consider when this tradeoff makes sense

**The decision framework is:**

- Use a single LLM call if the task can be solved in one prompt with the right context
- Use a workflow if the steps are fixed and predictable
- Use an agent only if the number of steps is genuinely unpredictable and requires dynamic decision-making

**Resources:**

**1\. Anthropic: Building effective agents, when to use agents (official, free)**

**Link:** [https://www.anthropic.com/research/building-effective-agents](https://www.anthropic.com/research/building-effective-agents)

The most authoritative answer to this question, straight from the team that builds the models

**2\. Simon Willison: Designing Agentic Loops (free)**

**Link:** [https://simonwillison.net/2025/Sep/30/designing-agentic-loops/](https://simonwillison.net/2025/Sep/30/designing-agentic-loops/)

A senior engineer's practical take on when agent complexity is justified and how to think about agentic loop design

**What to memorize:** A chain of 3 fixed LLM calls will always be faster, cheaper, and more debuggable than an agent that could make 3 calls. Reserve agents for genuinely open-ended tasks

## 6\. Multi-Step Workflows

Between "single prompt" and "full agent" there is a vast productive middle ground: workflows. Workflows are ideal when the task can be cleanly decomposed into fixed subtasks – trading off latency for higher accuracy by making each individual LLM call an easier, more focused task

Common patterns include prompt chaining (output of one call is input to the next), routing (classify input and send to specialized handlers), parallelization (run multiple calls simultaneously and aggregate), and orchestrator-subagent (one LLM plans, others execute)

**Resources:**

**1\. Anthropic: Workflow Patterns (official, free)**

**Link:** [https://www.anthropic.com/research/building-effective-agents#workflow-patterns](https://www.anthropic.com/research/building-effective-agents#workflow-patterns)

Covers all the main patterns with diagrams and code examples. The parallelization and orchestration sections are particularly useful

**2\. LangGraph: Multi-Agent Networks (official docs, free)**

**Link:** [https://langchain-ai.github.io/langgraph/concepts/multi\_agent/](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)

Explained how to wire multiple agents together as a network, with supervisor and handoff patterns

**Practice project:** Build a 3-step content pipeline:

Step 1 – an LLM extracts key facts from an article

Step 2 – another LLM call uses those facts to generate a tweet, a LinkedIn post, and a summary in parallel

Step 3 – a final LLM call scores all three for quality and picks the best

No agent required, pure workflow

## 7\. Evaluation Harnesses

Evals are how you know if your AI system is actually working — not just on the examples you tested by hand, but systematically across hundreds of inputs

AI agents are powerful but complex to deploy because their probabilistic, multi-step behavior introduces many points of failure

Different parts of an agent – the LLMs, tools, retrievers, and workflows – each need their own evaluation approach

**Resources:**

**1\. DeepEval (open source, free)**

**Link:** [https://deepeval.com/docs/getting-started](https://deepeval.com/docs/getting-started)

An open-source LLM evaluation framework inspired by pytest. Write test cases with inputs and expected outputs, run them with 50+ built-in metrics including hallucination, answer relevancy, and factual consistency, and catch regressions between versions

**2\.** [Promptfoo (open source, free)](https://github.com/promptfoo/promptfoo)

**Link:** [https://github.com/promptfoo/promptfoo](https://github.com/promptfoo/promptfoo)

A CLI and library for testing and evaluating LLM apps with automated test suites. Supports side-by-side comparison of multiple prompts across multiple models, CI/CD integration, and red teaming for security vulnerabilities

**3\. LangSmith (free tier)**

**Link:** [https://smith.langchain.com/](https://smith.langchain.com/)

Tracing, debugging, and evaluation for LangChain and LangGraph apps. The free tier is generous and the tracing UI makes debugging agent loops dramatically easier

**4\. Ragas (open source, free)**

**Link:** [https://docs.ragas.io/](https://docs.ragas.io/)

Specialized evaluation framework for RAG pipelines. Measures faithfulness, answer relevancy, context precision, and context recall. Essential if you're evaluating RAG systems from Month 3

**What to focus on:** Building a golden test set of 20-50 representative inputs with expected outputs or rubrics, writing eval functions that score outputs deterministically (string match, JSON schema validation) or with LLM-as-judge, and running evals automatically when you change a prompt or swap a model

**Critical mindset:** Evals are not optional polish. Every prompt change, model swap, or retrieval tweak you make without running evals is a gamble. The engineers who ship reliable AI products run evals constantly

## 8\. Task Success Metrics

Beyond automated evals, you need metrics that tell you whether your agent is accomplishing its actual goal

**Resources:**

**1\. Hamel Husain: Your AI Product Needs Evals (free)**

**Link:** [https://hamel.dev/blog/posts/evals/](https://hamel.dev/blog/posts/evals/)

One of the most practical pieces written on building eval pipelines for real production AI systems, by someone who has done it at scale

**2\. OpenAI Evals Framework (open source, free)**

**Link:** [https://github.com/openai/evals](https://github.com/openai/evals)

OpenAI's own evaluation framework, with a large library of community-contributed eval patterns you can adapt

**What to focus on:** The difference between process metrics (did the agent call the right tool?) and outcome metrics (did the task succeed?), defining clear success criteria before building anything, and using LLM-as-judge for evaluation of outputs that resist exact matching (like long-form answers or multi-step reasoning traces)

**Practice project:** Take your RAG pipeline from Month 3 and build a proper eval harness around it. Create 30 question-answer pairs from your documents, run them through your pipeline, and score each answer for relevance, faithfulness, and completeness using DeepEval. Then change one thing (chunk size, model, top-k) and re-run to see if it improved

## Month 4 Milestone

By the end of this month you should be able to:

- Explain what an agent loop is and implement one from scratch without a framework
- Write tool descriptions that get selected correctly and reliably
- Manage agent state properly using LangGraph or equivalent
- Handle failures inside agent loops without crashing
- Decide confidently whether a task needs an agent, a workflow, or a single prompt
- Build multi-step workflows that chain, route, and parallelize LLM calls
- Write automated evals that catch regressions when you change prompts or models
- Define and measure task success metrics for any AI system you build

⏩------------------------------------------------------------------------⏪

## Month 5: Deployment, Product Thinking, and Reliability

Your goal this month: Take everything you've built and make it production-ready

By the end you should be able to deploy an AI app that handles real users, real traffic, and real failures without falling apart at 2am

This is where most AI engineers stall. They can build a great demo but can't ship a product that survives contact with the real world

The skills here are what companies actually pay for: reliability, security, cost control, and the ability to keep things running when something inevitably breaks

## 1\. FastAPI Production Patterns

You already know how to build a FastAPI app from Month 1. Now you need to make it survive production traffic

The difference between dev and prod is brutal. A single uvicorn process with --reload is fine for building. In production it becomes the bottleneck the moment real traffic arrives

What you actually need: multi-worker ASGI configuration, proper error handling middleware, health check endpoints, and CORS policies

**Resources:**

**1\. FastAPI Deployment Docs (official, free)**

**Link:** [https://fastapi.tiangolo.com/deployment/](https://fastapi.tiangolo.com/deployment/)

The official guide covering Uvicorn workers, Gunicorn, and Docker deployment. Start here before anything else

**2\. FastAPI Production Deployment Guide (CYS Docs, free)**

**Link:** [https://craftyourstartup.com/cys-docs/fastapi-production-deployment/](https://craftyourstartup.com/cys-docs/fastapi-production-deployment/)

Comprehensive production patterns: Gunicorn config, Nginx reverse proxy, health checks, rate limiting. Includes real config files you can adapt

**3\. FastAPI Best Practices for Production (FastLaunchAPI, free)**

**Link:** [https://fastlaunchapi.dev/blog/fastapi-best-practices-production-2026](https://fastlaunchapi.dev/blog/fastapi-best-practices-production-2026)

Covers async database pooling, Redis caching, JWT auth, and background tasks. Production-tested patterns from a real template used by 100+ developers

**What to focus on:** Running Gunicorn with Uvicorn workers (not bare Uvicorn), setting up health check endpoints, adding CORS middleware, implementing proper async database sessions, and using background tasks for anything that doesn't need to block the response

## 2\. Docker

Docker is how you stop saying "it works on my machine" and start shipping consistent deployments

If you're building AI apps, Docker solves dependency conflicts, ensures consistent environments, and makes scaling straightforward

You don't need to become a Docker expert. You need to be able to containerize your FastAPI + LLM app and deploy it anywhere

**Resources:**

**1\. Docker Official Getting Started Guide (free)**

**Link:** [https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)

The canonical starting point. Covers images, containers, Dockerfiles, and Docker Compose

**2\. freeCodeCamp: How to Build and Deploy a Multi-Agent AI System with Python and Docker (free)**

**Link:** [https://www.freecodecamp.org/news/build-and-deploy-multi-agent-ai-with-python-and-docker/](https://www.freecodecamp.org/news/build-and-deploy-multi-agent-ai-with-python-and-docker/)

Practical end-to-end tutorial building a real multi-agent pipeline with Docker Compose. Covers separation of concerns, cron scheduling, and security considerations

**3\. DataCamp: Deploy LLM Applications Using Docker (free)**

**Link:** [https://www.datacamp.com/tutorial/deploy-llm-applications-using-docker](https://www.datacamp.com/tutorial/deploy-llm-applications-using-docker)

Step-by-step guide specifically for LLM apps with RAG pipelines. Covers Dockerfile creation, environment management, and deployment

**4\. Docker Containerization for LLM Apps (ApXML, free)**

**Link:** [https://apxml.com/courses/python-llm-workflows/chapter-10-deployment-operational-practices/containerization-docker-llm-apps](https://apxml.com/courses/python-llm-workflows/chapter-10-deployment-operational-practices/containerization-docker-llm-apps)

Covers base image selection, dependency management, multi-stage builds, and Docker Compose for multi-service LLM deployments

**What to focus on:** Writing a Dockerfile for a Python/FastAPI app, using multi-stage builds to keep images small, Docker Compose for multi-service setups (app + database + Redis), environment variables for secrets, and .dockerignore to avoid leaking sensitive files

**Practice project:** Containerize your RAG app from Month 3. Create a docker-compose.yml that runs your FastAPI app, a vector database (Chroma or Qdrant), and Redis for caching. Deploy it so that docker compose up starts everything

## 3\. Background Jobs and Queues

LLM calls are slow. If a user asks your app to process a document and you make them wait 30 seconds for a response, they'll leave

Background jobs let you accept the request immediately, process it async, and notify the user when it's done

**Resources:**

**1\. Celery Official Getting Started Guide (free)**

**Link:** [https://docs.celeryq.dev/en/stable/getting-started/introduction.html](https://docs.celeryq.dev/en/stable/getting-started/introduction.html)

The standard Python task queue. Covers basic setup, task definition, and worker management

**2\. FastAPI Background Tasks Docs (official, free)**

**Link:** [https://fastapi.tiangolo.com/tutorial/background-tasks/](https://fastapi.tiangolo.com/tutorial/background-tasks/)

Built-in lightweight background tasks for simple use cases. Use this for quick fire-and-forget tasks, Celery for anything heavier

What to focus on: Understanding when to use FastAPI's built-in BackgroundTasks vs a proper task queue like Celery, setting up Redis as a message broker, handling task failures and retries, and returning job status to the user

## 4\. Auth and API Key Security

If your AI app has an API, it needs authentication. Without it, anyone can use your endpoints, burn through your LLM credits, and you'll wake up to a $5,000 bill

**Resources:**

**1\. FastAPI Security Docs (official, free)**

**Link:** [https://fastapi.tiangolo.com/tutorial/security/](https://fastapi.tiangolo.com/tutorial/security/)

Covers OAuth2, JWT tokens, API keys, and dependency-based auth patterns. The official reference, work through the full tutorial

**2\. OWASP API Security Top 10 (free)**

**Link:** [https://owasp.org/API-Security/](https://owasp.org/API-Security/)

The authoritative list of API security risks. Understand broken authentication, injection, and mass assignment before shipping anything

**3\. Auth0: API Auth Best Practices (free)**

**Link:** [https://auth0.com/docs/get-started/authentication-and-authorization](https://auth0.com/docs/get-started/authentication-and-authorization)

Practical guide to implementing authentication and authorization in APIs

**What to focus on:** JWT tokens for user auth, API key management for service-to-service communication, rate limiting per user/key, never storing secrets in code (use environment variables), and understanding the difference between authentication (who are you) and authorization (what can you do)

## 5\. Logging and Observability

In production, if you can't see what's happening, you can't fix what's broken

LLM apps have a unique challenge: the model can return a 200 status code and still produce a useless or hallucinated answer. Traditional monitoring doesn't catch this. You need LLM-specific observability

**Resources:**

**1\. Langfuse (open source, free tier)**

**Link:** [https://langfuse.com/docs/observability/overview](https://langfuse.com/docs/observability/overview)

Open-source LLM observability platform. Traces every request: prompt sent, response received, token usage, latency, tool calls. Supports prompt versioning, evaluation, and LLM-as-judge scoring. Integrates with OpenAI, Anthropic, LangChain, LlamaIndex

**2\. LangSmith (free tier)**

**Link:** [https://smith.langchain.com/](https://smith.langchain.com/)

From the LangChain team. If you're using LangChain/LangGraph, setup is one environment variable. Tracing, debugging, monitoring dashboards, and online evals. The free tier is generous for development and small-scale production

**3\. Python Structlog (free)**

**Link:** [https://www.structlog.org/](https://www.structlog.org/)

Structured logging for Python. Produces JSON logs that are actually searchable and parseable. Far better than print() or basic logging for production apps

**What to focus on:** Tracing every LLM call (input prompt, output, tokens, latency, cost), structured logging with JSON output, setting up dashboards that show request volume, error rates, and cost per day, and alerting when something breaks or costs spike

## 6\. Prompt and Version Management

In production, your prompts are code. They need version control, testing, and rollback ability

Changing a prompt in production without tracking what you changed is how you break things and can't figure out why

**Resources:**

**1\. Langfuse Prompt Management (free)**

**Link:** [https://langfuse.com/docs/prompts](https://langfuse.com/docs/prompts)

Centralized prompt versioning with a built-in playground for testing. Version control your prompts separately from your application code. Deploy prompt changes without redeploying your app

**2\. Anthropic Prompt Management Best Practices (free)**

**Link:** [https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)

Best practices for organizing, iterating, and managing prompts at scale

What to focus on: Storing prompts outside your application code, versioning every prompt change, A/B testing prompt variants in production, and having a rollback strategy when a new prompt performs worse

## 7\. Cost Monitoring and Rate Limits

LLM APIs charge per token. Without cost controls, a traffic spike or a bug in your prompt can burn through hundreds of dollars in minutes

**Resources:**

**1\. OpenAI Usage Dashboard (official)**

**Link:** [https://platform.openai.com/usage](https://platform.openai.com/usage)

Track spending by model, by day, and set usage limits

**2\. Anthropic Usage Dashboard (official)**

**Link:** [https://console.anthropic.com/Same](https://console.anthropic.com/Same) for Claude API usage

**3\. Helicone (free tier)**

**Link:** [https://www.helicone.ai/](https://www.helicone.ai/)

Proxy-based observability that captures every LLM call with automatic cost tracking. One line of code to set up: just change your base URL

**4\. LiteLLM (open source, free)**

**Link:** [https://github.com/BerriAI/litellm](https://github.com/BerriAI/litellm)

Unified interface for 100+ LLM providers. Includes budget management, rate limiting, and spend tracking across providers

**What to focus on:** Setting hard spending limits per day/month, implementing per-user rate limits in your API, using cheaper models for simple tasks (don't use GPT-4/Opus for everything), caching repeated identical requests with Redis, and monitoring cost per request to catch expensive prompts early

## 8\. Caching

If 20% of your users ask similar questions, you're paying for the same LLM call 20 times

Caching is the simplest way to reduce costs and latency simultaneously

**Resources:**

**1\. Redis Official Docs (free)**

**Link:** [https://redis.io/docs/](https://redis.io/docs/)

The standard in-memory data store. Fast, simple, and works perfectly for LLM response caching

**2\. GPTCache (open source, free)**

**Link:** [https://github.com/zilliztech/GPTCache](https://github.com/zilliztech/GPTCache)

Semantic caching specifically designed for LLM applications. Uses embedding similarity to find cached responses for semantically similar (not just identical) queries

**What to focus on:** Exact-match caching for identical prompts, semantic caching for similar queries, cache invalidation strategies (TTL-based is simplest), and measuring cache hit rates to understand real cost savings

## Month 5 Milestone

By the end of this month you should be able to:

- Deploy a FastAPI + LLM app in Docker with proper production configuration
- Handle long-running tasks with background jobs and queues
- Secure your API with auth, rate limits, and API key management
- Trace and debug LLM calls using Langfuse or LangSmith
- Manage prompts with version control and rollback capability
- Monitor costs in real time and set spending limits
- Cache LLM responses to reduce latency and cost

⏩------------------------------------------------------------------------⏪

## Month 6: Specialize and Become Hireable

These knowledge and skills you gained can be applied in three directions (for sure it's only those which I see)

You need to choose one of them and focus on practice

Although everything mentioned above is also best learned purely through practice

## Direction 1: AI Product Engineer

Best if you want startup jobs fast

This is the most common path. You build AI-powered products that real users interact with

You already have most of the skills from Months 1-5. Now go deeper on the product side

Focus on:

- LLM apps
- RAG
- agents
- deployment
- product UX

**What to learn this month:**

## 1\. End-to-End Product Building

Stop building tutorials. Build products people can use

Resources:

**1\. Vercel AI SDK (free)**

**Link:** [https://sdk.vercel.ai/docs](https://sdk.vercel.ai/docs)

The fastest way to build AI-powered UIs with streaming support. React, Next.js, and Vue integrations with built-in streaming UI components

**2\. Streamlit (free)**

**Link:** [https://docs.streamlit.io/](https://docs.streamlit.io/)

Build data apps and AI demos in pure Python. Ideal for internal tools and MVPs, not production-scale UIs

**3\. Gradio (free)**

**Link:** [https://www.gradio.app/docsQuick](https://www.gradio.app/docsQuick) ML/AI interfaces with minimal code. Especially good for demoing models and building prototypes

What to focus on: Building 2-3 complete projects this month that you can demo. A "chat with your docs" app, an AI-powered internal tool, or an agent that automates a real workflow. Ship them. Put them on GitHub. Deploy them somewhere people can try them

## 2\. Product UX for AI

AI products fail when the UX doesn't account for the model's limitations

**Resources:**

**1\. Google: People + AI Guidebook (free)**

**Link:** [https://pair.withgoogle.com/guidebook/](https://pair.withgoogle.com/guidebook/)

The best resource on designing human-AI interaction. Covers setting expectations, handling errors, and building trust

**2\. Nielsen Norman Group: AI UX Guidelines (free)**

**Link:** [https://www.nngroup.com/topic/artificial-intelligence/](https://www.nngroup.com/topic/artificial-intelligence/)

Research-backed guidelines for AI interfaces

What to focus on: How to handle loading states with streaming, what to show when the model is wrong, how to let users give feedback, and designing for the fact that AI output is probabilistic – it will sometimes be wrong

## Direction 2: Applied ML / LLM Engineer

Best if you want deeper technical roles

This direction is for engineers who want to go beyond API calls and understand what's happening under the hood

**Focus on:**

- fine-tuning
- when to fine-tune vs prompt
- evaluation
- inference optimization
- open-source models
- training pipelines

**What to learn this month:**

## 1\. When to Fine-tune vs Prompt Engineer

The most important decision in applied ML: do you need to change the model, or just change how you talk to it?

**Resources:**

**1\. Google ML Crash Course: Fine-tuning, Distillation, and Prompt Engineering (free)**

**Link:** [https://developers.google.com/machine-learning/crash-course/llm/tuning](https://developers.google.com/machine-learning/crash-course/llm/tuning)

The clearest explanation of the three approaches and when to use each

**2\. Codecademy: Prompt Engineering vs Fine-Tuning (free)**

**Link:** [https://www.codecademy.com/article/prompt-engineering-vs-fine-tuning](https://www.codecademy.com/article/prompt-engineering-vs-fine-tuning)

Practical decision framework with clear use cases for each approach

**3\. IBM: RAG vs Fine-Tuning vs Prompt Engineering (free)**

**Link:** [https://www.ibm.com/think/topics/rag-vs-fine-tuning-vs-prompt-engineering](https://www.ibm.com/think/topics/rag-vs-fine-tuning-vs-prompt-engineering)

Covers the complete decision space including when to combine approaches

Decision framework to memorize: Start with prompt engineering (cheapest, fastest) Add RAG if the model needs access to specific data Fine-tune only when prompting + RAG can't achieve the required quality, consistency, or latency

## 2\. Fine-tuning in Practice

When you do need to fine-tune, here's how

**Resources:**

**1\. OpenAI Fine-tuning Guide (official, free)**

**Link:** [https://platform.openai.com/docs/guides/fine-tuning](https://platform.openai.com/docs/guides/fine-tuning)

The easiest way to start fine-tuning. Upload a JSONL dataset, run a job, get a custom model. Good for learning the workflow even if you later move to open-source models

**2\. HuggingFace Transformers Fine-tuning Tutorial (free)**

**Link:** [https://huggingface.co/docs/transformers/training](https://huggingface.co/docs/transformers/training)

The standard library for working with open-source models. Covers training, evaluation, and model saving

**3\. Unsloth (open source, free)**

**Link:** [https://github.com/unslothai/unsloth](https://github.com/unslothai/unsloth)

2x faster fine-tuning with 80% less memory. Supports LoRA and QLoRA out of the box. The fastest path to fine-tuning open-source models on consumer hardware

**4\. LLaMA-Factory (open source, free)**

**Link:** [https://github.com/hiyouga/LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory)

Unified framework for fine-tuning 100+ LLMs. Includes a web UI for no-code fine-tuning. Supports LoRA, QLoRA, full fine-tuning, RLHF, and DPO

**What to focus on:** Preparing training datasets (JSONL format), understanding LoRA and QLoRA (parameter-efficient fine-tuning), running a fine-tuning job on OpenAI or with HuggingFace, evaluating the fine-tuned model against the base model, and knowing when fine-tuning isn't worth the cost

## 3\. Open-Source Models

Not everything needs to go through OpenAI or Anthropic. Open-source models give you full control, no API costs, and the ability to run locally

**Resources:**

**1\. Ollama (free)**

**Link:** [https://ollama.ai/](https://ollama.ai/)

Run open-source LLMs locally with one command. Supports Llama, Mistral, Gemma, and dozens of others. The fastest way to experiment with open-source models

**2\. HuggingFace Model Hub (free)**

**Link:** [https://huggingface.co/models](https://huggingface.co/models)

The largest repository of open-source models. Browse, download, and deploy models for any task

**3\. vLLM (open source, free)**

**Link:** [https://github.com/vllm-project/vllm](https://github.com/vllm-project/vllm)

High-throughput LLM inference engine. 2-4x faster than naive HuggingFace serving. The standard for production serving of open-source models

**What to focus on:** Running models locally with Ollama for testing, understanding quantization (GGUF, GPTQ, AWQ) and why it matters for deployment, benchmarking open-source models against API models for your use case, and serving models in production with vLLM

## 4\. Inference Optimization

Making models run faster and cheaper in production

**Resources:**

**1\. HuggingFace: Optimizing LLM Inference (free)**

**Link:** [https://huggingface.co/docs/transformers/llm\_optims](https://huggingface.co/docs/transformers/llm_optims)

Covers KV-cache optimization, quantization, and batching strategies

**2\. NVIDIA TensorRT-LLM (free)**

**Link:** [https://github.com/NVIDIA/TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM)

Maximum inference performance on NVIDIA GPUs. Used by most production LLM serving at scale

**What to focus on:** Batching strategies for throughput, quantization for reducing memory and cost, KV-cache optimization for faster generation, and choosing the right hardware for your inference workload

## Direction 3: AI Automation Engineer

Best if you want to build for businesses immediately

This direction is about automating real business workflows with AI. Less about building products, more about solving operational problems

**Focus on:**

- workflow orchestration
- business process automation
- multi-tool systems
- CRM, docs, email, support, ops use cases

**What to learn this month:**

## 1\. Workflow Orchestration

Real business automation is almost never one LLM call. It's chains of actions across multiple systems

**Resources:**

**1\. n8n (open source, free to self-host)**

**Link:** [https://docs.n8n.io/](https://docs.n8n.io/)

Visual workflow automation with AI nodes. Connect LLMs to 400+ integrations (Slack, Gmail, Notion, CRMs, etc.). The best no-code/low-code option for AI automation

**2\. LangGraph: Multi-Agent Workflows (free)**

**Link:** [https://langchain-ai.github.io/langgraph/concepts/multi\_agent/](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)

Code-first orchestration for complex multi-agent systems. When n8n isn't enough and you need full programmatic control

**3\. Temporal (open source, free)**

**Link:** [https://docs.temporal.io/](https://docs.temporal.io/)

Durable workflow engine for long-running, fault-tolerant processes. When your automation needs to survive crashes, retries, and timeouts

**What to focus on:** Designing workflows that handle failures gracefully, connecting AI to real business tools (email, CRM, databases, spreadsheets), building human-in-the-loop approval steps, and logging every automated action for audit trails

## 2\. Business Process Automation

The money in AI automation is in solving specific, expensive business problems

**Resources:**

**1\. Zapier AI Actions (free tier)**

**Link:** [https://zapier.com/ai](https://zapier.com/ai)

Connect AI to 6,000+ apps without code. Good for prototyping automations before building custom solutions

**2\. Make (Integromat) (free tier)**

**Link:** [https://www.make.com/](https://www.make.com/)

Visual automation platform with advanced logic and AI integrations. More powerful than Zapier for complex workflows

**What to focus on:** Identifying the highest-ROI automation targets (usually tasks that are repetitive, time-consuming, and rules-based), building automations that augment humans rather than replace them, and measuring the actual time and money saved

## 3\. CRM, Docs, Email, Support Automation

The most common and most valuable AI automation use cases

**Resources:**

**1\. OpenAI Cookbook: AI-Powered Email Processing (free)**

**Link:** [https://github.com/openai/openai-cookbook](https://github.com/openai/openai-cookbook)

Patterns for classifying, routing, and responding to emails with AI

**2\. LangChain: Document Processing Pipelines (free)**

**Link:** [https://python.langchain.com/docs/how\_to/#document-loaders](https://python.langchain.com/docs/how_to/#document-loaders)

Ingesting and processing documents from 80+ sources

**What to focus on:** Building an AI-powered email classifier and auto-responder, creating a document processing pipeline that extracts structured data, building a support chatbot that uses RAG over your knowledge base, and integrating AI into existing CRM workflows (HubSpot, Salesforce, etc.)

**Practice project for Direction 3:** Build an end-to-end lead qualification system. It should:

Scrape or import leads from a source (CSV, API, or form)

Use an LLM to research each lead (company info, fit assessment)

Score and rank leads based on your ICP

Draft personalized outreach messages

Log everything to a spreadsheet or CRM This is a real, sellable automation that businesses actually pay for

⏩------------------------------------------------------------------------⏪

# CONCLUSION

What you can expect after these 6 months???

I'm going to be honest with you, without some money's mountains

This roadmap will not make you a senior AI engineer in 6 months

But it will make you someone who can build, ship, and deploy real AI systems that solve real problems

And right now, that is exactly what the market is paying for

The demand for AI engineers is not slowing down. Job postings grew 25% year-over-year

PwC found a 56% wage premium for roles that require AI skills vs the same roles without

Only 1% of companies are considered "AI mature" which means 99% still need help. The US Bureau of Labor Statistics projects 26% job growth through 2034

These are not hype numbers. That's the real numbers based on analytics (took from Claude kek)

If you go full-time in the US:

**Junior AI engineers** start at $90,000-$130,000

**Mid-level (3-5 years)** sits at $155,000-$200,000

**Senior roles** go $195,000-$350,000+

According to Glassdoor (March 2026), the average is **$184,757**

The mid-level band is growing the fastest at 9.2% year-over-year because companies desperately need people who can ship production AI without constant supervision

If freelance is more your thing:

**AI agent development** goes for $175-$300/hour

**RAG implementation** $150-$250/hour

**LLM integration** $125-$200/hour

One developer on Reddit built a document summarization tool for a legal firm in two weeks and made $8,000. A freelancer billing 25 hours/week at $150/hour pulls $195,000/year

And if you go the consulting route, which is what I talked about in my earlier post, you can charge:

$300-$5,000 to set up an **AI agent for a business**

$500-$2,000/month for **AI content management**

$1,000-$4,000 to **automate customer support**

$500-$2,000 for **cold outreach setup**

The service spectrum is even wider but once you master the skills from this roadmap, you are already a demanded specialist in 2026

These are real numbers from real people doing real work

Now here is what I actually want you to take away from all of this:

Pick one project from each month and build it. Not read about it. Not watch a tutorial. Build it, break it, fix it, deploy it, put it on GitHub. The engineers who get hired are the ones who show what they've built, not what they've studied

Start sharing what you learn. Write about it on X, LinkedIn, anywhere. Teaching is the fastest way to learn and it builds your reputation at the same time. The best opportunities I've seen come from people who were visible, not from people who applied to 500 job listings

And please don't wait until you feel ready. You will never feel ready. The gap between "I'm learning" and "I'm building" is where most people get stuck forever

Start applying, start freelancing, start offering services the moment you have working projects. Even if they're not perfect. The market doesn't reward perfection. It rewards people who can ship

6 months is enough to change everything if you actually put in the work

And I really believe each of you reading this can do it

Just never stop building and never stop learning

Hope this was useful for you my fam ❤️