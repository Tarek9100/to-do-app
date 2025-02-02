# To-Do App Deployment with Helm and ArgoCD

## Overview
This repository contains the Helm charts and configurations for deploying a To-Do application using Kubernetes, Helm, and ArgoCD.

## Prerequisites
- Kubernetes cluster (Minikube, Kind, or managed service)
- Helm installed (`helm version`)
- Git repository for tracking Helm charts and configurations

## Deployment Steps
### 1. Install ArgoCD from Helm Chart
```sh
helm install argocd ./charts/argo-cd -n argocd --create-namespace
```
Verify installation:
```sh
kubectl get pods -n argocd
```
Expose the UI:
```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Get the admin password:
```sh
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode
```
Access UI: [https://localhost:8080](https://localhost:8080)

### 2. Deploy To-Do App via ArgoCD

### 3. Monitor & Sync
Check ArgoCD UI for `my-todo-app`. If needed, click **Sync** to deploy.

## Repository Structure
```
.
├── charts/
│   ├── todo-app/  # Helm chart for the To-Do application
│   ├── argo-cd/  # ArgoCD Helm chart
├── README.md  # This file
```
