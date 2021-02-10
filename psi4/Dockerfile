FROM ubuntu:18.04

RUN apt-get update && apt-get install -y wget \
    build-essential \
    clang \
    git \ 
    gdb \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && apt-get autoremove -y

ENV PATH="/usr/local/miniconda3/bin:${PATH}"
ARG PATH="/usr/local/miniconda3/bin:${PATH}"
RUN wget \
    https://repo.anaconda.com/miniconda/Miniconda3-py37_4.9.2-Linux-x86_64.sh \ 
    && bash Miniconda3-py37_4.9.2-Linux-x86_64.sh -p /usr/local/miniconda3 -b \
    && rm -f Miniconda3-py37_4.9.2-Linux-x86_64.sh 
RUN conda --version

RUN conda install -c psi4 -c conda-forge psi4 jupyter 

RUN ldconfig

ENTRYPOINT bash
