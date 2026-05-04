# 🚀 Local Platform Engineering Lab

![CI](https://github.com/0BinayaGhimire0/local-platform-engineering-lab/actions/workflows/ci.yml/badge.svg)
![Release](https://github.com/0BinayaGhimire0/local-platform-engineering-lab/actions/workflows/release.yml/badge.svg)

A fully local **Platform Engineering & DevOps lab** that simulates a cloud-native environment without AWS or any cloud provider.

---

## 🧠 What This Project Demonstrates

* Containerized application deployment (Docker)
* Local Kubernetes cluster (Kind)
* CI/CD pipelines (GitHub Actions)
* Versioned Docker builds (release pipeline)
* Observability using Prometheus & Grafana
* Platform engineering concepts applied locally

---

## 🧰 Tech Stack

* Python (Flask)
* Docker
* Kubernetes (Kind)
* GitHub Actions
* Helm
* Prometheus & Grafana

---

## 🏗️ Architecture Overview

```text
GitHub → CI Pipeline → Docker Image → Kubernetes (Kind) → Application → Monitoring
```

---

## ⚙️ Prerequisites

Install:

* Docker
* kubectl
* Kind
* Git
* Helm

---

# 🚀 Quick Start (Recommended)

Run the platform locally:

```bash
docker build -t platform-lab-app:local -f docker/Dockerfile .
docker run -p 5000:5000 platform-lab-app:local
```

Test:

```bash
curl http://localhost:5000
```

---

# ☸️ Run on Kubernetes

### 1. Create cluster

```bash
kind create cluster --name platform-lab --config kubernetes/kind-cluster.yaml
```

---

### 2. Load image

```bash
kind load docker-image platform-lab-app:local --name platform-lab
```

---

### 3. Deploy application

```bash
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

---

### 4. Verify

```bash
kubectl get pods
kubectl get svc
```

---

### 5. Access application

```bash
curl http://localhost:8080
```

---

# 🔁 CI Pipeline

GitHub Actions pipeline runs on every push.

It validates:

* Python syntax
* Application build
* Docker image build
* Kubernetes manifests

View in:

```
GitHub → Actions tab
```

---

# 📦 Release Pipeline

Triggered using Git tags:

```bash
git tag v1.0.0
git push origin v1.0.0
```

This will:

* Build versioned Docker image
* Tag latest image
* Simulate deployment workflow

---

# 📊 Monitoring (Prometheus + Grafana)

### Install monitoring stack

```bash
kubectl create namespace monitoring

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

helm install monitoring prometheus-community/kube-prometheus-stack \
  --namespace monitoring
```

---

### Check pods

```bash
kubectl get pods -n monitoring
```

---

### Open Grafana

```bash
kubectl port-forward -n monitoring svc/monitoring-grafana 3000:80
```

Open:

```
http://localhost:3000
```

Login:

```
admin / <for password see the description during installation>

```

---

### Open Prometheus

```bash
kubectl port-forward -n monitoring svc/monitoring-kube-prometheus-prometheus 9090:9090
```

Open:

```
http://localhost:9090
```

---

# 🧹 Cleanup

```bash
kubectl delete -f kubernetes/
kind delete cluster --name platform-lab
```

---

# 🎯 Key Takeaways

This project demonstrates:

* How platform engineering works locally
* How CI/CD pipelines integrate with infrastructure
* How Kubernetes-based systems are deployed
* How observability is integrated into platforms

---

# 👤 Author

**Binaya Ghimire**