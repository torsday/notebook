# DevOps

*From: [Wikipedia](https://en.wikipedia.org/wiki/DevOps)*

> A culture, movement or practice that emphasizes the collaboration and communication of both software developers and other information-technology (IT) professionals while automating the process of software delivery and infrastructure changes. It **aims at establishing a culture and environment where building, testing, and releasing software, can happen rapidly, frequently, and more reliably**.

![DevOps Venn Diagram](https://upload.wikimedia.org/wikipedia/commons/b/b5/Devops.svg)

## Toolchain

-   **Code**: Code Development and Review, continuous integration tools

-   **Build**: Version control tools, code merging, Build status

    -   [Babel]()
    -   [Gulp](dev_ops/gulp.md): A streaming build system.
    -   [Grunt](): Automation, performing repetitive tasks like minification, compilation, unit testing and linting; a JavaScript Task Runner.
    -   [Jenkins](./jenkins.md)
    -   [Phing](dev_ops/phing.md)

-   **Test**: Test and results determine performance

    -   [Jenkins](./jenkins.md)
    -   [Travis CI](./travis.md): Test and Deploy.

-   **Package**: Artifact repository *(a.k.a. binary repository manager)*, Application pre-deployment staging

    -   [Artifactory]()
    -   [Satis](./satis.md)

-   **Release**: Change management, Release approvals, release automation

    -   [Jenkins](./jenkins.md): an open source automation server

-   **Configure**: Infrastructure configuration and management, Infrastructure as Code tools

-   **Monitor**: Applications performance monitoring, End user experience

    -   [New Relic]()
    -   [Splunk]()

## TODO: sort

-   [Build & Release](dev_ops/build_and_release.md)
-   [Composer](dev_ops/composer.md)
-   [Docker](dev_ops/docker.md)
-   [Gearman](dev_ops/gearman.md)
-   [JWT](dev_ops/jwt.md)
-   [Nginx]()
-   [NPM](dev_ops/npm.md)
-   [NVM](dev_ops/nvm.md)
-   [Okta]()
-   [SAML]()
-   [Vagrant]()

## References

-   [Wikipedia: Comparison of continuous integration software](https://en.wikipedia.org/wiki/Comparison_of_continuous_integration_software)
