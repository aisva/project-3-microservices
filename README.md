# Udagram
Udagram is a cloud application that allows users to register and log into a web client where they can post photos to a feed. It is the third project of Udacity's [Cloud Developer Nanodegree Program](https://www.udacity.com/course/cloud-developer-nanodegree--nd9990).

Udagram is split in 4 services:

1. The [User microservice](https://github.com/aisva/project-3-microservices/tree/master/restapi-user), a Node.js - Express server for managing user registration and authentication.
2. The [Feed microservice](https://github.com/aisva/project-3-microservices/tree/master/restapi-feed), a Node.js - Express server for handling photos posted by the users.
3. A [proxy server](https://github.com/aisva/project-3-microservices/tree/master/deployment).
4. A [frontend application](https://github.com/aisva/project-3-microservices/tree/dev/frontend) that access the Feed and User microservices via the proxy server.

# Docker
All the 4 services above are containerized in Docker containers. You can build their Docker images by using *docker-compose*:

```docker-compose -f deployment/docker/docker-compose-build.yaml build --parallel```

Then, you can run all the containers with the following commands:

```
cd deployment/docker
docker-compose up
```

The application will be accessible on: `http://localhost:8100`.

# Kubernetes
This application can also be deployed to a Kubernetes cluster. Configuration files for Kubernetes' services and deployments are provided [here](https://github.com/aisva/project-3-microservices/tree/dev/deployment/k8s).

# CI / CD
A `.travis.yml` configuration file is provided for building and deploying the application with [Travis CI](https://travis-ci.org). The build and deployment process is split in three steps:

1. Building the images of the 4 services of the application with *docker-compose*.
2. Pushing the images to [Docker Hub](https://hub.docker.com/).
3. Deploying the application to a Kubernetes cluster.

# Evidence: screenshots and links
To demonstrate the implementation of all of the features required by the rubric of the third project of Udacity's [Cloud Developer Nanodegree Program](https://www.udacity.com/course/cloud-developer-nanodegree--nd9990), the following screenshots and links are provided:

* A screenshot of the application running (see [screenshots](https://github.com/aisva/project-3-microservices/tree/master/screenshots) folder).
* Screenshots of Travis CI that show how the application is successfully built and deployed (see [screenshots](https://github.com/aisva/project-3-microservices/tree/master/screenshots) folder).
* Links to the Docker Hub images of all the services: 
  * [User microservice](https://hub.docker.com/r/antonioisasi/udacity-restapi-user)
  * [Feed microservice](https://hub.docker.com/r/antonioisasi/udacity-restapi-feed)
  * [Proxy server](https://hub.docker.com/r/antonioisasi/reverseproxy)
  * [Frontend application](https://hub.docker.com/r/antonioisasi/udacity-frontend)
* A screenshot of the outputs of the following commands: `kubectl get pods` and `kubectl get deployments` (see [screenshots](https://github.com/aisva/project-3-microservices/tree/master/screenshots) folder).
* A screenshot that shows how the application is monitored by AWS CloudWatch (see [screenshots](https://github.com/aisva/project-3-microservices/tree/master/screenshots) folder).