FROM debian:13

# Install Yocto dependencies
RUN apt-get update && apt-get install -y \
    build-essential chrpath cpio debianutils diffstat file gawk gcc git \
    iputils-ping libacl1 locales lz4 pcre2-utils python3 python3-git \
    python3-jinja2 python3-pexpect python3-pip python3-subunit \
    python3-venv socat texinfo tftp-hpa unzip wget xz-utils zstd

# Set locale (important for some Yocto operations)
#RUN locale-gen en_US.UTF-8
RUN echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen

# Create a non-root user (optional, but recommended)
ARG USER_UID=1500
ARG USER_GID=1500
RUN groupadd -g $USER_GID yoctouser && useradd -m -u $USER_UID -g $USER_GID -s /bin/bash yoctouser
USER yoctouser
WORKDIR /home/yoctouser/yocto-build
