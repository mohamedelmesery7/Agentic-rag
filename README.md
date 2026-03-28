---
title: AgenticRAG
sdk: gradio
sdk_version: 5.29.1
app_file: app.py
pinned: false
license: apache-2.0
---

# 🤖 Agentic RAG — Alfred the Gala Butler

An agentic AI assistant named **Alfred** that combines Retrieval-Augmented Generation (RAG) with multiple tools to answer questions about gala guests, weather, Hugging Face models, and the web — all through a friendly Gradio chat interface.

Built as part of the [Hugging Face Agents Course – Unit 3](https://huggingface.co/learn/agents-course).

---

## 🚀 Features

- 🧠 **Agentic reasoning** with planning every 3 steps via `smolagents` `CodeAgent`
- 📚 **RAG-powered guest lookup** using BM25 retrieval over a Hugging Face dataset
- 🌤️ **Weather info tool** for any location
- 📊 **Hugging Face Hub stats** — find the most downloaded model by any author
- 🔍 **DuckDuckGo web search** for real-time information
- 🖥️ **Gradio UI** for easy interaction

---

## 🏗️ Project Structure

```
Agentic Rag/
├── app.py           # Main entry point — sets up Alfred and launches Gradio UI
├── retriever.py     # RAG tool — loads guest dataset and builds BM25 retriever
├── tools.py         # Custom tools: WeatherInfoTool, HubStatsTool
├── requirements.txt # Python dependencies
└── README.md
```

---

## 🛠️ Alfred's Tools

| Tool | Description |
|---|---|
| `guest_info_retriever` | Retrieves gala guest info (name, relation, email) via BM25 RAG |
| `weather_info` | Returns weather conditions for a given location |
| `hub_stats` | Finds the most downloaded model by a Hugging Face author |
| `DuckDuckGoSearchTool` | Performs live web searches |

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/mohamedelmesery7/Agentic-rag
cd agentic-rag
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Install and run Ollama with Gemma 3

This project uses a **local LLM** via [Ollama](https://ollama.com). Make sure Ollama is installed and the model is pulled:

```bash
ollama pull gemma3:4b
```

### 4. Run the app

```bash
python app.py
```

Then open your browser at `http://localhost:7860`.

---

## 📦 Dependencies

- [`smolagents`](https://github.com/huggingface/smolagents) — Agentic framework
- [`langchain-community`](https://github.com/langchain-ai/langchain) — BM25 retriever
- [`datasets`](https://github.com/huggingface/datasets) — Guest dataset loading
- [`rank_bm25`](https://github.com/dorianbrown/rank_bm25) — BM25 ranking
- [`gradio`](https://gradio.app) — Web UI
- [`huggingface-hub`](https://github.com/huggingface/huggingface_hub) — Hub API access
- [`ddgs`](https://pypi.org/project/ddgs/) — DuckDuckGo search

---

## 🧠 How It Works

1. **Alfred** is a `CodeAgent` that reasons step-by-step and plans every 3 steps.
2. When asked about a guest, it uses the **BM25 RAG retriever** to search the `agents-course/unit3-invitees` dataset.
3. For web questions, it falls back to **DuckDuckGo search**.
4. Weather and Hub stats are handled by lightweight **custom tools**.
5. Everything runs locally using **Gemma 3 (4B)** via Ollama.

---

## 📄 License

This project is licensed under the [Apache 2.0 License](LICENSE).