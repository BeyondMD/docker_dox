# Docker Training for Developers
## Introduction

Docker is a framework that developers use to eliminate "works on my machine" problems when collaborating on code with co-workers. It allows you to automate the deployment, scaling, and management of applications, making it a crucial tool in the world of DevOps.

## What is Docker?

Docker is an open-source platform that uses OS-level virtualization to deliver software in packages called containers. Unlike traditional virtual machines, containers share the host system's OS kernel, making them lightweight and fast.

## Docker Images and Containers

A Docker image is a read-only template with instructions for creating a Docker container. On the other hand, Docker containers are running instances of Docker images. They can be started, stopped, moved, and deleted. Each container is isolated from other containers and its host machine.

## Dockerfile

A Dockerfile is a text file that Docker reads to build an image. It contains a series of instructions that Docker uses step by step to construct the image. Here are some common Dockerfile instructions:

- `FROM`: Sets the base image for instructions dictated later in the Dockerfile.
- `RUN`: Executes any commands in a new layer on top of the current image and commits the results.
- `CMD`: Provides defaults for an executing container.
- `ENTRYPOINT`: Allows you to configure a container that will run as an executable.
- `COPY`: Copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.
- `ADD`: Allows you to copy files, directories or remote file URLs from <src> and adds them to the filesystem of the image at the path <dest>.
- `ENV`: Sets the environment variable <key> to the value <value>.

## Basic Docker Commands

- `docker build`: Builds an image from a Dockerfile.
- `docker run`: Runs a command in a new container. It is important to note this will create an entirely new container not attach to a pre-existing one
- `docker ps`: Lists containers. 
- `docker pull`: Pulls an image or a repository from a registry.
- `docker push`: Pushes an image or a repository to a registry.
- `docker rm`: Removes one or more containers.
- `docker stop`: Stops one or more running containers.

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services, which can be started all at once with a single command.

## Local Development with Docker

Docker can be used to set up a local development environment. This allows developers to work on their code locally, yet have it run within a Docker container. This ensures that the development environment is consistent across all developers' machines.

## Debugging with Docker

Debugging applications running inside Docker containers is similar to debugging applications running outside of Docker. Common methods include viewing logs with docker logs and getting a shell inside a running container with docker exec -it <container_id> bash.

## Docker Best Practices

- Minimize the number of layers: Each instruction in a Dockerfile creates a new layer in the image. Minimize the number of layers by consolidating commands.
- Avoid running processes as root: It's a best practice to run your processes as a non-root user in the container if possible.
- Use .dockerignore: It's a good practice to use a .dockerignore file to avoid adding unnecessary files into your Docker context.
- Use specific tags instead of 'latest': Using 'latest' might lead to unexpected results if the image changes. It's better to use a specific version number.
