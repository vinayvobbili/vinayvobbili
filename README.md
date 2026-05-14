# Hi, I'm Vinay Vobbilichetty

**Security Automation Engineer** | MS CS (Cybersecurity track), NC State '25

I build tools that help security teams work smarter - from LLM-powered investigation assistants to self-healing chat bots and automated incident response workflows.

---

## Featured Project

### [vllm-mlx — System-prompt KV cache for `stream_chat`](https://github.com/waybarrios/vllm-mlx/pull/523)

Merged upstream into [vllm-mlx](https://github.com/waybarrios/vllm-mlx), the Apple Silicon LLM server (OpenAI-compatible) that many self-hosted Claude Code / OpenCode setups run behind.

- **The bottleneck:** every follow-up turn was re-prefilling the same ~23K-token system+tools prefix. A system-prompt KV cache existed, but only on the multimodal path — pure-LLM models routing through `stream_chat` re-paid the full prefill on every turn.
- **The fix:** extend the same hash-keyed snapshot logic into the pure-LLM path. HIT restores the cached system prefix and prefills only the new user message. MISS prefills, snapshots, then continues. Anything unexpected (sliding-window models, per-request decode overrides, engine-level features) falls back to the uncached path.
- **Impact:** ~100s → ~7s on follow-up turns of self-hosted Claude Code. Same model, same prompts, identical outputs.

[![PR #523](https://img.shields.io/badge/PR_%23523-merged-success?style=for-the-badge&logo=github)](https://github.com/waybarrios/vllm-mlx/pull/523)
[![vllm-mlx](https://img.shields.io/badge/vllm--mlx-upstream-blue?style=for-the-badge&logo=apple)](https://github.com/waybarrios/vllm-mlx)

---

## Writing

Engineering notes on distributed LLM platforms, RAG, and self-hosted inference — at [**vinayvobbili.github.io**](https://vinayvobbili.github.io/).

- [**Teaching a Reranker the Language of Security Tickets (+41% MRR@10)**](https://vinayvobbili.github.io/posts/three-phases-of-rag-quality/) — Mining 24K analyst-curated training pairs from XSOAR close-notes, dodging a polynomial blow-up in transitive sibling generation, filtering same-rule near-duplicates out of hard negatives, and lifting held-out test MRR@10 from 0.598 to 0.846.
- [**Why Self-Hosted Claude Code Was 15× Slower Than It Should Be**](https://vinayvobbili.github.io/posts/billing-header-kv-cache/) — A debugging story about a rotating billing header that quietly busts the prefix-KV cache, plus a SimpleEngine patch that actually carries KV state across turns. Two fixes together turn 108-second turns into 7-second turns.

---

## Tech Stack

**Security:** CrowdStrike, QRadar, Tanium, XSOAR, ServiceNow, Recorded Future, VirusTotal

**Backend:** Python, Flask, LangChain, ChromaDB

**Communication:** Webex SDK, Microsoft Teams

**DevOps:** Docker, GitHub Actions, Systemd

---

## Currently

- Building security automation tools
- Open to opportunities in Security Engineering / Security Automation / Detection Engineering

---

## Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/vinay-vobbilichetty)
[![Blog](https://img.shields.io/badge/Blog-100000?style=for-the-badge&logo=jekyll&logoColor=white)](https://vinayvobbili.github.io/)
