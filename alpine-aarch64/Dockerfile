FROM yobasystems/alpine:3.8.1-aarch64
LABEL maintainer "Dominic Taylor <dominic@yobasystems.co.uk>" architecture="ARM64v8/aarch64" version="11.5.0" alpineversion="3.8.1" build="23-nov-2018"

RUN apk add --update \
		bash \
		ca-certificates \
		git \
		openssl \
		wget

RUN wget -O /usr/bin/gitlab-ci-multi-runner https://gitlab-runner-downloads.s3.amazonaws.com/v11.5.0/binaries/gitlab-runner-linux-arm && \
	chmod +x /usr/bin/gitlab-ci-multi-runner && \
	ln -s /usr/bin/gitlab-ci-multi-runner /usr/bin/gitlab-runner && \
	wget -q https://github.com/docker/machine/releases/download/v0.16.0/docker-machine-Linux-armhf -O /usr/bin/docker-machine && \
	chmod +x /usr/bin/docker-machine && \
	mkdir -p /etc/gitlab-runner/certs && \
	chmod -R 700 /etc/gitlab-runner

ADD files/entrypoint.sh /
RUN chmod +x /entrypoint.sh

VOLUME ["/etc/gitlab-runner", "/home/gitlab-runner"]
ENTRYPOINT ["/entrypoint.sh"]
CMD ["run", "--user=gitlab-runner", "--working-directory=/home/gitlab-runner"]