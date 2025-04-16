# Project Name: Coworking Space Microservice

## Overview

This project deploys a Coworking Space microservice using Kubernetes, Docker, and AWS. The service is designed to manage coworking space operations, using PostgreSQL for data storage and Flask for the web API. The deployment process is automated using AWS CodeBuild to build and push images to ECR, monitoring with CloudWatch.

### Dependencies
#### Local Environment
1. Python Environment 
2. Docker CLI 
3. Kubectl


#### Remote Resources
1. AWS CodeBuild - build Docker images remotely
2. AWS ECR - host Docker images
3. Kubernetes Environment with AWS EKS - run applications in k8s
4. AWS CloudWatch - monitor activity and logs in EKS


Updated by Aravind on 16th April
---------------------------------


### Setup
#### 1. Create EKS cluster and update the kubeconfig

install latest K8'services version
----------------------------------
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin

Create an EKS Cluster
-----------------------
eksctl create cluster --name my-eks-cluster --region us-east-1 --version 1.28 --nodegroup-name my-node-group --node-type t3.small --nodes 1 --nodes-min 1 --nodes-max 2

Update the Kubeconfig
-----------------------
aws eks --region us-east-1 update-kubeconfig --name my-eks-cluster

### 2. Create a postgres database
followed the instaruction within the course

### 3. Running the Analytics Application Locally
In the `analytics/` directory:

1. Install dependencies

2. Run and verify the application 

### 4. Create a buildProject in CodeBuild console and set variables

project created in codebuild with below environment variables

AWS_DEFAULT_REGION 		us-east-1
IMAGE_REPO_NAME 		coworking
AWS_ACCOUNT_ID 			734133008668
DOCKERHUB_TOKEN			xxxxxxxxxxxx  (for unlimited docker pulls)
DOCKERHUB_USERNAME		arbaravind

### 5. Create a private repository in ECR for docker images

1. created my `buildspec.yaml` in the root folder: to automate docker build and push it to the ECR

- start build

### Deploy application

1. created `configmap.yaml`, secrets.yml and `coworking.yaml` in the deployment/

- kubectl get svc

- AWS CloudWatch Container Insights created and logs for the applicationsi s available in the screensho

- ***ALL screenshots are under the folder 'screenshots and Evidences'


