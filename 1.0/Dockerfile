FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

ENV TZ=Asia/Seoul
RUN sed -i 's/kr.archive.ubuntu.com/mirror.kakao.com/g' /etc/apt/sources.list


RUN apt update
RUN apt install -y apt-utils

RUN apt dist-upgrade -y
RUN apt install -y software-properties-common lsb-release

RUN add-apt-repository ppa:openjdk-r/ppa --yes
RUN apt update -y

RUN apt install -y locales
RUN locale-gen en_US.UTF-8

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt install -y adduser sudo vim tree mc htop inxi cron anacron \
		file time gawk git tig diffstat rsync wget curl coreutils tmux pseudo \
		python2.7 python3 python3-pip python3-dev python3-venv python3-distutils bash-completion bison \
		libpq-dev libgraphviz-dev graphviz sysstat build-essential chrpath cpio libxml2 libxml-simple-perl \
		gcc-multilib g++-multilib clang \
		iputils-ping liblz4-tool texinfo zstd libglib2.0-0 \
		openjdk-11-jdk ant bzip2 gzip tar zip

		RUN echo '*               soft    nofile          1048576'>>/etc/security/limits.conf
		RUN echo '*               hard    nofile          1048576'>>/etc/security/limits.conf

		RUN apt update \
		    && apt install -qq -y init systemd \
			&& apt install -qq -y build-essential \
		    && apt install -qq -y tzdata \
		    && apt install -qq -y vim curl \
		    && apt-get clean autoclean \
			&& apt-get autoremove -y \
		    && rm -rf /var/lib/{apt,dpkg,cache,log}


CMD /bin/bash
