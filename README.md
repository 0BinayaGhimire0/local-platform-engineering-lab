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


Release Pipeline

This project includes a release pipeline triggered by Git tags.

When a version tag such as `v1.0.0` is pushed, GitHub Actions:

- Extracts the version from the Git tag
- Builds a Docker image using the version tag
- Builds a `latest` Docker image
- Simulates a deployment step for a local Kubernetes environment

This demonstrates a release-style CI/CD workflow without using any cloud provider.