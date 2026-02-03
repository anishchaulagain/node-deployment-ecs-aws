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

# Install dev dependencies
npm install -D typescript ts-node-dev @types/node @types/express
