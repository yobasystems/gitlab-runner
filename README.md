# Gitlab Runner on Alpine Linux

This is the Container image for the Gitlab runner, running on Alpine Linux.

[![Docker Automated build](https://img.shields.io/docker/automated/yobasystems/gitlab-runner.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/r/yobasystems/gitlab-runner/)
[![Docker Pulls](https://img.shields.io/docker/pulls/yobasystems/gitlab-runner.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/r/yobasystems/gitlab-runner/)
[![Docker Stars](https://img.shields.io/docker/stars/yobasystems/gitlab-runner.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/r/yobasystems/gitlab-runner/)

[![Alpine Version](https://img.shields.io/badge/Alpine%20version-v3.21.1-green.svg?style=for-the-badge)](https://alpinelinux.org/)
[![Gitlab Runner Version](https://img.shields.io/badge/Gitlab%20Runner%20version-v17.8.3-green.svg?style=for-the-badge)](https://www.docker.com/)


This Container image [(yobasystems/gitlab-runner)](https://hub.docker.com/r/yobasystems/gitlab-runner/) is based on the minimal [Alpine Linux](https://alpinelinux.org/) with [Gitlab Runner](https://packages.gitlab.com/runner/gitlab-runner) pre-installed.

### Alpine Version 3.21.1 (Released 2025-01-06)
##### Gitlab Runner Version 17.8.3
##### Docker Machine Version 0.16.2-gitlab.31

----


- [What is Alpine Linux?](#what-is-alpine-linux)
- [Features](#features)
- [Architectures](#architectures)
- [Tags](#tags)
- [Layers & Sizes](#layers--sizes)
- [How to use this image](#how-to-use-this-image)
- [Image contents & Vulnerability analysis](#image-contents--vulnerability-analysis)
- [Source Repositories](#source-repositories)
- [Container Registries](#container-registries)
- [Links](#links)
- [Donation](#donation)


## 🏔️ What is Alpine Linux?
Alpine Linux is a Linux distribution built around musl libc and BusyBox. The image is only 5 MB in size and has access to a package repository that is much more complete than other BusyBox based images. This makes Alpine Linux a great image base for utilities and even production applications. Read more about Alpine Linux here and you can see how their mantra fits in right at home with Container images.

## 👟 What is Gitlab Runner?
GitLab Runner is the open source project that is used to run your jobs and send the results back to GitLab. It is used in conjunction with GitLab CI, the open-source continuous integration service included with GitLab that coordinates the jobs.


## ✨ Features

* Minimal size only
* 50 MB and only 5 layers
* Memory usage is minimal on a simple install

## 🏗️ Architectures

* ```:amd64```, ```:x86_64``` - 64 bit Intel/AMD (x86_64/amd64)
* ```:arm64v8```, ```:aarch64``` - 64 bit ARM (ARMv8/aarch64)
* ```:arm32v7```, ```:armhf``` - 32 bit ARM (ARMv7/armhf)

#### 📝 PLEASE CHECK TAGS BELOW FOR SUPPORTED ARCHITECTURES, THE ABOVE IS A LIST OF EXPLANATION

## 🏷️ Tags

* ```:latest``` latest branch based (Automatic Architecture Selection)
* ```:master``` master branch usually inline with latest
* ```:17.8.3```, ```:17.8.3-arch``` version tag (Automatic Architecture Selection)
* ```:amd64```, ```:x86_64``` amd64 based on latest tag but amd64 architecture
* ```:aarch64```, ```:arm64v8``` Armv8 based on latest tag but arm64 architecture
* ```:armhf```, ```:arm32v7``` Armv7 based on latest tag but arm architecture

## 📏 Layers & Sizes

![Version](https://img.shields.io/badge/version-amd64-blue.svg?style=for-the-badge)
![MicroBadger Layers (tag)](https://img.shields.io/docker/layers/yobasystems/gitlab-runner/amd64.svg?style=for-the-badge)
![MicroBadger Size (tag)](https://img.shields.io/docker/image-size/yobasystems/gitlab-runner/amd64.svg?style=for-the-badge)

![Version](https://img.shields.io/badge/version-aarch64-blue.svg?style=for-the-badge)
![MicroBadger Layers (tag)](https://img.shields.io/docker/layers/yobasystems/gitlab-runner/aarch64.svg?style=for-the-badge)
![MicroBadger Size (tag)](https://img.shields.io/docker/image-size/yobasystems/gitlab-runner/aarch64.svg?style=for-the-badge)

![Version](https://img.shields.io/badge/version-armhf-blue.svg?style=for-the-badge)
![MicroBadger Layers (tag)](https://img.shields.io/docker/layers/yobasystems/gitlab-runner/armhf.svg?style=for-the-badge)
![MicroBadger Size (tag)](https://img.shields.io/docker/image-size/yobasystems/gitlab-runner/armhf.svg?style=for-the-badge)

## 🚀 How to use this image

### amd64/armhf/aarch64 (Alpine)

```
docker pull yobasystems/gitlab-runner

sudo docker run -d --name=gitlab-runner --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /data/gitlab-runner/config:/etc/gitlab-runner yobasystems/gitlab-runner
```

#### Register runner with gitlab server
These can be passed at runtime as environment variables or by running the following command:

```
docker exec -it gitlab-runner /bin/sh

gitlab-runner register -n --url https://gitlab.url.domain.co.uk/ci --registration-token eRp938AHcv8JiHi4hUip --executor docker --docker-image "yobasystems/gitlab-runner-docker" --docker-privileged
```

### Config file

Sometimes it is needed to add the following `"/var/run/docker.sock:/var/run/docker.sock"`, in the example below you will see the placement.

```
concurrent = 1
check_interval = 0
[[runners]]
  name = "gitlab-runner001"
  url = "https://gitlab.url.domain.co.uk/ci"
  token = "eRp938AHcv8JiHi4hUip"
  executor = "docker"
  [runners.docker]
    tls_verify = false
    image = "yobasystems/gitlab-runner-docker:dind"
    privileged = true
    disable_cache = true
    volumes = ["/var/run/docker.sock:/var/run/docker.sock", "/cache"]
    shm_size = 0
  [runners.cache]
```


### Usage

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
    tty: true
```

## 🔍 Image contents & Vulnerability analysis

| PACKAGE NAME          | PACKAGE VERSION | VULNERABILITIES |
|-----------------------|-----------------|-----------------|


## 📚 Source Repositories

* [Github - yobasystems/gitlab-runner](https://github.com/yobasystems/gitlab-runner)
* [Gitlab - yobasystems/gitlab-runner](https://gitlab.com/yobasystems/gitlab-runner)
* [Bitbucket - yobasystems/gitlab-runner](https://bitbucket.org/yobasystems/gitlab-runner/)


## 🐳 Container Registries

* [Dockerhub - yobasystems/gitlab-runner](https://hub.docker.com/r/yobasystems/gitlab-runner/)
* [Quay.io - yobasystems/gitlab-runner](https://quay.io/repository/yobasystems/gitlab-runner)
* [GHCR - yobasystems/gitlab-runner](https://ghcr.io/yobasystems/gitlab-runner)


## 🔗 Links

* [Yoba Systems](https://yoba.systems/)
* [Github - Yoba Systems](https://github.com/yobasystems/)
* [Dockerhub - Yoba Systems](https://hub.docker.com/u/yobasystems/)
* [Quay.io - Yoba Systems](https://quay.io/organization/yobasystems)
* [GHCR - Yoba Systems](https://ghcr.io/yobasystems)
* [Maintainer - Dominic Taylor](https://github.com/dominictayloruk)

## 💰 Donation

[![BMAC](https://img.shields.io/badge/BUY%20ME%20A%20COFFEE-£5-blue.svg?style=for-the-badge&logo=buy-me-a-coffee)](https://www.buymeacoffee.com/dominictayloruk?new=1)

[![BITCOIN](https://img.shields.io/badge/BTC-bc1q7hy8qmyvq7rw6slrna7yffcdnj9rcg4e9xjecc-blue.svg?style=for-the-badge&logo=bitcoin)](bitcoin:bc1q7hy8qmyvq7rw6slrna7yffcdnj9rcg4e9xjecc)

[![ETHEREUM](https://img.shields.io/badge/ETH-0xb6bE2e4da3d86b50Bdae1F9B6960c23dd87C532C-blue.svg?style=for-the-badge&logo=ethereum)](ethereum:0xb6bE2e4da3d86b50Bdae1F9B6960c23dd87C532C)
