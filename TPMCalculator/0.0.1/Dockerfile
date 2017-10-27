# Base Image
FROM biocontainers/biocontainers:latest

# Metadata
LABEL base.image="biocontainers:latest"
LABEL version="3"
LABEL software="TPMCalculator"
LABEL software.version="0.0.1"
LABEL description="This program calculates the TPM (Transcript per Millions) values for the exons and introns from NGS RNA-Seq aligned reads (BAM files)"
LABEL website="https://github.com/r78v10a07/TPMCalculator"
LABEL documentation="https://github.com/r78v10a07/TPMCalculator"
LABEL license="http://www.gnu.org/licenses/"
LABEL tags="RNA-seq"

# Maintainer
MAINTAINER Roberto Vera Alvarez <r78v10a07@gmail.com>

USER biodocker

ENV URL=https://github.com/r78v10a07/TPMCalculator
ENV DEP=https://github.com/pezmaster31/bamtools
ENV FOLDER=TPMCalculator
ENV DEPFOLDER=/home/biodocker/
ENV DST=/tmp
ENV BAMTOOLS_DIR=/home/biodocker/usr
ENV CPPFLAGS="-I $BAMTOOLS_DIR/local/include/bamtools"
ENV LDFLAGS="-L $BAMTOOLS_DIR/local/lib -Wl,-rpath,$BAMTOOLS_DIR/local/lib"

RUN cd $DST && \
	git clone $URL && \
	cd $FOLDER && \
	git clone https://github.com/pezmaster31/bamtools && \
	cd bamtools && mkdir build && cd build && \
	cmake .. && make && \
	make DESTDIR=$DEPFOLDER install && \
	cd $DST/$FOLDER && \
	make && \
	mv $DST/$FOLDER/bin/* /home/biodocker/bin/ && \
	rm -rf $DST/$FOLDER

WORKDIR /data/

CMD ["TPMCalculator"]
