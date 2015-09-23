#################################################################
# Dockerfile
#
# Version:          1
# Software:         snpEff
# Software Version: 4.1k
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckr/snpeff 4.1k/.
# Pull Cmd:         docker pull biodckr/snpeff
# Run Cmd:          docker run --rm biodckr/snpeff <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

# Change user to root
USER root

################## BEGIN INSTALLATION ######################
RUN apt-get update && \
    apt-get install -y \
      openjdk-7-jre && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Change user to back to biodocker
USER biodocker

RUN ZIP=snpEff_v4_1k_core.zip && \
    wget https://github.com/BioDocker/software-archive/releases/download/snpEff/$ZIP -O /tmp/$ZIP && \
    unzip /tmp/$ZIP -d /home/biodocker/bin/ && \
    rm /tmp/$ZIP && \
    bash -c 'echo -e "#!/bin/bash\njava -jar /home/biodocker/bin/snpEff/snpEff.jar \$@" > /home/biodocker/bin/snpeff' && \
    chmod +x /home/biodocker/bin/snpeff && \
    bash -c 'echo -e "#!/bin/bash\njava -jar /home/biodocker/bin/snpEff/SnpSift.jar \$@" > /home/biodocker/bin/snpsift' && \
    chmod +x /home/biodocker/bin/snpsift

ENV PATH=$PATH:/home/biodocker/bin/snpEff/scripts:/home/biodocker/bin/snpEff/scripts/gsa

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["snpeff"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

