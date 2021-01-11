# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=37.62
LABEL software="BBMap"
LABEL software.version="37.62"
LABEL description="Adapter and quality trimming of FastQ files"
LABEL webstie="https://sourceforge.net/project/bbmap"
LABEL license="https://github.com/BioInfoTools/BBMap/blob/master/license.txt"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    bbmap=${VERSION}

RUN conda clean -afy
