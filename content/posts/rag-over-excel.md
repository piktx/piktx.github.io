+++
title= "Chat with Excel files using RAG"
description= "An intelligent chatbot that performs RAG on Excel files using cutting-edge AI models."
date= 2025-01-29
ShowReadingTime= true
author= "PKT"
showToc= true
TocOpen= false
draft= false
tags= ["AI", "Excel", "RAG", "Streamlit", "Python", "Docling"]
weight= 203
[cover]
image= "/posts/ragexcel/ragexcel.png"
+++

Hi everyone (if someone's there). In today's data-driven world, Excel spreadsheets remain the workhorse of business analytics. But what if you could chat with your financial reports or sales data like you'd converse with a colleague? In this post, we'll explore how I built a completely local AI assistant that understands Excel files using cutting-edge open-source tools.

## The Tech Stack Breakdown

This program combines several powerful technologies=

- **Ollama** for running the Llama3.2-vision model locally
- **Hugging Face** embeddings for document understanding
- **Streamlit** for the chat interface
- **LlamaIndex** for RAG (Retrieval-Augmented Generation) implementation

The magic happens in three key phases:

1. **Document Processing**: Excel files are parsed using DoclingReader
2. **AI Brain**: Local LLM processing with custom knowledge integration
3. **Conversation**: Natural language interface powered by Streamlit

## Code Walkthrough: How It All Connects

Let's peek under the hood at the key components:

### The Document Processing Engine

```python
# Custom reader for Excel files
reader = DoclingReader()
loader = SimpleDirectoryReader(
    input_dir=temp_dir,
    file_extractor={".xlsx": reader},
)
```
This code converts Excel tables into structured markdown, preserving crucial relationships between columns and rows. The MarkdownNodeParser then breaks this content into digestible chunks for our AI model.

### Local AI Configuration
```py
# Local LLM setup
llm = Ollama(model="llama3.2-vision", request_timeout=120.0)
# Semantic understanding
embed_model = HuggingFaceEmbedding(
    model_name="BAAI/bge-large-en-v1.5", 
    trust_remote_code=True
)
```
We're using quantized models that balance performance with hardware requirements. The BAAI embeddings create a mathematical "map" of document content, while Llama3 handles reasoning.

### The Conversation Engine
```py
# Custom prompt template
qa_prompt_tmpl_str = (
    "Context information is below.\n"
    "Given the context information above I want you to think step by step..."
)
```
This carefully crafted prompt forces the AI to show its work while maintaining concise answers. The streaming response implementation creates that familiar "typing" effect seen in commercial chatbots.


## Running the Assistant Locally
###  Prerequisites
1. Python 3.10+ environment
2. Ollama installed and running
3. 8GB+ RAM (16GB recommended)

### Installation Steps
1. Clone the repository:
```sh
git clone https://github.com/piktx/excel-rag.git
cd excel-rag
```

2. Install dependencies:
```sh
pip install -r requirements.txt
```

3. Start Ollama service:
```sh
ollama serve
```

4. Launch the Streamlit app:
```sh
streamlit run app.py
```
The interface will automatically open in your default browser at `localhost:8501`.
![](/projects/rag-excel/excelrag.png)

## Key Benefits
1. **Complete Data Privacy**: All processing stays on your machine

2. **Customizable**: Swap models or add new file types easily

3. **No Cloud Costs**: Runs on existing hardware

## Final Thoughts

While commercial AI solutions dominate headlines, this project demonstrates the remarkable capabilities of open-source. The ability to chat with complex spreadsheets opens new possibilities for data analysis while maintaining strict data control.

Last but not the least, If you liked this project, don't forget to give it a **star** on **[Github](https://github.com/piktx/excel-rag)**