# 🐳 Docker Lab: Hello Web Server

This lab teaches you how to create a simple Dockerized web server, run it with Docker Compose, and automate image publishing with GitHub Actions.

---

## 📁 Project Structure

- `app/index.html` – HTML content served by Nginx
- `Dockerfile` – Defines the container
- `docker-compose.yml` – Orchestrates services
- `.github/workflows/` – CI pipeline to build and push
- `.dockerignore` – Prevents unnecessary files in build

---

## 🚀 Quick Start

### 🧪 Build and Run with Docker
```bash
docker build -t docker-lab .
docker run -p 8080:80 docker-lab
