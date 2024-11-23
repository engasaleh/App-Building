# Nodejs App-Buildin
This repository contains the source code and GitHub Actions workflow configuration for a Node.js application. 
The CI/CD pipeline automates the process of building, testing, containerizing, and deploying the application to an AWS EC2 instance. 
The project leverages modern tools and best practices to ensure efficient and reliable deployments.


<h2>Features</h2>

    Continuous Integration:
        Automatically builds and tests the application on every push or pull request to the main branch.
        Uses Docker to containerize the application for consistent runtime environments.

    Continuous Deployment:
        Automatically deploys the latest Docker image to an AWS EC2 instance upon a successful push to the main branch.
        Ensures seamless and robust application updates with health checks and rollback support.

    Docker Support:
        Images are built and pushed to Docker Hub with caching for faster subsequent builds.
        Tags include latest and a unique SHA for traceability.

    AWS EC2 Deployment:
        Deploys the containerized application to an EC2 instance.
        Configured with health checks to ensure the container is running correctly.
        Old images and containers are cleaned up to optimize resources.


Workflow Steps

    Build and Test:
        The workflow is triggered on push or pull request events targeting the main branch.
        Node.js dependencies are installed, and tests are run.

    Docker Image Build and Push:
        Docker images are built using the Dockerfile in the root directory.
        Built images are pushed to Docker Hub.

    AWS EC2 Deployment:
        The workflow uses SSH to connect to the EC2 instance.
        The container is pulled, stopped (if running), removed, and restarted with the new image.

    Health Check:
        Ensures the application is healthy and accessible after deployment.


