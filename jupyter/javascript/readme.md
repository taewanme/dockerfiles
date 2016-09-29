# Dockerfile for Jupyter image with JavaScript Kernel.

-This project maintains dockerfile developed by Taewan.kim

- docker images
  - Jupyter Image is installed of Node.js Kernel
    - The images could be used for documentation of programming with node.js and ES6
    - Volume: /home/jovyan/work/data 
    - Port: 8888

- the command for running container

```bash
docker run -itd -p 8888:8888 \
  -v <host_path>:/home/jovyan/work/data \
   --name jupyter taewanme/jupyter:1.0 startJupyter.sh
```

- How to access the jupyter web site
  - http://localhost:8888

