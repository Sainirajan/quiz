# 🚀 Quiz App - CI/CD with GitHub Actions & Docker on EC2

A simple quiz application built using **HTML, CSS, and JavaScript**, designed to test basic web development knowledge.

This project is deployed using **GitHub Actions**, **Docker**, and **AWS EC2** with automatic deployment on every push to `main`.

---

## 📁 Project Structure

.
├── index.html
├── css/
│ └── style.css
├── js/
│ ├── questions.js
│ └── script.js
├── Dockerfile
└── .github/
└── workflows/
└── deploy.yml


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


## ⚙️ Dockerfile

```Dockerfile
FROM nginx
COPY . /usr/share/nginx/html
This Dockerfile uses NGINX to serve your static files.

🔐 GitHub Secrets Required
Secret Name	Purpose
EC2_SSH_KEY	Your private .pem file content

🧪 Sample Questions
The js/questions.js file contains an array of quiz questions like:

{
  numb: 1,
  question: "What does HTML stand for?",
  answer: "Hyper Text Markup Language",
  options: [
    "Hyper Tool Markup Language",
    "Hyper Text Markup Language",
    "Hyperlinking Text Mark Language",
    "Hyper Text Multiple Language"
  ]
}
To update questions, simply edit this file and push your changes — GitHub Actions will auto-deploy it.

📦 Commands for Manual Docker Run (if needed)
docker build -t quiz-app .
docker run -d -p 80:80 --name quiz quiz-app
🖥️ Access the App
Once deployed, access the app in your browser:

http://<EC2_PUBLIC_IP>
🙌 Credits
Built by Sai Niranjan
CI/CD powered by GitHub Actions
Hosted on AWS EC2
