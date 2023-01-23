FROM ubuntu:18.04

# Adapted Dockerfile from Biobakery for Metaphlan version 4.0.2 docker image
# also install python version 2 used by bowtie2
RUN apt-get update && \
    DEBIAN_FRONTEND="noninteractive" apt-get install -y python python-dev python3 python3-dev python3-pip apt-transport-https openjdk-8-jre wget zip git-all zlib1g-dev libbz2-dev liblzma-dev libjpeg-dev
RUN pip3 install boto3 cloudpickle awscli

RUN pip3 install anadama2

RUN apt-get install -y bowtie2
RUN apt-get install -y python3.8
RUN pip3 install numpy
RUN pip3 install cython
RUN pip3 install biom-format

# install cmseq
RUN pip3 install cmseq
RUN pip3 install metaphlan==4.0.4

# Not installing database since this is already present on our HPC (keeps size of image significantly smaller)
#RUN metaphlan --install --nproc 24 

WORKDIR /tmp
