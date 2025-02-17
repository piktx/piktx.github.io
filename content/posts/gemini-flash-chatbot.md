+++
title = "Building Conversational AI Experiences: From Spreadsheets to Multimodal Magic"
description = "A comprehensive guide that will walk you throught the process of making your own Flash chatbot."
date = 2025-02-02
ShowReadingTime = true
author = "PKT"
showToc = true
TocOpen = false
draft = false
tags = ["Chatbot", "AI", "Gemini", "Streamlit", "Python"]
weight = 202
[cover]
image = "/posts/gemini/gemini.jpg"
+++

Hi everyone (if someone’s there). There's something magical about teaching computers to understand not just our words, but our _intent_. I recently made a chatbot with Google's Gemini 2.0 Flash model - and the best part? You can create it too. Let me walk you through this project that blend cutting-edge AI with practical applications.

## 1. The Spreadsheet Whisperer

### Behind the Curtain

This chatbot project came from a simple question: "Why can't I just make a chatbot to _ask questions_ about any sort of data I give it and ask questions about it?" Here's how it works:

```py
# The brain of the operation
llm = Ollama(model="llama3.2-vision")
embed_model = HuggingFaceEmbedding(model_name="BAAI/bge-large-en-v1.5")

# Custom prompt engineering
qa_prompt = (
    "Context information:\n{context_str}\n"
    "Answer like a data analyst friend: {query_str}\n"
    "If unsure, just say so - no guessing!"
)
```
The magic happens in three layers:

1. **Document Alchemy**: Converts tables into searchable knowledge using DoclingReader

2. **Contextual Understanding**: BAAI embeddings create "mental maps" of data relationships

3. **Conversational Interface**: Streamlit provides the chat interface we all recognize

## 2. Seeing Through AI's Eyes: Multimodal Chat
### When Words Meet Images

This project answers: "What if I could show pictures AND ask questions?" Using Google's Gemini 2.0 Flash model:
```py
def initialize_gemini():
    # Secure API handling
    genai.configure(api_key=decoded_key)
    return genai.GenerativeModel("gemini-2.0-flash-exp")

# Handling multimodal input
if uploaded_file:
    inputs.append(Image.open(uploaded_file))
response = model.generate_content(inputs)
```
This implementation does something remarkable:

1. Seamless blending of visual and textual understanding

2. Context-aware responses that reference image content

3. Streaming interface that feels truly conversational

I particularly love how it handles follow-up questions about previously uploaded images.

## Making It Work: A Developer's Journey
###  Prerequisites
1. Python 3.10+ environment
2. Ollama installed and running
3. 8GB+ RAM (16GB recommended)

### Installation Steps
1. Clone the repository:
```sh
git clone https://github.com/piktx/flash-mutimodal-chatbot.git
cd flash-mutimodal-chatbot
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
![](/projects/gemini/gemini.png)

## Final Thoughts

This project demonstrate how accessible AI has become. Whether you're:

- A business user tired of pivot tables or

- A developer exploring multimodal AI or

- An AI enthusiast curious about real applications

There's never been a better time to experiment.

Last but not the least, If you liked this project, don't forget to give it a **star** on **[Github](https://github.com/piktx/flash-mutimodal-chatbot)**