---
layout: page
title: "Local AI Platform with Open WebUI + Cloudflare Tunnel"
permalink: /Projects/open-webui-local-llm/
---

## 🚀 Local AI Platform with Open WebUI + Cloudflare Tunnel

This project documents how I deployed a local AI assistant on my Mac using **Open WebUI**, connected to **local large language models (LLMs)** served by **Ollama**, and enabled secure public access using **Cloudflare Tunnel** with a custom domain.

It highlights my ability to integrate tools across backend, networking, storage, and user access — all relevant to data-focused technical roles.

---

### 🛠️ Stack Used
- `Open WebUI` for front-end interface
- `Ollama` for local model inference (e.g., LLaMA 3, Qwen)
- `Cloudflare Tunnel` + `muzdata.top` (custom domain)
- `Google Programmable Search` + `OpenAI GPT-4o` API fallback
- macOS + external SSD for model storage optimization

---

### 🔧 Setup Summary

- Installed Open WebUI using `pip` for better control than Docker.
- Used Ollama for running local models, and moved model data to external SSD.
- Created a persistent `cloudflared` tunnel and routed it to `www.muzdata.top`.
- Configured DNS through Cloudflare to link my domain with the running tunnel.
- Enabled Web Search via Google CSE + API, and added OpenAI GPT API for internet access fallback.

---

### 🌐 Remote Access Enabled
Through `https://www.muzdata.top`, I can:
- Switch between local and GPT-4o models
- Access the WebUI remotely from any device
- Share limited access with friends

---

### 🧠 Key Learnings
- Tunnel configuration and DNS routing
- Linux/macOS permissions and symbolic links
- Token cost management across LLM backends
- Practical end-to-end AI platform deployment

---

### 📌 Live Demo
- [www.muzdata.top](https://www.muzdata.top) *(may be inactive when self-hosted server is down)*
- GitHub repo: [github.com/muli0992/muzhaoli.github.io](https://github.com/muli0992/muzhaoli.github.io)

---

