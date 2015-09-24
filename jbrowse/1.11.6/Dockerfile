#################################################################
# Dockerfile
#
# Version:          1
# Software:         jbrowse
# Software Version: 1.11.6
# Provides:         jbrowse 1.11.6
# Tags:             Genomics
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/jbrowse 1.11.6/.
# Pull Cmd:         docker pull biodckrdev/jbrowse
# Run Cmd:          docker run --rm biodckrdev/jbrowse
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
#USER root

#apt-get install libpng-dev libgd2-noxpm-dev build-essential

#https://github.com/BioDocker/software-archive/releases/download/jbrowse/JBrowse-1.11.6.zip
ENV ZIP=JBrowse-1.11.6.zip
ENV URL=https://github.com/BioDocker/software-archive/releases/download/jbrowse/
ENV DST=/home/biodocker/
ENV FOLDER=JBrowse-1.11.6

RUN set -xeu && \
    mkdir -p $DST && \
    wget $URL/$ZIP -O $DST/$ZIP && \
    unzip $DST/$ZIP -d $DST && \
    rm $DST/$ZIP && \
    cd $DST && \
    mv JBrowse-1.11.6 jbrowse && \
    cd jbrowse && \
    ./setup.sh

#    ./configure && \
#    make && \
#    make install && \
#    cp /usr/local/lib/libjbrowse-2.0.* /lib/x86_64-linux-gnu/ && \
#    cd / && \
#    rm -rf $DST/$FOLDER

# Change user to back to biodocker
#USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /home/biodocker/jbrowse

# DEFINE DEFAULT COMMAND
CMD ["python", "-m", "SimpleHTTPServer", "8000"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

