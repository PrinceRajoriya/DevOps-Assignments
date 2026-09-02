# 🐳 Docker — Application Deployment

<p align="center">
  <img src="https://raw.githubusercontent.com/docker-library/docs/master/_config/logo.png" width="110" alt="Docker Logo"/>
</p>

<h1 align="center">🚀 Application Deployment Using Docker</h1>

<p align="center">
  <b>DevOps Assignment — Group 2</b>
</p>

<p align="center">
  <i>Learn • Build • Containerize • Deploy • Automate</i>
</p>

<p align="center">

![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?style=for-the-badge\&logo=docker\&logoColor=white)
![DevOps](https://img.shields.io/badge/DevOps-Deployment-6C63FF?style=for-the-badge)
![GitHub](https://img.shields.io/badge/GitHub-Version%20Control-181717?style=for-the-badge\&logo=github)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Automation-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

</p>

---

## 🌟 About This Project

This repository is created for the **DevOps Assignment — Group 2** and focuses on **Docker as an application deployment tool**.

The project explains Docker from the fundamentals to practical deployment, including:

* 🐳 Docker fundamentals
* 🏗️ Docker architecture
* 📦 Images and containers
* 📝 Dockerfile
* 🚀 Application deployment
* 🔌 Port mapping
* 💾 Volumes
* 🌐 Networking
* ⚙️ Docker Compose
* ☁️ Docker Hub / Registries
* 🔄 CI/CD integration
* 🔐 Docker security
* 🛠️ Troubleshooting
* 📚 Docker commands and cheat sheets

> **Main Goal:** Understand how Docker packages an application and its dependencies into a portable container that can be deployed consistently across environments.

---

# 🎯 Learning Objectives

By completing this repository, you will understand:

```text
Docker Fundamentals
       ↓
Docker Images
       ↓
Docker Containers
       ↓
Dockerfile
       ↓
Build Image
       ↓
Run Container
       ↓
Networking + Volumes
       ↓
Docker Compose
       ↓
Docker Registry
       ↓
CI/CD
       ↓
Application Deployment
```

---

# 🧠 What is Docker?

**Docker** is a platform used to package, distribute, and run applications inside lightweight isolated environments called **containers**.

Instead of installing an application and all its dependencies manually on every machine, Docker allows us to package them together.

### Without Docker

```text
Application
    +
Dependencies
    +
Runtime
    +
Configuration
    ↓
Different Environment
    ↓
❌ Compatibility Problems
```

### With Docker

```text
Application
     +
Dependencies
     +
Runtime
     +
Configuration
     ↓
🐳 Docker Image
     ↓
📦 Container
     ↓
🚀 Running Application
```

---

# 💡 Why Docker?

Docker helps solve the famous:

> **"It works on my machine!"**

problem.

### Docker provides:

| Feature             | Benefit                                         |
| ------------------- | ----------------------------------------------- |
| 📦 Containerization | Packages applications with dependencies         |
| 🚀 Fast Deployment  | Containers start quickly                        |
| 🔄 Consistency      | Same environment across systems                 |
| 🌍 Portability      | Run applications across compatible environments |
| 🔒 Isolation        | Separate application environments               |
| 📈 Scalability      | Easy to create multiple containers              |
| ⚙️ Automation       | Works well with CI/CD                           |
| 🔧 Reproducibility  | Dockerfiles define repeatable builds            |

---

# 🏗️ Docker Architecture

```text
                 👨‍💻 Developer
                      │
                      ▼
                ┌─────────────┐
                │ Docker CLI  │
                └──────┬──────┘
                       │
                       ▼
                ┌─────────────┐
                │Docker Engine│
                │   /Daemon   │
                └──────┬──────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      📦 Images    🚀 Containers   🌐 Networks
                       │
                       ▼
                  💾 Volumes
                       │
                       ▼
                 🖥️ Application
```

---

# 📚 Core Docker Concepts

## 📦 Docker Image

An image is a **read-only package/template** used to create containers.

Example:

```bash
nginx:latest
node:20
mysql:8
```

---

## 🚀 Docker Container

A container is a **running instance of an image**.

```text
Docker Image
     │
     ├── Container 1
     ├── Container 2
     └── Container 3
```

One image can create multiple containers.

---

## 📝 Dockerfile

A Dockerfile contains instructions used to build a Docker image.

Example:

```dockerfile
FROM node:20

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

### Dockerfile Workflow

```text
Application Code
       ↓
  Dockerfile
       ↓
 docker build
       ↓
 Docker Image
       ↓
 docker run
       ↓
 Docker Container
```

---

# 🚀 Application Deployment Workflow

The main deployment process covered in this project:

```text
       💻 CODE
          │
          ▼
     📝 Dockerfile
          │
          ▼
    🔨 Docker Build
          │
          ▼
     📦 Docker Image
          │
          ▼
   ☁️ Docker Registry
          │
          ▼
     ⬇️ Docker Pull
          │
          ▼
    🚀 Container
          │
          ▼
   🌐 APPLICATION
```

### Complete Deployment Command Flow

```bash
docker build -t my-app:1.0 .

docker run -d \
  -p 3000:3000 \
  --name my-app \
  my-app:1.0

docker ps

docker logs my-app

docker tag my-app:1.0 username/my-app:1.0

docker push username/my-app:1.0

docker pull username/my-app:1.0

docker run -d \
  -p 3000:3000 \
  --name my-app \
  username/my-app:1.0
```

---

# 🐳 Essential Docker Commands

## 🔍 Docker Information

```bash
docker --version
docker info
docker help
```

---

## 📦 Images

```bash
docker images
docker image ls
docker pull nginx
docker image inspect nginx
docker image rm IMAGE
```

---

## 🚀 Containers

```bash
docker run nginx
docker run -d nginx
docker run -d --name my-nginx nginx

docker ps
docker ps -a

docker start CONTAINER
docker stop CONTAINER
docker restart CONTAINER

docker rm CONTAINER
```

---

## 📋 Container Logs

```bash
docker logs CONTAINER

docker logs -f CONTAINER
```

---

## 🖥️ Access Container Shell

```bash
docker exec -it CONTAINER sh
```

---

# 🔌 Port Mapping

Docker allows applications running inside containers to be accessed from outside.

```bash
docker run -d -p 3000:3000 my-app
```

### Meaning

```text
Host Port : Container Port

3000 : 3000
```

### Request Flow

```text
🌐 Browser
     │
     ▼
localhost:3000
     │
     ▼
Docker Port Mapping
     │
     ▼
Container:3000
     │
     ▼
Application
```

---

# 💾 Docker Volumes

Containers can be temporary. Important application data should therefore be stored using persistent storage such as Docker volumes.

### Commands

```bash
docker volume ls

docker volume create app-data

docker volume inspect app-data
```

### Mount Volume

```bash
docker run -d \
  -v app-data:/data \
  IMAGE
```

### Why Volumes?

```text
Container
   │
   ├── Application
   │
   └── /data
          │
          ▼
      💾 Volume
          │
          ▼
    Persistent Data
```

Useful for:

* 🗄️ Databases
* 📁 Uploaded files
* 💾 Application data
* 📊 Persistent state

---

# 🌐 Docker Networking

Docker networking allows containers to communicate with each other.

### Commands

```bash
docker network ls

docker network create app-network

docker network inspect app-network
```

### Example

```bash
docker run -d \
  --name backend \
  --network app-network \
  backend-image
```

```bash
docker run -d \
  --name frontend \
  --network app-network \
  frontend-image
```

### Architecture

```text
       🌐 Frontend
            │
            ▼
       🌐 Docker Network
         /           \
        ▼             ▼
   ⚙️ Backend      🗄️ Database
```

---

# ⚙️ Docker Compose

Docker Compose is used to define and run **multi-container applications**.

Example architecture:

```text
             🌐 Frontend
                  │
                  ▼
             ⚙️ Backend
                  │
                  ▼
             🗄️ Database
```

Example `compose.yaml`:

```yaml
services:

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    depends_on:
      - backend

  backend:
    build: ./backend
    ports:
      - "5000:5000"
    depends_on:
      - db

  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: appdb
    volumes:
      - db-data:/var/lib/mysql

volumes:
  db-data:
```

### Compose Commands

```bash
docker compose up

docker compose up -d

docker compose ps

docker compose logs

docker compose build

docker compose restart

docker compose down
```

---

# ☁️ Docker Hub & Registries

A container registry stores Docker images so they can be shared and deployed from other machines.

### Workflow

```text
💻 Developer
     │
     ▼
🔨 Build Image
     │
     ▼
🏷️ Tag Image
     │
     ▼
☁️ Docker Registry
     │
     ▼
🖥️ Deployment Server
     │
     ▼
🚀 Container
```

### Commands

```bash
docker login
```

```bash
docker tag my-app:1.0 username/my-app:1.0
```

```bash
docker push username/my-app:1.0
```

```bash
docker pull username/my-app:1.0
```

---

# 🔄 Docker + CI/CD

Docker integrates with CI/CD pipelines to automate application delivery.

```text
        👨‍💻 Developer
             │
             ▼
          GitHub
             │
             ▼
       🔄 CI/CD Pipeline
             │
      ┌──────┴──────┐
      ▼             ▼
   🔨 Build       🧪 Test
      │             │
      └──────┬──────┘
             ▼
        🐳 Docker Image
             │
             ▼
       ☁️ Registry
             │
             ▼
       🚀 Deployment
```

Docker can be integrated with:

* Jenkins
* GitHub Actions
* GitLab CI/CD
* Azure DevOps

---

# 🔐 Docker Security

Security is an important part of container deployment.

### Best Practices

```text
🔐 Use trusted images
      ↓
🔄 Keep images updated
      ↓
👤 Avoid unnecessary root privileges
      ↓
🔑 Never hard-code secrets
      ↓
🔎 Scan images
      ↓
🌐 Expose only required ports
```

### Important Rules

* Use trusted base images.
* Keep images updated.
* Do not store passwords/API keys inside Dockerfiles.
* Avoid running applications as root when unnecessary.
* Scan images for vulnerabilities.
* Expose only required ports.
* Use secure secret/configuration management.

---

# 🛠️ Docker Troubleshooting

## Container is not running

```bash
docker ps -a
docker logs CONTAINER
```

---

## Port already in use

Change the host port:

```bash
docker run -p 8080:3000 IMAGE
```

---

## Image not found

```bash
docker images
docker pull IMAGE
```

---

## Inspect container

```bash
docker inspect CONTAINER
```

---

## Check resource usage

```bash
docker stats
```

---

## Check Docker disk usage

```bash
docker system df
```
---

# 📅 Learning Roadmap

```text
WEEK 01
🐳 Docker Basics
        ↓
WEEK 02
📦 Images & Containers
        ↓
WEEK 03
📝 Dockerfile
        ↓
WEEK 04
💾 Volumes + Networking
        ↓
WEEK 05
⚙️ Docker Compose
        ↓
WEEK 06
☁️ Docker Hub
        ↓
WEEK 07
🚀 Application Deployment
        ↓
🔄 CI/CD + Security
```

---

# 🧪 Practical Assignments

| Assignment | Topic          | Practical                           |
| ---------- | -------------- | ----------------------------------- |
| 01         | Docker Basics  | Install Docker and run Nginx        |
| 02         | Dockerfile     | Create custom application image     |
| 03         | Docker Compose | Deploy multi-container application  |
| 04         | Networking     | Connect containers                  |
| 05         | Deployment     | Deploy application using Docker     |
| 06         | Final Project  | Complete Docker deployment workflow |

---

# 📊 Docker vs Virtual Machines

| Feature         | Docker                 | Virtual Machine      |
| --------------- | ---------------------- | -------------------- |
| Virtualization  | OS-level               | Hardware-level       |
| Size            | Usually lightweight    | Usually larger       |
| Startup         | Fast                   | Comparatively slower |
| OS              | Uses host-kernel model | Guest OS required    |
| Deployment      | Very fast              | Comparatively slower |
| Best suited for | Applications/services  | Full OS environments |

---

# ⭐ Advantages of Docker

* 🚀 Fast deployment
* 📦 Portable applications
* 🔄 Consistent environments
* ⚡ Lightweight containers
* 🔧 Easy application packaging
* 🌐 Microservices support
* 🔄 CI/CD integration
* 📈 Easy scaling
* 🧪 Useful for testing
* ☁️ Cloud-friendly

---

# ⚠️ Limitations

Docker is powerful, but it is not a solution for every problem.

* Security requires proper configuration.
* Networking can become complex.
* Persistent storage needs planning.
* Container management becomes harder at large scale.
* Large systems may require an orchestration platform such as Kubernetes.

---

# 🎓 Viva Questions

### 1. What is Docker?

Docker is a platform used to package and run applications inside containers.

### 2. What is a Docker image?

A Docker image is a packaged template used to create containers.

### 3. What is a container?

A container is a running instance of a Docker image.

### 4. What is Dockerfile?

A Dockerfile contains instructions for building a Docker image.

### 5. What is Docker Hub?

Docker Hub is a container registry service used to store and distribute images.

### 6. What is port mapping?

Port mapping connects a host port to a container port.

Example:

```bash
-p 3000:3000
```

### 7. Why are Docker volumes used?

Volumes provide persistent storage for data that should survive container replacement.

### 8. What is Docker Compose?

Docker Compose is used to define and run multi-container applications.

### 9. Why is Docker useful in deployment?

Docker provides consistent, portable, repeatable application packaging and execution.

### 10. What is CI/CD?

CI/CD is the automated process of building, testing, delivering, and deploying software.

---

# 🏆 Final Deployment Workflow

```text
                💻 SOURCE CODE
                      │
                      ▼
                📝 DOCKERFILE
                      │
                      ▼
                 🔨 BUILD
                      │
                      ▼
                📦 DOCKER IMAGE
                      │
                      ▼
              ☁️ DOCKER REGISTRY
                      │
                      ▼
                  ⬇️ PULL
                      │
                      ▼
                🚀 CONTAINER
                      │
                      ▼
             🌐 DEPLOYED APP
```

---

# 💬 Key Takeaway

> **Docker packages an application and its dependencies into portable containers, making deployment consistent, repeatable, and easier to automate.**

---

# 📚 Documentation & References

* Docker Documentation
* Docker Hub
* Docker Compose Documentation
* Dockerfile Reference
* Containerization & DevOps concepts
* CI/CD documentation

---

<p align="center">

### 🐳 Learn Docker • Build Containers • Deploy Applications 🚀

**DevOps Assignment — Group 2**

</p>

<p align="center">
  <b>Made for learning, experimentation and practical DevOps deployment.</b>
</p>

<p align="center">
  ⭐ Star this repository if you found it useful!
</p>
