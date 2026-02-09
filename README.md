# Autonomous Financial Research Agent

## Project Overview
This repository contains the implementation of a local-first, multi-agent system designed to automate financial due diligence workflows. The system utilizes **LangGraph** to orchestrate cyclical agentic workflows, enabling autonomous routing between structured data retrieval (SQL) and unstructured document analysis (RAG).

The core objective is to mitigate hallucination in automated analytics by implementing a **Self-Reflection** loop, where the agent critiques its own intermediate outputs and iteratively refines its queries before presenting a final answer.

**Current Status:** `v0.1.0`

## Technical Architecture

* **Orchestration:** [LangGraph](https://langchain-ai.github.io/langgraph/) (Cyclical state management for multi-step reasoning).
* **Inference:** [Ollama](https://ollama.com/) running locally (Targeting Llama 3.1 or DeepSeek-R1 for privacy-preserving inference).
* **Knowledge Base:**
    * **Structured:** PostgreSQL (Financial metrics, sales data).
    * **Unstructured:** `pgvector` extension on PostgreSQL (Vector embeddings for annual reports/10-Ks).
* **Infrastructure:** Fully containerized via Docker.

## Roadmap & Implementation Status

This project follows an iterative development timeline. The following tasks track the implementation progress of the agentic pipeline.

### Phase 1: Infrastructure & Environment
- [x] Initial Repository Setup & Poetry Dependency Management
- [ ] Configure Docker Compose for local Ollama service
- [ ] Configure PostgreSQL container with `pgvector` extension enabled
- [ ] Implement database initialization scripts (Schema setup for SQL tools)

### Phase 2: Tool Development
- [ ] **SQL Tool:** Implement LangChain `SQLDatabase` wrapper for safe query execution
- [ ] **RAG Tool:** Build ingestion pipeline for PDF processing (Chunking/Embedding)
- [ ] **Web Search Tool:** Integrate searching for real-time market data (e.g., Tavily/DuckDuckGo)

### Phase 3: Agent Logic (LangGraph)
- [ ] Define Agent State schema (Messages, Errors, Tool Outputs)
- [ ] Implement the `Router` node (Decision logic: SQL vs. Vector Store)
- [ ] Implement the `Generator` node (Answer synthesis)
- [ ] **Critical:** Implement the `Reflector` node (Self-correction loop for hallucination checks)

### Phase 4: Evaluation & UI
- [ ] Build Streamlit frontend for chat interface
- [ ] Develop evaluation dataset (Golden Q&A pairs)
- [ ] Run latency benchmarks for local inference

## Setup and Usage

**Prerequisites:**
* Docker & Docker Compose
* Python 3.11+

**Installation:**

```bash
git clone [https://github.com/KTB2110/autonomous-financial-agent.git](https://github.com/KTB2110/autonomous-financial-agent.git)
cd autonomous-financial-agent
docker-compose up -d
```

**License**
MIT
