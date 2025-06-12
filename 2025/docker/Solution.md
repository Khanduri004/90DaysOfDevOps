**Docker: Simplifying Modern Application Development**

🔹 **Understanding Docker**

Docker is a platform designed to make it easier to build, deploy, and run applications using containers. Containers package your code, system libraries, and settings into one neat bundle, ensuring your application runs reliably in any environment.

**Why Docker?**

Simplifies deployment and CI/CD pipelines

Ensures consistency across development, testing, and production

Enables microservices and scalable systems

### 🔹 Virtualization vs. Containerization

| Feature         | Virtual Machines             | Containers                    |
|-----------------|------------------------------|-------------------------------|
| OS Overhead     | High (full OS per VM)        | Low (share host OS kernel)    |
| Boot Time       | Minutes                      | Seconds                       |
| Resource Usage  | Heavy                        | Lightweight                   |
| Isolation Level | Strong                       | Moderate (namespace-based)    |


Containers are faster, more efficient, and ideal for deploying apps in cloud-native environments.

🔹 **Docker Architecture & How It Works**

🧱 **Docker Engine**

A client-server application with:

Docker Daemon (dockerd): Manages images, containers, and networks.

Docker CLI: Command-line tool to interact with Docker.

📦 **Containers vs. Images**

Image: A read-only template (e.g., Ubuntu with Java installed).

Container: A running instance of an image (with its own environment).

🌐 **Docker Registry**

Docker Hub: Default public registry to pull/push images.

🏃‍♂️ Running Containers
🔹 Essential Docker Hands-On
```
docker run hello-world
docker run -it ubuntu bash
```
📝 **Writing a Dockerfile**
```
# Simple Python App
FROM python:3.9
COPY app.py .
CMD ["python", "app.py"]
```
🚀 **Build & Run in Containers**
Java
```
docker build -t java-app .
docker run java-app
```
Python
```
docker build -t python-app .
docker run python-app
```
JavaScript (Node.js)
```
FROM node:18
COPY . .
RUN npm install
CMD ["node", "index.js"]
```
⚡ **Advanced Docker Concepts**

🔸 **Distroless Images & Multi-Stage Builds**

Distroless: No package manager/shell; more secure and lightweight

Multi-stage: Compile code in one stage, copy to minimal image in next
```
# Multi-stage for Go
FROM golang:1.20 AS builder
WORKDIR /app
COPY . .
RUN go build -o app

FROM gcr.io/distroless/static
COPY --from=builder /app/app /
CMD ["/app"]
```

🔸 **Delete All Images (Without System Prune)**
``
docker rmi $(docker images -aq)
```
🔸 **Docker Hub**
```
# Tag & push image
```
docker tag my-app username/my-app:v1

docker push username/my-app:v1
# Pull image
docker pull username/my-app:v1
```
🔸 Docker Volumes
```
# Create volume
docker volume create myvol
# Mount volume
docker run -v myvol:/data alpine
```
**Docker Networking**
```
# Create network
docker network create mynet
# Run containers on it
docker run -d --name c1 --network mynet nginx
docker run -d --name c2 --network mynet busybox sleep 3600
```
**Network Types:**

There are 7 types of network but the 4 below mentioned are used often :

1) Bridge (default)
2) Host (shares host network)
4) Overlay (used in Docker Swarm)
5) None (no network)

**Docker Compose & Docker Scout**

Docker Compose: Define multi-container apps using docker-compose.yml
```
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
  db:
    image: postgres
```

**Docker Scout: Analyze image security and dependencies.**
```
docker scout quickview my-app
```
**Conclusion**
Docker is an essential tool for modern DevOps and software development.
With containers, you get reliable deployments, fast builds, and consistent environments—making your development process
smooth and scalable.

Happy Dockering! 🐳
