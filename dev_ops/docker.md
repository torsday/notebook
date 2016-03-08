# Docker

A two part shell/management layer for building and running virtual linux containers, based on LXC.

A tool for deploying and running applications. Docker provides a way to run an application securely isolated in a container in a way that is platform agnostic.

---

## Docker Tools

|                                  |                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------|
| [Docker Engine][docker engine]   | runs on Linux to create the operating environment for your distributed applications.       |
| [Docker Machine][docker machine] | automate Docker provisioning                                                               |
| [Docker Toolbox][toolbox]        | an installer to quickly and easily install and setup a Docker environment on your computer |
| [Kitematic][kitematic]           | build and run containers through a GUI                                                     |

*NOTE: [Docker Machine](https://docs.docker.com/machine) deprecates Boot2Docker*

---

## Docker Elements

![](https://m3xg3lob3p2dp7jl2yeyci13-wpengine.netdna-ssl.com/wp-content/uploads/2014/06/DockerizeImage2.png)

![](https://docs.docker.com/tutimg/container_explainer.png)

### Image

Read-only template for a docker container.

-   An inert, immutable, file that's essentially a snapshot of a container. Images are created with the build command, and they'll produce a container when started with run.
-   Uses a union file system (UFS) to 'layer' file system branches on top of each other. **Every time a change is made to a Docker image, a new layer is created.**
-   Docker images are built from a set a steps called instructions. These instructions can be built either by executing commands manually or automatically through Dockerfiles.
-   As more layers (tools, applications, etc.) are added on top of the base, new images can be formed by committing these changes – like a version control system!
-   Images are stored in a Docker registry such as registry.hub.docker.com.
-   Because they can become quite large, images are designed to be composed of layers of other images, allowing a miminal amount of data to be sent when transferring images over the network.

#### Commands

Search

```sh
docker search [image_name]
docker pull [image_name]
```

List all images on your system

```sh
docker images
```

Build an image from a dockerfile

```sh
docker build -t NAME_OF_IMAGE [directory where Dockerfile lives] NAME_OF_CONTAINER
```

Commit an image

```sh
sudo docker commit [container ID] IMAGE_NAME
```

Remove

```sh
docker rmi -f IMAGE_ID
```

### Container

A Linux Container, (sort of) like a directory, it holds everything needed for an app to run.

-   Docker containers are essentially directories that can be packed (e.g. tar-archived), then shared and run on other hosts. The only dependency is having docker installed on the hosts.

-   Docker containers allow:

    -   Application portability
    -   Process isolation
    -   Preventing access beyond the container's own filesystem
    -   Lightweight, esp. relative to VMs

-   When everything is self-contained and the risk of system-level changes are eliminated, the container becomes immune to external exposures which could put it out of order (i.e. 'dependency hell').

-   NB: docker depends on a single process to run. When that process stops, the container stops.

-   If an image is a class, then a container is an instance of a class.

#### Commands

List

```sh
docker ps     # those running
docker ps -l  # both running & dormant
```

Create *(either from an existing image or creating a new one)*

```sh
docker run IMAGE_NAME COMMAND_TO_RUN
docker run my_image echo 'hello'
```

Running

```sh
docker run CONTAINER_ID
docker run IMAGE_NAME COMMAND_TO_RUN
```

Start an interactive shell within your container

```sh
docker run -it IMAGE_NAME /bin/sh
```

Forward port on the host to a port on the container

```sh
docker run --publish 3000:3000 IMAGE_NAME COMMAND_TO_RUN
```

Stopping a container

```sh
docker stop CONTAINER_ID
```

Removing a container

```sh
docker rm CONTAINER_ID
```

Attaching yourself to a container *(your console will run commands within the container itself)*

```sh
docker attach CONTAINER_ID
```

Detach the current container: type `^` + `P` followed by `^` + `Q`

---

## Vocabulary

|                  |                                                                                                  |
|------------------|--------------------------------------------------------------------------------------------------|
| Docker Container | A running image; an instance of an image. You can have many running containers of the same image |
| Docker Image     |                                                                                                  |

---

## References

-   [Deploy Rails Application using Docker](http://steveltn.me/blog/2014/03/15/deploy-rails-applications-using-docker)
-   [Docker Explained: How To Containerize and Use Nginx as a Proxy](https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy)
-   [Docker Hub][docker-hub]
-   [Docker: Docs](https://docs.docker.com)
-   [Docker: Get Started with Docker for Mac OS X](https://docs.docker.com/mac/)
-   **[GitHub: veggiemonk/awesome-docker](https://github.com/veggiemonk/awesome-docker): curated list of Docker resources and projects**
-   [How To Install and Use Docker: Getting Started](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-getting-started)
-   [Intro to Docker](http://jdlm.info/ds-docker-demo/#15)
-   [Quora: What is the difference between Docker and Vagrant? When should you use each one?](https://www.quora.com/What-is-the-difference-between-Docker-and-Vagrant-When-should-you-use-each-one)
-   [StackOverflow: Docker image vs container](http://stackoverflow.com/questions/23735149/docker-image-vs-container)

[docker engine]: "https://www.docker.com/products/docker-engine"
[docker machine]: "https://docs.docker.com/machine"
[docker-hub]: "https://hub.docker.com"
[kitematic]: "https://kitematic.com"
[toolbox]: "https://www.docker.com/products/docker-toolbox"
