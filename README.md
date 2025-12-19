# AI_SEARCH_AGENT

## 🔍 Multi-Source AI Research Agent

AI_SEARCH_AGENT is an **agentic AI-powered research assistant** that performs parallel web research across **Google, Bing, and Reddit**, analyzes results using a Large Language Model, and synthesizes them into a **single, well-structured answer**.

This project demonstrates **real-world usage of LangGraph + LangChain**, structured LLM outputs, and external data providers (Bright Data) to build an **end-to-end autonomous research agent**.

---

## 🧠 Key Capabilities

* 🔎 Parallel search across **Google, Bing, and Reddit**
* 🧩 Graph-based orchestration using **LangGraph**
* 🤖 LLM-powered analysis and synthesis (GPT-4o)
* 🧵 Reddit post selection + comment retrieval
* 📊 Structured prompt engineering
* 🔐 Secure API key handling via `.env`

---

## 🏗️ Architecture Overview

```
User Question
      │
      ▼
┌───────────────────┐
│ Parallel Searches │
│ Google | Bing |   │
│ Reddit            │
└───────────────────┘
      │
      ▼
┌───────────────────┐
│ Reddit URL        │
│ Selection (LLM)   │
└───────────────────┘
      │
      ▼
┌───────────────────┐
│ Reddit Comments   │
│ Retrieval         │
└───────────────────┘
      │
      ▼
┌───────────────────┐
│ Source-wise       │
│ Analysis (LLM)    │
│ Google | Bing |   │
│ Reddit            │
└───────────────────┘
      │
      ▼
┌───────────────────┐
│ Final Synthesis   │
│ (LLM)             │
└───────────────────┘
      │
      ▼
 Final Answer
```

---

## 📁 Project Structure

```
AI_SEARCH_AGENT/
├── main.py                 # Entry point & LangGraph workflow
├── prompts.py              # Prompt templates & message builders
├── web_operations.py       # Google, Bing & Reddit search logic
├── snapshot_operations.py  # Bright Data snapshot polling & download
├── requirements.txt        # Python dependencies
├── .env                    # API keys (not committed)
└── README.md
```

---

## ⚙️ Tech Stack

* **Python 3.11**
* **LangGraph** – Agent workflow orchestration
* **LangChain** – LLM abstraction
* **GPT-4o** – Analysis & synthesis
* **Bright Data API** – SERP & Reddit scraping
* **Pydantic** – Structured LLM outputs
* **dotenv** – Environment variable management

---

## 🔐 Environment Setup

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key
BRIGHTDATA_API_KEY=your_brightdata_api_key
```

---

## 📦 Installation

```bash
git clone https://github.com/Amitsarkar02/AI_SEARCH_AGENT.git
cd AI_SEARCH_AGENT
pip install -r requirements.txt
```

---

## ▶️ Running the Agent

```bash
python main.py
```

You will see:

```
Multi-Source Research Agent
Ask me anything:
```

Type a question, and the agent will:

1. Search Google, Bing, and Reddit
2. Analyze each source using GPT-4o
3. Retrieve relevant Reddit discussions
4. Produce a synthesized final answer

Type `exit` to quit.

---

## 🧩 How It Works (Code-Level)

### 1️⃣ Graph State

The agent maintains a shared state containing:

* User question
* Search results
* Source-wise analyses
* Final synthesized answer

Defined using `TypedDict` for clarity and safety.

---

### 2️⃣ Parallel Search Nodes

```python
graph_builder.add_edge(START, "google_search")
graph_builder.add_edge(START, "bing_search")
graph_builder.add_edge(START, "reddit_search")
```

All sources are queried **in parallel**.

---

### 3️⃣ Reddit Intelligence

* LLM selects the **most valuable Reddit URLs**
* Comments are fetched using Bright Data snapshots
* Community insights are extracted separately

---

### 4️⃣ Source Analysis

Each source has a **dedicated analysis prompt**:

* Google → factual & authoritative
* Bing → complementary & technical
* Reddit → community experiences

---

### 5️⃣ Final Synthesis

A final LLM call combines all analyses into a **single coherent answer**, citing source types and highlighting contradictions.

---

## 🧪 Example Use Cases

* Market research
* Product comparisons
* Technical topic exploration
* Community sentiment analysis
* Competitive intelligence

---

## 🚀 Future Improvements

* Add result caching
* Add vector store (RAG)
* Support more data sources
* Web UI / API endpoint
* Async execution

---

## 🧑‍💻 Author

**Amit Sarkar**
GitHub: [https://github.com/Amitsarkar02](https://github.com/Amitsarkar02)

---

## 📄 License

This project is open-source. Add a license (MIT / Apache 2.0) as needed.

---

⭐ If you found this useful, consider starring the repository!
