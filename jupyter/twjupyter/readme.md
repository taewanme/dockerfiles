# Dockerfile of Jupyter image for Taewanme
-This project maintains dockerfile developed by Taewan.kim

## Docker Image
- Jupyter Image has following component
  - Node.js Kernel
  - Python 2 Kernel
  - Python 3 Kernel
  - Python Components
    - numpy (for python 2.7 & 3.5)
    - pillow (for python 2.7 & 3.5)
    - matplotlib (for python 2.7 & 3.5)
    - scikit-learn (for python 2.7 & 3.5)
    - Pandas (for python 2.7 & 3.5)
    - scrapy (for python 2.7 & 3.5)
    - NLTK (for python 2.7 & 3.5)
    - bokeh (for python 2.7 & 3.5)
    - NetworkX (for python 2.7 & 3.5)
    - scipy (for python 2.7 & 3.5)
    - Seaborn (for python 2.7 & 3.5)
    - Tensorflow (for python 2.7 & 3.5)

- the command for running this container.

```bash
docker run -itd -p 8888:8888 \
-v <host_path>:/home/taewan/ipython \
--name jupyter taewanme/twjupyter start-notebook.sh
```

- How to access to the jupyter web application
  - http://localhost:8888
