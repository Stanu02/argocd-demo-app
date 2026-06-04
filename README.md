# GitOps Demo with ArgoCD 🚀

This project demonstrates a simple GitOps workflow using Kubernetes, ArgoCD, and GitHub.

The goal was to understand how applications can be deployed automatically to Kubernetes whenever changes are pushed to GitHub.

---

## What I Built

- Used Terraform to learn Infrastructure as Code (IaC) concepts
- Created a local Kubernetes cluster using kind
- Installed ArgoCD inside the cluster
- Stored Kubernetes manifests in GitHub
- Connected ArgoCD to the GitHub repository
- Deployed an Nginx application using GitOps
- Verified the deployment by accessing the application in a browser

---

## End-to-End Flow

```text
Terraform
   ↓
Learned Infrastructure as Code concepts

Docker
   ↓
Runs kind cluster nodes

kind
   ↓
Creates local Kubernetes cluster

kubectl
   ↓
Manages Kubernetes resources

ArgoCD
   ↓
Installed inside Kubernetes

GitHub
   ↓
Stores Kubernetes manifests

ArgoCD
   ↓
Watches GitHub for changes

Kubernetes
   ↓
Deploys resources automatically

Nginx Application
   ↓
Accessible in browser
```

---

## GitOps Workflow

```text
Developer updates manifest
            ↓
         git push
            ↓
     GitHub Repository
            ↓
    ArgoCD detects change
            ↓
      Syncs Kubernetes
            ↓
   Application updated automatically
```

---

## Technologies Used

- Terraform
- Docker
- kind
- Kubernetes
- ArgoCD
- GitHub
- kubectl

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

## Screenshots

### ArgoCD Successfully Synced

![ArgoCD Sync](screenshots/argocd-sync.png)

ArgoCD continuously watches the GitHub repository and keeps the Kubernetes cluster synchronized.

### Kubernetes Resources Created

![Kubernetes Resources](screenshots/kubernetes-resources.png)

Namespace, Deployment, ReplicaSet, Pod, and Service were automatically created from the manifests stored in GitHub.

### Nginx Running in Browser

![Nginx Running](screenshots/nginx-running.png)

The application was successfully deployed and accessed through Kubernetes.

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

