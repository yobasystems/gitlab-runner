FROM yobasystems/alpine:x86

RUN apk add --update \
		bash \
		ca-certificates \
		docker \
		git \
		openssl \
		wget

RUN wget -O /usr/bin/gitlab-ci-multi-runner https://gitlab-ci-multi-runner-downloads.s3.amazonaws.com/v9.5.0/binaries/gitlab-ci-multi-runner-linux-i386 && \
	chmod +x /usr/bin/gitlab-ci-multi-runner && \
	ln -s /usr/bin/gitlab-ci-multi-runner /usr/bin/gitlab-runner && \
	mkdir -p /etc/gitlab-runner/certs && \
	chmod -R 700 /etc/gitlab-runner

ADD files/entrypoint.sh /
RUN chmod +x /entrypoint.sh

VOLUME ["/etc/gitlab-runner", "/home/gitlab-runner"]
ENTRYPOINT ["/entrypoint.sh"]
CMD ["run", "--user=gitlab-runner", "--working-directory=/home/gitlab-runner"]
