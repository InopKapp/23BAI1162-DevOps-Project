# Corporate Company Website - DevOps Pipeline

This repository contains the source code and configuration files for a complete DevOps pipeline deployment of a Corporate Company Website (ABC Technologies).

## Project Overview
The objective of this project is to implement an automated DevOps workflow that enables collaborative development, automated CI/CD deployment, containerized hosting, container orchestration, and continuous monitoring. 

## Technology Stack
* **Version Control:** Git & GitHub
* **Build Tool:** Maven
* **Containerization:** Docker (Tomcat Base Image)
* **Orchestration:** Kubernetes (Deployment & NodePort Service)
* **CI/CD Automation:** Jenkins
* **Monitoring & Metrics:** Nagios, Graphite, Grafana

## Repository Structure
* `src/main/webapp/` - Contains the static HTML/CSS source code for the website.
* `pom.xml` - Maven configuration file to package the website into a `.war` file.
* `Dockerfile` - Docker configuration to host the `.war` file using Tomcat.
* `Jenkinsfile` - The Jenkins pipeline script that automates the checkout, build, and deployment processes.
* `k8s/` - Contains Kubernetes manifests (`deployment.yaml` and `service.yaml`).
* `docker-compose-monitoring.yml` - Docker Compose file used to spin up the monitoring stack (Nagios, Graphite, Grafana).

## How to Run Locally

### 1. Build and Run the Web Application
```bash
# Build the WAR file using Maven
mvn clean package

# Build the Docker image
docker build -t corporate-website:v1 .

# Run the application locally
docker run -d -p 8080:8080 --name corporate-website corporate-website:v1
```

### 2. Deploy to Kubernetes
Ensure Kubernetes is enabled in your environment (e.g., Docker Desktop).
```bash
# Apply the manifests
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

# Verify deployment
kubectl get pods
kubectl get services
```

### 3. Start the Monitoring Stack
```bash
docker compose -f docker-compose-monitoring.yml up -d
```
* **Grafana:** `http://localhost:3000`
* **Nagios:** `http://localhost:8080`
* **Graphite:** `http://localhost:8081`

## Project Screenshots

<details>
  <summary>Click to view screenshots of the implementation.</summary>

  <br>
  
  ![Screenshot 1](images/Screenshot%202026-07-02%20235725.png)
  ![Screenshot 2](images/Screenshot%202026-07-03%20000500.png)
  ![Screenshot 3](images/Screenshot%202026-07-03%20000605.png)
  ![Screenshot 4](images/Screenshot%202026-07-03%20000648.png)
  ![Screenshot 5](images/Screenshot%202026-07-03%20000709.png)
  ![Screenshot 6](images/Screenshot%202026-07-03%20000748.png)
  ![Screenshot 7](images/Screenshot%202026-07-03%20000811.png)
  ![Screenshot 8](images/Screenshot%202026-07-03%20000858.png)
  ![Screenshot 9](images/Screenshot%202026-07-03%20002312.png)
  ![Screenshot 10](images/Screenshot%202026-07-03%20002544.png)
  ![Screenshot 11](images/Screenshot%202026-07-03%20002829.png)
  ![Screenshot 12](images/Screenshot%202026-07-03%20002852.png)
  ![Screenshot 13](images/Screenshot%202026-07-03%20004353.png)
  ![Screenshot 14](images/Screenshot%202026-07-03%20125845.png)

</details>
