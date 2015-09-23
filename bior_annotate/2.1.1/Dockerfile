#################################################################
# Dockerfile
#
# Version:          1
# Software:         BioR annotate
# Software Version: 2.1.1
# Base Image:       biodckrdev/bior_annotate
# Build Cmd:        docker build --rm -t biodckrdev/bior_annotate 2.1.1/.
# Pull Cmd:         docker pull biodckrdev/bior_annotate
# Run Cmd:          docker run --rm -it biodckrdev/bior_annotate bash
#################################################################

# Set the base image to Ubuntu
FROM biodckr/biodocker:latest

################## BEGIN INSTALLATION ######################

#####################################################
# Install system wide libraries
#####################################################
USER root

RUN apt-get update && \
    apt-get install -y \
      libncurses5-dev \
      libncursesw5-dev && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


#####################################################
# Install htslib
#####################################################
RUN ZIP=htslib-1.2.1.tar.bz2 && \
    FOLDER=htslib-1.2.1 && \
    DST=/tmp && \
    wget https://github.com/BioDocker/software-archive/releases/download/htslib/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    make && \
    make install && \
    cd / && \
    rm -rf $DST/$FOLDER


#####################################################
# Install SAMtools
#####################################################
RUN ZIP=samtools-1.2.tar.bz2 && \
    FOLDER=samtools-1.2 && \
    DST=/tmp && \
    wget https://github.com/BioDocker/software-archive/releases/download/samtools/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    make && \
    make install && \
    cd / && \
    rm -rf $DST/$FOLDER


#####################################################
# Get BEDtools
#####################################################
RUN ZIP=bedtools-2.25.0.tar.gz && \
    FOLDER=bedtools2 && \
    DST=/tmp && \
    wget https://github.com/arq5x/bedtools2/releases/download/v2.25.0/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    make && \
    make install && \
    cd / && \
    rm -rf $DST/$FOLDER


#####################################################
# Install SNPEFF
#####################################################
USER biodocker

RUN ZIP=snpEff_v4_1k_core.zip && \
    FOLDER=snpEff && \
    DST=/home/biodocker/bin && \
    wget https://github.com/BioDocker/software-archive/releases/download/snpEff/$ZIP -O $DST/$ZIP && \
    unzip $DST/$ZIP -d $DST && \
    rm $DST/$ZIP && \
    bash -c 'echo -e "#!/bin/bash\njava -jar '$DST/$FOLDER'/snpEff.jar  \$@" > '$DST'/snpeff' && \
    chmod +x $DST/snpeff && \
    bash -c 'echo -e "#!/bin/bash\njava -jar '$DST/$FOLDER'/SnpSift.jar \$@" > '$DST'/snpsift' && \
    chmod +x $DST/snpsift

ENV PATH=$PATH:/home/biodocker/bin/snpEff/scripts:/home/biodocker/bin/snpEff/scripts/gsa


#####################################################
# Install perl modules
#####################################################
USER root

RUN cpan -i Data::Dumper Getopt::Long List::MoreUtils Switch 


#####################################################
# Install Cava
#####################################################
RUN pip install pysam==0.8.3

# Change user to back to biodocker
USER biodocker

RUN ZIP=cava-full-v1.1.1.tgz && \
    FOLDER=cava-v1.1.1 && \
    DST=/home/biodocker/bin && \
    wget https://github.com/BioDocker/software-archive/releases/download/cava/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    sed -i -e 's#human_g1k_v37.fasta#'$DST/$FOLDER'/human_g1k_v37.fasta#;s#hg19.fa#'$DST/$FOLDER'/hg19.fa#;s#exome_65_GRCh37.gz#'$DST/$FOLDER'/exome_65_GRCh37.gz#;s#dbSNP138.gz#.#' $DST/$FOLDER/config.txt && \
    cd / && \
    rm -rf $DST/$FOLDER

ENV PATH=$PATH:/home/biodocker/bin/cava-v1.1.1/


#####################################################
# Install BIOR
#####################################################
RUN ZIP=bior_2.1.1.tar.gz && \
    FOLDER=bior_2.1.1 && \
    DST=/home/biodocker/bin && \
    wget https://github.com/BioDocker/software-archive/releases/download/BioR/$ZIP -O $DST/$ZIP && \
    tar xvzf $DST/$ZIP -C $DST && \
    rm -f $DST/$ZIP && \
    echo "export BIOR_LITE_HOME=$DST/$FOLDER" > $DST/$FOLDER/PKG_PROFILE && \
    ln -s $DST/$FOLDER/bin/* $DST/$FOLDER

ENV BASEDIR=/home/biodocker/bin/bior_2.1.1
ENV FOLDER=/home/biodocker/bin/bior_2.1.1
ENV BIOR_LITE_HOME=$BASEDIR
ENV PATH=$PATH:$BIOR_LITE_HOME/bin

COPY annotate/ /home/biodocker/bin/annnotate/

ENV PATH=$PATH:/home/biodocker/bin/annnotate/scripts/

# Change user to back to biodocker
USER biodocker

# CHANGE WORKDIR TO /DATA
WORKDIR /data

# DEFINE DEFAULT COMMAND
CMD ["bash"]

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Saulo Alves Aflitos <sauloal@gmail.com>
