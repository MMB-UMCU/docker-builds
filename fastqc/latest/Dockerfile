# Base image
FROM continuumio/miniconda3

# Container metadata
LABEL container.version="0"
LABEL base.image="continuumio/miniconda3"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="rsilvame@umcutrecht.nl"

# Software metadata
LABEL software="FastQC"
LABEL software.version="latest"
LABEL description="Quality control of high throughput sequence data"
LABEL webstie="https://github.com/s-andrews/FastQC"
LABEL license="https://github.com/s-andrews/FastQC/blob/master/LICENSE"

# Installation
ENV PYTHONDONTWRITEBYTECODE=true
RUN conda config --add channels bioconda

RUN conda install -c bioconda --yes --freeze-installed \
    nomkl \
    fastqc

RUN conda clean -afy