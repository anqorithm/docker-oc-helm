# Docker Image with OpenShift CLI and Helm

This Docker image contains both OpenShift Command Line Interface (oc) and Helm package manager, making it useful for container orchestration and Kubernetes/OpenShift operations.

## Contents

- OpenShift CLI (oc)
- Helm

## Building the Image

```bash
docker build -t oc-helm-image .
```

## Usage

### Running Single Commands
```bash
docker run --rm oc-helm-image oc version
docker run --rm oc-helm-image helm version
```

### Running as a Persistent Container
To keep the container running and execute commands inside it:

```bash
# Start the container in detached mode
docker run -d --name oc-helm-container oc-helm-image tail -f /dev/null

# Execute commands in the running container
docker exec oc-helm-container oc version
docker exec oc-helm-container helm version

# Stop and remove the container when done
docker stop oc-helm-container
docker rm oc-helm-container
```

## Tags

- `latest`: Contains the latest stable versions of oc and helm
