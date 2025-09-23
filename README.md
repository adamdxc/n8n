
# 🧩 n8n Deployment Guide

Easily run [n8n](https://n8n.io) using Docker or Azure Container Instances (ACI).

---

## 🚀 Quick Start

- **Linux / macOS:** Follow the steps below.
- **Windows users:** See 👉 [Docker Run for Windows](./docker_run_for_windows.md)

---

## ▶️ One-Click Run in Docker Desktop

[![Run in Docker Desktop](https://img.shields.io/badge/Run%20in-Docker%20Desktop-blue.svg?logo=docker)](https://open.docker.com/dashboard/run?image=docker.n8n.io/n8nio/n8n&name=n8n&ports=5678:5678&env=GENERIC_TIMEZONE=Asia%2FKuala%20Lumpur&env=TZ=Asia%2FKuala%20Lumpur&env=N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true&env=N8N_RUNNERS_ENABLED=true&volume=n8n_data:/home/node/.n8n)

---

## 🐳 Run via CLI (Linux / macOS)

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
```

---

## ☁️ Run on Azure Container Instances (ACI)

Deploy n8n on Azure Container Instances for cloud-native automation:

```bash
az container create \
  --resource-group rgACI \
  --name n8n \
  --image docker.n8n.io/n8nio/n8n \
  --cpu 1 \
  --memory 2 \
  --ports 5678 \
  --environment-variables GENERIC_TIMEZONE="Asia/Kuala Lumpur" TZ="Asia/Kuala Lumpur" N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true N8N_RUNNERS_ENABLED=true \
  --azure-file-volume-account-name n8npvc \
  --azure-file-volume-account-key <YOUR_AZURE_STORAGE_KEY> \
  --azure-file-volume-share-name n8ndata \
  --azure-file-volume-mount-path /home/node/.n8n \
  --ip-address Public \
  --os-type Linux
```

> **Note:**
> - Install the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) and log in with `az login`.
> - Replace `<YOUR_AZURE_STORAGE_KEY>` with your actual Azure Storage Account Key.
> - The above command mounts Azure File storage for persistent n8n data.
> - Adjust CPU, memory, and other parameters as needed.

---

## 📚 Resources

- [n8n Documentation](https://docs.n8n.io/)
- [Azure Container Instances](https://learn.microsoft.com/en-us/azure/container-instances/)
For more details, see the [n8n documentation](https://docs.n8n.io/) and [Azure Container Instances docs](https://learn.microsoft.com/en-us/azure/container-instances/).
