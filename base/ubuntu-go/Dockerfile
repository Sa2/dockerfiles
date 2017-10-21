#FROM buildpack-deps:artful
FROM arcielsa2/ubuntu-base:latest
MAINTAINER Sa2 <ar-ciel_ar-dor_harvestasya@live.jp>

# protobuf install 
ENV PROTOBUF_VERSION 3.4.0
RUN wget https://github.com/google/protobuf/releases/download/v3.4.0/protoc-3.4.0-linux-x86_64.zip -P /tmp && \
    cd /tmp && \
    unzip protoc-3.4.0-linux-x86_64.zip && \
    sudo mv /tmp/bin/protoc /usr/local/bin/ && \
    sudo mv /tmp/include/google /usr/local/include/


# golang install
RUN mkdir -p /home/base-user/app
ENV GOPATH /home/base-user/app
RUN cd ~/ && \
    sudo apt-get update && \
    sudo apt-get install -y golang && \
    go get google.golang.org/grpc && \
    go get -u github.com/golang/protobuf/protoc-gen-go


