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

## Notable Packages

```sh
npm install -g cleaver
```

## References

-   [npmjs: Creating Node.js modules](https://docs.npmjs.com/getting-started/creating-node-modules)
