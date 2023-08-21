# Slim Shield CircleCI Orb: Node JS Demo
This CircleCI demo project showcases the integration of the `slim-shield` orb with a Node.js application containerized using Docker.

# Setting up CircleCI Slim Shield Orb
Slim.AI offers a public orb that is configurable with your Node.JS project with a Docker container. The `slim shield` orb automates the process of container hardening by observing the running container, understanding its requirements, and removing unecessary components. By implementing best practices for container hardening, the outcome is a leaner, more secure container image accessible via the Slim portal.

## Project Environment Variables
Your Node.JS project will need the following environment variables:
```
DOCKERHUB_PASSWORD=
DOCKERHUB_USERNAME=
SLIM_ORG_ID=
SLIM_API_TOKEN=
SOURCE_CONNECTOR_ID=
TARGET_CONNECTOR_ID=
```
- `DOCKERHUB_PASSWORD` and `DOCKERHUB_USERNAME` are your Docker Hub credentials. Sign up [here](https://hub.docker.com/signup)
- `SLIM_ORG_ID` and `SLIM_API_TOKEN` are found in the Slim Platform, from your Profile Settings, in the Tokens and Organization tabs. Sign up [here](https://portal.slim.dev/login)
- `TARGET_CONNECTOR_ID` and `SOURCE_CONNECTOR_ID`: You can find your Connector ID's in the "My Registries" section of the Slim Platform. Note: Target & Source can be same.


## About the `.circleci/config.yml` file
The Slim.AI Orb is imported into your project here along with other `orbs`, with a organization identifier and orb slug, for example `slimdevops/slim-shield@0.0.3`. Other notable areas of the configuration include:
- `parameters` define CircleCI orb metadata about the Docker image intended for hardening (`image-name`) and the foundational image tag (`cimg-tag`).
- `executors` define the "docker-publisher" environment, setting up the image name and authentication details for publishing the Docker image.
- `jobs` handle the Docker image of the Node.js app, from building and pushing to Docker Hub, to testing, instrumenting, evaluating, hardening, and assessing the image for optimal security and functionality.
- `workflows` orchestrates the execution of jobs in a certain sequence, ensuring each step follows the successful completion of the previous.

## Accessing the Hardened Image
You can find the hardened image within the Slim portal under 'My Registries', specifically in the 'My Connectors' directory. This will correspond to the Target Connector defined earlier.

## Slim Community
For more information about configuring containers, vulnerability scans, or this orb example, check out the [SlimDevOps Community Discord](https://discord.com/invite/uBttmfyYNB), [SlimDevOps Community Forums](https://community.slim.ai/) and the [blog](https://www.slim.ai/blog/).
