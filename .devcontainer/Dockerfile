FROM ubuntu:20.04

LABEL maintainer="VzdornovNA88@yandex.com"

RUN apt-get update

# Define username and temporary uid and gid
ENV USER=vscode

# now creating user, change password to 'ubuntu'
RUN useradd --create-home --shell /bin/bash ${USER}

#setup locale
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get install -y locales && dpkg-reconfigure locales --frontend noninteractive && locale-gen "en_US.UTF-8" && update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

# Yocto
RUN apt-get update && apt-get install -y \
     gawk wget git diffstat unzip texinfo gcc-multilib \
     build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
     xz-utils debianutils iputils-ping libsdl1.2-dev xterm \
     autoconf libtool libglib2.0-dev libarchive-dev \
     sed cvs subversion coreutils texi2html docbook-utils python-pysqlite2 \
     help2man make gcc g++ desktop-file-utils libgl1-mesa-dev libglu1-mesa-dev \
     mercurial automake groff curl lzop asciidoc u-boot-tools dos2unix mtd-utils pv \
     libncurses5 libncurses5-dev libncursesw5-dev libelf-dev zlib1g-dev bc rename \
     iproute2 zstd liblz4-tool tar net-tools rsync sudo vim python3-git python3-jinja2 pylint3 lz4 libssl-dev libsdl1.2-dev

RUN curl https://storage.googleapis.com/git-repo-downloads/repo > /bin/repo && chmod a+rx /bin/repo

# Update to latest
RUN apt-get update && apt-get dist-upgrade -y

RUN mkdir -m 777 /home/vscode/projects
RUN ln -s /home/vscode/projects /projects