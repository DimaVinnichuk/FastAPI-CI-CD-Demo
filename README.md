[![CI Pipeline](https://github.com/DimaVinnichuk/FastAPI-CI-CD-Demo/actions/workflows/ci.yaml/badge.svg)](https://github.com/DimaVinnichuk/FastAPI-CI-CD-Demo/actions/workflows/ci.yaml)
# FastAPI + Docker + CI/CD Pipeline

This project demonstrates the automation of the development and deployment cycle for a web application using modern DevOps tools.

Live project link: [https://fastapi-ci-cd-demo.onrender.com/](https://fastapi-ci-cd-demo.onrender.com)

---

## Implemented Functionality

### 1. Backend API
- Developed a web interface based on **FastAPI**.
- Configured automatic Swagger documentation generation at the `/docs` endpoint.

### 2. Containerization
- Created a `Dockerfile` for application packaging.
- Configured the service to run within a Docker container to ensure environment parity between development and production.

### 3. Continuous Integration (GitHub Actions)
Implemented a workflow in `.github/workflows/ci.yml` that automatically triggers on every `push` and performs the following stages:
- **Environment Setup:** Python environment preparation and dependency installation.
- **Automated Testing:** Execution of unit tests using the `pytest` framework.
- **Docker Build Validation:** Verification of the Docker image build process for configuration errors.

### 4. Continuous Deployment
- Configured automated service updates on the **Render** platform via Deploy Webhooks.
- The deployment process is initiated only after the successful completion of all testing stages in GitHub Actions.

### 5. Activity Monitoring (Keep-Alive)
- Created an additional workflow (`keep_alive.yml`) that uses a `cron` schedule to perform periodic requests to the API.
- This prevents the service from entering "Spin down" mode on the hosting's free tier, ensuring fast system response times.

---

## Tech Stack
- **Language:** Python
- **Framework:** FastAPI
- **Testing Tools:** Pytest
- **Infrastructure:** Docker, GitHub Actions
- **Hosting:** Render

## Local Setup
To run the project locally using Docker, use the following commands:

```bash
docker build -t fastapi-app .
docker run -p 80:80 fastapi-app
