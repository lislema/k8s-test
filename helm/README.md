# Helm Charts for Web Application

This repository contains Helm charts for deploying a web application with two components:
- `web-app`: Frontend application
- `web-app-backend`: Backend application

## Usage

To install the frontend chart:
```bash
helm install web-app ./web-app

To install the backend chart:
helm install web-app-backend ./web-app-backend

## Note 

for packaging tgz  to the public we need to 
helm package ./web-app
helm package ./web-app-backend

and create an index with
  
helm repo index . --url https://your-repo-url

assuming you have git pages set up 
