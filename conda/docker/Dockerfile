FROM python:3-slim

ARG GIT_REPO
ARG GIT_FOLDER
ARG PATH_TO_ENVFILE

RUN apt-get update \
    && apt-get install git-core curl bzip2 -y --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && git clone ${GIT_REPO} /${GIT_FOLDER} \
    && curl https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && bash /tmp/miniconda.sh -b -p $HOME/miniconda \
    && rm /tmp/miniconda.sh \
    && /bin/bash -c "echo -e '\nexport PATH=$HOME/miniconda/bin:$PATH' >> $HOME/.bashrc" \
    && . $HOME/.bashrc && conda update conda -y \
    && cd /${GIT_FOLDER} && conda env create -f ${PATH_TO_ENVFILE} --name myenv

CMD cd /${GIT_FOLDER} && $HOME/miniconda/envs/myenv/bin/jupyter lab --ip 0.0.0.0 --port 8888 --no-browser --allow-root --NotebookApp.token=''
