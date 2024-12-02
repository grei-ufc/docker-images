# Use a base image
FROM ubuntu:24.04

# Set environment variables for non-interactive installation
ENV DEBIAN_FRONTEND=noninteractive

# Install required packages
RUN apt-get update && apt-get install -y \
    wget \
    bzip2 \
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
