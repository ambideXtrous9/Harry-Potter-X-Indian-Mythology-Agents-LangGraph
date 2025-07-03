
# 🧙‍♂️🪄 Harry Potter X Indian Mythology : Multi‑Agent LangGraph Pipeline with GroqChat, RAG & Web Search

![Harry](https://deep-image.ai/blog/content/images/size/w2000/2023/11/12d8bbec-eb85-4cae-83c3-b88621e64013-1.png)

A robust multi-agent pipeline powered by **LangGraph**, **GroqChat (Qwen 3 32B)**, RAG over Harry Potter documents, and real-time search using DuckDuckGo & Tavily.

---

## 🚀 Architecture Overview

This system implements a cyclic workflow of three agents:

1. **🧑‍🔬 Researcher**
   - Fetches domain context via FAISS + BGE reranker (`retrieve_context` tool).
   - Augments it with live web facts using DuckDuckGo (`ddg_search`).
   - Structured as ReAct streaming agent.

2. **✍️ Writer**
   - Crafts a polished article using the research.
   - Leverages `ddg_search` to enrich with quotes, stats.
   - Uses ReAct with `Thought:`, `Action:`, `Observation:`, `Final Answer:` tags.

3. **🧑‍⚖️ Critic**
   - Evaluates the draft for factual correctness and clarity.
   - Returns approval (`yes`/`no`) to determine looping.
   - Uses substring check (`"yes" in feedback.lower()`).

The agents are connected via **LangGraph**:


