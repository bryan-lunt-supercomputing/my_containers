FROM uiuccs484parallelprog/cs484_base:latest

MAINTAINER Bryan Lunt <bjlunt2@illinois.edu>

RUN curl -sSL https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && bash /tmp/miniconda.sh -bf -p /opt/conda \
    && rm -rf /tmp/miniconda.sh \
    && . /opt/conda/etc/profile.d/conda.sh \
    && conda activate base \
    && conda update conda \
    && conda install -y python=3.6 \
    && ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh \
    && echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc \
    && echo "conda activate base" >> ~/.bashrc


ENV PATH /opt/conda/bin:$PATH

RUN (conda config --add channels r) \
    && conda config --add channels defaults \
    && conda config --add channels conda-forge \
    && conda config --add channels bioconda 
