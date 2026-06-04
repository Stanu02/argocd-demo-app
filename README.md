# GitOps Demo with ArgoCD 🚀

A beginner-friendly GitOps implementation using Kubernetes, ArgoCD, and GitHub.

## What This Project Does

Every time a Kubernetes manifest is pushed to GitHub:

1. ArgoCD detects the change
2. Synchronizes the cluster automatically
3. Deploys the updated resources to Kubernetes
4. Keeps the cluster state aligned with Git

No manual `kubectl apply` commands required.

---

## Tech Stack

| Layer                   | Tool       |
| ----------------------- | ---------- |
| Version Control         | GitHub     |
| GitOps Engine           | ArgoCD     |
| Container Runtime       | Docker     |
| Kubernetes Cluster      | kind       |
| Container Orchestration | Kubernetes |
| CLI Tools               | kubectl    |

---

## Architecture

```text
GitHub Repository
        ↓
      ArgoCD
        ↓
 Kubernetes Cluster (kind)
        ↓
 Namespace
        ↓
 Deployment
        ↓
 Service
        ↓
   Nginx Application
```

---

## Project Structure

```text
argocd-demo-app/
├── application.yaml
├── k8s/
│   ├── app.yaml
│   ├── deployment.yaml
│   └── service.yaml
├── screenshots/
│   ├── argocd-sync.png
│   ├── kubernetes-resources.png
│   └── nginx-running.png
└── README.md
```

---

## Kubernetes Resources Deployed

### Namespace

* Created a dedicated namespace called `demo-app`

### Deployment

* Deployed an Nginx container
* 1 replica managed by Kubernetes Deployment

### Service

* Created a ClusterIP Service
* Exposed the Nginx application inside the cluster

---

## GitOps Workflow

```text
Update Kubernetes Manifest
            ↓
         git push
            ↓
     GitHub Repository
            ↓
    ArgoCD detects change
            ↓
      Syncs Kubernetes
            ↓
   Application updated
```

---

## Screenshots

### ArgoCD Application Sync

![ArgoCD Sync](screenshots/argocd-sync.png)

### Kubernetes Resources

![Kubernetes Resources](screenshots/kubernetes-resources.png)

### Nginx Running

![Nginx Running](screenshots/nginx-running.png)

---

## Verification

Check deployed resources:

```bash
kubectl get all -n demo-app
```

Access the application:

```bash
kubectl port-forward svc/nginx-service 8080:80 -n demo-app
```

Open:

```text
http://localhost:8080
```

---

## Key Concepts Demonstrated

* GitOps
* ArgoCD Continuous Deployment
* Kubernetes Deployments
* Kubernetes Services
* Declarative Infrastructure
* Automated Synchronization

---

Built as a hands-on project to understand how modern teams deploy applications using GitOps principles.
