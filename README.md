# 🧪 Kubernetes Homelab with GitOps

This repository documents the evolving infrastructure of my self-hosted Kubernetes homelab, built as part of my DevOps upskilling journey with [Kubecraft](https://www.skool.com/kubecraft/about). The lab is designed to simulate production-grade workflows using GitOps principles, lightweight tooling, and secure configuration practices.

---

## 🚀 Project Goals

- Build a reproducible, scalable homelab using [k3s](https://k3s.io/)  
- Manage deployments declaratively with [FluxCD](https://fluxcd.io/)  
- Secure secrets using [SOPS](https://github.com/mozilla/sops)  
- Explore real-world service deployment (e.g., Linkding)  
- Practice infrastructure-as-code and CI/CD workflows  
- Document and share progress for public learning

---

## 🧱 Current Architecture

- **Cluster**: Single-node k3s running on GMKtec Mini PC (Debian)
- **GitOps**: FluxCD v2.7.1 syncing manifests from this repo
- **Secrets**: Encrypted with SOPS and decrypted via Flux integration
- **Networking**: Cloudflare Tunnel for secure external access
- **Storage**: Persistent volumes configured for Linkding
- **Editor**: LazyVim (local) and Vim (server) for workflow efficiency

---

## 📦 Key Deployments

- `linkding`: Self-hosted bookmark manager deployed via Helm
- `namespace.yaml`: Target namespace for app isolation
- `apps.yaml`: Flux source and kustomization definitions
- `kustomization.yaml`: Resource bundling with Kustomize

---

## 📁 Repo Structure

```
homelab-gitops/
├── apps
│   ├── base
│   │   └── linkding
│   │       ├── deployment.yaml        # Linkding deployment spec
│   │       ├── kustomization.yaml     # Base kustomization for linkding
│   │       ├── namespace.yaml         # Namespace definition
│   │       ├── service.yaml           # Service exposure config
│   │       └── storage.yaml           # Persistent volume claim
│   └── staging
│       └── linkding
│           ├── cloudflare.yaml        # Cloudflare Tunnel config
│           └── kustomization.yaml     # Staging-specific overrides
└── clusters
    └── staging
        ├── apps.yaml                  # Flux source and kustomization
        └── flux-system
            ├── gotk-components.yaml   # Flux core components
            ├── gotk-sync.yaml         # Git sync configuration
            └── kustomization.yaml     # Flux-system kustomization
```

---

## 🛠️ Setup Instructions (WIP)

> This section will be expanded with step-by-step setup, prerequisites, and automation scripts.

---

## 🧠 Learning in Progress

This repo reflects an active learning journey. Expect iterative improvements, refactoring, and documentation updates as I scale the homelab to multi-node architecture, integrate monitoring, and automate provisioning.

---

## 🤝 Acknowledgments

Special thanks to [@mishavandenburg] for championing the homelab-first approach to DevOps education. This project is inspired by [Kubecraft](https://kubecraft.dev)’s belief that hands-on infrastructure builds confidence and clarity.

---
