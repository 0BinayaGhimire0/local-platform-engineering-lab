# Local Platform Engineering Lab

This project is a local DevOps and Platform Engineering lab built without using any cloud provider.

## What this project demonstrates

- Containerising a Python Flask application using Docker
- Running a local Kubernetes cluster using Kind
- Deploying an application to Kubernetes
- Exposing the application locally using a NodePort service
- Using readiness and liveness probes for basic reliability checks

## Tech Stack

- Python
- Flask
- Docker
- Kubernetes
- Kind
- kubectl

## Project Structure

```text
local-platform-engineering-lab/
├── app/
├── docker/
├── kubernetes/
└── README.md

CI Pipeline

This project includes a GitHub Actions CI pipeline that runs on push and pull requests.

The pipeline validates:

- Python application syntax
- Python dependencies
- Docker image build
- Kubernetes manifest syntax using kubectl dry-run

This simulates the CI stage of a DevOps workflow before deployment to a local Kubernetes environment.