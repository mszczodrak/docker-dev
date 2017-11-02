FROM ubuntu:16.04

USER root

# install packages
RUN apt-get -y update
RUN apt-get -y install curl git vim build-essential wget rsync sudo clang llvm lcov
RUN apt-get -y install nmap htop net-tools iputils-ping openssh-server unzip subversion
RUN apt-get -y install gcc g++ pkg-config autoconf autoconf-archive make automake man

# wpantund
RUN apt-get -y install libglib2.0-dev libdbus-1-dev libreadline-dev libtool
RUN apt-get -y install dbus xtables-addons-source usbutils libfuzzer-3.8-dev
RUN apt-get -y install bsdtar libboost-dev libboost-signals-dev clang-3.8 clang++-3.8

# SSH
RUN mkdir /var/run/sshd
# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

#RUN ln -s /usr/bin/clang-3.8 /usr/bin/clang
#RUN ln -s /usr/bin/clang++-3.8 /usr/bin/clang++
#RUN ln -s /usr/bin/llvm-symbolizer-3.8 /usr/bin/llvm-symbolizer

# REPO
RUN curl https://storage.googleapis.com/git-repo-downloads/repo > /usr/local/bin/repo
RUN chmod a+x /usr/local/bin/repo

EXPOSE 22

ENTRYPOINT service ssh restart && bash
