# context-pilot-agentic-rag
# 🚀 ContextPilot

### Agentic RAG System with Hybrid Retrieval (Local + Web)

ContextPilot is an **agentic Retrieval-Augmented Generation (RAG)** system that intelligently answers user queries by combining **internal knowledge (PDFs)** with **real-time web data**.

Unlike traditional RAG pipelines, ContextPilot uses a **query routing mechanism** to decide whether to rely on local context, external sources, or both — enabling more accurate, grounded, and context-aware responses.

---

## 🧠 Key Features

* 🔀 **Intelligent Query Routing**

  * Decides whether to use local knowledge, web data, or hybrid mode

* 📄 **Local Knowledge Retrieval (FAISS)**

  * Semantic search over PDF documents
  * Fast and efficient vector-based retrieval

* 🌐 **Web Search via CrewAI Agents**

  * Dynamically fetches external information when needed
  * Multi-agent workflow for search, scraping, and summarization

* ⚡ **Fast LLM Inference (Groq)**

  * Low-latency response generation

* 🧩 **Hybrid Answer Generation**

  * Combines internal and external data sources

* 🧾 **Source Grounding (Planned)**

  * Traceable answers with document and web references

* 🔁 **Self-Correction Loop (Planned)**

  * Agent critiques its own responses and improves them

---

## 🏗️ Architecture Overview

```mermaid
flowchart TD
    A[User Query] --> B[Router Agent]

    B -->|Local| C[FAISS Retriever]
    B -->|Web| D[CrewAI Web Agents]
    B -->|Hybrid| E[Local + Web]

    C --> F[Context Aggregation]
    D --> F
    E --> F

    F --> G[LLM (Groq)]
    G --> H[Final Answer]

    H --> I[Self-Critique (Optional)]
```

---

## ⚙️ Tech Stack

* **LLM**: Groq (LLaMA / Mixtral)
* **Vector DB**: FAISS
* **Framework**: CrewAI (for agent workflows)
* **Embeddings**: Sentence Transformers / OpenAI Embeddings
* **Backend**: Python (FastAPI / CLI)
* **Web Search**: Tavily / SerpAPI / custom scraping

---

## 📂 Project Structure

```
context-pilot/
│── app/
│   ├── router/            # Query routing logic
│   ├── retriever/         # FAISS + embeddings
│   ├── agents/            # CrewAI agents (web search)
│   ├── llm/               # Groq integration
│   ├── pipelines/         # RAG + hybrid workflows
│   └── utils/             # Helpers

│── data/
│   ├── raw_pdfs/
│   └── processed_chunks/

│── vectorstore/           # FAISS index

│── configs/               # Model + routing configs

│── tests/

│── main.py
│── requirements.txt
│── README.md
```

---

## 🚦 How It Works

1. User submits a query
2. Router agent evaluates:

   * Is local knowledge sufficient?
3. Based on decision:

   * ✅ Retrieve from FAISS (PDFs)
   * 🌐 Trigger CrewAI web agents
   * 🔀 Combine both (hybrid)
4. Context is passed to LLM (Groq)
5. Final answer is generated and returned

---

## 🧪 Example Use Cases

* Internal company knowledge assistant
* Technical documentation Q&A
* Research assistant with live data
* Customer support automation
* Competitive analysis (internal vs external data)

---

## 🛠️ Installation

```bash
git clone https://github.com/your-username/context-pilot.git
cd context-pilot
pip install -r requirements.txt
```

---

## ▶️ Usage

```bash
python main.py
```

Example query:

```
"What are our onboarding steps for new clients?"
```

---

## 📈 Roadmap

* [ ] Confidence-based query routing (replace Yes/No)
* [ ] Hybrid retrieval optimization
* [ ] Reranking layer (cross-encoder)
* [ ] Source attribution (PDF + web)
* [ ] Self-correcting agent loop
* [ ] Role-based access control
* [ ] Evaluation dashboard (RAG metrics)

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

---

## 📜 License

MIT License

---

## 💡 Vision

To build a **production-grade agentic knowledge system** that goes beyond static RAG — enabling intelligent reasoning, adaptive retrieval, and reliable real-world deployment.

---
