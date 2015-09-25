#################################################################
# Dockerfile
#
# Version:          1
# Software:         AllPathsLG
# Software Version: 52488
# Provides:         allpathslg 52488
# Tags:             Genomics
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/allpathslg 52488/.
# Pull Cmd:         docker pull biodckrdev/allpathslg
# Run Cmd:          docker run --rm -it biodckrdev/allpathslg <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root


ENV ZIP=allpathslg-52488.tar.gz
ENV URL=https://github.com/BioDocker/software-archive/releases/download/allpathslg/
ENV FOLDER=allpathslg-52488
ENV DST=/tmp

RUN wget $URL/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    ./configure && \
    make && \
    make install && \
    cd / && \
    rm -rf $DST/$FOLDER

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["allpathslg"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

