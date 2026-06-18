# Agentic LLM Architectures

![Python](https://img.shields.io/badge/Python-3.10+-3776ab.svg?logo=python&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-0.2+-1a1a2e.svg)
![DeepSeek](https://img.shields.io/badge/Model-DeepSeek--V3-4f46e5.svg)
![Gemma](https://img.shields.io/badge/Model-Gemma--2-34a853.svg)
![Notebooks](https://img.shields.io/badge/Notebooks-12-f59e0b.svg)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> A hands-on, intermediate-level collection of Jupyter notebooks exploring **12 modern agentic design patterns** — built with LangGraph, DeepSeek-V3, and Gemma 2, by [Yehia Gewily](https://github.com/YehiaGewily).

Each notebook is structured as a standalone deep-dive: it explains the *problem* the architecture solves, builds the solution step by step, runs a realistic end-to-end scenario, and measures the result. No boilerplate, no toy examples.

---

## Notebook Index

| # | Notebook | Architecture | Model | Key Concept |
|---|----------|-------------|-------|-------------|
| 01 | [Self-Critique & Refinement](01_self_critique.ipynb) | Reflection Loop | Gemma 2 | Agent critiques and rewrites its own output |
| 02 | [Structured Tool Use](02_tool_use.ipynb) | Tool Calling | DeepSeek | Parallel tool calls, error recovery |
| 03 | [ReAct from Scratch](03_react_from_scratch.ipynb) | ReAct | DeepSeek | Full loop without prebuilt helpers |
| 04 | [Plan-and-Execute](04_plan_and_execute.ipynb) | Planning | DeepSeek | Decoupled planner + executor agents |
| 05 | [Supervisor Multi-Agent](05_supervisor_multiagent.ipynb) | Multi-Agent | DeepSeek | Central coordinator dispatching specialist workers |
| 06 | [Episodic Memory Agent](06_episodic_memory.ipynb) | Memory | Gemma 2 | Short + long-term memory via vector store |
| 07 | [Tree of Thoughts](07_tree_of_thoughts.ipynb) | ToT | DeepSeek | Parallel reasoning branches, scored & pruned |
| 08 | [Map-Reduce Summarization](08_map_reduce.ipynb) | Map-Reduce | Gemma 2 | Parallel chunk processing, single coherent output |
| 09 | [Context Engineering](09_context_engineering.ipynb) | Context Mgmt | DeepSeek | Token-aware context compression & retrieval |
| 10 | [Human-in-the-Loop](10_human_in_the_loop.ipynb) | HITL | DeepSeek | Checkpointed graph with approval gates |
| 11 | [Hierarchical Agents](11_hierarchical_agents.ipynb) | Hierarchy | DeepSeek | 3-tier: strategic → tactical → execution |
| 12 | [LLM-as-a-Judge](12_llm_judge.ipynb) | Evaluation | DeepSeek | Automated scoring framework for agent outputs |

---

## Architecture at a Glance

```
Foundational                    Intermediate                     Advanced
─────────────────────────────────────────────────────────────────────────
Self-Critique   Tool Use        Plan-Execute    Tree-of-Thoughts   Hierarchical
    ↓               ↓               ↓                ↓                ↓
  [Gemma 2]    [DeepSeek]      [DeepSeek]       [DeepSeek]       [DeepSeek]
  single loop   tool router    planner/exec    branch & prune    3-tier graph
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Agent Graph** | [LangGraph](https://github.com/langchain-ai/langgraph) |
| **LLM Orchestration** | [LangChain](https://github.com/langchain-ai/langchain) |
| **Reasoning Model** | DeepSeek-V3 via [Nebius AI Studio](https://studio.nebius.ai) |
| **Lightweight Model** | Gemma 2 (9B) via [Nebius AI Studio](https://studio.nebius.ai) |
| **Search Tool** | [Tavily](https://tavily.com) |
| **Vector Memory** | [Chroma](https://www.trychroma.com/) |
| **Observability** | [LangSmith](https://smith.langchain.com) |

---

## Getting Started

### 1. Create a virtual environment

```bash
# Windows (PowerShell)
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure API keys

Copy `.env.example` to `.env` and fill in your keys:

```bash
cp .env.example .env
```

Required keys:

| Key | Required by | Where to get it |
|-----|------------|-----------------|
| `NEBIUS_API_KEY` | All notebooks | [studio.nebius.ai](https://studio.nebius.ai) |
| `TAVILY_API_KEY` | Notebooks 02, 03, 05 | [tavily.com](https://tavily.com) |
| `LANGCHAIN_API_KEY` | Optional (tracing) | [smith.langchain.com](https://smith.langchain.com) |

### 4. Launch Jupyter

```bash
jupyter notebook
# or
jupyter lab
```

---

## Notebook Format

Every notebook follows a consistent structure so you can jump in anywhere:

1. **The Problem** — what limitation this architecture addresses
2. **Architecture Diagram** — visual graph of the agent flow
3. **Step-by-Step Build** — each node/edge explained with inline comments
4. **Live Scenario** — a realistic task run end-to-end with real output
5. **Evaluation** — metric or judge scoring the result
6. **When to Use This** — honest tradeoffs and practical guidance

---

## Learning Path

**If you're new to agents:** Start with `01 → 02 → 03` to build intuition for reflection, tools, and the ReAct loop before tackling graphs and orchestration.

**If you understand the basics:** Jump to `04 → 05 → 07` for planning, multi-agent systems, and branching reasoning — these are where most production systems live.

**If you're building for production:** Focus on `10 → 11 → 12` — human oversight, hierarchical control, and systematic evaluation are what separate demos from shipped products.

---

## Contributing

Issues, ideas, and PRs are welcome. If you spot a bug or want to add a notebook on a pattern not covered here, open an issue first so we can discuss the design.

---

## License

MIT © 2025 [Yehia Gewily](https://github.com/YehiaGewily)
