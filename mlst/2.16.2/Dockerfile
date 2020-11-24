# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
ENV VERSION=2.16.2
LABEL software="MLST"
LABEL software.version=${VERSION}
LABEL description="Contig scan against PubMLST typing schemes"
LABEL webstie="https://github.com/tseemann/mlst"
LABEL license="https://github.com/tseemann/mlst/blob/master/LICENSE"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    mlst=${VERSION}

RUN conda clean -afy