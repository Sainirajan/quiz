# 🚀 Quiz App - CI/CD with GitHub Actions & Docker on EC2

A simple quiz application built using **HTML, CSS, and JavaScript**, designed to test basic web development knowledge.

This project is deployed using **GitHub Actions**, **Docker**, and **AWS EC2** with automatic deployment on every push to `main`.

## 🎮 Features

- ✨ Interactive quiz with multiple-choice questions
- 🐳 Dockerized for consistent deployment
- ⚙️ Auto-deployed on AWS EC2 via GitHub Actions
- 🔐 Secrets managed via GitHub Secrets (SSH key)


## 🚀 How It Works

### 1. Code Push
You push changes (like updating `questions.js`) to the `main` branch.

### 2. GitHub Actions Workflow
GitHub Actions triggers `.github/workflows/deploy.yml`, which:

- SSHs into EC2
- Installs Docker (if missing)
- Pulls the latest code
- Builds the Docker image
- Stops any existing container
- Runs a new container on port `80`

### 3. App is Live!  
Visit your EC2 public IP to see the updated quiz app.

