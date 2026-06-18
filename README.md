# Hi, I'm Vinay Vobbilichetty

**Principal Security Automation Engineer** | MS CS, Cybersecurity (NC State '25) | B.Tech CE, IIT Kharagpur

I build the systems that let security teams move faster — an on-prem LLM investigation-agent fleet, a multi-agent autonomous SOC, self-healing chat bots, and auditable AI pipelines that replace recurring manual SOC work. I ship pieces of that platform back to the community as open-source Python packages.

Raleigh, NC · Open to Principal / Staff roles in Security Automation, AI/ML Security, and Security Platform Engineering.

---

## Open Source — four packages on PyPI

- **[iocflow](https://github.com/vinayvobbili/iocflow)** — the full IOC lifecycle as an agentic toolkit: extract, enrich, comment, hunt, block, and an LLM agent. STIX/MISP ingestion, an MCP server, CLI/Docker/GitHub Action distribution, and MITRE ATT&CK coverage-gap assessment.
- **[detflow](https://github.com/vinayvobbili/detflow)** — a detection-engineering copilot: draft detections from plain English (Sigma or Cortex XQL) and review them like a senior detection engineer. Offline-safe, model-agnostic.
- **[domainflow](https://github.com/vinayvobbili/domainflow)** — the lookalike-domain lifecycle: generate typo-squats, monitor (CT + WHOIS), score weaponization, and cluster findings into actor campaigns.
- **[langchain-failover](https://github.com/vinayvobbili/langchain-failover)** — primary/secondary failover for LangChain chat models, with tool-calling preserved across failover.

Plus **[find-evil](https://github.com/vinayvobbili/find-evil)** — an IOC-lifecycle MCP layer that stops a forensic agent from hallucinating indicators (SANS FIND EVIL! hackathon), and **[security-ops-platform](https://github.com/vinayvobbili/security-ops-platform)** — the public mirror of the detection & response platform behind all of the above.

---

## Featured Upstream Contribution

### [vllm-mlx — System-prompt KV cache for `stream_chat`](https://github.com/waybarrios/vllm-mlx/pull/523) (merged)

Merged upstream into [vllm-mlx](https://github.com/waybarrios/vllm-mlx), the Apple Silicon LLM server (OpenAI-compatible) that many self-hosted Claude Code / OpenCode setups run behind.

- **The bottleneck:** every follow-up turn re-prefilled the same ~23K-token system+tools prefix. A system-prompt KV cache existed, but only on the multimodal path — pure-LLM models routing through `stream_chat` re-paid the full prefill on every turn.
- **The fix:** extend the same hash-keyed snapshot logic into the pure-LLM path. HIT restores the cached system prefix and prefills only the new user message; MISS prefills, snapshots, then continues; anything unexpected falls back to the uncached path.
- **Impact:** ~100s → ~7s on follow-up turns of self-hosted Claude Code. Same model, same prompts, identical outputs.

[![PR #523](https://img.shields.io/badge/PR_%23523-merged-success?style=for-the-badge&logo=github)](https://github.com/waybarrios/vllm-mlx/pull/523)
[![vllm-mlx](https://img.shields.io/badge/vllm--mlx-upstream-blue?style=for-the-badge&logo=apple)](https://github.com/waybarrios/vllm-mlx)

---

## Writing — [vinayvobbili.github.io](https://vinayvobbili.github.io/)

- [**SOC-in-a-Box: One LLM, Eight Hats — A Production-Bar AI SOC on a Single GPU**](https://vinayvobbili.github.io/posts/building-soc-in-a-box/) — a LangGraph multi-agent SOC where one on-prem model plays eight specialized roles over an internal message bus, with a red-team agent in the loop.
- [**Teaching a Reranker the Language of Security Tickets (+41% MRR@10)**](https://vinayvobbili.github.io/posts/three-phases-of-rag-quality/) — mining 24K analyst-curated pairs from XSOAR close-notes and lifting held-out MRR@10 from 0.598 to 0.846 over off-the-shelf bge-reranker-v2-m3.
- [**Why Self-Hosted Claude Code Was 15× Slower Than It Should Be**](https://vinayvobbili.github.io/posts/billing-header-kv-cache/) — a rotating billing header quietly busting the prefix-KV cache; two fixes turn 108-second turns into 7-second turns.
- [**The Day My AI SOC Went Quiet**](https://vinayvobbili.github.io/posts/the-day-my-ai-soc-went-quiet/) — an incident retrospective on silent LLM-failover gaps and how to make them loud.
- [**Three Chat Template Patterns That Silently Kill Your Prompt Cache**](https://vinayvobbili.github.io/posts/three-chat-template-patterns-kill-prompt-cache/) — the subtle template choices that defeat KV caching on self-hosted inference.

---

## Tech Stack

**Security:** CrowdStrike Falcon · Cortex XSOAR/XSIAM · Tanium · IBM QRadar · ServiceNow · Recorded Future · AttackIQ · Veracode

**AI/ML:** LangChain · LangGraph · Model Context Protocol (MCP) · RAG · ChromaDB · cross-encoder rerankers · mlx-lm on Apple Silicon

**Backend & Infra:** Python · Flask · FastAPI · Docker · systemd · Nginx · GitHub Actions · GitLab CI/CD

**Standards:** MITRE ATT&CK · Sigma · STIX/TAXII · MISP · EPSS · CISA KEV

---

## Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/vinay-vobbilichetty)
[![Blog](https://img.shields.io/badge/Blog-100000?style=for-the-badge&logo=jekyll&logoColor=white)](https://vinayvobbili.github.io/)
