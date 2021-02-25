# project_template

### Run with vanillin 

Build image:
```
vanillin IMAGE_NAME
```

Run JupyterLab:
```
vanillin IMAGE_NAME 10000
```

Don't have `vanillin` alias installed? Add to `zsh` here.

***

# Vanillin

Get coding using community Jupyter containers ("regular cola", 😀) just the way you like 'em ("vanilla cola", 🤩).

## Add vanillin alias

Add this alias function to `~/.zshrc`. Makes it easier to build/run docker images for a given project

```
# vanillin: alias for docker build/run JupyterLab
vanillin() {
    EMOJI=🍦
    if [ "$#" = 1 ]
    then
        echo "$EMOJI"
        echo "$EMOJI Building image \"$1\" from this directory's Dockerfile..."
        echo "$EMOJI"

        docker build --rm -t "$1" .
    elif [ "$#" = 2 ]
    then
        echo "$EMOJI"
        echo "$EMOJI Opening JupyterLab from image \"$1\" on port $2"
        echo "$EMOJI"
        echo "$EMOJI http://localhost:$2"
        echo "$EMOJI"

        docker run --rm -p "$2":8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/work "$1"
    else
        echo "$EMOJI"
        echo "$EMOJI Usage:"
        echo "$EMOJI"
        echo "$EMOJI  vanillin name"
        echo "$EMOJI    Alias for: \`docker build --rm -t name .\`"
        echo "$EMOJI    - Shorthand for building image from pwd Dockerfile"
        echo "$EMOJI"
        echo "$EMOJI  vanillin name port"
        echo "$EMOJI    Alias for: \`docker run --rm -p port:8888 -e JUPYTER_ENABLE_LAB=yes -v "\$PWD":/home/jovyan/work name\`"
        echo "$EMOJI    - Shorthand for running JupyterLab"
        echo "$EMOJI"
        echo "$EMOJI  -- Example --"
        echo "$EMOJI"
        echo "$EMOJI    Build \`cool_image_name\` from Dockerfile and run JupyterLab of the result on port 10000"
        echo "$EMOJI"
        echo "$EMOJI    1. \`vanillin cool_image_name\`"
        echo "$EMOJI    2. \`vanillin cool_image_name 10000\`"
        echo "$EMOJI"
    fi
}
```

## Use as Template

Can use this repo as a template for a new project.

*** 

### What the `docker run` Command Does

This command is explained in the [Jupyter Docker Stacks Quickstart](https://jupyter-docker-stacks.readthedocs.io/en/latest/#quick-start), Example 3

In this case, `zachbogart/vanillin` (with the provided tag after the colon) is built off of a base docker image provided by the Jupyter Docker Stacks. Any additional setup is included in the Dockerfile and the result is pushed to DockerHub, which is used to run a container. So running the command will pull the base image if not already available locally, add any custom stuff, and start JupyterLab.

### Further Reading

- [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/): Main documentation for "ready-to-run Docker images containing Jupyter applications and interactive computing tools". This explains all the ins-and-outs regarding the image setup, versioning schema, setting up additional features, etc.
- [Image Selection](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html): All docker images available on DockerHub, used as starting point for this repo. Can easily find image by filtering for given type, links to DockerHub.

***

Made with 💖
