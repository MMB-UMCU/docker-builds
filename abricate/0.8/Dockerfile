# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=0.8
LABEL software="Abricate"
LABEL software.version=${VERSION}
LABEL description="Contig screening for AMR and virulence genes"
LABEL webstie="https://github.com/tseemann/abricate"
LABEL license="https://github.com/tseemann/abricate/blob/master/LICENSE"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    abricate=${VERSION}

RUN conda clean -afy