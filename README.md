# LangGraph Exploration: Agentic Workflows & State Management

This repository has a collection of code examples that show how to use LangGraph.
Examples start with simple steps and move on to more advanced features. They show how to:
* Let the AI use outside tools to fetch information.
* Pause the AI so a human can check and approve its actions before it continues.

## Key Concepts Explored

* **Stateful Graph Construction:** Designing Directed Acyclic Graphs (DAGs) to manage conversational context and typed state variables.
* **Tool Calling & Binding:** Connecting LLMs to external Python functions to access real-time data (e.g.stock prices).
* **Human-In-The-Loop (HITL):** Adding checkpoints and interrupts to pause execution and require user approval before performing important actions.
* **Observability:** Integrating LangSmith for tracing, debugging, and monitoring LLM calls and graph execution steps.

## Repository Structure

* **`chatbot.ipynb`**: Demonstrates the foundational setup of a LangGraph `StateGraph`. Implements a basic conversational loop utilizing `add_messages` to maintain memory and context across turns.
* **`graph.ipynb`**: Showcases custom state management using Python `TypedDict`. It routes data through mathematical nodes to calculate portfolio totals and currency conversions (USD to INR).
* **`tool_call.ipynb`**: Explores LLM tool binding. The model dynamically decides when to invoke the `get_stock_price` tool to answer user queries, utilizing `MemorySaver` for thread-level persistence.
* **`HITL.ipynb`**: A robust implementation of a Human-In-The-Loop workflow. The graph interrupts execution before calling the `buy_stocks` tool, waits for user confirmation via the checkpointing system, and resumes upon approval.
* **`langsmith.ipynb`**: Highlights LLM observability by utilizing the `@traceable` decorator to log and monitor graph invocations in LangSmith.

## Tech Stack
* Framework: LangGraph, LangChain Core
* Models: Groq (Llama 3.3 70B Versatile)
* Observability: LangSmith
* Environment: Python >= 3.13, Jupyter Notebook

## Installation & Setup

1. **Clone the repository:**
```bash
git clone https://github.com/shimilgithub/langraph-exploration.git
cd langraph-exploration
```
2. **Create Virtual Environment:**
```bash
python -m venv .venv
```

3. **Activate Virtual Environment:**
```bash
.venv\Scripts\activate  
``` 

4. **Set up the environment:**
```bash
pip install -r requirements.txt
```

5. **Configure Environment Variables:**

Create an `.env` file in the root directory and add your API keys:

```bash
GROQ_API_KEY=<your_groq_api_key>
LANGCHAIN_API_KEY=<your_langsmith_api_key>
LANGSMITH_ENDPOINT="https://api.smith.langchain.com"
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=<your_langraph_project>
```

6. **Run the Notebooks:**

```bash
jupyter notebook
```