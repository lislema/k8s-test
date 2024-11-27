# Terraform Helm Integration for Kubernetes



## Overview

This repository provides Helm charts for deploying a **web application** in a Kubernetes cluster. The project includes separate charts for:
- A **frontend application** called `web-app`.
- A **backend application** called `web-app-backend`.

The charts are parameterized using `values.yaml` files to allow easy customization of deployment configurations.

---

## Features

- **Frontend (`web-app`)**:
  - Deployed as a Kubernetes Deployment.
  - Exposed via a `LoadBalancer` service on port 80.
  - Configurable replicas, resource limits, and probes.

- **Backend (`web-app-backend`)**:
  - Deployed as a Kubernetes Deployment.
  - Exposed internally via a `ClusterIP` service on port 8080.
  - Configurable replica count, resource requests/limits, and environment variables.

- **Helm Charts**:
  - Simplified deployment of both frontend and backend applications.


## Configuration Files

### Helm Charts
- **`helm/web-app/`**: Helm chart for the frontend application.
- **`helm/web-app-backend/`**: Helm chart for the backend application.

### Terraform (`main.tf`)
- Configures the infrastructure required for Kubernetes.
- Deploys:
  - VPC and subnets.
  - EKS Kubernetes cluster.

---

## Usage

### Prerequisites
1. Install [Terraform](https://www.terraform.io/downloads.html).
2. Install [kubectl](https://kubernetes.io/docs/tasks/tools/) and configure access to your Kubernetes cluster (`~/.kube/config`).
3. Install [Helm](https://helm.sh/docs/intro/install/).

### Steps to Deploy

#### **1. Setup Infrastructure**
1. Navigate to the Terraform directory:

	```
   cd terraform
   ```
   
2. Initialize Terraform:

	```
	terraform init
	```
3. Preview the change 

	```
	terraform plan
	```
4. Apply the terrafrom configuration 

	```
	terrafrom apply
	```
#### **2. Deploy Applications using Helm 


* Navigate to the Helm directory:
	
	For the frontend (web-app):
	
	```
	cd helm/web-app
   helm install web-app ./web-app
	```
	
	For the backend (web-app-backend):

	```
	cd helm/web-app-backend
   helm install web-app ./web-app-backend
	```

* Verify deployments

	```
	kubectl get deployments
	kubectl get services
	```
#### **3 . CleanUp 

* Delete the Helm resources 

	```
	helm uninstall web-app
	helm uninstall web-app-backend
	```
* Destroy the infrastructure

	```
	terraform destroy
	```






