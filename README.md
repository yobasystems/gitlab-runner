# Gitlab Runner on Alpine Linux

This is the Docker image for the Gitlab runner, running on Alpine Linux.

[![Docker Layers](https://img.shields.io/badge/docker%20layers-5-blue.svg?maxAge=2592000?style=flat-square)](https://hub.docker.com/r/yobasystems/gitlab-ci-multi-runner/) [![Docker Size](https://img.shields.io/badge/docker%20size-50%20MB-blue.svg?maxAge=2592000?style=flat-square)](https://hub.docker.com/r/yobasystems/gitlab-ci-multi-runner/) [![Docker Stars](https://img.shields.io/docker/stars/yobasystems/gitlab-ci-multi-runner.svg?maxAge=2592000?style=flat-square)](https://hub.docker.com/r/yobasystems/gitlab-ci-multi-runner/) [![Docker Pulls](https://img.shields.io/docker/pulls/yobasystems/gitlab-ci-multi-runner.svg?maxAge=2592000?style=flat-square)](https://hub.docker.com/r/yobasystems/gitlab-ci-multi-runner/)

[![Alpine Version](https://img.shields.io/badge/alpine%20version-v3.7.0-green.svg?maxAge=2592000?style=flat-square)](http://alpinelinux.org/) [![Gitlab Runner Version](https://img.shields.io/badge/gitlabrunner%20version-v10.6.0-green.svg?maxAge=2592000?style=flat-square)](https://packages.gitlab.com/runner/gitlab-ci-multi-runner)



This Docker image [(yobasystems/gitlab-ci-multi-runner)](https://hub.docker.com/r/yobasystems/gitlab-ci-multi-runner/) is based on the minimal [Alpine Linux](http://alpinelinux.org/) with [Gitlab Runner](https://packages.gitlab.com/runner/gitlab-ci-multi-runner) pre-installed.

##### Alpine Version 3.7.0 (Released Jun 17, 2017)
##### Gitlab Runner Version 10.6.0

----

## What is Alpine Linux?
Alpine Linux is a Linux distribution built around musl libc and BusyBox. The image is only 5 MB in size and has access to a package repository that is much more complete than other BusyBox based images. This makes Alpine Linux a great image base for utilities and even production applications. Read more about Alpine Linux here and you can see how their mantra fits in right at home with Docker images.

## What is Gitlab Runner?
GitLab Runner is the open source project that is used to run your jobs and send the results back to GitLab. It is used in conjunction with GitLab CI, the open-source continuous integration service included with GitLab that coordinates the jobs.


## Features

  * Minimal size only
    * 50 MB and only 5 layers
  * Memory usage is minimal on a simple install

## Architectures

  * ```:amd64```, ```:latest``` - 64 bit Intel/AMD (x86_64/amd64)
  * ```:i386```, ```:x86``` - 32 bit Intel/AMD (x86/i686)
  * ```:arm64v8```, ```:aarch64``` - 64 bit ARM (ARMv8/aarch64)
  * ```:arm32v7```, ```:armhf``` - 32 bit ARM (ARMv7/armhf)

#### PLEASE CHECK TAGS BELOW FOR SUPPORTED ARCHITECTURES, THE ABOVE IS A LIST OF EXPLANATION

## Tags

  * ```:latest```, ```:amd64``` latest branch based on amd64
  * ```:master``` master branch usually inline with latest
  * ```:v0.0.0``` version number related to gitlab runner version
  * ```:armhf```, ```:arm32v7``` Armv7 based on latest tag but arm architecture

## How to use this image
#### Usage

Use like you would any other base image:

```
version: '2'
services:
  gitlab-runner:
    privileged: true
    image: yobasystems/gitlab-ci-multi-runner:amd64
    stdin_open: true
    volumes:
    - /var/run/docker.sock:/var/run/docker.sock
    - /data/gitlab-runner/config:/etc/gitlab-runner
    - /data/gitlab-runner/builds:/home/gitlab-runner
    tty: true
```

then register with gitlab server by running the following command:

```
sudo gitlab-ci-multi-runner register -n --url https://gitlab.url.domain.co.uk/ci --registration-token eRp938AHcv8JiHi4hUip --executor docker --docker-image "docker:git" --docker-privileged

```

## Image contents & Vulnerability analysis


## Source Repository

* [Bitbucket - yobasystems/gitlab-ci-multi-runner](https://bitbucket.org/yobasystems/gitlab-ci-multi-runner/)

* [Github - yobasystems/gitlab-ci-multi-runner](https://github.com/yobasystems/gitlab-ci-multi-runner)

## Links

* [Yoba Systems](https://www.yobasystems.co.uk/)

* [Dockerhub - yobasystems](https://hub.docker.com/u/yobasystems/)

* [Quay.io - yobasystems](https://quay.io/organization/yobasystems)
