# deployment-docker-sample

Dockers are containers for your applications to run on any device/OS. This repo contains commands & setup instructions to deploy a python app to a Docker.

## Setting Up & Operating Docker on Localhost

1. Build a simple app (python)
2. Install Docker on your device
3. Setup Docker using CLI commands

## Docker CLI Commands

### Check version of docker
```bash
docker --version
```

### Initialize the docker and create the default files
```bash
docker init
```

### Build the image called 'sample-docker' in the current working directory (which is '.')
```bash
docker build -t sample-docker .
```

### Run the image 'sample-docker' on localhost (127.0.0.1) by mapping the port 8080 of localhost & docker
```bash
docker run -p 127.0.0.1:8080:8080 sample-docker
```

**Your app should be live on http://127.0.0.1:8080/**

### Create a volume shared between the container & its underlying host
<!-- Volumes allow data (db & files) to persist even after container shuts down -->
<!-- Host source is denoted by "C:.." Destination container is denoted by directory after ":/folder-name.." -->
```bash
docker run -v C:\Users\u1\Documents:/container_folder sample-docker
```

### Create shared volume by name and attach it between the host & container
```bash
docker volume create sample-shared-volume
docker run -v sample-shared-volume:/container_folder sample-docker
```

### Create shared volume for the container & attach the port
```bash
docker run -v sample-shared-volume:/container_folder -p 127.0.0.1:8080:8080 sample-docker
```

---

## Additional Notes

- Volumes allow data (database & files) to persist even after container shuts down
- Host source is denoted by `C:\..` (Windows) or `/path/to/folder` (Linux/Mac)
- Destination container is denoted by directory after `:/folder-name`
- Use `-p` flag to map ports between host and container
- Use `-v` flag to create volume mounts

## Quick Reference

| Command | Purpose |
|---------|---------|
| `docker --version` | Check Docker version |
| `docker init` | Initialize Docker in current directory |
| `docker build -t <name> .` | Build image from Dockerfile |
| `docker run -p <host>:<container> <image>` | Run container with port mapping |
| `docker volume create <name>` | Create named volume |
| `docker run -v <source>:<dest> <image>` | Run with volume mount |
