# Jenkins

An open source application written in Java.

It is one of the most popular continuous integration tools used to build and test different kinds of projects.

Used to automate development workflow, commonly:

-   Building projects
-   Running tests to detect bugs and other issues as soon as they are introduced
-   Static code analysis
-   Deployment

## Installation

You have a number of ways to go about this.

-   Docker

    -   Pull the official jenkins image from Docker repository

        ```sh
        docker pull jenkins
        ```

    -   Next, run a container using this image and map data directory from the container to the host; e.g in the example below /var/jenkins_home from the container is mapped to jenkins/ directory from the current path on the host. Jenkins 8080 port is also exposed to the host as 49001.

        ```sh
        docker run -d -p 49001:8080 -v $PWD/jenkins:/var/jenkins_home -t jenkins
        ```

    -   You can configure nginx as a reverse proxy to your Jenkins instance, e.g.

        ```js
        upstream app {
            server 127.0.0.1:49001;
        }
        server {
            listen 80;
            server_name jenkins.your-domain.com;

            location / {
                proxy_pass http://app;
            }
        }
        ```

-   Homebrew

    ```sh
    brew install jenkins
    jenkins # starts a server at localhost:8080
    ```

## Process

1. push code to source control

## References

-   [GitHub: jenkinsci/jenkins](https://github.com/jenkinsci/jenkins)
-   [Jenkins-CI.org/](https://jenkins-ci.org)
-   [Jenkins: Installing Jenkins with Docker](https://wiki.jenkins-ci.org/display/JENKINS/Installing+Jenkins+with+Docker)
-   [TutsPlus: Introduction to Jenkins](http://code.tutsplus.com/tutorials/introduction-to-jenkins-an-open-source-continuous-integration-server--cms-23879)
