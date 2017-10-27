# Base Image
FROM biocontainers/biocontainers:latest

# Metadata
LABEL base.image="biocontainers:latest"
LABEL version="3"
LABEL software="STAR"
LABEL software.version="2.5.3a"
LABEL description="RNA-seq aligner"
LABEL website="https://github.com/alexdobin/STAR"
LABEL documentation="https://github.com/alexdobin/STAR/blob/master/doc/STARmanual.pdf"
LABEL license="http://www.gnu.org/licenses/"
LABEL BIOTOOLS="https://bio.tools/star"
LABEL tags="RNA-seq"

# Maintainer
MAINTAINER Roberto Vera Alvarez <r78v10a07@gmail.com>

USER biodocker

ENV ZIP=2.5.3a.tar.gz
ENV URL=https://github.com/alexdobin/STAR/archive/
ENV FOLDER=STAR-2.5.3a
ENV DST=/tmp

RUN wget $URL/$ZIP -O $DST/$ZIP && \
	tar xzf $DST/$ZIP -C $DST && \
	mv $DST/$FOLDER/bin/Linux_x86_64_static/* /home/biodocker/bin/ && \
	rm -rf $DST/$ZIP

WORKDIR /data/

CMD ["STAR"]
