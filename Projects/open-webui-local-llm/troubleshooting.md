# 🛠 Troubleshooting Notes – Open WebUI + Local LLM Deployment

This document outlines real technical problems I encountered during the deployment of Open WebUI, Ollama, and Cloudflare Tunnel, along with how I diagnosed and resolved them.

---

## ❌ Problem 1: Open WebUI container keeps restarting (Docker install)

**Symptoms:**  
- The WebUI container exited repeatedly or failed to start  
- Accessing `localhost:3000` returned “connection reset” or nothing loaded

**Root Cause:**  
- Docker container used outdated volume mapping or internal network conflict  
- Some images failed to expose the correct port (`8080`)

**Fix:**  
- Switched from Docker to pip installation:
  ```bash
  pip install open-webui
  open-webui serve
  ```
  Note: I suggest using conda to create a separate environment for open webUI
- Then you can directly activate the open webUI:
  ```bash
  open-webui serve
  ```

---

## ❌ Problem 2: Accessing WebUI remotely doesn't work

**Symptoms:**  
- Tunnel starts successfully, but `muzdata.top` returns “Site Not Found”  
- Phone browser can’t load even with mobile data

**Root Cause:**  
- DNS records for the domain weren’t configured in Cloudflare  
- Tunnel routing config was missing `ingress` or had wrong service target

**Fix:**  
- Created `CNAME` DNS records for `muzdata.top` and `www.muzdata.top`  
- Wrote `config.yml` with:
  ```yaml
  ingress:
    - hostname: muzdata.top
      service: http://localhost:8080
    - service: http_status:404
  ```

---

## ❌ Problem 3: Models not visible in Open WebUI

**Symptoms:**  
- Ollama models (like qwen, llama3) weren’t listed in WebUI  
- Sometimes caused by symlink or permission issues

**Root Cause:**  
- Created nested folder like `/models/models` by mistake  
- Symlink pointed to wrong location

**Fix:**  
- Verified actual path: `/Volumes/iTGZ_2t/AI_lib/models`  
- Created symbolic link again:
  ```bash
  ln -s /Volumes/iTGZ_2t/AI_lib/models ~/.ollama/models
  ```

---

## ❌ Problem 4: Login from a friend's device failed with 500 error

**Symptoms:**  
- Friend in China could access login page, but login always failed (HTTP 500)

**Root Cause:**  
- Not related to GFW; actual cause was local machine-level permission issue  
- New accounts didn’t have model access granted

**Fix:**  
- Logged in as admin  
- Went to WebUI `Settings → Users`  
- Manually enabled model access for that user

---

## ❌ Problem 5: Cloudflared tunnel fails with certificate error

**Symptoms:**  
- `cloudflared tunnel run` throws:
  ```
  cannot find cert.pem or credentials file
  ```

**Root Cause:**  
- Attempted to start named tunnel without authenticating first

**Fix:**  
- Ran:
  ```bash
  cloudflared login
  cloudflared tunnel create open-webui
  cloudflared tunnel route dns open-webui muzdata.top
  ```

---

## ✅ Summary

These troubleshooting efforts show my ability to investigate CLI logs, cross-reference config files, and verify deployment health in a system-level AI toolchain.
