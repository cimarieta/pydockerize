# pydockerize
Creating docker containers for Python usage with Jupyter notebooks

Run [jupyterlab](https://jupyterlab.readthedocs.io/en/stable/)


## Requirements

* [Docker](://docs.docker.com/install/)

* a git repository with a conda environment file (`yaml` file)

* `jupyterlab` must be listed as a dependency in the conda environment file


## Building the image

Run the command below to build the image, replacing the variables with the appropriate names:

```bash
cd conda/docker && docker build -t <IMAGE_NAME>:<VERSION> --build-args GIT_REPO=<GIT_REPO> --build-args PATH_TO_ENVFILE=<PATH_TO_ENVFILE> .
```

If running this command is successful, your image with `<IMAGE_NAME>` and version `<VERSION>` should be shown
after running the command `docker images`.


### Pushing the image to [Docker Hub]()

Pushing the image to Docker Hub requires a login and password to `Docker Hub`. You may find it useful to read the instructions found in [this step-by-step guide](https://ropenscilabs.github.io/r-docker-tutorial/04-Dockerhub.html).


## Running the container and getting access to _jupyterlab_

Run the command below to run the container:

```bash
docker run --rm -p 8888:8888 <IMAGE_NAME>:<VERSION>
```

After successfully running this command, you may access the jupyter notebook by opening the address `0.0.0.0:8888` in your favorite browser.
