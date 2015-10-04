#################################################################
# Dockerfile
#
# Version:          1
# Software:         abyss
# Software Version: 1.9.0
# Description:      Assembly By Short Sequences - a de novo, parallel, paired-end sequence assembler
# Website:          http://www.bcgsc.ca/platform/bioinfo/software/abyss|https://github.com/bcgsc/abyss/
# Tags:             Genomics
# Provides:         sparsehash 2.0.2|abyss 1.9.0
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/abyss 1.9.0/.
# Pull Cmd:         docker pull biodckrdev/abyss
# Run Cmd:          docker run --rm -it biodckrdev/abyss <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

# Change user to root
USER root

RUN apt-get update && \
    apt-get install -y \
      libboost-all-dev \
      sqlite3          \
      libsqlite3-dev   \
    && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*



ENV ZIP=sparsehash-2.0.2.tar.gz
ENV URL=https://github.com/sparsehash/sparsehash/archive
ENV FOLDER=sparsehash-sparsehash-2.0.2
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



ENV ZIP=abyss-1.9.0.tar.gz
ENV URL=https://github.com/bcgsc/abyss/releases/download/1.9.0
ENV FOLDER=abyss-1.9.0
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
CMD ["abyss-pe"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

