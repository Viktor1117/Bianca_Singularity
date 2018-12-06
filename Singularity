#!/bin/bash
# 
# Tru Huynh <tru@pasteur.fr>
# 2017/10/26: initial version
# use as baseline to build a container from anaconda

BootStrap: docker
From: continuumio/anaconda

%runscript
echo "This is what happens when you run the container..."
export PATH=/opt/conda/bin:${PATH}
/bin/bash

%post
export PATH=/opt/conda/bin:${PATH}
echo "Hello from inside the container"
conda update -y conda
conda update --all
conda list > /conda.txt

conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda

conda install -c bioconda mummer4 samtools bwa picard
conda install -c bioconda abyss

touch /`date -u -Iseconds`

%labels
MAINTAINER truatpasteurdotfr
