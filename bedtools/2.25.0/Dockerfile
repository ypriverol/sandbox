#################################################################
# Dockerfile
#
# Version:          1
# Software:         Bedtools
# Software Version: 2.25.0
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckr/bedtools 2.25.0/.
# Pull Cmd:         docker pull biodckr/bedtools
# Run Cmd:          docker run --rm biodckr/bedtools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

# Change user to root
USER root

################## BEGIN INSTALLATION ######################
RUN apt-get update && \
    apt-get install -y \
      build-essential \
      zlib1g-dev \
      python && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN ZIP=bedtools-2.25.0.tar.gz && \
    wget https://github.com/arq5x/bedtools2/releases/download/v2.25.0/$ZIP -O /tmp/$ZIP && \
    tar xvf /tmp/$ZIP -C /tmp && \
    rm /tmp/$ZIP && \
    cd /tmp/bedtools2 && \
    make && \
    make install && \
    cd / && \
    rm -rf /tmp/bedtools2

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["bedtools"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

