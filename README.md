# Vanillin

Get coding using community Jupyter containers ("regular cola", 😀) just the way you like 'em ("vanilla cola", 🤩).

## Run JupyterLab

Run one line to use JupyterLab environment with any custom preferences built-in:

```
docker run --rm -p 10000:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/work zachbogart/vanillin:v1.1
```

### What the Command Does

This command is explained in the [Jupyter Docker Stacks Quickstart](https://jupyter-docker-stacks.readthedocs.io/en/latest/#quick-start), Example 3

In this case, `zachbogart/vanillin` (with the provided tag after the colon) is built off of a base docker image provided by the Jupyter Docker Stacks. Any additional setup is included in the Dockerfile and the result is pushed to DockerHub, which is used to run a container. So running the command will pull the base image if not already available locally, add any custom stuff, and start JupyterLab.

## Use as Template

Can use this repo as a template for a new project. Includes Dockerfile, can clone and build it locally if that's your preference.

## What is Vanillin?

Dear me,

Hi future me! (and "the internet")

- I realize I spend a lot of time just setting things up rather than working on something cool
- Hopefully this will smooth some of that out

It's super simple, but super useful. This is just taking the lovingly crafted [Jupyter Docker containers](https://jupyter-docker-stacks.readthedocs.io/en/latest/) and setting them up how I like them (include some packages, etc). This will evolve over time, but it will make it easy to just grab a setup I'm used to and go. Worry less about dependencies and environments and focus more on learning new coding things: Jupyter notebooks for everything, one command away.

As preferences/needs change, can update this repo with an updated Dockerfile (different preferences off of existing base images), add a new git tag (`v[0-9.]*`) and create different releases. These are then built using DockerHub, so the setup can travel no matter where you are, and you can use the release that suits your fancy.

You can find [published releases](https://github.com/zachbogart/vanillin/releases) and go from there or [visit DockerHub](https://hub.docker.com/r/zachbogart/vanillin) to see all published images.

Stop setting things up. Start coding.

Sincerely,

Past Me

*** 

### Further Reading

- [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/): Main documentation for "ready-to-run Docker images containing Jupyter applications and interactive computing tools". This explains all the ins-and-outs regarding the image setup, versioning schema, setting up additional features, etc.
- [Image Selection](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html): All docker images available on DockerHub, used as starting point for this repo. Can easily find image by filtering for given type, links to DockerHub.

***

Made with 💖