# 🏋️ Gym Static Website Deployment using Jenkins CI/CD

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Jenkins](https://img.shields.io/badge/CI%2FCD-Jenkins-red)
![Nginx](https://img.shields.io/badge/WebServer-Nginx-green)
![HTML](https://img.shields.io/badge/Frontend-HTML%20%7C%20CSS-blue)

---

# 📌 Project Overview

This project demonstrates how to **deploy a Gym Static Website using Jenkins CI/CD pipeline**.
The goal of the project is to automate the deployment of a static website using **Jenkins pipeline and cloud infrastructure**.

The project simulates a **real-world DevOps workflow** where developers push code to a repository and Jenkins automatically builds and deploys the website to the server.

This project helps in understanding:

* Continuous Integration and Continuous Deployment (CI/CD)
* Jenkins pipeline automation
* Static website hosting
* Automated deployment using Jenkinsfile

---


---

# 🔁 Architecture Workflow

```id="wh2h5h"
Developer
   │
   │ Push Code
   ▼
GitHub Repository
   │
   │ Webhook Trigger
   ▼
Jenkins Server
   │
   │ Pipeline Execution
   ▼
Web Server (Nginx / Apache)
   │
   ▼
Gym Static Website
```

---

# 🧰 Technologies Used

| Technology      | Purpose                |
| --------------- | ---------------------- |
| Jenkins         | CI/CD automation       |
| GitHub          | Source code repository |
| AWS EC2         | Web server hosting     |
| Nginx / Apache  | Web server             |
| HTML / CSS / JS | Static website         |
| Linux           | Server environment     |

---

# 📂 Project Structure

```id="66sgdz"
gym-static-website
│
├── index.html
├── style.css
├── images
│
├── Jenkinsfile
│
└── README.md
```

---

# ⚙️ CI/CD Pipeline Workflow

The pipeline follows these stages:

1. **Code Commit**

   * Developer pushes code to GitHub repository.

2. **Webhook Trigger**

   * GitHub triggers Jenkins automatically.

3. **Pipeline Execution**

   * Jenkins reads the `Jenkinsfile`.

4. **Build Stage**

   * Jenkins fetches the latest code.

5. **Deploy Stage**

   * Jenkins deploys the website to the web server.

6. **Website Live**

   * Updated website becomes available to users.

---

# 🧾 Jenkins Pipeline (Jenkinsfile)

Example Jenkins pipeline used for deployment:

```groovy id="d9or7d"
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/yourusername/gym-static-website.git'
            }
        }

        stage('Deploy Website') {
            steps {
                sh 'sudo cp -r * /usr/share/nginx/html/'
            }
        }

    }
}
```

This pipeline automatically pulls the latest code and deploys it to the web server directory.

---

# ⚙️ Jenkins Setup Steps

### 1️⃣ Install Jenkins

Install Jenkins on a server (EC2 or local machine).

Start Jenkins service:

```bash id="7yl1ss"
sudo systemctl start jenkins
```

Enable Jenkins on boot:

```bash id="x9tqr4"
sudo systemctl enable jenkins
```

---

### 2️⃣ Access Jenkins Dashboard

Open browser:

```id="xkvxt4"
http://SERVER-IP:8080
```

Complete the Jenkins setup wizard.

---

### 3️⃣ Install Required Plugins

Install the following plugins:

* Git Plugin
* Pipeline Plugin
* GitHub Integration Plugin

---

### 4️⃣ Create Jenkins Pipeline Job

Steps:

1. Open Jenkins Dashboard
2. Click **New Item**
3. Select **Pipeline**
4. Configure pipeline to use **Jenkinsfile from repository**

---

### 5️⃣ Configure GitHub Webhook

To enable automatic builds:

1. Go to GitHub repository settings
2. Select **Webhooks**
3. Add Jenkins webhook URL:

```id="ahw8i9"
http://JENKINS-IP:8080/github-webhook/
```

Now Jenkins will trigger automatically when code is pushed.

---

# 🚀 Deployment Process

1. Developer updates website code.
2. Code is pushed to GitHub repository.
3. GitHub webhook triggers Jenkins pipeline.
4. Jenkins clones the repository.
5. Jenkins deploys the files to the web server.
6. Website updates automatically.

---

# 🌍 Access the Website

Open the browser and enter:

```id="jbwthg"
http://SERVER-IP
```

The Gym website will be available to users.

---

# 📸 Project Screenshots

*(Add your project screenshots here)*

### Jenkins Pipeline Execution

![Jenkins Pipeline](images/jenkins-pipeline.png)

### Gym Website Output

![Website Output](images/website-output.png)

---

# 📊 Skills Learned

* Jenkins pipeline creation
* CI/CD automation
* GitHub integration
* Automated deployment
* Web server configuration
* DevOps workflow implementation

---

# 🔮 Future Improvements

Possible enhancements:

* Docker container deployment
* Kubernetes orchestration
* Automated testing stage
* Blue-Green deployment
* Monitoring using Prometheus and Grafana

---

# 👨‍💻 Author

**Sudarshan Mane**
DevOps & Cloud Enthusiast

---

⭐ If you found this project helpful, consider giving the repository a **star on GitHub**.
