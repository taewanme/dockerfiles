FROM ubuntu:16.04
MAINTAINER Taewan Kim <taewanme@gmail.com>

RUN apt-get update \
  &&  apt-get install -y curl apt-utils git make build-essential            \
              libssl-dev libffi-dev zlib1g-dev libbz2-dev libreadline-dev   \
              libsqlite3-dev python-pip python3-pip libjpeg8-dev python-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade pip \
 && python3 -m pip install --upgrade pip \
 && pip install numpy               \
 && pip install pillow              \
 && pip install matplotlib          \
 && pip install scikit-learn        \
 && pip install Pandas              \
 && pip install scrapy              \
 && pip install NLTK                 \
 && pip install bokeh                \
 && pip install NetworkX             \
 && pip install --no-cache-dir scipy \
 && pip install Seaborn         \
 && pip3 install numpy          \
 && pip3 install pillow         \
 && pip3 install matplotlib     \
 && pip3 install scikit-learn   \
 && pip3 install Pandas         \
 && pip3 install scrapy         \
 && pip3 install NLTK           \
 && pip3 install bokeh          \
 && pip3 install NetworkX       \
 && pip3 install scipy          \
 && pip3 install Seaborn        \
 && pip install ipython[all]    \
 && pip install jupyter         \
 && pip3 install ipykernel

ENV TFPY  https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.11.0rc1-cp27-none-linux_x86_64.whl
ENV TFPY3 https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.11.0rc1-cp35-cp35m-linux_x86_64.whl
RUN  pip3 install --upgrade ${TFPY3}
#RUN pip install --upgrade ${TFPY}


RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -  \
    && apt-get install -y nodejs libzmq3-dev \
    && npm install -g ijavascript \
    && npm install -g underscore-node  \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash -N -u 1000 taewan

COPY start-notebook.sh /usr/local/bin
RUN chmod 755 /usr/local/bin/start-notebook.sh \
    && chown -R taewan  /usr/local/bin/start-notebook.sh

USER taewan

RUN python3 -m ipykernel install --user \
    && ijs --ijs-install-kernel

RUN cp -rf /home/taewan/.local/share/jupyter/kernels/python3 /home/taewan/.local/share/jupyter/kernels/python2 \
  &&  sed -i 's/python3/python/g' /home/taewan/.local/share/jupyter/kernels/python2/kernel.json \
  &&  sed -i 's/Python 3/Python 2/g' /home/taewan/.local/share/jupyter/kernels/python2/kernel.json

EXPOSE 8888
VOLUME ["/home/taewan/ipython"]
WORKDIR /home/taewan
