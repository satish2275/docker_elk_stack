FROM phusion/baseimage:0.9.17

MAINTAINER Sloppy Lopez <sloppy@sloppylopez.com>

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]

# ...put your own build instructions here...
# Env Variables
ENV GIT_BASE_FOLDER=nodeapi
ENV PROJECT_NAME=nodeapi
ENV GIT_USER=sloppylopez
ENV NODE_VERSION=0.12
ENV ROOTFOLDER=opt

# Workdir
WORKDIR $ROOTFOLDER

# Dependencies
RUN apt-get update -qq && \
    apt-get install -y -qq \
    git \
    python

# Install
RUN curl -sL https://deb.nodesource.com/setup_$NODE_VERSION | sudo bash -
RUN apt-get install -y nodejs
RUN git clone https://github.com/$GIT_USER/$GIT_BASE_FOLDER.git
RUN cd ./$GIT_BASE_FOLDER;npm install

# nodejs port
EXPOSE  3000

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD node ./$GIT_BASE_FOLDER/server.js


# ...put your own build instructions here...