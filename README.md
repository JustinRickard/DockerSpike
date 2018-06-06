# Docker and Kubernetes Spike-out

The following commands work on linux Ubuntu. You may need to prefix the below commands with `sudo` to run with elevated priviledges.

## Download the dependencies

Download the dependencies

run `yarn`

## Run the app locally without docker

run `yarn start`

## Create a docker image

run `docker build . -t <app-name>`

## Run the docker image (as a container)

The `-d` flag runs it in detached mode.

run `docker run -d -p <PORT>:3000 --name <container-name> <app-name>:<tag>`

e.g. `docker run -d -p 8080:3000 --name myapp myapp:latest`

## Open the app in your browser
e.g. `http://localhost:8080`

## Stop the docker container

run `docker stop <container-name>`

e.g. `docker stop myapp`

## Delete the docker container

run `docker container rm <container-name>`

e.g `docker container rm myapp`

## Delete the docker image

run `sudo docker rmi <app-name> --force`

e.g. `sudo docker rmi myapp --force`

# Kubernetes

## Install Minikube (to run Kubernetes locally)
`https://kubernetes.io/docs/tasks/tools/install-minikube/`

### Install virtualbox
run `apt-get install virtualbox`

### Install kubectl
see `https://kubernetes.io/docs/tasks/tools/install-kubectl/`

### Install Minikube
see `https://github.com/kubernetes/minikube/releases`

run `curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.27.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/`

Ensure that virtualization is enabled in the BIOS. If it is not enabled, minikube will fail to start, indicating this as the reason.

## Run Minikube
`minikube start`

Put the kettle on (this might take a while if running for the first time)

## Deploy the service
`kubectl create -f service.yml`

You can use `apply` in place of create to update an existing service

## Deploy the pods
`kubectl create -f deployment.yml`

You can use `apply` in place of create to update an existing deployment

## Get the URL for the service
`minikube service docker-spike-service --url`

Navigate to the URL and check the app is running.

### Stop minikube
`minikube stop`
