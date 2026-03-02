# 🚀 Node.js + React CI/CD Pipeline using Jenkins & npm

This project demonstrates how to automate the build, test, and delivery process of a simple **Node.js and React application** using **Jenkins Pipeline** and **npm**.

The application renders a basic webpage displaying:

> **Learn React**

The main goal of this project is to understand how **CI/CD (Continuous Integration & Continuous Delivery)** works in a real-world DevOps workflow using Jenkins.

---

## 📌 What This Project Covers

This project walks through:

* Building a React + Node.js application
* Automating dependency installation
* Running tests
* Delivering the application
* Managing everything using **Pipeline-as-Code**

All automation is handled using a **Jenkinsfile**.

---

## 🛠️ Prerequisites

Make sure the following are installed on your system:

* Git
* Docker
* Docker Compose
* Node.js (optional for local testing)

System Requirements:

* Minimum 2 GB RAM
* Minimum 2 GB Storage

---

## 📂 Project Setup

### Step 1: Fork Repository

Fork the sample project to your GitHub account.

---

### Step 2: Clone Repository

```bash
git clone https://github.com/YOUR-GITHUB-USERNAME/simple-node-js-react-npm-app
cd simple-node-js-react-npm-app
```

---

## 🐳 Start Jenkins using Docker

Clone Jenkins quickstart setup:

```bash
git clone https://github.com/jenkins-docs/quickstart-tutorials.git
cd quickstart-tutorials
docker compose --profile node up -d
```

Access Jenkins at:

```
http://localhost:8080
```

Login with:

```
Username: admin
Password: admin
```

---

## ⚙️ Create Jenkins Pipeline

Inside Jenkins:

1. Click **New Item**
2. Enter project name
3. Select **Pipeline**
4. Choose:

```
Pipeline script from SCM
```

5. Select **Git**
6. Enter your forked repository URL

Save the project.

---

## 🧠 Jenkins Pipeline (Jenkinsfile)

Create a file named:

```
Jenkinsfile
```

at the root of your project.

---

### 🔨 Build Stage

Installs project dependencies.

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
```

---

### 🧪 Test Stage

Runs automated tests.

```groovy
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
```

---

### 🚀 Deliver Stage

Runs application and waits for user confirmation.

```groovy
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
```

---

## 📤 Push Changes

```bash
git add .
git commit -m "Added Jenkins Pipeline"
git push
```

---

## ▶️ Run Pipeline

Inside Jenkins:

Click:

```
Build Now
```

Pipeline will execute:

| Stage   | Action                |
| ------- | --------------------- |
| Build   | Installs npm packages |
| Test    | Runs test scripts     |
| Deliver | Runs the application  |

---

## 🌐 View Application

During Deliver stage, Jenkins will generate:

```
http://localhost:3000
```

Open it in your browser to view the app.

---

## 🧹 Cleanup

To stop Jenkins:

```bash
docker compose down
```

---

## 🎯 Outcome

You now have a working CI/CD pipeline that:

* Builds a Node.js + React app
* Runs automated tests
* Deploys the app locally
* Uses Pipeline-as-Code

---

## 📘 Learnings

This project helps understand:

* CI/CD fundamentals
* Jenkins Pipelines
* npm automation
* Docker-based Jenkins setup
* DevOps workflow for frontend apps

---

## 🤝 Contributing

Pull requests are welcome. For major changes, open an issue first.

---

## 📜 License

This project is open-source and available under the MIT License.
