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

Docker talks with the kernel of linux (and in a near future, windows) to create containers (think in a chroot that have its own network interfaces, users and process, isolated from the rest of the system ) to launch applications, in an opinionated way (the emphasis is in running single apps, declaring exposed network ports, and image based filesystems).

Vagrant talks with virtualization systems (VMware, virtualbox, aws, even docker) to mainly create full virtual machines with their own IPs, running any OS and of course, all the applications than implies booting that VM.

---

## References

-   [HackerNews: How to Deploy Software](https://news.ycombinator.com/item?id=11204736)
-   [PhantomJS](http://phantomjs.org)
-   [Wikipedia: Comparison of continuous integration software](https://en.wikipedia.org/wiki/Comparison_of_continuous_integration_software)
-   [Wikipedia: DevOps](https://en.wikipedia.org/wiki/DevOps)
