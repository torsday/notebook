# DevOps

A melding of QA, Development, and Operations that **aims at establishing a culture and environment where building, testing, and releasing software, can happen rapidly, frequently, and more reliably**.

![DevOps Venn Diagram](https://upload.wikimedia.org/wikipedia/commons/b/b5/Devops.svg)

---

## Toolchain

-   **Code**: Code Development and Review, continuous integration tools

-   **Build**: Version control tools, code merging, Build status

    -   [Babel]()
    -   [Gulp](./gulp.md): A streaming build system.
    -   [Grunt](): Automation, performing repetitive tasks like minification, compilation, unit testing and linting; a JavaScript Task Runner.
    -   [Jenkins](./jenkins.md)
    -   [Phing](./phing.md)

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

---

## TODO: sort

-   [Build & Release](./build_and_release.md)
-   [Composer](./composer.md)
-   [Docker](./docker.md)
-   [Gearman](./gearman.md)
-   [JWT](./jwt.md)
-   [Karma]()
-   [Nginx]()
-   [NPM](./npm.md)
-   [NVM](./nvm.md)
-   [Okta]()
-   [PhantomJS](): A headless WebKit scriptable with a JavaScript API. It has fast and native support for various web standards: DOM handling, CSS selector, JSON, Canvas, and SVG.
-   [SAML]()
-   [Selenium]()
-   [Vagrant]()

---

## Docker vs Vagrant (different beasts)

**Vagrant abstracts the machine, Docker abstracts the application.**

### Docker

-   Docker talks with the kernel to create containers to launch applications, in an opinionated way (the emphasis is in running single apps, declaring exposed network ports, and image based filesystems).
-   Docker on the other hand uses kernel cgroup and namespacing via lxc. It means that you are using the same kernel as the host and the same file system. You can use Dockerfile with the docker build command in order to handle the provisioning and configuration of your container. You have example at docs.docker.com on how to make your Dockerfile, it is very intuitive.
-   Use if you want isolation.

### Vagrant

-   Vagrant talks with virtualization systems (VMware, virtualbox, aws, even docker) to mainly create full VMs with their own IPs, running any OS and of course, all the applications than implies booting that VM.
-   Vagrant is a virtual machine manager, it allows you to script the virtual machine configuration as well as the provisioning. However, it is still a virtual machine depending on Virtual Box (or others) with a huge overhead. It requires you to have a hard drive file that can be huge, it takes a lot of ram, and performance may be not very good.
-   Use if you need to do BSD, Windows or other non-linux development on your ubuntu box.

---

## References

-   [HackerNews: How to Deploy Software](https://news.ycombinator.com/item?id=11204736)
-   [PhantomJS](http://phantomjs.org)
-   [StackOverflow: Should I use Vagrant or Docker for creating an isolated environment?](http://stackoverflow.com/questions/16647069/should-i-use-vagrant-or-docker-for-creating-an-isolated-environment)
-   [Wikipedia: Comparison of continuous integration software](https://en.wikipedia.org/wiki/Comparison_of_continuous_integration_software)
-   [Wikipedia: DevOps](https://en.wikipedia.org/wiki/DevOps)
