# 🚀 Local Platform Engineering Lab

A fully local DevOps and Platform Engineering lab that simulates a cloud-native environment **without using AWS or any cloud provider**.

---

## 🧠 What This Project Shows

* Containerisation using Docker
* Local Kubernetes cluster using Kind
* CI pipeline using GitHub Actions
* Versioned Docker builds (release pipeline)
* Monitoring using Prometheus and Grafana

---

## 🧰 Tech Stack

* Python (Flask)
* Docker
* Kubernetes (Kind)
* GitHub Actions
* Helm
* Prometheus & Grafana

---

## 📁 Project Structure

```
local-platform-engineering-lab/
├── app/
├── docker/
├── kubernetes/
├── .github/workflows/
└── README.md
```

---

## ⚙️ Prerequisites

Install the following:

* Docker
* kubectl
* Kind
* Git
* Helm

---

# 🧪 Phase 1: Run with Docker

### Build image

```bash
docker build -t platform-lab-app:local -f docker/Dockerfile .
```

### Run container

```bash
docker run -p 5000:5000 platform-lab-app:local
```

### Test

```bash
curl http://localhost:5000
```

---

# ☸️ Phase 2: Run on Kubernetes (Local)

### Create cluster

```bash
kind create cluster --name platform-lab --config kubernetes/kind-cluster.yaml
```

### Load image

```bash
kind load docker-image platform-lab-app:local --name platform-lab
```

### Deploy

```bash
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

### Check

```bash
kubectl get pods
kubectl get svc
```

### Access app

```bash
curl http://localhost:8080
```

---

# 🔁 Phase 3: CI Pipeline

GitHub Actions pipeline runs on push.

It checks:

* Code syntax
* Tests
* Docker build
* Kubernetes YAML

Check it in:

```
GitHub → Actions tab
```

---

# 📦 Phase 4: Release Pipeline

Triggered using Git tags.

### Run

```bash
git tag v1.0.0
git push origin v1.0.0
```

### What happens

* Builds versioned Docker image
* Builds latest image
* Simulates deployment

---

# 📊 Phase 5: Monitoring

### Install stack

```bash
kubectl create namespace monitoring

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

helm install monitoring prometheus-community/kube-prometheus-stack \
  --namespace monitoring
```

### Check pods

```bash
kubectl get pods -n monitoring
```

---

### Open Grafana

```bash
kubectl port-forward -n monitoring svc/monitoring-grafana 3000:80
```

Open in browser:

```
http://localhost:3000
```

Login:

```
admin / prom-operator
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

# 🎯 Summary

This project demonstrates a full DevOps workflow locally:

* Build → Container → Deploy → Monitor
* CI/CD without cloud
* Kubernetes-based platform simulation

---

# 👤 Author

Binaya Ghimire
GitHub: https://github.com/0BinayaGhimire0
LinkedIn: https://linkedin.com/in/binaya-ghimire