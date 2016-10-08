FROM taewanme/jupyter-javascript:latest
MAINTAINER Taewan Kim <taewanme@gmail.com>

USER root

RUN apt-get install -y libX11-6


USER jovyan

RUN pip install numpy && \
 pip install matplotlib
