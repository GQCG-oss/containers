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
    https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && bash Miniconda3-latest-Linux-x86_64.sh -p /usr/local/miniconda3 -b \
    && rm -f Miniconda3-latest-Linux-x86_64.sh 
RUN conda --version

ENV LIBINT_DATA_PATH=/usr/local/miniconda3/share/libint/2.6.0/basis
ARG LIBINT_DATA_PATH=/usr/local/miniconda3/share/libint/2.6.0/basis
RUN conda install -c conda-forge -c intel -c gqcg openmp=8.0.1 cmake=3.19.6 boost-cpp=1.75.0 eigen=3.3.9 blas=2.15 pybind11=2.6.2 benchmark=1.5.2 numpy=1.20.1 jupyter=1.0.0 libint=2.6.0 cint=3.0.17 mkl-include=2021.1.1 mkl-static=2021.1.1 intel-openmp=2021.1.1 doxygen=1.9.1 graphviz=2.42.3
RUN pip install -U jupyter-book

RUN ldconfig

ENTRYPOINT bash
