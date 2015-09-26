#################################################################
# Dockerfile
#
# Version:          1
# Software:         vcftools
# Software Version: 0.1.14
# Provides:         vcftools 0.1.14
# Tags:             Genomics
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/vcftools 0.1.14/.
# Pull Cmd:         docker pull biodckrdev/vcftools
# Run Cmd:          docker run --rm -it biodckrdev/vcftools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN apt-get update && \
    apt-get install -y \
      pkg-config && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*



ENV ZIP=vcftools-0.1.14.tar.gz
ENV URL=https://github.com/vcftools/vcftools/releases/download/v0.1.14/
ENV FOLDER=vcftools-0.1.14
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
CMD ["vcftools"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

