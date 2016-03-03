# Docker

A tool for deploying and running applications. Docker provides a way to run an application securely isolated in a container in a way that is platform agnostic.

---

## [Docker Machine](https://docs.docker.com/machine)

*NOTE: [Docker Machine](https://docs.docker.com/machine) deprecates Boot2Docker*

---

## Docker Tools

|                    |                                                              |
|--------------------|--------------------------------------------------------------|
| Daemon             | used to manage local docker containers.                      |
| CLI                | used to command and communicate with the docker daemon.      |
| Image Index        | a repository (public or private) for docker images.          |
| [Toolbox][toolbox] | an installer to setup a Docker environment on your computer. |

---

## Docker Elements

![](https://m3xg3lob3p2dp7jl2yeyci13-wpengine.netdna-ssl.com/wp-content/uploads/2014/06/DockerizeImage2.png)

### CONTAINER:

A Linux Container, (sort of) like a directory, it holds everything needed for an app to run.

-   Docker containers are essentially directories that can be packed (e.g. tar-archived), then shared and run on other hosts. The only dependency is having docker installed on the hosts.

-   Docker containers allow:

    -   Application portability,
    -   Isolating processes,
    -   Preventing access beyond the container's own filesystem,
    -   All while being more much lightweight than a virtual machine.

-   When everything is self-contained and the risk of system-level changes are eliminated, the container becomes immune to external exposures which could put it out of order (i.e. 'dependency hell').

-   NB: docker depends on a single process to run. When that process stops, the container stops.

### IMAGE:

Read-only template for a docker container.

-   Uses a union file system (UFS) to 'layer' file system branches on top of each other. Every time a change is made to a Docker image, a new layer is created.
-   Docker images are built from a set a steps called instructions. These instructions can be built either by executing commands manually or automatically through Dockerfiles.
-   As more layers (tools, applications, etc.) are added on top of the base, new images can be formed by committing these changes – like a version control system!

### REGISTRY:

Private or public stores for docker images. [Docker Hub][docker-hub] is a public registry.

---

## Working with a Dockerfile

BUILDING an image from a dockerfile:

```sh
docker build -t [name for image] [directory where Dockerfile lives]
```

This generates a docker image. You create the container from the image with:

---

## Working with Docker Images

![](https://docs.docker.com/tutimg/container_explainer.png)

### SEARCH for images.

```sh
docker search [image_name]
docker pull [image_name]
```

### LIST all images on your system:

```sh
docker images
```

### List all containers current running:

```sh
docker ps
```

### List both running and non-running containers:

```sh
docker ps -l
```

### COMMIT an image

As you work with a container and continue to perform actions on it (e.g. download and install software, configure files), to have it keep its state, commit:

```sh
sudo docker commit [container ID] [image name]
```

## Working with Docker Containers

```sh
# CREATE a new container, either from an existing image or creating a new one:
docker run [image name] [command to run]
docker run my_image echo 'hello'

# RUNNING a container
docker run [container id]
docker run [image name] [command to run]

docker run -it [image name] /bin/sh # Start an interactive shell within your container
docker run --publish 3000:3000 [image name] [command to run] # Forward a port on the host to a port on the container
docker stop [container id] # STOPPING a container
docker rm [container id] # DELETING a container
docker attach [container id] # ATTACHING yourself to a container; your console will run commands within the container itself
```

Detaching the current container: type ^+P followed by ^+Q

---

## References

-   [Deploy Rails Application using Docker](http://steveltn.me/blog/2014/03/15/deploy-rails-applications-using-docker)
-   [Docker Explained: How To Containerize and Use Nginx as a Proxy](https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy)
-   [Docker Hub][docker-hub]
-   [Docker: Docs](https://docs.docker.com)
-   [Docker: Get Started with Docker for Mac OS X](https://docs.docker.com/mac/)
-   [How To Install and Use Docker: Getting Started](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-getting-started)
-   [Intro to Docker](http://jdlm.info/ds-docker-demo/#15)

[toolbox]: "https://www.docker.com/products/docker-toolbox"
[docker-hub]: "https://hub.docker.com"
