# project_name

## Build (New to Project)
If base image is uncached expect:
- Build time: couple minutes
- Space: couple gigabytes
```
docker build --rm -t vanillin:1.0 .
```

## Run JupyterLab
```
docker run --rm -p 10000:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/work vanillin:1.0
```

### Refs
- https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html#quick-start
