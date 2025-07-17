# 🐳 Docker Image Registry

A **Docker Image Registry** is a storage and distribution system for Docker images. It allows you to **push**, **pull**, and **manage Docker images** in a centralized way.

---

## 🏛️ Types of Registries

| Type            | Examples                          | Use Case                             |
|-----------------|-----------------------------------|--------------------------------------|
| **Public**      | Docker Hub, GitHub Container Reg. | Open-source & public sharing         |
| **Private**     | AWS ECR, GCR, Harbor, Artifactory | Secure, internal company usage       |
| **Self-hosted** | Local Docker Registry             | Offline or custom controlled setup   |

---

## 🚀 Project Overview

We built a basic Node.js HTTP server, containerized it using `node:18-alpine` (a minimal base image), and deployed the image to Docker Hub.

This is ideal for:
- Learning Docker basics
- Creating optimized images
- Practicing CI/CD pipelines

---
## Building and Running the Custom Docker Image 🚀

## 📁 Project Structure

```
my-app/
├── server.js # Node.js app
├── package.json # Dependencies
├── Dockerfile # Docker instructions
```
--- 

### 📝  Step 1: Create App Files: `server.js`

```const http = require('http');
const port = 3000;

const server = http.createServer((req, res) => {
  res.end('Custom Docker image is running!');
});

server.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});

```

### 📝  Step 2: package.json `package.json`

```
{
  "name": "light-app",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  }
}

```

### 📝  Step 3: Create Dockerfile

```
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --only=production
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]

```
### 🧱  Step 4: Build Docker Image

```
docker build -t <yourdockerhubusername/image_name> .
```
🔁 Replace <yourdockerhubusername> with your actual Docker Hub username.

Example :
```
 docker build -t anikdevops/custom-app:v1 .
```
### 🧪  Step 5: Run Locally
```
docker run -p 3000:3000 anikdevops/custom-app:v1
```
🌐 Test in browser:
`http://localhost:3000`

### 🔐  Step 6: Login to Docker Hub
```
docker login
```
### ☁️ Step 7: Push to Docker Hub

```
docker push <yourdockerhubusername/image_name>
```
Example :
```
docker push anikdevops/custom-app:v1
```
✅ Image is now available at:
`https://hub.docker.com/r/anikdevops/custom-app`
