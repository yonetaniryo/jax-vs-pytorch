FROM nvidia/cuda:11.4.1-devel-ubuntu18.04

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y update && apt-get -y install --no-install-recommends software-properties-common libgl1-mesa-dev
RUN add-apt-repository -y ppa:deadsnakes/ppa && apt-get -y install --no-install-recommends python3.9 python3.9-distutils python3-pip python3.9-venv python3.9-tk

# change default python
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.9 1

# clear cache
RUN rm -rf /var/lib/apt/lists/*

RUN pip3 install -U pip distlib setuptools

WORKDIR /workspace

SHELL ["/bin/bash", "-c"]
COPY docker/entrypoint.sh /
ENTRYPOINT /bin/bash /entrypoint.sh