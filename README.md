# Create-docker-image-locally-and-pushed-to-ECR
build, tag a docker image locally and push it to AWS ECR
# 🐳 Build and Push Docker Image to AWS ECR (Local Workflow)

This guide explains how to build a Docker image locally and push it to Amazon Elastic Container Registry (ECR) manually.

---

## 🔧 Prerequisites

- Docker installed and running
- AWS CLI installed and configured (`aws configure`)
- IAM user with the necessary ECR permissions (e.g., `ecr:GetAuthorizationToken`, `ecr:PutImage`, etc.)

---

## 🛠️ Steps

### 1. Authenticate Docker with AWS ECR

Run this command to login Docker to your AWS ECR registry:

```bash
aws ecr get-login-password --region us-east-1 \
  | docker login --username AWS --password-stdin AWS_Account_ID.dkr.ecr.us-east-1.amazonaws.com
2. Build your Docker image locally
Make sure you have a Dockerfile in your project directory, then build the image:

bash
Copy
Edit
docker build -t sample-image-1.1:latest .
3. Tag the Docker image for your ECR repository
Tag your local image with your AWS account and repository info:

bash
Copy
Edit
docker tag sample-image-1.1:latest AWS_Account_ID.dkr.ecr.us-east-1.amazonaws.com/sample_app:latest
4. Push the Docker image to AWS ECR
Push the tagged image to your ECR repository:

bash
Copy
Edit
docker push AWS_Account_ID.dkr.ecr.us-east-1.amazonaws.com/sample_app:latest
📦 Create ECR repository (if not already created)
If you don't have the ECR repository sample_app, create it with:

bash
Copy
Edit
aws ecr create-repository --repository-name sample_app --region us-east-1
