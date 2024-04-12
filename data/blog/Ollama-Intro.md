---
title: 'Introduce Ollama'
date: '2024/11/15'
lastmod: '2024/11/15'
tags: [Ollama, LLM]
draft: false
summary: Introduce Ollama
images: https://ollama.com/public/blog/embedding-models.png
authors: ['default']
layout: PostLayout
---

# Ollama Introduce
Ollama is a user-friendly interface designed for running large language models (LLMs) locally, specifically on MacOS and Linux, with Windows support on the horizon. It is a valuable tool for researchers, developers, and anyone who wants to experiment with language models. Ollama supports a wide range of models, including Lama 2, Lama 2 uncensored, and the newly released Mistal 7B, among others 1.

**Link related Ollama**
- Project link:[OllamaGithub](https://github.com/ollama/ollama)  
- Official link:[OllamaWebsite](https://ollama.com/)
- Model Library:[OllamaLibrary](https://ollama.com/library)
- Logo:
<p align="center">
  <img src="https://ollama.com/public/ollama.png" alt="Image" />
</p>

**OpenAI compatibility**
![Logo](https://ollama.com/public/blog/openai.png)
Ollama's integration with the OpenAI Chat Completions API, allowing for enhanced tooling and application usage locally. It provides instructions on setting up and using Ollama with the OpenAI API through cURL, Python, and JavaScript libraries. 
For more detail Please refer below article
- OpenAI compatibility:[OpenAI compatibility](https://ollama.com/blog/openai-compatibility)

**Install Ollama**
To install Ollama, please visit the official website's download page: [OllamaWebsite](https://ollama.com/download) Here, you can select the appropriate version based on your operating system. Currently, Ollama supports macOS 11 Big Sur or later versions.

## Commanad for Ollama

```linux
After installation, Ollama also serves as a command. You can interact with the model through commands.

Command list:
ollama run llama2: Start Ollama in local
ollama list: Displays a list of models.
ollama show: Displays information about a model.
ollama pull: Pulls /Download a model.
ollama push: Pushes a model.
ollama cp: Copies a model.
ollama rm: Deletes a model.
ollama run: Runs a model.
--exp: ollama run llama2
```
**Ollama also supports serving Ollama as a service in a network environment. In macOS:**
```linux
OLLAMA_HOST=0.0.0.0:11434 ollama serve
```

In addition to Llama2, Ollama also supports other open-source models, as shown below:

<p align="center">
  <img src="/static/images/c1e12300dcd04b88a4f9f348ee6758b4.png" alt="Image" />
</p>

How to access your Ollama models using Langchain

If you want to access your Ollama models using Langchain, you can use the following code:

```python
from langchain_community.llms import Ollama
from langchain.chains import RetrievalQA

prompt = "What is the difference between an adverb and an adjective?"
llm = Ollama(model="mistral")
qa = RetrievalQA.from_chain_type(
    llm=llm,
    chain_type="stuff",
    retriever=retriever,
    return_source_documents=True,
)
response = qa(prompt)

```

**How to create your own models in Ollama**
You can also use the Modelfile concept in Ollama to create your own model variants. For more parameters that can be configured in the model file, you can refer to these documents:

Ollama Modelfile documentation:[modelfile](https://github.com/ollama/ollama/blob/main/docs/modelfile.md)

Model file example:
```
# Downloaded from Hugging Face https://huggingface.co/TheBloke/finance-LLM-GGUF/tree/main
FROM "./finance-llm-13b.Q4_K_M.gguf"

PARAMETER temperature 0.001
PARAMETER top_k 20

TEMPLATE """
{{.Prompt}}
"""

# set the system message
SYSTEM """
You are Elon Musk . Answer as Elon Musk to give useful advicce.
"""
```

Once you have obtained the model file, you can create a model using the following command:

```
ollama create breydan96/financellm -f Modelfile
```

Where financellm is the name of your LLM model, and breydan96 will be replaced with your ollama.com username (which also acts as the namespace for the online ollama registry). At this point, you can use the model you created like any other model on Ollama.

**Push your model to the remote ollama registry**
You can also choose to push your model to the remote ollama registry. To achieve this, you will need to:

Create your account on ollama.com
Add a new model
Set up a public key to allow you to push models from a remote computer.
**After creating a local llm, you can push it to the ollama registry using the following command:**

```
ollama push breydan96/financellm
```
**OpenWebUI: A Visual Interface for Local LLM Interaction**

Within the Ollama ecosystem, a plethora of outstanding open-source projects have emerged. Here, we'll introduce OpenWebUI, a local web interface that facilitates direct interaction with language models.

## OpenWebUI: Features and Benefits

OpenWebUI stands out as an extensible, feature-rich, and user-friendly self-hosted web interface. It offers complete offline operation and compatibility with both Ollama and OpenAI's API. This provides users with a visual interface that makes interacting with large language models more intuitive and convenient.

**Installation Instructions**
If you have Ollama and Docker installed on your system, follow these steps:

```bash
docker run -d -p 3000:8080 -e OLLAMA_BASE_URL=https://example.com -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

Once the installation is complete, you can access OpenWebUI via http://localhost:3000.
<p align="center">
  <img src="/static/images/openwebui.png" alt="Image" />
</p>
Upon accessing the interface, you'll notice the "Select a model" option, allowing you to choose the model you recently downloaded.
<p align="center">
  <img src="/static/images/openwebuiselect.png" alt="Image" />
</p>
This effectively provides you with a GPT-like visual interface for local LLM interaction.
<p align="center">
  <img src="/static/images/openwebuichat1.png" alt="Image" />
</p>

OpenWebUI empowers users to interact with LLMs in a more intuitive and user-friendly manner, enhancing the overall LLM exploration experience.
**Additional Resources =**
[Ollama official documentation:](https://github.com/ollama/ollama/blob/main/docs/api.md)
[Ollama GitHub repository:](https://github.com/ollama/ollama)
[Ollama discussion forum:](https://github.com/ollama/ollama/issues/2443)