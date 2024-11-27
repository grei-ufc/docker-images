# Use uma imagem base do Ubuntu
FROM ubuntu:24.04

# Defina o modo não interativo para evitar prompts durante a instalação
ENV DEBIAN_FRONTEND=noninteractive

# Atualizar pacotes e instalar dependências
RUN apt-get update && apt-get install -y \
    wget \
    bzip2 \
    build-essential \
    && apt-get clean

# Baixar e instalar o Anaconda

# RUN wget https://repo.anaconda.com/archive/Anaconda3-2023.07-1-Linux-x86_64.sh -O /tmp/anaconda.sh
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/anaconda.sh && \
    bash /tmp/anaconda.sh -b -p /opt/anaconda && \
    rm /tmp/anaconda.sh

# Adicionar Anaconda ao PATH
ENV PATH="/opt/anaconda/bin:$PATH"

# Criar um ambiente virtual chamado "mosaik-env" e instalar o pacote mosaik
RUN conda create -y -n mosaik-env python=3.10 && \
    conda run -n mosaik-env pip install mosaik

# Ativar o ambiente por padrão no container
RUN echo "source activate mosaik-env" >> ~/.bashrc

# Configurar o diretório de trabalho
WORKDIR /app

# Expor portas, caso necessário (por exemplo, para APIs ou servidores)
EXPOSE 8000

# Entrar no shell com o ambiente ativado por padrão
CMD ["/bin/bash"]
