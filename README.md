# Multi-Site Deployment on AWS EKS with Ingress

This repository contains the code and configurations for deploying multiple websites using Docker, AWS EKS, and Kubernetes with Ingress.

## Overview
This project showcases the deployment of two websites, a grocery, and a watch site, leveraging Docker containers, AWS EKS for orchestration, and integrating with Route 53 for DNS setup.

## Prerequisites
Ensure you have the following installed:
- Docker
- AWS CLI
- kubectl

## Docker Images
- Grocery site: `docker pull bsbiradar/my-shop-ingress:v1`
- Watch site: `docker pull bsbiradar/my-watch-ingress:v1`

## AWS EKS Cluster
1. Create an EKS cluster with two nodes.

## Kubernetes Deployments and Services

### Deploy Grocery site:
```bash
cd Kubernetes/Grocery 

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml


cd Kubernetes/Watch

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

#Ref to deploy ingress Controller
https://docs.nginx.com/nginx-ingress-controller/installation/installing-nic/installation-with-manifests/

# Download the Ingress Controller
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

# Load balancer
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml

# Apply the Ingress rule to visit sites
kubectl apply -f name-ingress.yaml

# Check load balancer 
kubectl get svc -n ingress-nginx
