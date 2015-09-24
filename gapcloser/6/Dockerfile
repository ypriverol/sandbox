#################################################################
# Dockerfile
#
# Version:          1
# Software:         gapcloser
# Software Version: 6
# Provides:         gapcloser 6
# Tags:             Genomics
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/gapcloser 6/.
# Pull Cmd:         docker pull biodckrdev/gapcloser
# Run Cmd:          docker run --rm biodckrdev/gapcloser <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

#https://github.com/BioDocker/software-archive/releases/download/gapcloser/GapCloser-bin-v1.12-r6.tgz
ENV ZIP=GapCloser-bin-v1.12-r6.tgz
ENV URL=https://github.com/BioDocker/software-archive/releases/download/gapcloser
ENV DST=/home/biodocker/bin

RUN wget $URL/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["GapCloser"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

