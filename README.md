# Python-webapp
Deploying Python webapp on miniKube using CI/CD with Jenkins

# Step 1 — Install Java, Jenkins, Docker, Trivy, minikube, and helm

## Java Installation
`apt install openjdk-17-jdk openjdk-17-jre`

verify installation
`java -v`

## Jenkins installation
`sudo apt update -y`

`wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | tee /etc/apt/keyrings/adoptium.asc`

`echo "deb [signed-by=/etc/apt/keyrings/adoptium.asc] https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list`

`sudo apt update -y`

`curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
                  /usr/share/keyrings/jenkins-keyring.asc > /dev/null`
                  
`echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
                  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
                              /etc/apt/sources.list.d/jenkins.list > /dev/null`
                              
`sudo apt-get update -y`

`sudo apt-get install jenkins -y`

`sudo systemctl start jenkins`

`sudo systemctl status jenkins`

the server will be running on `localhost:8080`

## Install Docker

`sudo apt-get update`

`sudo apt-get install docker.io -y`

`sudo usermod -aG docker $USER`

`sudo chmod 777 /var/run/docker.sock`

`sudo docker ps`

## Install Trivy

`sudo apt-get install wget apt-transport-https gnupg lsb-release -y`

`wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null`

`echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list`

`sudo apt-get update`

`sudo apt-get install trivy -y`

## Install miniKube and configure kubectl

### miniKube
`curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64`

`chmod +x ./minikube`

`sudo mv ./minikube /usr/local/bin/`

`minikube config set driver docker`

### Kubectl
`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`

`chmod +x ./kubectl`

`sudo mv ./kubectl /usr/local/bin/`

`kubectl config use-context minikube`

`minikube delete
minikube start`

This will start your minikube server with the docker driver

## Setup helm

`curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null`

`sudo apt-get install apt-transport-https --yes`

`echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list`

`sudo apt-get update`

`sudo apt-get install helm`

`curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3`

`chmod 700 get_helm.sh`

`./get_helm.sh`


