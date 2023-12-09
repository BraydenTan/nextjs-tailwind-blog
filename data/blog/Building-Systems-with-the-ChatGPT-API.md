---
title: 'Building Systems with the ChatGPT API'
date: '2023/11/15'
lastmod: '2023/11/15'
tags: [OpenAI, Python, LLM]
draft: false
summary: Andrew Ng and Isa Fulford's released great course called "Building Systems with the ChatGPT API" on DeepLearning.AI site.'
images: https://elasticbeanstalk-ap-southeast-1-733447040549.s3.ap-southeast-1.amazonaws.com/blog/Screenshot+2023-11-15+at+5.04.21%E2%80%AFPM.png
authors: ['default']
layout: PostLayout
---

# Building Systems with the ChatGPT API

Andrew Ng and Isa Fulford's released great course called ["Building Systems with the ChatGPT API"(https://learn.deeplearning.ai/chatgpt-building-system/lesson/1/introduction)，on DeepLearning.AI site.

I've followed on-screen instructions to re-create their practical Jupyter notebooks and sharing the my note and code here .

- Language Models, the Chat Format and Tokens;
- Classification;
- Moderation;
- Chain of Thoughts;
- Chaining Prompts;
- Check Outputs;
- Build an End-to-End System;
- Evaluation - Part 1;
- Evaluation - Part 2.

## Comprehensive Guide to AIGC and OpenAI's ChatGPT API

This guide is a deep dive into Artificial Intelligence Generated Content (AIGC), focusing on Language Models and their practical implementation using OpenAI's ChatGPT API, as demonstrated in a Jupyter notebook.

### Part 1: Understanding AIGC

_Language Models and the Chat Format_

- How Language Models Work:
  - Utilizing Supervised Learning, these models are trained to predict the next word in a sequence.
  - Prompt-based AI is a powerful approach, allowing quick and efficient model utilization.
- Types of Language Models:
  - Base LLMs predict the next word based on training data.
  - Instruction Tuned LLMs (like ChatGPT) follow input instructions more accurately.
- From Base LLM to Instruction Tuned LLM:
  - Training on large datasets and fine-tuning with examples that follow specific instructions.
  - Using human feedback to improve the model’s outputs.

_Tokens_

- Tokens represent words or parts of words.
- The tokenization process can vary based on word frequency and model design.

_System, User, and Assistant Messages_

- Different roles are defined for each entity interacting with the LLM.

_Additional Concepts_

- Classification, Moderation, Prompt Injections, and Chain of Thought Reasoning are essential in shaping the interaction with LLMs.

### Part 2: Practical Application with OpenAI's ChatGPT API

_Setting Up the Environment_
The Jupyter notebook begins with the setup required for using the OpenAI API, particularly focusing on integration with Azure's OpenAI services.

```python3
import openai
import os

# Define Azure OpenAI endpoint parameters
openai.api_type = "azure"
openai.api_version = "2023-05-15"
openai.api_base = os.getenv("OPENAI_API_BASE")
openai.api_key = os.getenv("OPENAI_API_KEY")
aoai_deployment = os.getenv("OPENAI_API_DEPLOY")

```

_Helper Functions for API Interaction_

- Basic API Call Function
- A function get_completion simplifies the process of sending prompts and receiving responses.

```python3
def get_completion(prompt, engine=aoai_deployment):
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        engine=engine,
        messages=messages,
        temperature=0,
    )
    return response.choices[0].message["content"]

```
