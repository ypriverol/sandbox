#################################################################
# Dockerfile
#
# Version:          1
# Software:         bowtie
# Software Version: 1.2
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/bowtie 1.1.2/.
# Pull Cmd:         docker pull biodckrdev/bowtie
# Run Cmd:          docker run --rm biodckrdev/bowtie <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

#RUN apt-get update && \
#    apt-get install -y \
#      libncurses5-dev \
#      libncursesw5-dev && \
#    apt-get clean && \
#    apt-get purge && \
#    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN ZIP=bowtie-1.1.2-linux-x86_64.zip && \
    FOLDER=bowtie-1.1.2 && \
    DST=/home/biodocker/bin && \
    wget https://github.com/BioDocker/software-archive/releases/download/bowtie/$ZIP -O $DST/$ZIP && \
    unzip $DST/$ZIP -d $DST && \
    rm $DST/$ZIP && \
    mv $DST/$FOLDER/* $DST && \
    rmdir $DST/$FOLDER

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["bowtie"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

