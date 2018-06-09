# Docker and Kubernetes Spike-out

The following commands work on linux Ubuntu. You may need to prefix the below commands with `sudo` to run with elevated priviledges.

## Run the app locally (without Docker)

### Download the repository

run `git clone https://github.com/JustinRickard/DockerSpike.git`

### Download the dependencies

run `yarn`

### Run the app

run `yarn start`

### Check the app runs in the browser

Go to `http://localhost:3000`


## Run the app locally with Docker

### Build the docker image

In the root folder, run `docker build . -t dockerspike:1.0.0`

### Run the docker image.

The `-d` flag runs it in detached mode.

e.g. `docker run -d -p 8080:3000 --name dockerspike1 dockerspike:1.0.0`

### Check the app runs in your browser.

Go to `http://localhost:8080`

### Stop the docker container

e.g. `docker stop dockerspike1`

### Delete the docker container

run `docker container rm dockerspike1`

### Delete the docker image

run `sudo docker rmi dockerspike --force`


## Run the app locally with Minikube (local Kubernetes)

### Install Minikube (to run Kubernetes locally)

Installation details at `https://kubernetes.io/docs/tasks/tools/install-minikube/`

### Install virtualbox

Download from `https://www.virtualbox.org/wiki/Downloads`

For linux, run `apt-get install virtualbox`

### Install kubectl (Kubernetes command line interface)

See `https://kubernetes.io/docs/tasks/tools/install-kubectl/`

### Install Minikube

See `https://github.com/kubernetes/minikube/releases`

For linux, run `curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.27.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/`

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

Navigate to the URL in your browser and check the app is running.

### Stop minikube
`minikube stop`


## Run in Google Cloud

### Create a Google Cloud account

In a browser, go to the Google Cloud Console. `https://console.cloud.google.com`

1. Create an account
2. Go to the Kubernetes engine
3. Create a new cluster (recommended: choose the smallest instance type)

### Install the Google Cloud CLI

see `https://cloud.google.com/sdk/`

For installing on Linux with apt-get, see `https://cloud.google.com/sdk/docs/downloads-apt-get`

In your terminal, run `gcloud init` to set up the gcloud CLI.

Select the cluster created earlier to connect to.

Run `gcloud container clusters list` to check your cluster is running with 3 nodes.

### Deploy to the Google Cloud

