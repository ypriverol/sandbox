# Base Image
FROM biocontainers/biocontainers:latest

# Metadata
LABEL base.image="biocontainers:latest"
LABEL version="3"
LABEL software="bamtools"
LABEL software.version="2.4.1"
LABEL description="C++ API & command-line toolkit for working with BAM data"
LABEL website="https://github.com/pezmaster31/bamtools"
LABEL documentation="https://github.com/pezmaster31/bamtools/wiki"
LABEL license="https://github.com/pezmaster31/bamtools/blob/master/LICENSE"
LABEL tags="BAM"

# Maintainer
MAINTAINER Roberto Vera Alvarez <r78v10a07@gmail.com>

USER biodocker

ENV ZIP=v2.4.1.tar.gz
ENV URL=https://github.com/pezmaster31/bamtools/archive
ENV FOLDER=bamtools-2.4.1
ENV INSTALL_FOLDER=/home/biodocker/
ENV DST=/tmp
ENV LD_LIBRARY_PATH=$INSTALL_FOLDER/lib/bamtools:$LD_LIBRARY_PATH

RUN cd $DST && \
	wget $URL/$ZIP -O $DST/$ZIP && \
	tar xzfv $DST/$ZIP -C $DST && \
	cd $DST/$FOLDER && mkdir build && cd build && \
	cmake -DCMAKE_INSTALL_PREFIX=$INSTALL_FOLDER .. && make && \
	make install && \
	rm -rf $DST/$FOLDER $DST/$ZIP

WORKDIR /data/

CMD ["bamtools"]
