# project_name

## Build (New to Project)
If base image is uncached expect:
- Build time: couple minutes
- Space: couple gigabytes
```
docker build --rm -t docker_image_name .
```

## Run JupyterLab
```
docker run --rm -p 10000:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/work docker_image_name
```

### Refs
- https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html#quick-start