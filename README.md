# Kubernetes Web Application Deployment – README

This project contains Kubernetes manifests for deploying a web application using a Deployment and exposing it through a Service and an Ingress. The setup is designed to run a frontend web application container and make it accessible externally through an NGINX Ingress Controller.

## Files Included

### 1. Deployment Manifest
Defines the webapp Deployment that runs the frontend application.

Creates 2 replicas of the frontend pod.  
Runs the container image:  
misterj25/letstravel-web-image:latest

Exposes container port 80.

### Purpose
This ensures that the frontend application is always running with multiple replicas for availability and load balancing.

### 2. Ingress Manifest
Defines an Ingress resource named main-ingress.

Uses nginx as the Ingress controller.  
Includes a rewrite rule:  
nginx.ingress.kubernetes.io/rewrite-target: /

Routes external traffic on path / to the frontend service on port 80.

## Purpose
This makes the application accessible externally via an ingress endpoint, handling routing from the cluster entry point to the backend service.

## Application Flow

User → Ingress (NGINX) → Service (frontend) → Pods (webapp deployment)

## How to Apply the Manifests

Apply each file using:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml

## Check resources:

kubectl get pods
kubectl get svc
kubectl get ingress

## Container Image Used

## The application is deployed using:
misterj25/letstravel-web-image:latest
This container is assumed to serve the frontend UI for the project.

## Requirements

Kubernetes cluster
NGINX Ingress Controller installed
kubectl configured to connect to your cluster
