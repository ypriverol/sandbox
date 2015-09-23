#################################################################
# Dockerfile
#
# Version:          1
# Software:         htslib
# Software Version: 1.2.1
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckr/htslib 1.2.1/.
# Pull Cmd:         docker pull biodckr/htslib
# Run Cmd:          docker run --rm biodckr/htslib <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN ZIP=htslib-1.2.1.tar.bz2 && \
    FOLDER=htslib-1.2.1 && \
    DST=/tmp && \
    wget https://github.com/BioDocker/software-archive/releases/download/htslib/$ZIP -O $DST/$ZIP && \
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
CMD ["tabix"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

