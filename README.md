# minikube 

#minikube installation

sudo apt update

sudo apt install curl apt-transport-https

curl -O https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo cp minikube-linux-amd64 /usr/local/bin/minikube

sudo chmod 755 /usr/local/bin/minikube

minikube version

sudo snap install kubectl --classic


curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"


chmod +x ./kubectl


sudo mv ./kubectl /usr/local/bin/kubectl


minikube start

minikube status

minikube addons list


##=============================
## Point Docker to Minikube's internal daemon:

eval $(minikube docker-env)

## Build the Docker Images

cd ~/docker/Crick12_Admin

docker build -t crick12-admin:v1 .

cd ~/docker/Crick12_App

docker build -t crick12-app:v1 .

cd ~/docker/crick12_web

docker build -t crick12-web:v1 .


##Create Kubernetes YAML Files

###  ~/k8s-manifests/
### ├── admin-deployment.yaml
##  ├── admin-service.yaml
### ├── app-deployment.yaml
### ├── app-service.yaml
### ├── web-deployment.yaml
### ├── web-service.yaml
### └── ingress.yaml  # Optional

##Then apply your Kubernetes manifests:

kubectl apply -f ~/k8s-manifests/

##Check Pods

kubectl get pods

## Access Your Applications

## Use minikube service to get URLs:

minikube service crick12-admin-service

minikube service crick12-app-service

minikube service crick12-web-service

## Check your services:

kubectl get svc


