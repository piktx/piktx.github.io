+++
title= "AI News Generator app"
description= "Automated Content Creation with CrewAI and Cohere."
date= 2025-01-20
ShowReadingTime= true
author= "AI"
showToc= true
TocOpen= false
draft= false
tags= ["News", "AI", "CrewAI", "Streamlit", "Python", "Cohere"]
weight= 205
[cover]
image= "/posts/newsgen/newsgen.png"
+++

Hi everyone (if someone’s there). In the evolving landscape of AI-powered content creation, this news generator represents a significant leap forward. By combining CrewAI's multi-agent framework with Cohere's powerful Command R7B language model, the system automates the entire process of researching and writing comprehensive articles on any given topic. Let's explore how this innovative application works and how you can implement it yourself.

## How the System Works
The application follows a sophisticated two-stage process that mimics human journalistic workflows. First, a Senior Research Analyst agent scours the web using SerperDev's search API, collecting and verifying information from multiple sources. This agent acts like a digital investigative reporter, checking facts and cross-referencing data to ensure accuracy.

The collected research then passes to a Content Writer agent, which functions as an experienced journalist. This component synthesizes the raw information into a coherent narrative, maintaining proper citations while ensuring readability. The final output is a well-structured markdown document complete with introduction, body sections, and proper references. Below is the whole workflow of this project:
![](/posts/newsgen/mermaid.png)

## Key Features and Capabilities

What makes this system particularly impressive is its ability to handle complex research tasks while maintaining narrative flow. The AI can process technical information from academic papers, news articles, and statistical reports, then transform it into accessible content suitable for general audiences. A unique temperature control slider allows users to adjust the creativity vs. factual accuracy balance, making it adaptable for different writing styles.

The built-in citation system ensures transparency by automatically linking claims to their sources. When testing the system, we found it particularly effective at generating technology explainers and current event analyses, though it performs well across most non-specialist topics.

## Installation and Setup
### Technical Requirements

Before beginning, ensure your system has:
- Python 3.9 or newer
- Valid API keys for Cohere and SerperDev
- Basic familiarity with command line operations

### Step-by-Step Implementation Guide

1. Begin by cloning the repository from GitHub:
```sh
git clone https://github.com/piktx/ai-news-gen.git
cd ai-news-gen
```

2. Install the required Python packages using pip:
```bash
pip install -r requirements.txt
```

3. Create your environment file:
```bash
echo "COHERE_API_KEY=your_key_here" > .env
echo "SERPER_API_KEY=your_key_here" >> .env
```

4. Launch the Streamlit interface:
```bash
streamlit run app.py
```
The interface will automatically open in your default browser at `localhost:8501`.

## Using the News Generator

Once the application is running, you'll be greeted by a clean web interface. The left sidebar contains all controls - simply enter your topic in the text area, adjust the creativity slider if desired, and click the prominent generate button.

![](/projects/news-gen/newsgenai.png)

## Ethical Considerations and Limitations

While impressive, users should be aware of the system's limitations. The AI occasionally misses nuanced context in highly technical subjects and should always be fact-checked before publication.

It's crucial to remember this tool augments rather than replaces human journalists. The ideal workflow uses AI-generated drafts as starting points for professional writers to refine and enhance.

## Final thoughts

This AI news generator demonstrates the remarkable potential of modern language models when combined with thoughtful system design. By automating the research and initial drafting process, it allows human writers to focus on high-value tasks like analysis and storytelling.

Last but not the least, If you liked this project, don't forget to give it a **star** on **[Github](https://github.com/piktx/ai-news-gen)**