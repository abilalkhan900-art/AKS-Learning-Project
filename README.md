# AKS Basic Website Project

A simple, scalable web server running on Azure Kubernetes Service (AKS) with a custom HTML landing page.

## 🚀 Overview
This project demonstrates how to deploy a containerized Nginx web server to AKS. It includes a workaround for environments where local Docker or ACR Build Tasks are restricted by using Kubernetes **ConfigMaps** to inject custom content into a standard image.

## 🛠️ Tech Stack
* **Infrastructure:** Azure Kubernetes Service (AKS)
* **Registry:** Azure Container Registry (ACR)
* **Orchestration:** Kubernetes (v1.33+)
* **Web Server:** Nginx (Alpine-based)

## 📁 Project Structure
* `index.html`: The custom website landing page.
* `deployment.yaml`: The Kubernetes manifest containing the Deployment and LoadBalancer Service.
* `Dockerfile`: (Optional) For building custom images.

## ⚙️ How it Works (The ConfigMap Workaround)
Since ACR Tasks and local Docker were unavailable, this project uses a "Volume Mount" strategy:
1. The `index.html` is stored as a **ConfigMap**.
2. The AKS Deployment mounts this ConfigMap as a volume.
3. The file is injected into `/usr/share/nginx/html/` inside the pod, overwriting the default Nginx page without needing a new image build.

## 💻 Quick Start
1. **Apply the ConfigMap:**
   ```powershell
   kubectl create configmap website-html --from-file=index.html
2. **Deploy to AKS:**
   ```powershell
   kubectl get service sample-app-service
3. **Get the IP**
   ```powershell
   kubectl get service sample-app-service
