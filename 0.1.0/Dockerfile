FROM ubuntu:18.04

USER root:root
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y wget curl

# Install Go

RUN wget --quiet https://dl.google.com/go/go1.9.7.linux-amd64.tar.gz -O /tmp/go1.9.7.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf /tmp/go1.9.7.linux-amd64.tar.gz && \
    rm /tmp/go1.9.7.linux-amd64.tar.gz

ENV GOPATH=/usr/local/go \
    PATH=/usr/local/go/bin:$PATH

# Install Hyperledger binaries
# (Supress image-download and repo-clone)

RUN mkdir /usr/local/hyperledger && \
    cd /usr/local/hyperledger && \
    curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/master/scripts/bootstrap.sh | bash -s -- -d -s

ENV PATH=/usr/local/hyperledger/bin:$PATH
