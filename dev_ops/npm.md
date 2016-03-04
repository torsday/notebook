# Node Package Manager (NPM)

The default package manager for the JavaScript runtime environment Node.js.

---

**Table of Contents**

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Basics](#basics)
	- [Updating NPM](#updating-npm)
	- [install npm's local dependencies](#install-npms-local-dependencies)
	- [list outdated packages](#list-outdated-packages)
	- [Update all global packages](#update-all-global-packages)
	- [package version](#package-version)
	- [list packages](#list-packages)
- [Favorite Global Packages](#favorite-global-packages)
	- [Install](#install)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

## Basics

### Updating NPM

```sh
npm install npm -g
```

### install npm's local dependencies

```sh
npm i
```

### list outdated packages

```sh
npm outdated
```

### Update all global packages

```sh
npm update -g
```

### package version

```sh
npm view <package> version
```

### list packages

```sh
npm ls
npm -g ls
```

## Favorite Global Packages

### Install

```sh
npm install -g \
babel-eslint \
eslint \
eslint-config-airbnb \
eslint-plugin-react \
gitbook-cli \
gitbook-plugin-collapsible-menu \
lodash \
react \
redux \
```

## Creating a module

### publish

*From: [NPM](https://docs.npmjs.com/cli/publish)*

> Publishes a package to the registry so that it can be installed by name. All files in the package directory are included if no local .gitignore or .npmignore file exists. If both files exist and a file is ignored by .gitignore but not by .npmignore then it will be included. See npm-developers for full details on what's included in the published package, as well as details on how the package is built.

> By default npm will publish to the public registry. This can be overridden by specifying a different default registry or using a npm-scope in the name (see package.json).

```sh
npm publish [<tarball>|<folder>] [--tag <tag>] [--access <public|restricted>]
```

-   Publishes `.` if no argument supplied
-   Sets tag `latest` if no `--tag` specified

## Notable Packages

```sh
npm install -g cleaver
```

## References

-   [npmjs: Creating Node.js modules](https://docs.npmjs.com/getting-started/creating-node-modules)
