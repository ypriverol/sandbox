#################################################################
# Dockerfile
#
# Version:          1
# Software:         bwa
# Software Version: 1.2
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/bwa 0.7.12/.
# Pull Cmd:         docker pull biodckrdev/bwa
# Run Cmd:          docker run --rm biodckrdev/bwa <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN ZIP=bwakit-0.7.12_x64-linux.tar.bz2 && \
    FOLDER=bwa.kit && \
    DST=/home/biodocker/bin && \
    wget https://github.com/BioDocker/software-archive/releases/download/bwa/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP --strip-components=1 -C $DST && \
    rm $DST/$ZIP

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["bwa"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

