FROM python:3.6-buster

# Container metadata
LABEL base.image="python:3.6-buster"
LABEL container.version="0.1"
LABEL maintainer="Rodrigo Meneses"
LABEL maintainer.email="R.SilvaMeneses@umcutrecht.nl"

# Software metadata
ARG VERSION="1.0"
LABEL software="DeepVirFinder"
LABEL software.version=${VERSION}
LABEL description="Identifying viruses from metagenomic data by deep learning "
LABEL website="https://github.com/jessieren/DeepVirFinder"
LABEL license="https://github.com/jessieren/DeepVirFinder/blob/6a823fbb5e554a8347df5c136af51d96168e77e5/licence.md"

# These are dependencies of DeepVirFinder
RUN pip3 install --upgrade pip && pip install \
    numpy \
    theano==1.0.3 \
    keras==2.2.4 \
    scikit-learn \
    Biopython \
    h5py==2.10.0 \
    mkl
    
# Install DeepVirFinder
RUN wget https://github.com/jessieren/DeepVirFinder/archive/refs/heads/master.zip && \
    unzip master.zip -d /opt && \
    rm -rf master.zip && \
    mv /opt/DeepVirFinder-master /opt/DeepVirFinder && \
    chmod +x /opt/DeepVirFinder/*.py &&\
    mkdir /data

# Setup environment
ENV PATH="/opt/DeepVirFinder:${PATH}" \
    LC_ALL=C.UTF-8 \
    LANG=C.UTF-8

WORKDIR /data