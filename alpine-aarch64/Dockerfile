FROM yobasystems/alpine:3.18.2-aarch64

ARG BUILD_DATE
ARG VCS_REF

LABEL maintainer="Dominic Taylor <dominic@yoba.systems>" \
    architecture="arm64v8/aarch64" \
    alpine-version="3.18.2" \
    gitlab-runner-version="16.1.0" \
    build="12-Jul-2023" \
    org.opencontainers.image.title="gitlab-runner" \
    org.opencontainers.image.description="Gitlab Runner image running on Alpine Linux" \
    org.opencontainers.image.authors="Dominic Taylor <dominic@yoba.systems>" \
    org.opencontainers.image.vendor="Yoba Systems" \
    org.opencontainers.image.version="v16.1.0" \
    org.opencontainers.image.url="https://hub.docker.com/r/yobasystems/gitlab-runner/" \
    org.opencontainers.image.source="https://github.com/yobasystems/gitlab-runner" \
    org.opencontainers.image.revision=$VCS_REF \
    org.opencontainers.image.created=$BUILD_DATE

ENV GITLAB_RUNNER_VERSION=16.1.0 DOCKER_MACHINE_VERSION=0.16.2-gitlab.21

RUN apk add --no-cache \
		bash \
		ca-certificates \
    dumb-init \
		git \
    git-lfs \
		openssl \
    tzdata \
		wget

RUN wget -O /usr/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/v${GITLAB_RUNNER_VERSION}/binaries/gitlab-runner-linux-arm64 && \
	chmod +x /usr/bin/gitlab-runner && \
	ln -s /usr/bin/gitlab-runner /usr/bin/gitlab-ci-multi-runner && \
	wget -q https://gitlab.com/gitlab-org/ci-cd/docker-machine/-/releases/v${DOCKER_MACHINE_VERSION}/downloads/docker-machine-Linux-aarch64 -O /usr/bin/docker-machine && \
	chmod +x /usr/bin/docker-machine && \
	mkdir -p /etc/gitlab-runner/certs && \
	chmod -R 700 /etc/gitlab-runner

ADD files/entrypoint.sh /
RUN chmod +x /entrypoint.sh

VOLUME ["/etc/gitlab-runner", "/home/gitlab-runner"]
ENTRYPOINT ["/usr/bin/dumb-init", "/entrypoint.sh"]
CMD ["run", "--user=gitlab-runner", "--working-directory=/home/gitlab-runner"]
