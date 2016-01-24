FROM ubuntu
MAINTAINER Sa2 <ar-ciel_ar-dor_harvestasya@live.jp>
RUN sudo apt-get install -y language-pack-ja
RUN sudo rm -f /etc/apt/sources.list && \
    echo "deb http://jp.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb http://jp.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb http://jp.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb http://security.ubuntu.com/ubuntu precise-security main restricted universe multiverse" >> /etc/apt/sources.list


RUN sudo apt-get -qy update && apt-get -fqy dist-upgrade
RUN mkdir /var/run/sshd
RUN sudo apt-get autoremove && apt-get clean

RUN sudo apt-get install -y wget
RUN sudo apt-get install -y git
RUN sudo apt-get install -y node

RUN echo "root:root" | chpasswd
EXPOSE 22
ENTRYPOINT [ "/usr/sbin/sshd", "-D" ]