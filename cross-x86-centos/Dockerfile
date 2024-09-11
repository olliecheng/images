# This container provides an image for cross-rs, but using a modern version of
# CentOS 7. It contains libc 2.17 and gcc 8.3.1 (devtoolset-8).
FROM --platform=linux/amd64 ghcr.io/cross-rs/x86_64-unknown-linux-gnu:main-centos
LABEL authors="olliecheng"

RUN yum install -y centos-release-scl
RUN sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/CentOS-*.repo && \
    yum install -y devtoolset-8

COPY scl_enable /usr/bin/scl_enable
ENV BASH_ENV="/usr/bin/scl_enable" \
    ENV="/usr/bin/scl_enable" \
    PROMPT_COMMAND=". /usr/bin/scl_enable"

RUN chmod +x /usr/bin/scl_enable
ENTRYPOINT ["/usr/bin/scl_enable"]