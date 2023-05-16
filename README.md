# Docker Training for Developers
## Introduction

Docker is a framework that developers use to eliminate "works on my machine" problems when collaborating on code with co-workers or deploying to a production environment. It allows you to automate the deployment, scaling, and management of software, making it an important tool in the world of DevOps.

## What is Docker?

Docker is a tool that packages software into standardized units called containers, which include everything the software needs to run including libraries, system tools, and code. This approach ensures that the software will always behave the same, regardless of where it's being run, offering convenience and consistency in software deployment.

## What Docker isn't

- Docker isn't an operating system: While Docker containers share the host's operating system, they are not themselves operating systems. They contain only the application and its dependencies.
- Docker isn't a virtual machine: Unlike virtual machines, Docker containers do not include a full operating system and do not require a hypervisor to emulate hardware. This makes them more lightweight and efficient.
- Docker isn't a programming language: Docker uses a Dockerfile to define a container, which might seem similar to code, however these are configuration files. The software running inside the container can be written in any language and that should be the focus

## Docker Images and Containers

A Docker image is a read-only template with instructions for creating a Docker container. On the other hand, Docker containers are running instances of Docker images. They can be started, stopped, moved, and deleted. Each container is isolated from other containers and its host machine.

## Advantages of Multi-Container Docker Architecture

Sometimes a monolith seems easier and in some ways they can be and they have some advantages of their own, however there are some major benefits to splitting your application into multiple containers.

- Isolation: Each container runs isolated from the others, which means if there's an issue in one container (like a crash or a memory leak), it doesn't directly affect the other containers. This makes the overall system more stable.
- Scalability: In a multi-container setup, each container can be scaled independently. ex: if a web service is experiencing more load, you can simply spin up more instances of your web service container to handle the load, without having to scale other services that might not be under as much load.
- Reusability: Containers can be reused across different environments. For example, the same database container can be used in development, staging, and production environments instead of having to configure a new one every time.
- Independent Deployments: With each service in its own container, it's possible to independently update and deploy services without affecting others. This can lead to fewer deployment-related issues and can support more frequent updates/releases.

## Dockerfile

A Dockerfile is a text file that Docker reads to build an image. It contains a series of instructions that Docker uses step by step to construct the image. Here are some common Dockerfile instructions:

- `FROM`: Choose the base image to start with.
- `RUN`: Execute a command.
- `CMD`: Specify a command that runs when the container starts.
- `ENTRYPOINT`: Set the main command for the container to run.
- `COPY`: Copy files from your computer into the container.
- `ADD`: Similar to COPY, but can also handle URLs and tar files.
- `ENV`: Set an environment variable.

## Basic Docker Commands

- `docker build`: Builds an image from a Dockerfile.
- `docker run`: Runs a command in a new container. It is important to note this will create an entirely new container not attach to a pre-existing one
- `docker ps`: Lists containers. 
- `docker pull`: Pulls an image or a repository from a registry.
- `docker push`: Pushes an image or a repository to a registry.
- `docker rm`: Removes one or more containers.
- `docker stop`: Stops one or more running containers.

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services, which can be started all at once with a single command. This can make it much easier to deploy multiple services at once or easily deploy a container without having to remember the same command or write a shell script to do it over and over again.

## Basic docker-compose Commands

All the `docker-compose` relate to the contents of a docker-compose.yml

- `docker-compose up`: Starts and runs your entire app. If it's run for the first time, it will build the services.
- `docker-compose down`: Stops and removes containers, networks, volumes, and images created by up.
- `docker-compose build`: Builds (or rebuilds) services.
- `docker-compose start`: Starts existing containers for a single service.
- `docker-compose stop`: Stops running containers without removing them.
- `docker-compose pause`: Pauses services.
- `docker-compose unpause`: Unpauses services.
- `docker-compose restart`: Restarts all the services.
- `docker-compose rm`: Removes stopped service containers.
- `docker-compose pull`: Pulls the latest versions of services declared to be images in the Docker Compose file.
- `docker-compose logs`: View the output from services.
- `docker-compose ps`: Lists the status of the services.

## Local Development with Docker

Docker can be used to set up a local development environment. This allows developers to work on their code locally, yet have it run within a Docker container. This ensures that the development environment is consistent across all developers' machines and the production environment.

## Debugging with Docker

Debugging applications running inside Docker containers is similar to debugging applications running outside of Docker. Common methods include viewing logs with `docker logs` or `docker-compose logs` and getting a shell inside a running container with `docker exec -it <container id/name> bash`.

## Docker Best Practices

- Minimize the number of layers: Each instruction in a Dockerfile creates a new layer in the image. Minimize the number of layers by consolidating commands.
- Avoid running processes as root: It's a best practice to run your processes as a non-root user in the container if possible.
- Use .dockerignore: It's a good practice to use a .dockerignore file to avoid adding unnecessary files into your Docker context.
- Use specific tags instead of 'latest': Using 'latest' for your base image might lead to unexpected results if the image changes. It's better to use a specific version number.
