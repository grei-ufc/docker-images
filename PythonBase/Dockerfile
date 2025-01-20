# Esta imagem tem como objetivo servir de base para os projetos do GREI
# desenvolvidos em liguagem de programação Python.
#
#   O que esta imagem faz?
# 
#   - usa uma imagem ubuntu:24.04 como base, 
#   - atualiza os respositorios do ubuntu, 
#   - instala alguns comandos uteis para se ter em um container ubuntu de desenvolvimento,
#   - faz o Download do arquivo de instalacao do anaconda (miniconda),
#   - realiza a instalacao do anaconda,
#   - seta o PATH para reconhecer o comando `anaconda`,
#   - remove o arquivo de instalacao do anaconda, 
#   - executa o comando `anaconda` para testar a instalacao.
#
# Esta imagem está disponível no registry Docker Hub:
# - No seguinte link: `https://hub.docker.com/r/lucassmelo/python-base-image`
# - Via terminal de comandos via: `docker pull lucassmelo/python-base-image` 


# Use a base image
FROM ubuntu:24.04

# Set environment variables for non-interactive installation
ENV DEBIAN_FRONTEND=noninteractive

# Install required packages
RUN apt-get update && apt-get install -y \
    wget \
    bzip2 \
    build-essential \
    git \
    && apt-get clean

# Download Anaconda installer
# RUN wget https://repo.anaconda.com/archive/Anaconda3-2023.07-1-Linux-x86_64.sh -O /tmp/anaconda.sh
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/anaconda.sh

# Install Anaconda
RUN bash /tmp/anaconda.sh -b -p /opt/anaconda

# Set PATH environment variable
ENV PATH="/opt/anaconda/bin:$PATH"

# Clean up
RUN rm /tmp/anaconda.sh

# Test installation
RUN conda --version
