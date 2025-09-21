# 🚀 Run n8n in Docker

Easily launch [n8n](https://n8n.io) using Docker.

---

## ▶️ One-Click Run in Docker Desktop

[![Run in Docker Desktop](https://desktop.docker.com/images/run-button.svg)](https://open.docker.com/dashboard/run?image=docker.n8n.io/n8nio/n8n&name=n8n&ports=5678:5678&env=GENERIC_TIMEZONE=Asia%2FKuala%20Lumpur&env=TZ=Asia%2FKuala%20Lumpur&env=N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true&env=N8N_RUNNERS_ENABLED=true&volume=n8n_data:/home/node/.n8n)

---

## ⚡ Quick Start

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop) if you haven’t already.  
2. Click the **Run in Docker Desktop** button above.  
3. Wait for Docker to pull the image and start the container.  
4. Open n8n in your browser:  
   👉 [http://localhost:5678](http://localhost:5678)  

---

## 🐳 Run via CLI

If you prefer the terminal, run:

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -e GENERIC_TIMEZONE="Asia/Kuala Lumpur" \
  -e TZ="Asia/Kuala Lumpur" \
  -e N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true \
  -e N8N_RUNNERS_ENABLED=true \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
