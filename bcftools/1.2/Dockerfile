#################################################################
# Dockerfile
#
# Version:          1
# Software:         Bcftools
# Software Version: 1.2
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/bcftools 1.2/.
# Pull Cmd:         docker pull biodckrdev/bcftools
# Run Cmd:          docker run --rm biodckrdev/bcftools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN ZIP=bcftools-1.2.tar.bz2 && \
    FOLDER=bcftools-1.2 && \
    DST=/tmp && \
    wget https://github.com/BioDocker/software-archive/releases/download/bcftools/$ZIP -O $DST/$ZIP && \
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
CMD ["bcftools"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

