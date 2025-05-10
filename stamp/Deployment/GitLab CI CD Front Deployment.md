# GitLab CI/CD Front Deployment Documentation

This document describes the GitLab CI/CD pipeline strategy for deploying a **Flutter Web Application** to **Google Kubernetes Engine (GKE)** using Docker and Google Cloud SDK.

---

## 📦 Pipeline Stages

The pipeline defines the following stages:

```yaml
stages:
  - build
  - test
  - deploy-dev
  - deploy-prod
```

### 1. Build
- **Objective**: Build and push the Docker image to **Google Container Registry (GCR)**.
- **Condition**: Executes on branches `main` and `dev`.
- **Docker Image**: `gcr.io/<PROJECT_ID>/flutter-web-app:<IMAGE_TAG>`

### 2. Test
Includes three types of tests:
- **unit-test**: Basic testing using Jest.
- **security-test**: Placeholder for integration testing.
- **performance-test**: Placeholder for end-to-end testing.

### 3. Deploy to Dev Environment
- **Triggered on**: `dev` branch.
- **GKE Cluster**: `test-cluster` in zone `me-central2` under project `stamptest`.
- **Resources Applied**:
  - `configmap-dev.yaml`
  - `pvc.yaml`
  - `deployment_dev.yaml` (with environment variables substituted)
  - `service.yaml`

### 4. Deploy to Prod Environment
- **Triggered on**: `main` branch.
- **GKE Cluster**: `stmap-cluster` in zone `me-central2` under project `stamp-446516`.
- **Resources Applied**:
  - `configmap-prod.yaml`
  - `pvc.yaml`
  - `deployment_prod.yaml` (with environment variables substituted)
  - `service.yaml`

---

## 🔐 Authentication

Before any stage, the pipeline performs the following steps:

1. Creates a service account key JSON on the fly.
2. Activates the service account using `gcloud auth activate-service-account`.
3. Configures Docker for GCR using `gcloud auth configure-docker`.

---

## 🔧 Environment Variables

| Variable           | Description                                      |
|--------------------|--------------------------------------------------|
| PROJECT_ID_DEV     | GCP project ID for development                  |
| PROJECT_ID_PROD    | GCP project ID for production                   |
| GKE_CLUSTER_dev    | GKE cluster name for dev                        |
| GKE_CLUSTER_prod   | GKE cluster name for prod                       |
| GKE_ZONE           | Google Cloud zone (e.g., `me-central2`)         |
| IMAGE_NAME_DEV     | Image name for dev                              |
| IMAGE_NAME_PROD    | Image name for prod                             |
| IMAGE_TAG          | Tag for the Docker image (commit SHA)           |
| DOCKER_HOST        | Docker host for Docker-in-Docker setup          |

---

## 🧪 Unit Testing (Optional)
```yaml
unit-test:
  image: node:20
  script:
    - npm ci
    - npm run test
```

---

## 🛠 Deployment Files
These files must be located in the `k8s/` directory:
- `configmap-dev.yaml`
- `configmap-prod.yaml`
- `deployment_dev.yaml`
- `deployment_prod.yaml`
- `service.yaml`
- `pvc.yaml`

Each deployment YAML file should use placeholders like `${IMAGE_NAME}` and `${IMAGE_TAG}` which will be dynamically replaced using `envsubst`.

---

## ✅ Tips
- Ensure your service account has the right permissions: **GKE Admin**, **Storage Admin**, and **Viewer**.
- Make sure Dockerfiles exist and reference proper `BASE_URL` if required.
- Always verify cluster connectivity and image existence in `gcr.io`.

---

## 📂 Output
Successful pipeline runs will:
1. Push the Docker image to GCR.
2. Deploy the image to the corresponding GKE cluster.
3. Apply necessary Kubernetes resources.
