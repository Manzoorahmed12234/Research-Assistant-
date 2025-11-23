
# 🤖 Deep-Research Agent (LangGraph/LLM Architecture)

An advanced, modular AI Agent built on **LangGraph** capable of **multi-step, deep research** by pulling and synthesizing live data from external sources like Google, Bing, and Reddit.

This architecture moves beyond simple prompt-response chains, implementing a complex, stateful workflow designed for high-quality information retrieval and synthesis.

## ✨ Features

* **Multi-Step Research:** Uses LangGraph to orchestrate complex, non-linear workflows.
* **Modular Design:** Clearly separated components for LLM interaction, Embedding storage, Memory, and Tool management.
* **External Tooling:** Integrates live data sources (Google/Bing search, Reddit scraping) for up-to-date information.
* **Dual Memory System:** Manages both short-term (session) and long-term (knowledge base) context.
* **Flexible Deployment:** Run as a simple **CLI** or a robust **FastAPI HTTP server**.

---

## 🏗️ Architecture Overview

The agent is designed around a set of decoupled Python modules, managed by the central **Agent Core**.

| Component | Description |
| :--- | :--- |
| **`src/agent/agent.py`** | The **Agent Core** (Orchestration logic) that determines the next step (e.g., call LLM, use a Tool, retrieve memory). |
| **`src/agent/llm.py`** | Wrapper for **OpenAI Chat models** and embedding generation services. |
| **`src/agent/embeddings.py`** | Handles vectorization and retrieval logic. Primary storage is **Pinecone**, with **FAISS/TF-IDF** as local fallbacks. |
| **`src/agent/memory.py`** | Manages conversation **Short-Term** context and **Long-Term** knowledge (via $EmbeddingStore$). |
| **`src/agent/tools.py`** | Registry of safe, functional tools the agent can execute (e.g., search, data scraping). |
| **`src/app.py`** | Entry point for running the application as a **CLI** or a **FastAPI** web service. |

---

## 🚀 Getting Started

### Prerequisites

* Python 3.9+
* An **OpenAI API Key** (for LLM and embeddings)
* A **Pinecone API Key** (for persistent vector storage)

### 1. Installation

Clone the repository and install dependencies:

```bash
git clone [YOUR_REPO_URL]
cd [your-project-folder]
pip install -r requirements.txt
````

### 2\. Configuration

Create a `.env` file in the root directory to store your credentials:

```bash
# .env file

OPENAI_API_KEY="sk-..."
PINECONE_API_KEY="abc-..."
PINECONE_ENVIRONMENT="us-west1-gcp" # or your chosen environment
```

-----

## 🏃 Usage

### 1\. Command Line Interface (CLI)

Run the agent for quick testing and single-turn interactions:

```bash
python src/app.py cli
```

### 2\. HTTP Server (FastAPI)

Run the agent as a production-ready API service:

```bash
uvicorn src.app:app --reload
```

The API will be available at `http://127.0.0.1:8000`. You can test the endpoints using the Swagger UI at `http://127.0.0.1:8000/docs`.

-----

## ✅ Productionizing Next Steps

To take this architecture from a functional prototype to a robust, scalable service, the following steps are prioritized:

1.  **Structured Tool Calls:** Implement **JSON-schema based tool calling** and add a **verification step** to ensure safety and reliability.
2.  **API Security:** Add **Authentication** (e.g., API keys, OAuth) and **Rate-Limits** to the FastAPI HTTP endpoint.
3.  **State Persistence:** Integrate a persistent store (e.g., Redis, database) for **Short-Term/Session state**.
4.  **Pinecone Hygiene:** Establish a robust protocol for generating unique indexing IDs and managing **namespace cleanup**.

-----

## 🤝 Contributing

Contributions, issues, and feature requests are welcome\! Feel free to check the [issues page](https://www.google.com/search?q=%5BYOUR_ISSUES_LINK%5D) for open tasks.

-----

## 📄 License

Distributed under the TECH FOR TIM License. See `LICENSE` for more information.

```

Would you like me to fill in the bracketed placeholders like `[YOUR_REPO_URL]` or `[YOUR_ISSUES_LINK]`?
```

