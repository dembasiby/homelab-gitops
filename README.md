# 🧪 Kubernetes Homelab with GitOps

This repository documents the evolving infrastructure of my self-hosted Kubernetes homelab, built as part of my DevOps upskilling journey with [Kubecraft](https://www.skool.com/kubecraft/about). The lab is designed to simulate production-grade workflows using GitOps principles, lightweight tooling, and secure configuration practices.

---

## 🚀 Project Goals

- Build a reproducible, scalable homelab using [k3s](https://k3s.io/)  
- Manage deployments declaratively with [FluxCD](https://fluxcd.io/)  
- Secure secrets using [SOPS](https://github.com/mozilla/sops)  
- Explore real-world service deployment (e.g., Linkding, Grafana)  
- Practice infrastructure-as-code and CI/CD workflows  
- Document and share progress for public learning

---

## 🧱 Current Architecture

- **Cluster**: Single-node k3s running on GMKtec Mini PC (Debian)
- **GitOps**: FluxCD v2.7.1 syncing manifests from this repo
- **Secrets**: Encrypted with SOPS and decrypted via Flux integration
- **Networking**: Cloudflare Tunnel for secure external access
- **Storage**: Persistent volumes configured for Linkding
- Monitoring: Added kube-prometheus-stack for observability (includes Prometheus, Grafana, and Alertmanager).
- **Editor**: LazyVim (local) and Vim (server) for workflow efficiency

---

## 📦 Key Deployments

1. `Linkding`:

- Self-hosted bookmark manager deployed via Helm
- Secrets securely managed by SOPS
- Exposed via Cloudflare Tunnel for secure external access

2. `Grafana`:

- Integrated as part of the kube-prometheus-stack
- Configured with TLS encryption for secure access
- Ingress added for external routing

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
│           ├── cloudflare-secret.yaml # Encrypted Cloudflare secret
│           ├── cloudflare.yaml        # Cloudflare Tunnel config
│           ├── kustomization.yaml     # Staging-specific overrides
│           └── linkding-container-env-secret.yaml # Encrypted app secrets
├── clusters
│   └── staging
│       ├── apps.yaml                  # Flux source and kustomization
│       ├── flux-system
│       │   ├── gotk-components.yaml   # Flux core components
│       │   ├── gotk-sync.yaml         # Git sync configuration
│       │   └── kustomization.yaml     # Flux-system kustomization
│       └── monitoring.yaml            # Monitoring stack integration
└── monitoring
    ├── configs
    │   ├── kustomization.yaml         # Kustomization for configs
    │   └── staging
    │       ├── grafana-tls-secret.yaml # Encrypted TLS secret for Grafana
    │       └── kustomization.yaml     # Kustomization for staging configs
    └── controllers
        ├── base
        │   └── kube-prometheus-stack
        │       ├── kustomization.yaml # Kustomization file
        │       ├── namespace.yaml     # Namespace definition
        │       ├── release.yaml       # Helm release configuration
        │       └── repository.yaml    # Helm repository definition
        └── staging
            ├── kube-prometheus-stack
            │   └── kustomization.yaml # Staging-specific configs
            └── kustomization.yaml     # Kustomization for all staging controllers
           └── kustomization.yaml     # Flux-system kustomization
```

---

## 🧠 Learning in Progress

This repo reflects an active learning journey. Expect iterative improvements, refactoring, and documentation updates as I scale the homelab to multi-node architecture and automate provisioning.

---

## 🤝 Acknowledgments

Special thanks to [Mischa van den Burg](https://mishavandenburg.com) for championing the homelab-first approach to DevOps education. This project is inspired by [Kubecraft](https://kubecraft.dev)’s belief that hands-on infrastructure builds confidence and clarity.

---
