# Build a custom MQ Docker Image for CP4I deployment

## Build Dockerfile

1. Create a file called dockerfile.
2. Copy the contents below into the dockerfile.

```
# Load mq docker image from local openshift repository

FROM default-route-openshift-image-registry.<OPENSHIFT DOMAIN>/mq/ibm-mqadvanced-server-integration:9.1.3.0-r1-amd64

# Copy the configuration script to /etc/mqm where it will be picked up automatically. Place script in same folder as dockerfile.

COPY mqload.mqsc /etc/mqm/
```

Alternative address for registry is:  

-  image-registry.openshift-image-registry.svc:5000

## Build Image

Run command to build (NOTE: add -amd64 at end because the installation automatically appends this)

`docker build -t default-route-openshift-image-registry.<OPENSHIFT DOMAIN>/mq/ibm-mqadvanced-server-integration-2:9.1.3.0-r1v2-amd64`

## Push New Image to Registry

`docker push docker-registry.default.svc:5000/mq/ibm-mqadvanced-server-integration-2:9.1.3.0-r1v2-amd64`