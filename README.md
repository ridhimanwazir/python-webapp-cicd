# Python-webapp
Deploying Python webapp on miniKube using CI/CD with Jenkins in `Ubuntu 22.04`

## Step 1 — Install Java, Jenkins, Docker, Trivy, minikube, Ansible, and helm

[Java](https://www.rosehosting.com/blog/how-to-install-java-17-lts-on-ubuntu-20-04/)

[Jenkins](https://www.jenkins.io/doc/book/installing/linux/)

[Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)

[Trivy](https://aquasecurity.github.io/trivy/v0.18.3/installation/)

[miniKube](https://minikube.sigs.k8s.io/docs/tutorials/wsl_docker_driver/)

[Helm](https://helm.sh/docs/intro/install/)

[Ansible](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)

## Step 2 - SonarQube Server

### Use docker to start a Sonarqube Server which will be accessible on `ip:9000`
`docker run -d --name sonar -p 9000:9000 sonarqube:lts-community`

## Jenkins Setup

- Install Jenkins Plugins like JDK, Sonarqube Scanner, Ansible, OWASP Dependency Check, Docker, and Kubernetes
- Enable jdk17, SonarScanner, Docker, and Ansible in Jenkins tools
- Configure sonarQube in the Jenkins system

## Step 3 - Setup Ansible Repository in Ubuntu

- Create an Inventory file in Ansible
  ```
  cd /etc/ansible
  sudo vi hosts
  ```


