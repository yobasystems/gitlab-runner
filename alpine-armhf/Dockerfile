FROM yobasystems/alpine:3.9.2-armhf

ARG BUILD_DATE
ARG VCS_REF

LABEL maintainer="Dominic Taylor <dominic@yobasystems.co.uk>" \
    architecture="arm32v7/armhf" \
    alpine-version="3.9.2" \
    gitlab-runner-version="11.8.0" \
    build="13-Mar-2019" \
    org.opencontainers.image.title="gitlab-runner" \
    org.opencontainers.image.description="Gitlab Runner image running on Alpine Linux" \
    org.opencontainers.image.authors="Dominic Taylor <dominic@yobasystems.co.uk>" \
    org.opencontainers.image.vendor="Yoba Systems" \
    org.opencontainers.image.version="v11.8.0" \
    org.opencontainers.image.url="https://hub.docker.com/r/yobasystems/gitlab-runner/" \
    org.opencontainers.image.source="https://github.com/yobasystems/gitlab-runner" \
    org.opencontainers.image.revision=$VCS_REF \
    org.opencontainers.image.created=$BUILD_DATE

RUN apk add --update \
		bash \
		ca-certificates \
		git \
		openssl \
		wget

RUN wget -O /usr/bin/gitlab-ci-multi-runner https://gitlab-runner-downloads.s3.amazonaws.com/v11.8.0/binaries/gitlab-runner-linux-arm && \
	chmod +x /usr/bin/gitlab-ci-multi-runner && \
	ln -s /usr/bin/gitlab-ci-multi-runner /usr/bin/gitlab-runner && \
	wget -q https://github.com/docker/machine/releases/download/v0.16.1/docker-machine-Linux-armhf -O /usr/bin/docker-machine && \
	chmod +x /usr/bin/docker-machine && \
	mkdir -p /etc/gitlab-runner/certs && \
	chmod -R 700 /etc/gitlab-runner

ADD files/entrypoint.sh /
RUN chmod +x /entrypoint.sh

VOLUME ["/etc/gitlab-runner", "/home/gitlab-runner"]
ENTRYPOINT ["/entrypoint.sh"]
CMD ["run", "--user=gitlab-runner", "--working-directory=/home/gitlab-runner"]
