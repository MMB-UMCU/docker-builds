# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=3.11.1
LABEL software="SPAdes"
LABEL software.version=${VERSION}
LABEL description="Genome assembly"
LABEL webstie="https://github.com/ablab/spades"
LABEL license="GPLv2"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    spades=${VERSION} python=3.7

RUN conda clean -afy