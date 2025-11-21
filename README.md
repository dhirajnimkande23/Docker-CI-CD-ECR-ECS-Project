# Docker-CI-CD-ECR-ECS-Project
This project sets up a complete CI/CD workflow for containerized applications using Jenkins, Docker, Amazon ECR, and ECS. It includes build automation, image versioning, and zero-downtime deployments.


# 🚀 Docker CI/CD Pipeline with Jenkins, Maven, SonarQube, ECR & ECS

### **End-to-End DevOps Automation Project**

This repository demonstrates a complete CI/CD workflow for containerized Java applications using:

* Jenkins
* Maven
* SonarQube
* Checkstyle
* Docker
* AWS ECR
* AWS ECS
* AWS CLI
* Quality Gates

The pipeline automatically builds code, performs quality checks, builds Docker images, pushes to ECR, and triggers ECS deployment.

---

## 📌 **Pipeline Flow**

```
GitHub → Jenkins → Maven Build → Unit Tests → Checkstyle → SonarQube Scan 
       → Quality Gate → Docker Build → Push to ECR → ECS Deployment → Success
```

---

## 🧩 **Key Features**

* ✔ Automated code fetch from GitHub
* ✔ Maven build + WAR packaging
* ✔ JUnit unit tests
* ✔ Checkstyle validation
* ✔ SonarQube scan + Quality Gate enforcement
* ✔ Multi-stage Docker image build
* ✔ Push image to AWS ECR
* ✔ ECS Deployment with **Force New Deployment**
* ✔ Automatic cleanup of Docker images

---

## 🏗️ **Technologies Used**

| Tool / Technology | Purpose                             |
| ----------------- | ----------------------------------- |
| Jenkins           | CI/CD Orchestration                 |
| Maven 3.9         | Build & Dependency Management       |
| JDK 17            | Java Compilation                    |
| Checkstyle        | Code Formatting Standards           |
| SonarQube         | Code Quality, Bugs, Vulnerabilities |
| Docker            | Containerization                    |
| AWS ECR           | Docker Image Registry               |
| AWS ECS           | Deployment & Orchestration          |
| GitHub            | Version Control                     |

---

## 🔧 **Jenkins Prerequisites**

### **Tools to Configure**

| Tool             | Name in Jenkins |
| ---------------- | --------------- |
| Maven            | `Maven3.9`      |
| JDK              | `JDK17`         |
| Sonar Scanner    | `sonar6.2`      |
| SonarQube Server | `sonarserver`   |

### **Credentials Needed**

| ID                       | Purpose                      |
| ------------------------ | ---------------------------- |
| `awscreds`               | AWS Access Key + Secret      |
| `ecr:us-east-1:awscreds` | ECR Login Auth               |
| Sonar Token              | For SonarQube authentication |

---

## 🏛️ **AWS Requirements**

### **ECR**

Repository must exist:

```
095031187881.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg
```

### **ECS**

* Cluster name: **Vprofile**
* Service name: **vprofileappsvc**
* Launch type: **Fargate** or **EC2**

---

## 📦 **Generated Artifacts**

During Jenkins build:

```
target/*.war
```

Docker build context (multi-stage):

```
./Docker-files/app/multistage/
```

Images pushed to ECR:

* `<BUILD_NUMBER>`
* `latest`

---

## 🔥 **Jenkinsfile Used in This Project**

👉 *Tell me “Add Jenkinsfile” and I will embed it cleanly here.*

---

## 🚀 **Pipeline Stages Explained**

### **1️⃣ Fetch Code**

Fetches from GitHub `docker` branch.

### **2️⃣ Maven Build**

```
mvn install -DskipTests
```

### **3️⃣ Unit Tests**

Runs all JUnit tests.

### **4️⃣ Checkstyle**

Validates code formatting.

### **5️⃣ SonarQube Analysis**

Includes:

* Bugs
* Code smells
* Vulnerabilities
* Test coverage
* Checkstyle violations

### **6️⃣ Quality Gate**

Build pauses until SonarQube finishes.

### **7️⃣ Docker Image Build**

Uses multi-stage Dockerfile.

### **8️⃣ Push to ECR**

Pushes:

* build tag
* latest

### **9️⃣ Remove Local Images**

Keeps Jenkins agent clean.

### **🔟 Deploy to AWS ECS**

```
aws ecs update-service --cluster Vprofile --service vprofileappsvc --force-new-deployment
```

Triggers new rollout.

---

## 🧪 **How to Run This Project**

1. Clone this repository
2. Configure Jenkins plugins
3. Create a Pipeline job
4. Select “Pipeline script from SCM”
5. Choose **docker** branch
6. Build the job

Jenkins will execute the pipeline end-to-end.

---

## 🤝 **Contribution**

PRs welcome for:

* Terraform IaC
* Multi-service ECS
* Blue-Green deployment
* GitHub Actions CI/CD
* Kubernetes (EKS) version

---

## ✅ Your README.md is now fixed and GitHub-compatible 🎉

If you want, I can also:

✔ Add your **Dockerfile** section
✔ Embed your **Jenkinsfile**
✔ Add architecture diagrams
✔ Add badges
✔ Add project logo

Just tell me **“Add Dockerfile”** or **“Add Jenkinsfile”** etc.

