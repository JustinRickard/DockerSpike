# Docker and Kubernetes Spike-out

In linux, you may need to prefix the below commands with `sudo`. 

## Download the dependencies

Download the dependencies
run `yarn`

## Run the app locally without docker

run `yarn start`

## Create a docker image

run `docker build . -t <app-name>`

## Run the docker image

The `-d` flag runs it in detached mode.

run `docker run -d -p <PORT>:3000 --name <container-name> <app-name>:<tag>`

e.g. `docker run -d -p 8080:3000 --name myapp myapp:latest`

## Stop the docker image

run `docker stop <container-name>`

e.g. `docker stop myapp`

## Delete the docker container

run `docker container rm <container-name>`

e.g `docker container rm myapp`

## Delete the docker image

run `sudo docker rmi <app-name> --force`
e.g. `sudo docker rmi myapp --force`