
# shipfast-gitops

A GitOps deployment workflow for a simple internal status check API built for ShipFast Logistics Technology.

## What This Project Does

This project containerizes a Python Flask app and deploys it to a Kubernetes cluster using Argo CD. Any future change to the app flows through a GitHub pull request instead of a manual command.

## What Is Inside

- **app.py** — Flask app with a /status endpoint that returns a health check response
- **requirements.txt** — Python dependencies
- **Dockerfile** — Container image built on a pinned Python slim base image with a non-root user for security
- **manifests/** — Kubernetes Deployment, Service, and ConfigMap for the shipfast namespace
- **argocd/** — Argo CD Application manifest that watches this repo and auto-syncs to the cluster

## How It Works

Argo CD watches the manifests folder in this repository. When a change is merged into the main branch, Argo CD automatically applies it to the cluster. If anything in the cluster drifts from what is in Git, Argo CD self-heals it automatically.

## Built With

- Python Flask
- Docker
- Kubernetes via kind
- Argo CD
- Claude Code

## Author

Blessing Okan
```
