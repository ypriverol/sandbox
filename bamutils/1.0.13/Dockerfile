#################################################################
# Dockerfile
#
# Version:          1
# Software:         bamutils
# Software Version: 1.0.13
# Provides:         bamutils 1.0.13
# Tags:             Genomics
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/bamutils 1.0.13/.
# Pull Cmd:         docker pull biodckrdev/bamutils
# Run Cmd:          docker run --rm biodckrdev/bamutils <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

ENV ZIP=bamutils-1.0.13.tar.bz2
ENV URL=https://github.com/BioDocker/software-archive/releases/download/bamutils
ENV FOLDER=bamutils-1.0.13
ENV DST=/tmp

RUN wget $URL/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    make && \
    make install && \
    cd / && \
    rm -rf $DST/$FOLDER

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["bamutils"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

