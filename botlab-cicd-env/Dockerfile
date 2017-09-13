#FROM buildpack-deps:artful
FROM ubuntu:17.10
MAINTAINER Sa2 <ar-ciel_ar-dor_harvestasya@live.jp>

# base package install
RUN apt-get update && \
    apt-get install -y sudo wget curl git

# add user
RUN groupadd --gid 1000 botlab && \
    useradd --uid 1000 --gid botlab --shell /bin/bash --create-home botlab && \
    echo 'Defaults visiblepw'             >> /etc/sudoers && \
    echo 'botlab ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# switch user
USER botlab

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

# build node env
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.4/install.sh | bash && \
    /bin/bash -c "source $HOME/.nvm/nvm.sh; nvm install 8.4.0"

# build gcloud command
ENV CLOUD_SDK_VERSION 170.0.1

RUN sudo apt-get update -qqy && \
    sudo apt-get install -qqy \
        gcc \
        python-dev \
        python-setuptools \
        apt-transport-https \
        lsb-release \
        openssh-client && \
    sudo easy_install -U pip && \
    sudo pip install -U crcmod && \
    export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" && \
    sudo bash -c "echo \"deb https://packages.cloud.google.com/apt $CLOUD_SDK_REPO main\" > /etc/apt/sources.list.d/google-cloud-sdk.list" && \
    sudo curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add - && \
    sudo apt-get update && sudo apt-get install -y google-cloud-sdk=${CLOUD_SDK_VERSION}-0 $INSTALL_COMPONENTS && \
    gcloud config set core/disable_usage_reporting true && \
    gcloud config set component_manager/disable_update_check true && \
    gcloud config set metrics/environment github_docker_image
