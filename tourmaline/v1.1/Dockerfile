# Base image qiime2-2022.2
FROM quay.io/qiime2/core:2022.2

# Container metadata
LABEL base.image=" qiime2-2022.2"
LABEL container.version="1.0.0"
LABEL maintainer="Malbert R.C. Rogers"
LABEL maintainer.email="M.R.C.Rogers-2@umcutrecht.nl"


# Software metadata
LABEL software="Tourmaline MMB UMCU"
LABEL description="UMC Utrecht MMB's QIIME 2 pipeline based on Tourmaline Snakemake workflow"
LABEL website="https://gitlab.com/malbert.rogers/tourmaline.git"
LABEL license="https://gitlab.com/malbert.rogers/tourmaline.git/license"


# Set up bash environment: aliases, colors, history
RUN echo "alias cd..='cd ..'" >> ~/.bashrc
RUN echo "alias l='ls --color'" >> ~/.bashrc
RUN echo "alias la='ls -a --color'" >> ~/.bashrc
RUN echo "alias lal='ls -alh --color'" >> ~/.bashrc
RUN echo "alias ll='ls -lh --color'" >> ~/.bashrc
RUN echo "alias rm='rm -i'" >> ~/.bashrc
RUN echo "alias taill='ls -lrt | tail'" >> ~/.bashrc
RUN echo "bind '\"\e[A\": history-search-backward'" >> ~/.bashrc
RUN echo "bind '\"\e[B\": history-search-forward'" >> ~/.bashrc


# Install dependencies using apt-get
RUN apt-get update -y && \
 apt-get install -y \
 build-essential \
 apt-utils \
 nano \
 unzip \
 pandoc && \
 rm -rf /var/lib/apt/lists/*


RUN R -e "install.packages(c('BiocManager'), dependencies=TRUE, repos='http://cran.rstudio.com/')" && \
    R -e "BiocManager::install(c('msa', 'odseq'))"


RUN pip install git+https://github.com/biocore/empress.git && \
    pip install tabview && \
    pip install tabulate && \
    pip install biopython
RUN qiime dev refresh-cache


# Add conda installation dir to $PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/qiime2-2022.2/bin:$PATH


# This is necessary to install snakemake using conda
SHELL ["conda", "run", "-n", "qiime2-2022.2", "/bin/bash", "-c"]


# Install snakemake and other dependencies using conda
RUN conda update -n base -c defaults conda
RUN conda install -c conda-forge -c bioconda snakemake=7.6.2
RUN conda install -c bioconda muscle
RUN conda install -c bioconda clustalo
RUN conda install -c conda-forge deicode


WORKDIR /data

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
