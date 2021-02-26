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

Don't have `vanillin` alias installed? Add to `zsh` [here](https://github.com/zachbogart/vanillin#vanillin).

***

# Vanillin

Get coding using community Jupyter containers ("regular cola", 😀) just the way you like 'em ("vanilla cola", 🤩).

Makes it easier to work with Jupyter Docker containers, simplifying commands and providing a nice project template.

## 0. Add vanillin alias

Add this alias function to `~/.zshrc`. Makes it easier to build/run docker images for a given project

```
# vanillin: alias for docker build/run JupyterLab
# https://github.com/zachbogart/vanillin
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
        echo "$EMOJI    Build \`cool_image_name\` from pwd Dockerfile"
        echo "$EMOJI     and run JupyterLab on the result, on port 10000"
        echo "$EMOJI"
        echo "$EMOJI    1. \`vanillin cool_image_name\`"
        echo "$EMOJI    2. \`vanillin cool_image_name 10000\`"
        echo "$EMOJI"
    fi
}
```

#### Usage
```
🍦
🍦 Usage:
🍦
🍦  vanillin name
🍦    Alias for: `docker build --rm -t name .`
🍦    - Shorthand for building image from pwd Dockerfile
🍦
🍦  vanillin name port
🍦    Alias for: `docker run --rm -p port:8888 -e JUPYTER_ENABLE_LAB=yes -v $PWD:/home/jovyan/work name`
🍦    - Shorthand for running JupyterLab
🍦
🍦  -- Example --
🍦
🍦    Build `cool_image_name` from pwd Dockerfile
🍦     and run JupyterLab on the result, on port 10000
🍦
🍦    1. `vanillin cool_image_name`
🍦    2. `vanillin cool_image_name 10000`
🍦
```

## 1. Use repo as a Template

Can use this repo as a template for a new project. Simply:

1. Rename `IMAGE_NAME` at the top to specify how you want to title your local images for this project
2. Remove Doc info from this README (info after first line break)
3. Ready to Go!

*** 

### What is this?

**A template** for making projects that use Jupyter Docker Images to run JupyterLab and **an alias for zsh** to make it easier to build/run the images.

Process
- Template has Dockerfile, builds off of [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/) base images, adding anything specified for custom build
- Run new image, accessing [JupyterLab](https://jupyterlab.readthedocs.io/)
- Includes nice alias function to avoid having to type really long docker commands

### What the `docker run` Command Does

This command is explained in the [Jupyter Docker Stacks Quickstart](https://jupyter-docker-stacks.readthedocs.io/en/latest/#quick-start), Example 3

### Further Reading

- [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/): Main documentation for "ready-to-run Docker images containing Jupyter applications and interactive computing tools". This explains all the ins-and-outs regarding the image setup, versioning schema, setting up additional features, etc.
- [Image Selection](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html): All docker images available on DockerHub, used as starting point for this repo. Can easily find image by filtering for given type, links to DockerHub.

***

Made with 💖
