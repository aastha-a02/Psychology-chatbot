# 🧠 Psychology Chatbot

A chatbot that answers psychology questions using only the content of a psychology textbook, and says so when the book doesn't cover something. It is built with Retrieval-Augmented Generation (RAG) and runs in Google Colab.

## Features
- Answers questions from the textbook, with page references inside the answer
- Says "the textbook doesn't seem to cover this" instead of making things up
- Understands questions in English and Hindi
- Simple chat interface with example questions
- No installation needed: runs entirely in Google Colab

## How it works
1. **Read:** the PDF is loaded page by page and cleaned (headers and footers removed).
2. **Split:** the text is cut into small overlapping chunks.
3. **Embed:** each chunk is turned into a vector with a multilingual sentence-transformer model and stored in a FAISS index.
4. **Retrieve:** for each question, the 6 most similar chunks are found.
5. **Generate:** a Groq-hosted LLM writes the answer using only those chunks.
6. **Chat:** the Gradio interface shows the conversation and gives a shareable link.

## Tech stack
Python · LangChain · Hugging Face sentence-transformers · FAISS · Groq (`openai/gpt-oss-20b`) · Gradio · Google Colab

## How to run
1. Open the notebook in Colab:
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/aastha-a02/Psychology-chatbot/blob/main/Psychology_Chatbot.ipynb)
2. Get a free API key from [Groq Console](https://console.groq.com) (**API Keys → Create API Key**).
3. Click **Runtime → Run all**.
4. When asked, upload the textbook PDF and paste your Groq API key.
5. After a few minutes, click the `gradio.live` link at the bottom to open the chatbot.

> Tip: switching the Colab runtime to a T4 GPU (**Runtime → Change runtime type**) makes the indexing step much faster.

## Example questions
- What is classical conditioning?
- How does the fight-or-flight response work?
- What did Piaget say about child development?
- What is the difference between short-term and long-term memory?

## Limitations
- Each question is answered on its own; the bot does not remember earlier messages.
- The `gradio.live` link is temporary and stops when the Colab session ends.
- Answers are only as good as the textbook passages found for the question.
- This is an educational tool, not a substitute for professional mental-health advice.

## Credits
The chatbot uses the textbook *Introduction to Psychology*, adapted by [Saylor Academy](https://www.saylor.org) and licensed under [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/). The PDF is not included in this repository.

## Author
Aastha Agarwal · [LinkedIn](https://www.linkedin.com/in/aastha-agarwal-741013423)
