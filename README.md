# docker-ci

docker-ci

[![Stars](https://img.shields.io/github/stars/arbing/docker-ci.svg?label=Stars&style=social)](https://github.com/arbing/docker-ci)
[![Docker Automated build](https://img.shields.io/docker/automated/arbing/docker-ci.svg)](https://hub.docker.com/r/arbing/docker-ci)

[![docker-ci:node](https://images.microbadger.com/badges/version/arbing/docker-ci:node.svg)![MicroBadger](https://images.microbadger.com/badges/image/arbing/docker-ci:node.svg)](https://microbadger.com/images/arbing/docker-ci:node)

[![docker-ci:node-maven](https://images.microbadger.com/badges/version/arbing/docker-ci:node-maven.svg)![MicroBadger](https://images.microbadger.com/badges/image/arbing/docker-ci:node-maven.svg)](https://microbadger.com/images/arbing/docker-ci:node-maven)

[![docker-ci:node-python](https://images.microbadger.com/badges/version/arbing/docker-ci:node-python.svg)![MicroBadger](https://images.microbadger.com/badges/image/arbing/docker-ci:node-python.svg)](https://microbadger.com/images/arbing/docker-ci:node-python)

## 镜像列表

- arbing/docker-ci:node
- arbing/docker-ci:node-maven
- arbing/docker-ci:node-python

## 基础镜像

- docker https://github.com/docker-library/docker/blob/master/19.03/Dockerfile

- docker:git https://github.com/docker-library/docker/blob/master/19.03/git/Dockerfile

- node:lts-alpine https://github.com/nodejs/docker-node/blob/master/12/alpine3.11/Dockerfile

- ibmjava:8-sdk-alpine https://github.com/ibmruntimes/ci.docker/blob/master/ibmjava/8/sdk/alpine/Dockerfile

- maven:ibmjava-8-alpine https://github.com/carlossg/docker-maven/blob/master/ibmjava-8-alpine/Dockerfile

- node:lts-buster https://github.com/nodejs/docker-node/blob/master/12/buster/Dockerfile

- openjdk:8-jdk https://github.com/docker-library/openjdk/blob/master/8/jdk/Dockerfile

- maven:3.6-openjdk-8 https://github.com/carlossg/docker-maven/blob/master/openjdk-8/Dockerfile

- python:3.7-alpine https://github.com/docker-library/python/blob/master/3.7/alpine3.12/Dockerfile

## Windows 下修改文件权限

```sh
git ls-tree HEAD
git update-index --chmod=+x mvn-entrypoint.sh
git commit -m "revise permission access"
```
