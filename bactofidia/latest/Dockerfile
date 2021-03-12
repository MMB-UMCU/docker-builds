FROM ubuntu:xenial

# Container metadata
LABEL base.image="ubuntu:xenial"
LABEL container.version="0.0.0"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="R.SilvaMeneses@umcutrecht.nl"

# Software metadata
ARG VERSION="master"
LABEL software="bactofidia"
LABEL software.version=${VERSION}
LABEL description="Snakemake workflow for microbial WGS assembly and basic analysis"
LABEL website="https://gitlab.com/aschuerch/bactofidia"
LABEL license="https://gitlab.com/aschuerch/bactofidia/blob/${VERSION}/LICENSE.txt"

# Install general dependencies
RUN apt-get update && apt-get install -y wget

# Install miniconda
RUN wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh &&\
    bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda3 -b &&\
    rm -f Miniconda3-latest-Linux-x86-64.sh

ENV PATH=/miniconda3/bin:${PATH}

RUN conda config --add channels defaults &&\
    conda config --add channels bioconda &&\
    conda config --add channels conda-forge

# Install bactofidia
RUN wget https://gitlab.com/aschuerch/bactofidia/-/archive/master/bactofidia-${VERSION}.tar.gz &&\
    tar -xzvf bactofidia-${VERSION}.tar.gz &&\
    rm -rf bactofidia-${VERSION}.tar.gz &&\
    mv bactofidia-${VERSION} bactofidia &&\
    cd bactofidia

# Singularity compatibility
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

WORKDIR /bactofidia
