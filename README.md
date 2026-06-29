🤖 Local AI Agent — RAG-based Document Chatbot
A privacy-focused, fully local AI agent that answers questions from custom documents using a Retrieval-Augmented Generation (RAG) pipeline. No cloud APIs. No data leaves your machine.

📌 What It Does
This agent lets you ask natural language questions about your own documents and get intelligent, context-aware answers — all running locally on your computer.

🏗️ Architecture

User Question
     ↓
LangChain (Orchestration)
     ↓
OllamaEmbeddings (mxbai-embed-large)
     ↓
ChromaDB (Vector Store — similarity search)
     ↓
Ollama LLM (Local Language Model)
     ↓
Answer


⚙️ Setup & Installation

1. Clone the repository


git clone https://github.com/mr6394163-jpg/AI-agent.git


cd AI-agent


2. Create and activate virtual environment


python -m venv .venv

 Windows
.venv\\Scripts\\activate


 Linux/Mac
source .venv/bin/activate


3. Install dependencies


pip install langchain langchain-ollama langchain-chroma chromadb ollama


 4. Install Ollama



Download from: https://ollama.com/download

5. Pull required models


 Pull embedding model (required)
ollama pull mxbai-embed-large

 Pull LLM model
ollama pull llama3


⚠️ Note: `mxbai-embed-large` is a large model. Download may take time and can break mid-way — simply re-run the command if it does.



 ▶️ Running the Agent

 Step 1 — Start Ollama server (keep this terminal open)


ollama serve


 Step 2 — Run the agent (in a new terminal)


python main.py


 Step 3 — Ask your question


ask a question (q to quit): What are the vegan options?




🐛 Common Errors & Fixes

Error

1) WinError 10061 Connection refused
   Cause: Ollama not running
   Fix:   Run `ollama serve` in a separate terminal
2) ChromaDB InvalidArgumentError
   Cause: Collection name has spaces
   Fix:   Use underscores: `restaurant_reviews` not `restaurant reviews`
3) mxbai-embed-large download breaks
   Cause:Large file + slow connection
   Fix:Re-run `ollama pull mxbai-embed-large` — it resumes and reliable and fast internet

📁 Project Structure


AI-agent/
├── main.py          # Main chatbot loop
├── vector.py        # ChromaDB setup and retriever
├── .venv/           # Virtual environment
└── README.md
👩‍💻 About

Built by Zainab as a self-directed learning project to understand RAG pipelines, local LLMs, and vector databases. All errors were debugged independently.

 📄 License

MIT
