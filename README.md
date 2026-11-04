# Vinay Vobbilichetty

**Principal AI Automation Engineer** | MS CS, Cybersecurity (NC State '25) | B.Tech CE, IIT Kharagpur

I build LLM agents for security work that can only report what they can prove. The model proposes, and plain code checks each claim against the tool output it cites before anyone sees it. The rest of my work sits around that idea: investigation agents, RAG, MCP servers, evals, and self-hosted inference with failover across hosts.

---

## Start here

- **[witness](https://github.com/vinayvobbili/witness)**: a DFIR agent that can only report what it can prove a tool said. A finding is admitted only when a deterministic check re-reads the cited tool output and confirms the field, with no second language model in the gate. Scored on 1,083 claims and 119 crafted attacks. Clone it and run `python demo.py`: no install, no API key, standard library only.
- **[hubtriage](https://github.com/vinayvobbili/hubtriage)**: the same gate on AWS Security Hub findings. A benign verdict has to rest entirely on evidence, and the IAM policy denies the agent the power to close a finding. Validated offline and in CI; not deployed yet.
- **[shortlist-ai](https://github.com/vinayvobbili/shortlist-ai)**: blind, evidence-cited resume shortlisting, where every quote is checked by code and the score is computed in code, with ranking evals and counterfactual bias tests.

## Merged upstream

### [vllm-mlx: system-prompt KV cache for `stream_chat`](https://github.com/waybarrios/vllm-mlx/pull/523)

[vllm-mlx](https://github.com/waybarrios/vllm-mlx) is the Apple Silicon LLM server (OpenAI-compatible) that many self-hosted Claude Code and OpenCode setups run behind.

- **The bottleneck:** every follow-up turn re-prefilled the same ~23K-token system and tools prefix. A KV cache existed, but only on the multimodal path.
- **The fix:** extend the same hash-keyed snapshot logic to the pure-LLM path, falling back to the uncached path for anything unexpected.
- **Impact:** ~100s to ~7s on follow-up turns. Same model, same prompts, identical outputs.

## More tools

- **[refutescan](https://github.com/vinayvobbili/refutescan)**: a code vulnerability scanner where one LLM hunts, a second tries to refute each finding, and every scan runs in a no-network Docker sandbox.
- **[jobwatch](https://github.com/vinayvobbili/jobwatch)**: watches company job boards and ranks new roles by fit, with a local UI and an MCP server. 1,650 tests.
- **[langchain-failover](https://github.com/vinayvobbili/langchain-failover)**: failover and cheap-then-frontier tier-splitting for LangChain chat models, with tool-calling preserved.

---

## Writing

More at [vinayvobbili.github.io](https://vinayvobbili.github.io/).

- [**Prove It, or It Doesn't Go in the Report**](https://vinayvobbili.github.io/posts/witness-prove-it-or-it-doesnt-go-in-the-report/): why I rebuilt a losing hackathon entry around an oracle that can't be argued with.
- [**Why Self-Hosted Claude Code Was 15× Slower Than It Should Be**](https://vinayvobbili.github.io/posts/billing-header-kv-cache/): a rotating billing header quietly busting the prefix-KV cache; two fixes turn 108-second turns into 7-second turns.
- [**Teaching a Reranker the Language of Security Tickets (+41% MRR@10)**](https://vinayvobbili.github.io/posts/three-phases-of-rag-quality/): lifting held-out MRR@10 from 0.598 to 0.846 over off-the-shelf bge-reranker-v2-m3.
- [**Three Chat Template Patterns That Silently Kill Your Prompt Cache**](https://vinayvobbili.github.io/posts/three-chat-template-patterns-kill-prompt-cache/): the small template choices that defeat KV caching on self-hosted inference.

---

## Tech Stack

**AI/ML:** LangChain · LangGraph · Model Context Protocol (MCP) · RAG · ChromaDB · cross-encoder rerankers · mlx-lm on Apple Silicon

**Backend & Infra:** Python · Flask · FastAPI · Docker · systemd · Nginx · GitHub Actions · GitLab CI/CD

**Security:** CrowdStrike Falcon · Cortex XSOAR/XSIAM · Tanium · IBM QRadar · ServiceNow · Recorded Future · AttackIQ · Veracode

**Standards:** MITRE ATT&CK · Sigma · STIX/TAXII · MISP · EPSS · CISA KEV

---

## Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/vinay-vobbilichetty)
[![Blog](https://img.shields.io/badge/Blog-100000?style=for-the-badge&logo=jekyll&logoColor=white)](https://vinayvobbili.github.io/)
