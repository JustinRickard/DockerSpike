# Docker and Kubernetes Spike-out

In linux, you may need to prefix the below commands with `sudo`. 

## Download the dependencies
Download the dependencies
run `yarn`

## Run the app locally without docker
run `yarn start`

## Create a docker image
run `docker build -t <app-name>`

## Run the docker image
The `-d` flag runs it in detached mode.
run `docker run -d -p <PORT>:3000 <app-name>:<tag>`
e.g. `docker run -d -p 8080:3000 myapp:latest`

## Stop the docker image
Find the container:
run `docker container ls`
run `docker stop <CONTAINER_ID>`