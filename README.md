# DevOps FastAPI Project 🚀

This is a simple FastAPI application used to demonstrate a DevOps CI/CD pipeline using:

- **Docker**
- **Jenkins**
- **Kubernetes** (optional)
- **GitHub**

## 📦 Features

- FastAPI backend with auto-reload
- Dockerized app build
- Jenkins CI pipeline for building & deploying
- Versioned Docker images (tagged builds)

## 🐳 Docker Commands

```bash
docker build -t fastapi-app:latest .
docker run -d -p 8000:8000 fastapi-app:latest

