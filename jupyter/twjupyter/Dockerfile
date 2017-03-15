FROM ubuntu:16.04
MAINTAINER Taewan Kim <taewanme@gmail.com>

RUN apt-get update \
  &&  apt-get install -y curl apt-utils git make build-essential            \
              libssl-dev libffi-dev zlib1g-dev libbz2-dev libreadline-dev libcurl4-openssl-dev  \
              libsqlite3-dev python-pip python3-pip libjpeg8-dev python-dev r-base \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip \
 && pip2 install --upgrade pip \
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

RUN pip install tensorflow
RUN pip3 install tensorflow


RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -  \
    && apt-get install -y nodejs libzmq3-dev libcurl4-openssl-dev \
    && npm install -g ijavascript \
    && npm install -g underscore-node  \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash -N -u 1000 taewan

COPY start-notebook.sh /usr/local/bin
RUN chmod 755 /usr/local/bin/start-notebook.sh \
    && chown -R taewan  /usr/local/bin/start-notebook.sh



RUN Rscript -e "install.packages(c(\"devtools\", \"testthat\", \"roxygen2\"), repos = c(\"http://irkernel.github.io/\", \"http://cran.rstudio.com\"))" \
            -e "library(devtools)" \
            -e "install_github('IRkernel/repr')" \
            -e "install_github('IRkernel/IRdisplay')"
RUN Rscript -e "library(devtools)" -e "install_github('IRkernel/IRkernel')"

USER taewan
RUN Rscript -e "IRkernel::installspec()"


RUN mkdir -p /home/taewan/.jupyter
RUN (echo "c.NotebookApp.ip = '0.0.0.0'" && \
     echo "c.NotebookApp.open_browser = False" && \
     echo "from IPython.lib import passwd" && \
     echo "import os" && \
     echo "c.NotebookApp.password = passwd('Welcome1')") \
     > /home/taewan/.jupyter/jupyter_notebook_config.py


RUN python3 -m ipykernel install --user \
    && ijs --ijs-install-kernel

RUN cp -rf /home/taewan/.local/share/jupyter/kernels/python3 /home/taewan/.local/share/jupyter/kernels/python2 \
  &&  sed -i 's/python3/python/g' /home/taewan/.local/share/jupyter/kernels/python2/kernel.json \
  &&  sed -i 's/Python 3/Python 2/g' /home/taewan/.local/share/jupyter/kernels/python2/kernel.json



VOLUME ["/home/taewan/notebooks"]
WORKDIR /home/taewan
ENV PASSWORD jupyter
EXPOSE 8888
