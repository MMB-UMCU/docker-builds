FROM continuumio/miniconda3

# Container metadata
LABEL base.image="continuumio/miniconda3"
LABEL container.version="1.0.0"
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

RUN conda install mamba
RUN mamba install snakemake=5.14.0

# Install bactofidia
RUN wget https://gitlab.com/aschuerch/bactofidia/-/archive/docker/bactofidia-${VERSION}.tar.gz &&\
    tar -xzvf bactofidia-${VERSION}.tar.gz &&\
    rm -rf bactofidia-${VERSION}.tar.gz &&\
    mv bactofidia-${VERSION} bactofidia &&\
    cp -r bactofidia /opt/bactofidia

# Setup environment
RUN ln -s /opt/bactofidia/*.sh /usr/bin/. &&\
    ln -s /opt/bactofidia/Snakefile.assembly /usr/bin/.
#    ln -sf /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh

#RUN cp ~/.bashrc ~/.bash_conda_env
#RUN echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bash_condaenv
#RUN echo "conda activate base" >> ~/.bash_condaenv

#ENV BASH_ENV="~/.bash_condaenv"
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN cd bactofidia
#ENTRYPOINT ["/bin/bash"]
