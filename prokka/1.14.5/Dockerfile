# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=1.14.5
LABEL software="Prokka"
LABEL software.version=${VERSION}
LABEL description="Rapid prokaryotic genome annotation"
LABEL webstie="https://github.com/tseemann/prokka"
LABEL license="https://github.com/tseemann/prokka/blob/master/doc/LICENSE.Prokka"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    prokka=${VERSION}

RUN conda clean -afy