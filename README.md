# Gitlab Runner on Alpine Linux

This is the Docker image for the Gitlab runner, running on Alpine Linux.

[![Docker Automated build](https://img.shields.io/docker/automated/yobasystems/gitlab-runner.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/r/yobasystems/gitlab-runner/)
[![Docker Pulls](https://img.shields.io/docker/pulls/yobasystems/gitlab-runner.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/r/yobasystems/gitlab-runner/)
[![Docker Stars](https://img.shields.io/docker/stars/yobasystems/gitlab-runner.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/r/yobasystems/gitlab-runner/)

[![Alpine Version](https://img.shields.io/badge/Alpine%20version-v3.9.2-green.svg?style=for-the-badge)](https://alpinelinux.org/)
[![Gitlab Runner Version](https://img.shields.io/badge/Gitlab%20Runner%20version-v11.8.0-green.svg?style=for-the-badge)](https://www.docker.com/)


This Docker image [(yobasystems/gitlab-runner)](https://hub.docker.com/r/yobasystems/gitlab-runner/) is based on the minimal [Alpine Linux](http://alpinelinux.org/) with [Gitlab Runner](https://packages.gitlab.com/runner/gitlab-runner) pre-installed.

##### Alpine Version 3.9.2 (Released January 29, 2019)
##### Gitlab Runner Version 11.8.0

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

* ```:amd64```, ```:x86_64``` - 64 bit Intel/AMD (x86_64/amd64)
* ```:arm64v8```, ```:aarch64``` - 64 bit ARM (ARMv8/aarch64)
* ```:arm32v7```, ```:armhf``` - 32 bit ARM (ARMv7/armhf)

#### PLEASE CHECK TAGS BELOW FOR SUPPORTED ARCHITECTURES, THE ABOVE IS A LIST OF EXPLANATION

## Tags

* ```:latest``` latest branch based (Automatic Architecture Selection)
* ```:master``` master branch usually inline with latest
* ```:v0.0.0``` version number related to gitlab runner version (Automatic Architecture Selection)
* ```:amd64```, ```:x86_64``` amd64 based on latest tag but amd64 architecture
* ```:armhf```, ```:arm32v7``` Armv7 based on latest tag but arm architecture
* ```:aarch64```, ```:arm64v8``` Armv8 based on latest tag but arm64 architecture

## How to use this image

#### aarch64

```
docker pull yobasystems/gitlab-runner:aarch64
docker pull yobasystems/gitlab-runner:aarch64-helper-11-2
docker tag yobasystems/gitlab-runner:aarch64-helper-11-2 gitlab-runner-helper:11.2.0

sudo docker run -d --name=gitlab-runner --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /data/gitlab-runner/config:/etc/gitlab-runner -v /data/gitlab-builds:/gitlab-builds yobasystems/gitlab-runner:aarch64
```

#### Usage

Use like you would any other base image:

```
version: '2'
services:
  gitlab-runner:
    privileged: true
    image: yobasystems/gitlab-runner
    stdin_open: true
    volumes:
    - /var/run/docker.sock:/var/run/docker.sock
    - /data/gitlab-runner/config:/etc/gitlab-runner
    - /data/gitlab-runner/builds:/home/gitlab-runner
    tty: true
```

then register with gitlab server by running the following command:

```
sudo gitlab-runner register -n --url https://gitlab.url.domain.co.uk/ci --registration-token eRp938AHcv8JiHi4hUip --executor docker --docker-image "yobasystems/alpine-docker" --docker-privileged

```

## Image contents & Vulnerability analysis


## Source Repository

* [Bitbucket - yobasystems/gitlab-runner](https://bitbucket.org/yobasystems/gitlab-runner/)

* [Github - yobasystems/gitlab-runner](https://github.com/yobasystems/gitlab-runner)

## Links

* [Yoba Systems](https://www.yobasystems.co.uk/)

* [Dockerhub - yobasystems](https://hub.docker.com/u/yobasystems/)

* [Quay.io - yobasystems](https://quay.io/organization/yobasystems)
