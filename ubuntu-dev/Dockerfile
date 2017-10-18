FROM ubuntu:16.04

USER root

# install packages
RUN apt-get -y update
RUN apt-get -y install curl git vim build-essential wget rsync sudo clang
RUN apt-get -y install nmap htop net-tools iputils-ping openssh-server unzip

# SSH
RUN mkdir /var/run/sshd
# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

# REPO
RUN curl https://storage.googleapis.com/git-repo-downloads/repo > /usr/local/bin/repo
RUN chmod a+x /usr/local/bin/repo

EXPOSE 22

ENTRYPOINT service ssh restart && bash
