# Dockerfile of Jupyter image for Taewanme
-This project maintains dockerfile developed by Taewan.kim

## Docker Image
- Jupyter Image has following component
  - Node.js Kernel
  - Python Lib
    - numpy
    - matplotlib

- the command for running container

```bash
docker run -itd -p 8888:8888 \
-v <host_path>:/home/jovyan/work/data \
--name jupyter taewanme/twjupyter:1.0 startJupyter.sh
```

- How to access the jupyter web site
  - http://localhost:8888
   
