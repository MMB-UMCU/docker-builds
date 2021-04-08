FROM continuumio/miniconda3

# Container metadata
LABEL base.image="continuumio/miniconda3"
LABEL container.version="0.1.0"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="R.SilvaMeneses@umcutrecht.nl"

# Software metadata
ARG VERSION="docker"
LABEL software="bactofidia"
LABEL software.version=${VERSION}
LABEL description="Snakemake workflow for microbial WGS assembly and basic analysis"
LABEL website="https://gitlab.com/aschuerch/bactofidia"
LABEL license="https://gitlab.com/aschuerch/bactofidia/blob/${VERSION}/LICENSE.txt"

# Install general dependencies
RUN apt-get update && apt-get install -y wget

# Set up conda channels
RUN conda config --add channels defaults &&\
    conda config --add channels bioconda &&\
    conda config --add channels conda-forge

# Install snakemake
RUN conda install mamba &&\
    mamba install snakemake=5.14.0

# Install bactofidia
RUN wget https://gitlab.com/aschuerch/bactofidia/-/archive/docker/bactofidia-${VERSION}.tar.gz &&\
    tar -xzvf bactofidia-${VERSION}.tar.gz &&\
    rm -rf bactofidia-${VERSION}.tar.gz &&\
    mv bactofidia-${VERSION} /opt/bactofidia

# Setup environment
RUN ln -s /opt/bactofidia/* /usr/bin/. &&\
    mkdir /data

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

WORKDIR /data
