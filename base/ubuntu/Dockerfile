#FROM buildpack-deps:artful
FROM ubuntu:latest
MAINTAINER Sa2 <ar-ciel_ar-dor_harvestasya@live.jp>

# base package install
RUN apt-get update && \
    apt-get install -y sudo wget curl git vim unzip

# add user
RUN groupadd --gid 1000 base-user && \
    useradd --uid 1000 --gid base-user --shell /bin/bash --create-home base-user && \
    echo 'Defaults visiblepw'             >> /etc/sudoers && \
    echo 'base-user ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# switch user
USER base-user

# build japanese env
RUN wget -q https://www.ubuntulinux.jp/ubuntu-ja-archive-keyring.gpg -O- | sudo apt-key add - && \
    wget -q https://www.ubuntulinux.jp/ubuntu-jp-ppa-keyring.gpg -O- | sudo apt-key add - && \
    sudo wget https://www.ubuntulinux.jp/sources.list.d/zesty.list -O /etc/apt/sources.list.d/ubuntu-ja.list && \
    sudo apt-get update && \
    sudo apt-get install -y language-pack-ja && \
    sudo locale-gen ja_JP.UTF-8

ENV sudo LANG ja_JP.UTF-8
ENV sudo LANGUAGE ja_JP:ja
ENV sudo LC_ALL ja_JP.UTF-8
