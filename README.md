# deployment-docker-sample
Dockers are containers for your applications to run on any device/OS. This repo contains commands &amp; setup instructions to deploy a python app to a Docker.

# Setting Up & Operating Docker on Localhost
1. Build a simple app (python)
2. Install Docker on your device
3. Setup Docker using CLI commands

# Docker CLI Commands
### to check version of docker
docker - - version

### to initialize the docker and create the default files
docker init

### to build the image called 'sample-docker' in the current working directory ( which is '.')
docker build -t sample-docker .

### to run the image 'sample-docker' on local host (127.0.0.1) by mapping the port 8080 of localhost & docker
docker run -p 127.0.0.1:8080:8080 sample-docker

## Your app should be live on http://127.0.0.1:8080/

### to create a volume shared between the container & its underlying host. Volumes allow to data (db & files) to persist even after container shuts down.
> Host source is denoted by "C:\.."
> Destination container is denoted by directory after ":/folder-name.."

docker run -v C:\Users\u1\Documents:/container_folder sample-docker


### to create shared volume by name and attach it between the host & container

docker volume create sample-shared-volume

docker run -v sample-shared-volume:/container_folder

### to create shared volume for the container & attach the port
docker run -v sample-shared-volume:/container_folder -p 127.0.0.1:8080:8080 sample-docker
