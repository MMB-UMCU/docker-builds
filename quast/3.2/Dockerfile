# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=3.2
LABEL software="Quast"
LABEL software.version=${VERSION}
LABEL description="Genome assembly quality assessment"
LABEL webstie="https://github.com/ablab/quast"
LABEL license="https://github.com/ablab/quast/blob/master/LICENSE.txt"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    quast=${VERSION} python=2.7

RUN conda clean -afy