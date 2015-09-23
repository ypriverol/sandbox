#################################################################
# Dockerfile
#
# Version:          1
# Software:         Samtools
# Software Version: 1.2
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckr/samtools 1.2/.
# Pull Cmd:         docker pull biodckr/samtools
# Run Cmd:          docker run --rm biodckr/samtools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################
# Change user to root
USER root

RUN apt-get update && \
    apt-get install -y \
      build-essential \
      zlib1g-dev \
      python \
      libncurses5-dev \
      libncursesw5-dev && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN ZIP=samtools-1.2.tar.bz2 && \
    wget https://github.com/BioDocker/software-archive/releases/download/samtools/$ZIP -O /tmp/$ZIP && \
    tar xvf /tmp/$ZIP -C /tmp && \
    rm /tmp/$ZIP && \
    cd /tmp/samtools-1.2 && \
    make && \
    make install && \
    cd / && \
    rm -rf /tmp/samtools-1.2

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["samtools"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

