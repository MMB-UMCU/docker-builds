# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=0.6.2
LABEL software="TrimGalore"
LABEL software.version="0.6.2"
LABEL description="Adapter and quality trimming of FastQ files"
LABEL webstie="https://github.com/FelixKrueger/TrimGalore"
LABEL license="https://github.com/FelixKrueger/TrimGalore/blob/master/LICENSE"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    trim-galore=${VERSION} \
    pigz=2.4 \
    python=3.6

RUN conda clean -afy
