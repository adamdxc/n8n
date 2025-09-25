# Copilot Instructions for n8n Deployment Repo

## Project Overview
This repo provides infrastructure and automation for deploying n8n using Docker, Kubernetes, and Azure Container Instances. It includes YAML manifests, Jsonnet templates, and CI/CD workflows for cloud and local environments.

## Key Components
- **Kubernetes Manifests:** All core resources (Deployments, Services, PVCs, ConfigMaps, Namespaces) are defined in YAML and mirrored as Jsonnet in `/jsonnet`.
- **Jsonnet Templates:** Use `/jsonnet` for templated, reusable Kubernetes resources. The `resources.libsonnet` file aggregates all resources for composition.
- **CI/CD Workflow:** `.github/workflows/deploy-n8n.yml` automates workflow import into n8n pods using `kubectl cp` and `kubectl exec`.
- **Workflow Import:** The `yaml.json` file is patched and imported into n8n via the CI pipeline.
- **Windows Support:** See `docker_run_for_windows.md` for platform-specific Docker instructions.

## Developer Workflows
- **Local Deployment:** Use Docker commands from the README or `docker_run_for_windows.md` for quick local setup.
- **Kubernetes Deployment:** Apply YAML or Jsonnet resources using `kubectl apply -f <file>` or render Jsonnet with `jsonnet` CLI.
- **Workflow Import:** Triggered by pushing to `main`, the CI pipeline patches and imports workflows into the running n8n pod.
- **Jsonnet Update:** When updating resources, modify files in `/jsonnet` and update `resources.libsonnet` for aggregation.

## Conventions & Patterns
- **Resource Naming:** All resources use clear, environment-specific names (e.g., `n8n`, `prometheus`, `alertmanager`).
- **Namespace Usage:** Monitoring resources are isolated in the `monitoring` namespace.
- **Environment Variables:** n8n containers are configured with explicit timezone and runner settings for portability.
- **Persistent Data:** PVCs and Azure File volumes are used for n8n data persistence.
- **YAML/Jsonnet Parity:** Every YAML manifest has a corresponding Jsonnet template for DRY infrastructure.

## Integration Points
- **External Services:** Integrates with Azure for cloud deployments and OpenAI for workflow analysis (see `yaml.json`).
- **CI/CD:** Uses GitHub Actions for workflow import automation.
- **Kubernetes:** All communication with n8n pods is via `kubectl` commands in CI.

## Examples
- See `n8n-deployment.yaml` and `jsonnet/n8n-deployment.jsonnet` for deployment patterns.
- See `.github/workflows/deploy-n8n.yml` for workflow import automation.
- See `resources.libsonnet` for aggregating Jsonnet resources.

## Quick Reference
- Local: `docker run ...` (see README)
- Kubernetes: `kubectl apply -f <manifest>`
- Jsonnet: `jsonnet jsonnet/<resource>.jsonnet`
- CI/CD: Push to `main` to trigger workflow import

---

_If any section is unclear or missing, please provide feedback for improvement._
