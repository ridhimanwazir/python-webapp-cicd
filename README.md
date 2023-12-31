# Python-webapp
Deploying Python webapp on miniKube using CI/CD with Jenkins

## Step 1 — Install Java, Jenkins, Docker, Trivy, minikube, Ansible, and helm

## Step 2 - SonarQube Server

### Use docker to start a Sonarqube Server which will be accessible on `ip:9000`
`docker run -d --name sonar -p 9000:9000 sonarqube:lts-community`

## Jenkins Setup

### Install Jenkins Plugins like JDK, Sonarqube Scanner, Ansible, OWASP Dependency Check, Docker, and Kubernetes
### Enable jdk17, SonarScanner, Docker, and Ansible in Jenkins tools
### Configure sonarQube in the Jenkins system

## Step 3 - 
