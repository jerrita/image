FROM ubuntu:23.04

RUN apt-get update \
      && apt-get install -y build-essential git zsh iputils-ping curl automake screenfetch htop \
      && apt-get install -y vim iproute2 dnsutils lsof \
      && apt-get clean \
      && rm -rf /var/lib/apt/lists/* \
      && sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
