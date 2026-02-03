# 🚀 Node.js Express TypeScript Deployment

A production-ready boilerplate for building a **Node.js Express server using TypeScript**, containerizing it with **Docker**, and deploying it to **AWS ECS Fargate** via **ECR** and **Application Load Balancer (ALB)**.

---

## 🛠️ Tech Stack

- **Node.js**
- **Express**
- **TypeScript**
- **Docker**
- **AWS**
  - ECR (Elastic Container Registry)
  - ECS Fargate
  - Application Load Balancer (ALB)
  - CloudWatch Logs

---

## ⚡ Project Setup

### 1️⃣ Initialize Node.js & Install Dependencies

```bash
# Initialize npm project
npm init -y

# Install runtime dependencies
npm install express


🐳 Docker Setup
Dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npx tsc

EXPOSE 3000

CMD ["node", "dist/index.js"]

# Install dev dependencies
npm install -D typescript ts-node-dev @types/node @types/express
```

Build & Run Locally
```
docker build -t node-deploy .
docker run -p 3000:3000 node-deploy


Open: http://localhost:3000
```

☁️ AWS Deployment
 Configure AWS CLI
 ```
aws --version
aws configure
```

Verify credentials:
```
aws sts get-caller-identity
```
2️⃣ Push Docker Image to Amazon ECR
```
aws ecr get-login-password --region us-east-1 | \
docker login --username AWS --password-stdin <ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com

docker tag node-deploy:latest <ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/node-deploy:latest

docker push <ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/node-deploy:latest
```
3️⃣ Deploy on ECS Fargate
```
Create an ECS Cluster (Fargate).

Create a Task Definition:

Use ECR image

Configure CPU and memory

Container port: 3000

Create a Service:

Launch type: Fargate

Attach Application Load Balancer

Enable CloudWatch logging

Access the app via ALB DNS
```
