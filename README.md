# 🚀 Multi-Agent Financial Analysis System (CrewAI)

A hierarchical multi-agent system that automates stock research, financial analysis, and investment decision-making using LLMs, tools, and memory.

This project demonstrates how to design and orchestrate multiple AI agents to collaborate on complex, real-world tasks under practical constraints such as API limits and model reliability.

---

## 🧠 Overview

This system uses a **multi-agent architecture** where each agent is responsible for a specific task:

1. **Market Researcher**
   - Identifies trending companies from real-time news

2. **Financial Researcher**
   - Performs deeper analysis on selected companies

3. **Stock Picker**
   - Evaluates options and selects the best investment

4. **Manager**
   - Orchestrates the workflow and delegates tasks

The system leverages:
- LLM reasoning
- External tools (search APIs)
- Memory for context persistence
- Structured task delegation

---

## 🏗️ Architecture
Manager (Coordinator)
├── Market Researcher → Finds trending companies
├── Financial Researcher → Analyzes companies
└── Stock Picker → Selects best investment

- Uses **hierarchical task delegation**
- Agents operate with **distinct roles and goals**
- Execution flow is optimized for **low-rate API environments**

---

## ⚙️ Features

### ✅ Multi-Agent Orchestration
- Modular agents with clearly defined responsibilities
- Task decomposition improves reasoning and maintainability

### 🌐 Real-Time Data Integration
- Uses external search APIs (Serper) to fetch up-to-date information
- Reduces hallucination by grounding responses in real data

### 🧠 Memory System
- Short-term memory
- Long-term memory
- Entity memory

Enables:
- Context persistence across tasks
- Improved continuity in multi-step workflows

### ⚡ Rate-Limit Aware Design
Designed to operate under strict API limits (e.g. 15 RPM / 500 RPD):
- Sequential execution to prevent burst requests
- Limited agent iterations
- Reduced redundant tool usage

### 🛡️ Robustness & Safeguards
- Handles LLM failures and API errors
- Prevents infinite loops via iteration constraints
- Validates tool inputs to avoid execution errors

---

## 🧩 Tech Stack

- **CrewAI** – Multi-agent orchestration
- **LLMs (Gemini / LiteLLM)** – Reasoning & generation
- **Serper API** – Real-time web search
- **Python** – Core implementation
- **RAG-style Memory** – Context persistence

---





---

## ⚠️ Challenges & Learnings

### 1. Rate Limits
- Multi-agent systems can easily exceed API quotas
- Solved via:
  - sequential execution
  - limiting iterations
  - reducing redundant calls

---

### 2. LLM Reliability
- Encountered:
  - hallucinations
  - inconsistent outputs
  - invalid tool inputs

Mitigated by:
- refining prompts
- constraining agent behavior
- grounding responses with search data

---

### 3. Tool Execution Errors
- Invalid input formats caused failures
- Added validation and stricter task instructions

---

## 🔍 Future Improvements

- Add evaluation layer (hallucination detection & scoring)
- Introduce caching to reduce API usage
- Use stronger model for final decision agent
- Add structured output validation (JSON schema)
- Integrate vector database for enhanced retrieval

---

## 📈 Why This Project Matters

This project goes beyond simple prompt engineering and demonstrates:

- Multi-agent system design
- LLM orchestration under constraints
- Real-world trade-offs (cost, latency, reliability)
- Debugging and stabilising AI systems

---

## 💼 Relevance

This project is relevant for roles in:

- AI Engineering
- Generative AI Systems
- LLM Application Development
- Applied Machine Learning

---

## Acknowledgements

This project is inspired by and initially based on:
https://github.com/ed-donner/agents

Significant modifications and improvements were made, including:
- Custom agent design and workflow orchestration
- Integration of Gemini models with rate-limit handling
- Memory system configuration and debugging (RAGStorage)
- Prompt engineering and task optimisation
- Error handling for tool execution and LLM failures


## My Contributions

Compared to the original implementation, I:
- Fixed embedding + memory system issues (SentenceTransformer / RAGStorage)
- Resolved multi-agent delegation bugs and tool mismatches
- Implemented strategies to handle LLM rate limits (Gemini RPM/RPD constraints)
- Improved prompt design to reduce hallucination and improve consistency
- Optimised agent workflow to reduce redundant tool calls
