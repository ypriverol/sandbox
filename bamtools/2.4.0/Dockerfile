#################################################################
# Dockerfile
#
# Version:          1
# Software:         bamtools
# Software Version: 1.2
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/bamtools 2.4.0/.
# Pull Cmd:         docker pull biodckrdev/bamtools
# Run Cmd:          docker run --rm biodckrdev/bamtools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN apt-get update && \
    apt-get install -y \
      cmake && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN URL=https://github.com/pezmaster31/bamtools/archive/ && \
    ZIP=v2.4.0.tar.gz && \
    FOLDER=bamtools-2.4.0 && \
    DST=/tmp && \
    wget $URL/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    mkdir build && \
    cd build && \
    cmake .. && \
    make && \
    make install && \
    cp $DST/$FOLDER/lib/* /lib/ && \
    rm -rf $DST/$FOLDER
   
# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["bamtools"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

