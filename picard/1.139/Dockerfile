#################################################################
# Dockerfile
#
# Version:          1
# Software:         picard
# Software Version: 1.139
# Provides:         picard 1.139
# Tags:             Genomics
# Base Image:       biodckr/biodocker
# Build Cmd:        docker build --rm -t biodckrdev/picard 1.139/.
# Pull Cmd:         docker pull biodckrdev/picard
# Run Cmd:          docker run --rm -it biodckrdev/picard <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker

################## BEGIN INSTALLATION ######################

ENV ZIP=picard-tools-1.139.zip
ENV URL=https://github.com/broadinstitute/picard/releases/download/1.139/
ENV FOLDER=picard-tools-1.139
ENV DST=/home/biodocker/bin/

RUN wget $URL/$ZIP -O $DST/$ZIP && \
    unzip $DST/$ZIP -d $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    mv * .. && \
    cd / && \
    bash -c 'echo -e "#!/bin/bash\njava -jar '$DST'/picard.jar \$@" > '$DST'/picard' && \
    chmod +x $DST/picard && \
    rm -rf $DST/$FOLDER

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["picard"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>

