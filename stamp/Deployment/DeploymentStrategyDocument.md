 Deployment Strategy Document
📌 Overview
This document outlines the deployment strategy used for the stamp-backend Node.js application, detailing the CI/CD workflow in GitLab, image handling, and the deployment process to Google Kubernetes Engine (GKE).

⚙️ Pipeline Flow
The CI/CD pipeline consists of the following stages:

Build

Test

Deploy to Development

Deploy to Production

Each stage is executed based on Git branch conditions and is designed to automate the entire delivery lifecycle.

🔨 1. Build Stage
Trigger: Runs on main and dev branches.

Purpose: Builds the Docker image for the backend.

Tools:

docker:24.0-dind (Docker-in-Docker)

google/cloud-sdk (for GCP CLI)

Steps:

Authenticates using a GCP service account.

Sets the project based on branch:

main → production project

dev → development project

Builds the Docker image.

Pushes the image to Google Container Registry (GCR).

🧪 2. Test Stage
Includes:

Unit Tests (with Jest)

Security Test placeholder (can be extended with SAST/Trivy)

Performance Test placeholder

Artifacts:

Test coverage (coverage/)

Test results (junit.xml)

🚀 3. Deployment to Development
Trigger: Only runs on dev branch.

Cluster: stmap-cluster-test (dev GKE cluster)

Process:

Installs gettext-base for variable substitution.

Authenticates with the GKE cluster.

Applies:

ConfigMap: k8s/configmap-dev.yaml

Deployment: k8s/deployment.dev.yaml (with envsubst)

Monitors rollout with kubectl rollout status.

🚀 4. Deployment to Production
Trigger: Only runs on main branch.

Cluster: stmap-cluster (prod GKE cluster)

Process is identical to development, but uses:

ConfigMap: k8s/configmap-prod.yaml

Deployment: k8s/deployment.prod.yaml

☁️ GCP Resources Used
Google Kubernetes Engine (GKE) for app hosting.

Google Container Registry (GCR) for storing Docker images.

Service Account Authentication using JSON key (/tmp/key.json).

kubectl for applying Kubernetes configurations.

🔐 Secrets Management
Credentials are managed via a Google Service Account JSON.

Sensitive variables like CI_COMMIT_SHA, GKE_ZONE, and project IDs are stored securely in the GitLab CI/CD environment.


