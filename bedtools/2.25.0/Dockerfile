#################################################################
# Dockerfile
#
# Version:          1
# Software:         Bedtools
# Software Version: 2.25.0
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/bedtools 2.25.0/.
# Pull Cmd:         docker pull biodckrdev/bedtools
# Run Cmd:          docker run --rm biodckrdev/bedtools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckrdev/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN ZIP=bedtools-2.25.0.tar.gz && \
    FOLDER=bedtools2 && \
    DST=/tmp && \
    wget https://github.com/arq5x/bedtools2/releases/download/v2.25.0/$ZIP -O $DST/$ZIP && \
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
CMD ["bedtools"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

