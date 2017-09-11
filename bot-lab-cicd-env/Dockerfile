FROM buildpack-deps:artful
MAINTAINER Sa2 <ar-ciel_ar-dor_harvestasya@live.jp>

# add user
RUN apt-get update
RUN apt-get install -y sudo
RUN groupadd --gid 1000 botlab \
  && useradd --uid 1000 --gid botlab --shell /bin/bash --create-home botlab
RUN echo 'Defaults visiblepw'             >> /etc/sudoers
RUN echo 'botlab ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER botlab

# building japanese env
RUN sudo apt-get install -y wget git
RUN wget -q https://www.ubuntulinux.jp/ubuntu-ja-archive-keyring.gpg -O- | sudo apt-key add -
RUN wget -q https://www.ubuntulinux.jp/ubuntu-jp-ppa-keyring.gpg -O- | sudo apt-key add -
RUN sudo wget https://www.ubuntulinux.jp/sources.list.d/zesty.list -O /etc/apt/sources.list.d/ubuntu-ja.list
RUN sudo apt-get update
RUN sudo apt-get install -y language-pack-ja
RUN locale-gen ja_JP.UTF-8  
ENV LANG ja_JP.UTF-8  
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
