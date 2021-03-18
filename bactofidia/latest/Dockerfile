FROM continuumio/miniconda3

# Container metadata
LABEL base.image="continuumio/miniconda3"
LABEL container.version="0.0.1"
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

# Set up conda channels
RUN conda config --add channels defaults &&\
    conda config --add channels bioconda &&\
    conda config --add channels conda-forge

# Install bactofidia
RUN wget https://gitlab.com/aschuerch/bactofidia/-/archive/master/bactofidia-${VERSION}.tar.gz &&\
    tar -xzvf bactofidia-${VERSION}.tar.gz &&\
    rm -rf bactofidia-${VERSION}.tar.gz &&\
    mv bactofidia-${VERSION} /opt/bactofidia

RUN ln -s /opt/bactofidia/*.sh /usr/bin/. &&\
    ln -s /opt/bactofidia/Snakefile.assembly /usr/bin/.

# Singularity compatibility
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

# Workdir for Docker users
RUN mkdir /data
WORKDIR /data
